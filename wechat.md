- Start Date: 2019-05-10
- RFC PR: (留空)
- Issue: (留空)

# Summary 总结

用于快速接入微信JS-SDK

# Motivation 动机

内部项目，微信公众号开发，h5项目，需要对接微信扫一扫功能
期望能够通过简单的配置达到快速接入微信JS-SDK
在微信平台运行h5项目，希望能够使用一些微信提供的原生能力
每个项目都单独接入和维护，有点繁琐，还需要指导成本


# Detailed design 详细设计

## config 配置

通过设置配置，实现设置微信 config

```js
export default {
  plugins: [
    ['umi-plugin-wechat', {
        wechat:{
            'appId': 'xxx',
            'jsApiList': [], //设置所有想要使用的微信jsapi列表, 默认值为 ['scanQRCode', 'updateAppMessageShareData', 'updateTimelineShareData',]
            'serviceUri': '',
            'debug': true, //开启 debug 模式
            'isEnable': true, // 是否使用微信sdk，默认开启，用于将项目接入其他app时需要关闭，使用第三方app提供原生能力支持
        }
    }],
  ],
}
```

## runtime 运行时配置

在src/app.js里面暴露wechatReady接口，回调微信ready方法，也可以直接在页面中使用 `WeChat.ready(()=>{})`
不知道这是只调用一次还是调用多次，可以在wx.ready会掉之后，在启动项目，保证wx变量一定生效。

## 用法

在项目中，通过以下方式引入使用

```js
import { WeChat } from alita;
const { scanQRCode, updateAppMessageShareData, updateTimelineShareData, } = WeChat;
```

> 这里其实是 `import from umi`, 通过 `api.addUmiExports` 接口实现

# How We Teach This 用法推广

## 自定义“分享给朋友”及“分享到QQ”按钮的分享内容

```js
updateAppMessageShareData({
    title: '', // 分享标题
    desc: '', // 分享描述
    link: '', // 分享链接，该链接域名或路径必须与当前页面对应的公众号JS安全域名一致
    imgUrl: '', // 分享图标
    success: function () {
      // 设置成功
    }
})
```

## 自定义“分享到朋友圈”及“分享到QQ空间”按钮的分享内容

```js
updateTimelineShareData({
    title: '', // 分享标题
    link: '', // 分享链接，该链接域名或路径必须与当前页面对应的公众号JS安全域名一致
    imgUrl: '', // 分享图标
    success: function () {
      // 设置成功
    }
})
```

## 调起微信扫一扫接口

```js
scanQRCode({
    needResult: 0, // 默认为1，直接返回扫描结果，0则为扫描结果由微信处理
    scanType: ["qrCode","barCode"], // 可以指定扫二维码还是一维码，默认二者都有
    success: function (res) {
        var result = res.resultStr; // 当needResult 为 1 时，扫码返回的结果
    }
});
```

> 微信中 `needResult` 默认为0，为了方便项目使用，这里需要改成默认为1

# Drawbacks 缺点

接入微信SDK之后，只能在微信浏览器环境中打开项目
期望正常项目功能可以直接运行，只有在调用微信sdk的功能的时候给出错误提示
便于开发调试和其他的app的接入

# Supplementary 补充方案

可以考虑增加wxerror回调，当不是微信环境的时候，默认给出错误提示，
如果用户重新定义了wxerror，则调用用户定义的函数，可以在这里接入第三方的JS-Bridge

# 未解决的问题

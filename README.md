# Alita的业务支撑能力

umi 框架支撑能力，请提交到[umijs/rfcs](https://github.com/umijs/rfcs)
这里接收的是业务上的支撑需求，如 Cordova 支撑，快速接入微信，约定式的权限路由，业务组件

## Authorize 权限路由

### Summary 总结

用于约定式中的权限路由配置，在 Alita 中，可以通过新建 `src/Authority.js` 文件，默认所有的路由都会使用这个文件做鉴权

### Detailed design 详细设计

```js
export default {
  plugins: [
    ['umi-plugin-authorize', options],
  ],
}
```

### Realization 实现

[umi-plugin-authorize](https://www.npmjs.com/package/umi-plugin-authorize)

## Cordova

### Summary 总结

添加umi的Cordova支持，使umi的h5项目，能快速打包成原生App

### Detailed design 详细设计

在《前端一起学》里面写了，已经实现了，就没有再写一次了。

### Realization 实现

[umi-plugin-corodva](https://www.npmjs.com/package/umi-plugin-cordova)

## Wechat

### Summary 总结

快速接入微信JS-SDK

### Detailed design 详细设计

```js
export default {
  plugins: [
    ['umi-plugin-cordova', options],
  ],
}
```

详见 [Wechat](./wechat.md)

### Realization 实现

未实现

## 模版

### Summary 总结

### Detailed design 详细设计

### Realization 实现

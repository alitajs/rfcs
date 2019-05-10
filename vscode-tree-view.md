- Start Date: 2019-05-10
- RFC PR: (留空)
- Issue: (留空)

# Summary 总结

umi 的 VS Code 插件实现

# Motivation 动机

希望在 VS Code 的侧边面板中管理umi的一些文件和功能

# Detailed design 详细设计

在实际项目开发中，比较常用到的命令是 `umi g pages pageName`
希望通过可视化的方式，实现新建页面。
另外在umi约定式方案中，存在一些约定文件，对于，不是很熟悉umi的开发人员，很难记住全部的文件

| 文件路径 | 作用 |
|  :-  | :-:  |
| config/config.js | umi配置文件 |
| src/global.js | 全局js |
| src/global.less | 全局样式 |
| src/app.js | 运行时配置 |
| src/pages/document.ejs | 运行时配置 |
| layout/index.js | 运行时配置 |

> 以上js文件，都支持ts文件

期望通过tree view管理这个页面
如:

```sh
 ├── global files       (add btn)  // 约定文件 右侧有一个按钮
        ├── config/config.js       // umi配置文件
        ├── src/global.js           // 全局js
        ├── src/global.less                 // 全局样式
        ├── src/app.js                 // 运行时配置
        ├── src/pages/document.ejs                 // 运行时配置
        └── layout/index.js               // 运行时配置
```

> 右侧添加按钮说明：点击可以选择新增哪个文件，按语义化的方式选择，只能添加不存在的文件，如果所有的约定文件都存在，则隐藏该按钮

同样的在这个位置可以用来管理pages
同样的右侧有一个按钮，用于点击新建页面
同样的可以管理models和layouts


# How We Teach This 用法推广

可视化的用法，学习成本应该很低

# Drawbacks 缺点

# Alternatives 替代方案

umi ui

# 未解决的问题

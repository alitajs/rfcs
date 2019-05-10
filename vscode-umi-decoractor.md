- Start Date: 2019-05-10
- RFC PR: (留空)
- Umi Issue: (留空)

# Summary 总结

在VS Code中增加umi config 的提醒，类似[LintLens — ESLint rules made easier](https://marketplace.visualstudio.com/items?itemName=ghmcadams.lintlens)

# Motivation 动机

能够直接在配置文件中查看配置说明，提供配置项联想

# Detailed design 详细设计

通过 `setDecorations` 实现给当前行增加标注
可以在当前配置项的行内显示样式，点击配置项可以跳转到umi的官网。
在输入新的配置项的时候，提供单词联想和单词错误矫正

# How We Teach This 用法推广

提示优化，不需要学习成本

# Drawbacks 缺点

习惯了看这里之后，可能会很少查看官网，减少了官网和项目库的流量
官方文档修正，这里需要手动同步，感觉也是个大问题

# Alternatives 替代方案

自己查阅官方文档

# 未解决的问题

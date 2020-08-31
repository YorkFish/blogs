# flow

## 1. 用法

- 初始化变量

        start=>start: 开始
        end=>end: 结束
        operation=>operation: 操作
        condition=>condition: 条件

- 设置路径

        start->operation->condition

- 添加线路上的标记

        condition(yes)->end
        condition(no)->operation

## 2. 说明

- 代码语言填 **flow**

## 3. 效果

![](.\imgs\19-01_flow.png)

***

- 注
    - *MkDocs* 上默认不支持 *Markdown* 的“流程图”功能
    - 若想使用：需要安装额外的插件、需要借助 *H5* 标签
# GANTT

## 1.  用例

```
    gantt
            dateFormat  YYYY-MM-DD
            title Adding GANTT diagram functionality to mermaid
            section 现有任务
            已完成               :done,    des1, 2020-01-01, 2020-01-05
            进行中               :active,  des2, 2020-01-05, 3d
            计划一               :         des3, after des2, 5d
            计划二               :         des4, after des3, 5d
```

## 2. 说明

- 代码语言填 **mermaid**
- 此图被称为“甘特图”
- 若当前日期在图中范围之内，则甘特图中会以一条“细红线”表示当前日子

## 3. 效果

![](.\imgs\20-01_GANTT.png)

***

- 注
    - *MkDocs* 上默认不支持 *Markdown* 的“流程图”功能
    - 若想使用：需要安装额外的插件、需要借助 *H5* 标签

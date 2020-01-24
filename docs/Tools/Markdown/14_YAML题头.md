---
title:   [Markdown] 14 YAML 题头 <br>
date:    2020/01/05 <br>
tags:    Markdown <br>
summary: Markdown 进阶语法
---

# YMAL 题头

## 1. 用法

- 必须写在开头
- 用两行 `---` 包起来
- 里面是“属性名” + *1* 个英文冒号 + 空格（至少 *1* 个，可以多个） + 解释

## 2. 说明

- 也称为“YAML 标头”
- 是一种直观的能够被电脑识别的数据序列化格式
- 是一个可读性高并且容易被人类阅读，容易和脚本语言交互，用来表达资料序列的编程语言
- 不同的编辑器有所不同
    - 有的没有效果（因为不支持）
    - 有的没有换行（可以手动加 `<br>`）
    - 有的没有空格、制表效果

## 3. 示例与效果

- 示例

        ---
        title:   [Markdown] 03 进阶语法 第一弹
        date:    2019/04/25
        tags:    Markdown
        summary: Markdown 进阶语法
        ---

- 效果
    
    - 最上方那个长得像代码块的就是 *YAML*[^1] 题头

***

[^1]: "Yet Another Markup Language"
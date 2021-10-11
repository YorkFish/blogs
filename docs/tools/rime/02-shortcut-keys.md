## 8. 一些快捷键

```yaml
# default.custom.yaml
patch:
  # 其他配置...
  key_binder:
    bindings:
  - { when: has_menu, accept: "Control+k", send: Page_Up }
  - { when: has_menu, accept: "Control+j", send: Page_Down }
  - { when: has_menu, accept: "Control+h", send: Left }
  - { when: has_menu, accept: "Control+l", send: Right }
  - { when: has_menu, accept: ";", send: 2 }
```

| 选项 | 释义 |
| :--- | :--- |
| when   | 作用范围 |
| accept | 实际接受的按键 |
| send   | 输出效果 |
| toggle | 切换开关 |

- when 的候选项
    - paging 翻页
    - has_menu 操作候选项用
    - composing 操作输入码用
    - always 全域

- accept, send 除了字母和数字外，还包含键盘上实际的所有键

- toggle 的候选项
    - ascii_mode
    - ascii_punct
    - full_shape 全角字符
    - simplification 繁简
    - extended_charset

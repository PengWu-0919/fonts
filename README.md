# fonts

自用字体分发仓库。**只放字体文件，不放代码。**

## 用途

程序运行时按需下载字体，而不是把字体打包进 `.app`。
好处是应用更新时不重复下发字体（字体几乎不变），一次下载、长期复用。

## 文件

| 文件 | 字体 | 用途 |
|---|---|---|
| `Allo-Bold.otf` | [Allo](https://joshpuckett.me) Bold | 世界时钟「极光」主题数字 |
| `JetBrainsMonoNL-Bold.ttf` | [JetBrains Mono](https://github.com/JetBrains/JetBrainsMono) NL Bold | 世界时钟「流光」主题数字 |

`NL` = No Ligature，去掉编程连字，用于非代码场景更干净。

## 许可

两款字体均为 **SIL Open Font License 1.1**，可自由使用、修改、再分发。

- `LICENSE-Allo.txt` — Copyright 2026 Josh Puckett
- `LICENSE-JetBrainsMono.txt` — Copyright 2020 The JetBrains Mono Project Authors

按 OFL 要求，分发时须随附上述许可与版权声明。

## 直接下载

公开仓库，无需凭据：

```
https://raw.githubusercontent.com/PengWu-0919/fonts/main/Allo-Bold.otf
https://raw.githubusercontent.com/PengWu-0919/fonts/main/JetBrainsMonoNL-Bold.ttf
```

下载后注册到进程即可使用：

```swift
CTFontManagerRegisterFontsForURL(url as CFURL, .process, nil)
```

**注意**：PostScript 名与文件名不同，`NSFont(name:)` 要用字体内部的名字：

| 文件 | PostScript 名 |
|---|---|
| `Allo-Bold.otf` | `Allo-Bold` |
| `JetBrainsMonoNL-Bold.ttf` | `JetBrainsMonoNL-Bold` |

## 加新字体

1. 把字体文件和对应许可放进本仓库并推送
2. 确认其 PostScript 名（`fonttools` 或 CoreText 读取）
3. 在调用方的字体清单里加一条

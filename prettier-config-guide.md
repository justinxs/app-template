# Prettier 配置指南

Prettier 是流行的代码格式化工具，其配置选项涵盖了行宽、缩进、引号风格等众多方面。以下列出 Prettier 所有可配置项及其含义，并给出面向前端 TypeScript（含 React、Vue）的推荐配置及说明。

## 可配置项列表

| 配置项 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| `printWidth` | `number` | 80 | 每行最大字符数，超出将自动换行。 |
| `tabWidth` | `number` | 2 | 缩进空格数。 |
| `useTabs` | `boolean` | false | 是否使用 tab 替代空格缩进。 |
| `semi` | `boolean` | true | 语句结尾是否加分号。 |
| `singleQuote` | `boolean` | false | 字符串是否使用单引号。 |
| `jsxSingleQuote` | `boolean` | false | JSX 中是否使用单引号。 |
| `quoteProps` | `"as-needed"` \| `"consistent"` \| `"preserve"` | `"as-needed"` | 对象属性是否使用引号。 |
| `trailingComma` | `"none"` \| `"es5"` \| `"all"` | `"es5"` | 多行结构最后是否加逗号。 |
| `bracketSpacing` | `boolean` | true | 对象字面量中 `{}` 是否有空格。 |
| `bracketSameLine` | `boolean` | false | 将 `>` 符号放在多行元素最后一行的末尾（如 JSX）。 |
| `arrowParens` | `"avoid"` \| `"always"` | `"always"` | 箭头函数参数是否总是使用括号。 |
| `proseWrap` | `"always"` \| `"never"` \| `"preserve"` | `"preserve"` | Markdown 文本是否自动换行。 |
| `htmlWhitespaceSensitivity` | `"css"` \| `"strict"` \| `"ignore"` | `"css"` | HTML 空白敏感度。 |
| `vueIndentScriptAndStyle` | `boolean` | false | 是否缩进 Vue 文件中的 `<script>` 和 `<style>` 标签内的内容。 |
| `endOfLine` | `"auto"` \| `"lf"` \| `"crlf"` \| `"cr"` | `"lf"` | 行尾换行符风格。 |
| `embeddedLanguageFormatting` | `"auto"` \| `"off"` | `"auto"` | 是否格式化嵌入式代码块（如 markdown 中的 JS）。 |
| `singleAttributePerLine` | `boolean` | false | HTML/JSX 中每个属性是否单独一行。 |

## 推荐配置及说明

以下为面向前端 TypeScript 项目的推荐配置及原因：

```jsonc
{
  "printWidth": 100,               
  "tabWidth": 2,                   
  "useTabs": false,                
  "semi": true,                    
  "singleQuote": true,             
  "jsxSingleQuote": false,         
  "quoteProps": "as-needed",       
  "trailingComma": "all",          
  "bracketSpacing": true,          
  "bracketSameLine": false,        
  "arrowParens": "always",         
  "proseWrap": "preserve",         
  "htmlWhitespaceSensitivity": "css",
  "vueIndentScriptAndStyle": true, 
  "endOfLine": "lf",              
  "embeddedLanguageFormatting": "auto",
  "singleAttributePerLine": false  
}
```

### 推荐配置说明

- `printWidth: 100`：提升可读性，适配大多数显示器。
- `tabWidth: 2`：减少嵌套缩进导致的行变长。
- `useTabs: false`：统一使用空格以避免不同编辑器表现差异。
- `semi: true`：显式使用分号防止自动插入错误。
- `singleQuote: true`：更贴近 JavaScript 常见风格。
- `jsxSingleQuote: false`：保持 JSX 的 HTML 属性风格一致性（用双引号）。
- `quoteProps: "as-needed"`：只有必要时为属性加引号，保持简洁。
- `trailingComma: "all"`：多行结构中添加尾逗号，便于 diff。
- `bracketSpacing: true`：对象字面量添加空格，提高可读性。
- `bracketSameLine: false`：换行时 `>` 单独成行，易读易维护。
- `arrowParens: "always"`：一致性强，避免潜在歧义。
- `proseWrap: "preserve"`：保持原文格式，适合文档场景。
- `htmlWhitespaceSensitivity: "css"`：遵循 CSS 渲染规则，最直观。
- `vueIndentScriptAndStyle: true`：提升代码一致性和可读性。
- `endOfLine: "lf"`：跨平台统一换行符。
- `embeddedLanguageFormatting: "auto"`：启用嵌入语言自动格式化。
- `singleAttributePerLine: false`：减少冗余换行，适合小组件。

## 不推荐配置及原因

- `printWidth: 80`：过于保守，现代显示器已经支持更宽行。
- `semi: false`：可能引发 ASI 问题（自动插入分号错误）。
- `trailingComma: "none"`：修改结构时需手动维护逗号，增加 diff 噪声。
- `arrowParens: "avoid"`：在参数为单个标识符时省略括号，但不利于一致性。
- `endOfLine: "auto"`：不同平台换行符不一致，版本控制易产生 diff。
- `vueIndentScriptAndStyle: false`：脚本、样式块不缩进影响结构清晰度。

## 示例 `.prettierrc` 配置

```json
{
  "printWidth": 100,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": true,
  "jsxSingleQuote": false,
  "quoteProps": "as-needed",
  "trailingComma": "all",
  "bracketSpacing": true,
  "bracketSameLine": false,
  "arrowParens": "always",
  "proseWrap": "preserve",
  "htmlWhitespaceSensitivity": "css",
  "vueIndentScriptAndStyle": true,
  "endOfLine": "lf",
  "embeddedLanguageFormatting": "auto",
  "singleAttributePerLine": false
}
```

以上配置可直接复制到项目的 `.prettierrc` 文件中，确保团队代码风格的一致性，同时兼顾 React、Vue 等前端框架和 TypeScript 的特性。
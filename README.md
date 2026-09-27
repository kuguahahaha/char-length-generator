# 字符长度生成器

给测试工程师用的**长度边界测试数据生成器**。输入规范里的「长度要求」，一键生成正好卡边界的数据。

- **单文件、零依赖、可离线** —— 双击 HTML 就能用，不联网、不上传任何数据
- 记录保存在浏览器 `localStorage`（纯本地）

## 在线使用（GitHub Pages）

| 版本 | 入口 | 说明 |
|---|---|---|
| **极简版 v1.0** | [index.html](https://kuguahahaha.github.io/char-length-generator/) | 一个屏幕搞定，够用就够 |
| **完整版 v1.1** | [index-pro.html](https://kuguahahaha.github.io/char-length-generator/index-pro.html) | 带批量导入、批次管理、导出中心 |

## 两个版本怎么选

| 能力 | 极简版 v1.0 | 完整版 v1.1 |
|---|---|---|
| 字符类型 | vchar(byte) / ANC / N / uInt / 日期 / 金额 / 自定义 | 12 种（含 CHAR / C / AN / Int / Decimal / DATE / --） |
| 长度口径 | 字符数、GBK 字节、UTF-8 字节 | 同上 + 可切换，三口径实时并列显示 |
| 字节口径 | GBK / UTF-8 切换 | 同上 |
| 边界形态 | ±1 / 空值 / 全中文 / 全英文 / 特殊字符 / 首尾空格 | 11 种（含全 0 / 全 9 / 纯空格串 / NULL / 随机长度） |
| 语义模板 | — | 手机号 / 身份证 / 金额 / 日期 / 机构名称 / 地址 / 邮箱，按数据项名自动匹配 |
| 历史记录 | ✅ 500 条，可搜索 | ✅ 2000 条（可配），标签 / 备注 / 收藏 / JSON 备份 |
| 导出 | CSV | TSV / CSV / Markdown / HTML 表格 + 19 列自由勾选 + 导出前自检 |
| **批量粘贴整表导入** | — | ✅ 规范整表粘贴 → 一键生成整批 → 批次管理 |
| 文件大小 | 约 31 KB | 约 110 KB |

## 关于 Excel 粘贴「多一个空格」

两个版本都已处理：

1. 复制走**纯文本**通道（不经过富文本），内容首尾部无空格、无尾部换行
2. CSV 导出带 **UTF-8 BOM**，字段用双引号包裹，`\r\n` 换行，分隔符后不带任何空格
3. 完整版额外提供「复制到 Excel」——同时写入 `text/html` 紧凑表格 + TSV，Excel 直接按表格读取，绕开 CSV 解析；导出前还会逐格自检并剔除 `U+00A0` / `U+3000` / 零宽字符

## 下载

- [Releases 页面](https://github.com/kuguahahaha/char-length-generator/releases)
- [极简版 v1.0](https://github.com/kuguahahaha/char-length-generator/releases/download/v1.0/char-length-generator-v1.0.html)（约 31 KB）
- [完整版 v1.1](https://github.com/kuguahahaha/char-length-generator/releases/download/v1.1/char-length-generator-v1.1.html)（约 110 KB）

## 使用速查

| 规范里的写法 | 含义 |
|---|---|
| `vchar(180) byte` | 180 **字节**，GBK 下 90 个汉字、UTF-8 下 60 个汉字（按字符数则是 180 个汉字） |
| `N11` | 固定 11 位数字 |
| `ANC..100` | 最多 100 位字母数字汉字 |
| `uInt..15` | 最多 15 位无符号整数 |
| `decimal(18,2)` | 定点数值，18 位含 2 位小数 |
| `--` | 无长度要求，不需要做长度测试 |

## 更新日志

### v1.1（完整版）
- 新增**批量粘贴整表导入**：任意列数自动定位「长度要求」列，自动跳过表头，支持 Excel / Markdown / 多空格分隔
- 新增**批次管理**：批次命名、按批次筛选、整批导出、删除整批
- 新增多边界形态批量生成、导出列扩展（批次 / 边界形态，共 19 列）

### v1.0（极简版）
- 首版：类型选择、长度 / 字节双口径、边界快捷生成、历史记录与搜索、CSV 导出

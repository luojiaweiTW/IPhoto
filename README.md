## IPhoto - 照片水印

让你的照片，一键拥有专业感。IPhoto 是一款面向摄影爱好者与内容创作者的桌面级“照片加水印”工具，支持中文字体完美显示、圆角卡片风格、自动品牌 Logo、批量处理与可视化模板编辑。

> 仓库地址：[`luojiaweiTW/IPhoto`](https://github.com/luojiaweiTW/IPhoto)  
> 适配 Windows（Python 3.x + PyQt5 + Pillow）。


### 亮点特性

- 中文字体完美支持：自动匹配系统中文字体（含 .ttc），支持自定义 `font_path`
- 文本高级排版：自动换行、按宽度自适应字号、字距与行距、对齐（left/center/right）
- 专业观感增强：描边、阴影、半透明文本（RGBA 图层合成，彻底避免“白框/锯齿”）
- 圆角边框：任意模板可配置 `corner_radius`，即刻变身“卡片风”
- 自动品牌 Logo：依据 EXIF 识别品牌，自动放置对应 Logo（可自定义素材库）
- 预设模板开箱即用：内置 4 款常用风格，一键出片
- 可视化模板编辑器：拖拽/数值化调参，实时预览所见即所得
- 批量处理：文件夹全量生成，进度提示与失败列表
- 图像与元数据：导出 PNG/JPEG/TIFF，JPEG 保留 EXIF（含尺寸更新）
- RAW 友好：NEF/CR2/ARW… 优先使用内嵌 JPEG 预览并自动裁黑边（可选）


### 内置模板（示例）

1. 大标题+底栏（自动Logo）：顶部大中文标题，底部左右参数，底部居中品牌 Logo
2. 圆角卡片+品牌+参数：白色卡片风格，机型名+品牌标+参数行
3. 圆角卡片+模糊边框：使用模糊边框模拟投影，底部参数行
4. 品牌强调+大参数：品牌居中，下方大号参数

可在左侧“边框设置”直接调节：上/下/左/右边距、类型（纯色/渐变/模糊）、颜色与【圆角】数值。


### 快速开始

```bash
python -m venv .venv
.venv\Scripts\activate  # Windows
pip install -U pip
pip install PyQt5 Pillow piexif numpy

python main.py
```

- 首次运行如无 `config/templates.json`，会自动写入内置 4 款模板。
- 左侧面板可选择模板、调整边框/圆角与颜色、添加文字/图片元素；右侧实时预览；点“生成”导出。


### 文本元素高级参数（节选）

```json
{
  "type": "text",
  "content": "自动\\n水印相机",
  "area": "top-left",
  "x": 40,
  "y": 30,
  "align": "left",
  "font": "Arial",
  "size": 72,
  "bold": true,
  "color": "#FFFFFF",
  "opacity": 100,
  "stroke": { "enable": true, "width": 4, "color": "#000000" },
  "shadow": { "enable": true, "offset": 3, "color": "#000000", "opacity": 60 },

  "max_width": 900,           // 自动换行 & 宽度限制
  "auto_wrap": true,
  "fit_to_width": false,      // 按宽度自适应字号（需配合 max_width）
  "min_size": 16,
  "letter_spacing": 2,        // 字距（px）
  "line_spacing": 8           // 行距附加（px）
}
```


### 边框与圆角

```json
{
  "border": {
    "top": 160,
    "bottom": 200,
    "left": 160,
    "right": 160,
    "type": "solid",          // solid | gradient | blur
    "color": "#FFFFFF",
    "corner_radius": 24       // 圆角半径（px）
  }
}
```


### 提示与常见问题

- 字体显示为方块/缺字
  - 在文本元素里加入 `font_path` 指向你随项目分发的中文字体（如思源黑体）。
  - Windows 系统自带字体路径：`C:/Windows/Fonts/`（支持 .ttf / .ttc）。

- 半透明文字出现白边/锯齿
  - 已采用 RGBA 图层合成与 `alpha_composite`，无需额外设置；如遇第三方插件另作处理，请关闭其后处理。

- 批量导出命名冲突
  - 目标目录存在同名文件时自动加序号后缀。


### 适配与打包

- 运行环境：Windows 10/11，Python 3.8+，PyQt5，Pillow，piexif，numpy（可选）
- 打包建议：PyInstaller（需把中文字体与模板文件放到资源目录，启动时用相对路径加载）


### 开源协议

- 本项目以 MIT 许可开源，你可自由用于个人/商用项目（保留版权声明）。


### 相关链接

- 项目仓库：[`https://github.com/luojiaweiTW/IPhoto`](https://github.com/luojiaweiTW/IPhoto)

如果你喜欢这款“照片水印”，欢迎 Star、提 Issue/PR，一起把它打磨成更好用的出片利器！



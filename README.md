# PageOfYanxh — 严旭铧的个人简历网站

基于 [MkDocs](https://www.mkdocs.org/) + [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 搭建的个人简历静态网站，部署于 GitHub Pages，自定义域名 [randomyanxh.top](http://randomyanxh.top)。

---

## 📁 项目结构

```
mypage/
├── mkdocs.yml              # 网站配置文件（主题、导航、插件等）
├── notes/                  # docs_dir，所有 Markdown 内容
│   ├── index.md            # 主页（简历首页）
│   ├── project1_ecg.md     # 项目详情：心电监测设备
│   ├── project2_wind.md    # 项目详情：风电功率时序预测
│   ├── project3_simulation.md  # 项目详情：硬件在环仿真平台
│   ├── student_work.md     # 学生工作详情
│   ├── about.md            # 备用页面
│   ├── CNAME               # 自定义域名配置
│   ├── assets/             # 图片资源（按项目分子文件夹存放）
│   ├── javascripts/
│   │   └── mathjax.js      # MathJax 数学公式渲染配置
│   └── stylesheets/
│       └── extra.css       # 自定义 CSS 样式
├── docs/                   # 其他静态资源（暂留）
├── site/                   # 编译输出目录（已 gitignore，勿手动修改）
├── Lib/                    # uv 虚拟环境依赖（已 gitignore）
├── Scripts/                # uv 虚拟环境脚本（已 gitignore）
└── .gitignore
```

---

## 🚀 在新设备上部署

### 1. 克隆项目

```bash
git clone https://github.com/Random-Yanxh/PageOfYanxh.git
cd PageOfYanxh/mypage
```

### 2. 创建并激活虚拟环境（推荐使用 uv）

```bash
# 安装 uv（如果未安装）
pip install uv

# 在 mypage 目录下初始化虚拟环境
uv venv

# 激活虚拟环境（Windows PowerShell）
.venv\Scripts\activate
# 或 Linux / macOS
# source .venv/bin/activate
```

### 3. 安装依赖

```bash
uv pip install mkdocs mkdocs-material
```

### 4. 本地预览

```bash
mkdocs serve --livereload
```

打开浏览器访问 [http://127.0.0.1:8000](http://127.0.0.1:8000) 即可实时预览。

---

## 📤 部署到 GitHub Pages

```bash
mkdocs gh-deploy
```

该命令会自动构建网站并推送到 `gh-pages` 分支，GitHub Pages 会随即更新你的网站。

> 部署成功后访问：[http://randomyanxh.top](http://randomyanxh.top)

---

## ✏️ 日常编辑流程

1. 编辑 `notes/` 下对应的 Markdown 文件（可用 VS Code 配合 MkDocs 实时预览）。
2. 图片资源放入 `notes/assets/<子文件夹>/`，在 Markdown 中用相对路径引用。
3. 编辑完成后，提交变更：
   ```bash
   git add -A
   git commit -m "描述你的变更内容"
   git push origin main
   ```
4. 部署更新：
   ```bash
   mkdocs gh-deploy
   ```

---

## 📐 数学公式支持

本网站已配置 MathJax，支持标准 LaTeX 语法：

- **行内公式**：`$公式$`
- **块公式**：
  ```markdown
  $$
  公式内容
  $$
  ```

---

## ⚙️ 关键配置说明

| 配置项 | 说明 |
|---|---|
| `docs_dir: notes` | 内容目录为 `notes/` 而非默认的 `docs/` |
| `theme: material` | 使用 Material for MkDocs 主题 |
| `extra_css` | 自定义样式文件路径相对于 `docs_dir` |
| `extra_javascript` | MathJax 配置，文件和 CDN 均已配置 |
| `CNAME` | 放于 `notes/CNAME`，用于 GitHub Pages 自定义域名绑定 |

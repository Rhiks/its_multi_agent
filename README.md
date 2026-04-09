# ITS Multi-Agent 知识平台

这是一个包含前后端的完整知识平台项目。当前项目尚在开发中，后端包含知识数据爬虫，前端包含用于展示和交互的 Vue 3 界面层。

## 项目结构

```text
its_multi_agent/               # 项目根目录
├── backend/                   # 🐍 后端代码目录
│   └── knowledge/             # 知识系统核心逻辑
│       ├── cli/               # 命令行程序 (主要产物是 crawl_cli.py，用于爬取数据)
│       ├── config/            # 配置文件目录 (存放 settings 相关的定义)
│       ├── data/              # 数据存储目录 (存放爬取到的 markdown 知识文件)
│       ├── repositories/      # 存储层逻辑 (文件读写等)
│       ├── services/          # 核心业务逻辑实现 (crawler 爬虫服务、解析服务等)
│       ├── utils/             # 工具类 (文本清洗等通用函数)
│       ├── test/              # 单元测试代码目录
│       └── requirements.txt   # Python 依赖清单
└── front/                     # 🌐 前端代码目录
    └── knowlege_platform_ui/  # 前端 Vue 项目
        ├── src/               # 前端核心源码 (包含页面、组件、路由、API 封装)
        ├── package.json       # Node.js 项目配置文件及依赖
        └── vite.config.js     # 前端构建工具 Vite 的配置
```

## 环境准备

- **Node.js**: 用于运行 Vue 3 前端项目 (推荐 LTS 版本)。
- **Python**: 用于运行后端逻辑。
- **uv**: Python 的依赖和环境管理工具，本项目强制使用 `uv` 运行 Python 代码。

## 如何运行项目

### 1. 运行前端 (Vue 3 界面)

前端是一个标准的基于 Vite 构建的 Vue 3 项目。通过 Node.js 环境及 NPM 进行管理。

```bash
# 1. 切换到前端目录
cd ./its_multi_agent/front/knowlege_platform_ui

# 2. 安装项目依赖包
npm install

# 3. 启动开发服务器
npm run dev
```

启动完成后，将出现本地服务地址（例如：`http://localhost:5173`），在浏览器中打开即可查看前端系统。

### 2. 运行后端 (Python 爬虫)

本项目要求使用 `uv` 工具进行环境管理。当前后端主要功能为其爬虫脚本，负责拉取外部知识并转换为 `Markdown` 文档。

```bash
# 1. 切换到后端目录
cd ./its_multi_agent/backend/knowledge

# 2. 从 requirements.txt 安装依赖包
uv pip install -r requirements.txt

# 3. 运行爬虫脚本
uv run python cli/crawl_cli.py
```

执行期间，输出窗口将展示爬取进度并将解析生成的 Markdown 文档存储至设定的 `data` 工作目录中。

## 下一步计划
- 接入 FastAPI/Flask 实现规范的后端 API 接口。
- 持久化打通前后端数据交互机制。

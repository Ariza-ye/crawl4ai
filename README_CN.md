# 🚀🤖 Crawl4AI：开源 LLM 友好型网络爬虫与抓取工具

<div align="center">

<a href="https://trendshift.io/repositories/11716" target="_blank"><img src="https://trendshift.io/api/badge/repositories/11716" alt="unclecode%2Fcrawl4ai | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>

[![GitHub Stars](https://img.shields.io/github/stars/unclecode/crawl4ai?style=social)](https://github.com/unclecode/crawl4ai/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/unclecode/crawl4ai?style=social)](https://github.com/unclecode/crawl4ai/network/members)

[![PyPI version](https://badge.fury.io/py/crawl4ai.svg)](https://badge.fury.io/py/crawl4ai)
[![Python Version](https://img.shields.io/pypi/pyversions/crawl4ai)](https://pypi.org/project/crawl4ai/)
[![Downloads](https://static.pepy.tech/badge/crawl4ai/month)](https://pepy.tech/project/crawl4ai)
[![GitHub Sponsors](https://img.shields.io/github/sponsors/unclecode?style=flat&logo=GitHub-Sponsors&label=Sponsors&color=pink)](https://github.com/sponsors/unclecode)

---
#### 🚀 Crawl4AI 云端 API — 封闭测试版（即将发布）
可靠、大规模的网络数据提取，现已构建为比现有任何解决方案**大幅降低成本**的选择。

👉 **点击[此处](https://forms.gle/E9MyPaNXACnAMaqG7)申请提前体验**  
_我们将分阶段上线，并与早期用户密切合作。名额有限。_

---

<p align="center">
    <a href="https://x.com/crawl4ai">
      <img src="https://img.shields.io/badge/Follow%20on%20X-000000?style=for-the-badge&logo=x&logoColor=white" alt="关注 X" />
    </a>
    <a href="https://www.linkedin.com/company/crawl4ai">
      <img src="https://img.shields.io/badge/Follow%20on%20LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="关注 LinkedIn" />
    </a>
    <a href="https://discord.gg/jP8KfhDhyN">
      <img src="https://img.shields.io/badge/Join%20our%20Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="加入 Discord" />
    </a>
  </p>
</div>

Crawl4AI 将网络内容转化为简洁、LLM 就绪的 Markdown，适用于 RAG、智能体和数据管道。快速、可控，经过 50k+ Star 社区的实战检验。

[✨ 查看最新更新 v0.8.6](#-最新更新)

✨ **v0.8.6 新特性**：安全热修复——由于 PyPI 供应链遭到入侵，已将 `litellm` 替换为 `unclecode-litellm`。如果您使用的是 v0.8.5，请立即升级。

✨ 近期 v0.8.5：反机器人检测、Shadow DOM 支持及 60+ 项 Bug 修复！自动三级反机器人检测（含代理升级）、Shadow DOM 扁平化、深度爬取取消、配置默认值 API、同意弹窗移除及关键安全补丁。[发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.8.5.md)

✨ 之前 v0.8.0：崩溃恢复与预取模式！深度爬取崩溃恢复（支持 `resume_state` 与 `on_state_change` 回调），适用于长时间运行的爬取任务。新增 `prefetch=True` 模式，URL 发现速度提升 5-10 倍。[发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.8.0.md)

✨ 之前 v0.7.8：稳定性与 Bug 修复版本！共修复 11 个 Bug，涉及 Docker API 问题、LLM 提取改进、URL 处理修复及依赖更新。[发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.7.8.md)

<details>
  <summary>🤓 <strong>我的个人故事</strong></summary>

我在 Amstrad 上长大，这得益于我父亲的影响，从未停止过构建。在研究生阶段，我专注于 NLP 并为研究构建了爬虫。正是在那时，我深刻认识到数据提取的重要性。

2023 年，我需要一个网页转 Markdown 的工具。当时所谓的"开源"选项需要账号、API 令牌和 16 美元，但仍然无法满足需求。我义愤填膺，几天之内就构建了 Crawl4AI，它随即迅速走红。现在它是 GitHub 上 Star 最多的爬虫工具。

我将其开源是为了**可用性**——任何人都可以无门槛使用。现在我正在构建平台以实现**可负担性**——任何人都可以在不花大钱的情况下进行大规模爬取。如果您认同这一理念，欢迎加入、提供反馈，或者直接用它爬取一些精彩内容。
</details>


<details>
  <summary>为什么开发者选择 Crawl4AI</summary>

- **LLM 就绪输出**：智能 Markdown，包含标题、表格、代码、引用提示
- **实际运行快速**：异步浏览器池、缓存、最少跳转
- **完全可控**：会话、代理、Cookie、用户脚本、钩子
- **自适应智能**：学习网站模式，仅探索重要内容
- **随处部署**：无需密钥，支持 CLI 和 Docker，云端友好
</details>


## 🚀 快速开始

1. 安装 Crawl4AI：
```bash
# 安装包
pip install -U crawl4ai

# 预发布版本
pip install crawl4ai --pre

# 运行安装后设置
crawl4ai-setup

# 验证安装
crawl4ai-doctor
```

如果遇到浏览器相关问题，可以手动安装：
```bash
python -m playwright install --with-deps chromium
```

2. 使用 Python 运行简单的网络爬取：
```python
import asyncio
from crawl4ai import *

async def main():
    async with AsyncWebCrawler() as crawler:
        result = await crawler.arun(
            url="https://www.nbcnews.com/business",
        )
        print(result.markdown)

if __name__ == "__main__":
    asyncio.run(main())
```

3. 或使用新的命令行界面：
```bash
# 基本爬取，输出 Markdown
crwl https://www.nbcnews.com/business -o markdown

# 使用 BFS 策略深度爬取，最多 10 页
crwl https://docs.crawl4ai.com --deep-crawl bfs --max-pages 10

# 使用 LLM 提取并提出具体问题
crwl https://www.example.com/products -q "提取所有产品价格"
```

## 💖 支持 Crawl4AI

> 🎉 **赞助计划现已开放！** 在为 51K+ 开发者提供服务并持续增长一年之后，Crawl4AI 正式为**初创公司**和**企业**推出专属支持计划。成为前 50 名**创始赞助商**，在我们的荣誉殿堂获得永久认可。

Crawl4AI 是 GitHub 上排名第一的热门开源网络爬虫。您的支持使其保持独立、创新，并对社区免费开放——同时为您提供高级福利。

<div align="">
  
[![成为赞助商](https://img.shields.io/badge/Become%20a%20Sponsor-pink?style=for-the-badge&logo=github-sponsors&logoColor=white)](https://github.com/sponsors/unclecode)  
[![当前赞助商](https://img.shields.io/github/sponsors/unclecode?style=for-the-badge&logo=github&label=Current%20Sponsors&color=green)](https://github.com/sponsors/unclecode)

</div>

### 🤝 赞助等级

- **🌱 信仰者（$5/月）** — 加入数据民主化运动  
- **🚀 构建者（$50/月）** — 优先支持与功能提前访问  
- **💼 成长团队（$500/月）** — 每两周同步会议及优化协助  
- **🏢 数据基础设施合作伙伴（$2000/月）** — 全面合作，配备专属支持  
  *可提供自定义安排——详情及联系方式请参阅 [SPONSORS.md](SPONSORS.md)*

**为什么要赞助？**  
无限速 API。无锁定。在 Crawl4AI 创始人的直接指导下构建并拥有您的数据管道。

[查看所有等级和福利 →](https://github.com/sponsors/unclecode)


## ✨ 功能特性

<details>
<summary>📝 <strong>Markdown 生成</strong></summary>

- 🧹 **清洁 Markdown**：生成格式准确的干净结构化 Markdown。
- 🎯 **精简 Markdown**：基于启发式的过滤，去除噪音和无关内容，适合 AI 友好处理。
- 🔗 **引用与参考**：将页面链接转换为带编号的参考列表，并附上清晰引用。
- 🛠️ **自定义策略**：用户可根据特定需求创建自己的 Markdown 生成策略。
- 📚 **BM25 算法**：采用基于 BM25 的过滤来提取核心信息并去除无关内容。
</details>

<details>
<summary>📊 <strong>结构化数据提取</strong></summary>

- 🤖 **LLM 驱动提取**：支持所有 LLM（开源和专有）进行结构化数据提取。
- 🧱 **分块策略**：实现分块处理（基于主题、正则表达式、句子级别），针对性地处理内容。
- 🌌 **余弦相似度**：根据用户查询查找相关内容块，实现语义提取。
- 🔎 **基于 CSS 的提取**：使用 XPath 和 CSS 选择器进行快速模式化数据提取。
- 🔧 **模式定义**：定义自定义模式，从重复模式中提取结构化 JSON。

</details>

<details>
<summary>🌐 <strong>浏览器集成</strong></summary>

- 🖥️ **托管浏览器**：使用用户自有浏览器，完全可控，避免机器人检测。
- 🔄 **远程浏览器控制**：连接 Chrome 开发者工具协议，进行远程大规模数据提取。
- 👤 **浏览器配置文件**：创建和管理持久配置文件，保存认证状态、Cookie 和设置。
- 🔒 **会话管理**：保留浏览器状态并在多步骤爬取中重复使用。
- 🧩 **代理支持**：无缝连接带认证的代理，实现安全访问。
- ⚙️ **完全浏览器控制**：修改请求头、Cookie、用户代理等，打造定制化爬取设置。
- 🌍 **多浏览器支持**：兼容 Chromium、Firefox 和 WebKit。
- 📐 **动态视口调整**：自动调整浏览器视口以匹配页面内容，确保完整渲染和捕获所有元素。

</details>

<details>
<summary>🔎 <strong>爬取与抓取</strong></summary>

- 🖼️ **媒体支持**：提取图片、音频、视频及响应式图片格式（如 `srcset` 和 `picture`）。
- 🚀 **动态爬取**：执行 JS，等待异步或同步以提取动态内容。
- 📸 **截图**：在爬取过程中捕获页面截图，用于调试或分析。
- 📂 **原始数据爬取**：直接处理原始 HTML（`raw:`）或本地文件（`file://`）。
- 🔗 **全面链接提取**：提取内部链接、外部链接和嵌入式 iframe 内容。
- 🛠️ **可定制钩子**：在每个步骤定义钩子以自定义爬取行为（支持字符串和函数两种 API）。
- 💾 **缓存**：缓存数据以提高速度并避免重复获取。
- 📄 **元数据提取**：从网页检索结构化元数据。
- 📡 **IFrame 内容提取**：无缝提取嵌入 iframe 中的内容。
- 🕵️ **懒加载处理**：等待图片完全加载，确保不因懒加载而遗漏内容。
- 🔄 **全页面扫描**：模拟滚动以加载和捕获所有动态内容，完美支持无限滚动页面。

</details>

<details>
<summary>🚀 <strong>部署</strong></summary>

- 🐳 **Docker 化设置**：优化的 Docker 镜像，配备 FastAPI 服务器，便于部署。
- 🔑 **安全认证**：内置 JWT 令牌认证，保障 API 安全。
- 🔄 **API 网关**：一键部署，带安全令牌认证的 API 工作流。
- 🌐 **可扩展架构**：专为大规模生产和优化服务器性能而设计。
- ☁️ **云端部署**：为主要云平台提供即用型配置。

</details>

<details>
<summary>🎯 <strong>附加功能</strong></summary>

- 🕶️ **隐身模式**：通过模拟真实用户来避免机器人检测。
- 🏷️ **基于标签的内容提取**：根据自定义标签、标题或元数据细化爬取。
- 🔗 **链接分析**：提取并分析所有链接，进行详细的数据探索。
- 🛡️ **错误处理**：强健的错误管理，确保无缝执行。
- 🔐 **CORS 与静态服务**：支持基于文件系统的缓存和跨域请求。
- 📖 **清晰文档**：简化且更新的上手和高级用法指南。
- 🙌 **社区认可**：表彰贡献者和 PR，保持透明度。

</details>

## 立即试用！

✨ 在 Colab 中体验 [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1SgRPrByQLzjRfwoRNq1wSGE9nYY_EE8C?usp=sharing)

✨ 访问我们的[文档网站](https://docs.crawl4ai.com/)

## 安装 🛠️

Crawl4AI 提供灵活的安装选项，适合各种使用场景。您可以将其作为 Python 包安装或使用 Docker。

<details>
<summary>🐍 <strong>使用 pip</strong></summary>

根据您的需求选择最合适的安装选项：

### 基本安装

适用于基本的网络爬取和抓取任务：

```bash
pip install crawl4ai
crawl4ai-setup # 设置浏览器
```

默认情况下，这将安装 Crawl4AI 的异步版本，使用 Playwright 进行网络爬取。

👉 **注意**：安装 Crawl4AI 时，`crawl4ai-setup` 应该会自动安装和设置 Playwright。但是，如果遇到任何与 Playwright 相关的错误，可以通过以下方法手动安装：

1. 通过命令行：

   ```bash
   playwright install
   ```

2. 如果上述方法不起作用，尝试以下更具体的命令：

   ```bash
   python -m playwright install chromium
   ```

第二种方法在某些情况下被证明更可靠。

---

### 同步版本安装

同步版本已弃用，将在未来版本中移除。如果需要使用 Selenium 的同步版本：

```bash
pip install crawl4ai[sync]
```

---

### 开发安装

适用于计划修改源代码的贡献者：

```bash
git clone https://github.com/unclecode/crawl4ai.git
cd crawl4ai
pip install -e .                    # 以可编辑模式进行基本安装
```

安装可选功能：

```bash
pip install -e ".[torch]"           # 包含 PyTorch 功能
pip install -e ".[transformer]"     # 包含 Transformer 功能
pip install -e ".[cosine]"          # 包含余弦相似度功能
pip install -e ".[sync]"            # 包含同步爬取（Selenium）
pip install -e ".[all]"             # 安装所有可选功能
```

</details>

<details>
<summary>🐳 <strong>Docker 部署</strong></summary>

> 🚀 **现已发布！** 我们全新设计的 Docker 实现来了！这个新解决方案使部署比以往更高效、更无缝。

### 新 Docker 功能

新的 Docker 实现包括：
- **实时监控仪表板**，提供实时系统指标和浏览器池可见性
- **浏览器池化**，页面预热以加快响应时间
- **交互式操作台**，用于测试和生成请求代码
- **MCP 集成**，可直接连接到 Claude Code 等 AI 工具
- **全面的 API 端点**，包括 HTML 提取、截图、PDF 生成和 JavaScript 执行
- **多架构支持**，自动检测（AMD64/ARM64）
- **优化资源**，改进内存管理

### 开始使用

```bash
# 拉取并运行最新发布版本
docker pull unclecode/crawl4ai:latest
docker run -d -p 11235:11235 --name crawl4ai --shm-size=1g unclecode/crawl4ai:latest

# 访问监控仪表板：http://localhost:11235/dashboard
# 或访问操作台：http://localhost:11235/playground
```

### 快速测试

运行快速测试（适用于两种 Docker 选项）：

```python
import requests

# 提交爬取任务
response = requests.post(
    "http://localhost:11235/crawl",
    json={"urls": ["https://example.com"], "priority": 10}
)
if response.status_code == 200:
    print("爬取任务提交成功。")
    
if "results" in response.json():
    results = response.json()["results"]
    print("爬取任务完成。结果：")
    for result in results:
        print(result)
else:
    task_id = response.json()["task_id"]
    print(f"爬取任务已提交。任务 ID：{task_id}")
    result = requests.get(f"http://localhost:11235/task/{task_id}")
```

更多示例请参阅 [Docker 示例](https://github.com/unclecode/crawl4ai/blob/main/docs/examples/docker_example.py)。高级配置、监控功能和生产部署，请参阅[自托管指南](https://docs.crawl4ai.com/core/self-hosting/)。

</details>

---

## 🔬 高级使用示例 🔬

您可以在 [docs/examples](https://github.com/unclecode/crawl4ai/tree/main/docs/examples) 目录中查看项目结构。在那里，您可以找到各种示例；以下是一些常用示例。

<details>
<summary>📝 <strong>启发式 Markdown 生成：清洁与精简 Markdown</strong></summary>

```python
import asyncio
from crawl4ai import AsyncWebCrawler, BrowserConfig, CrawlerRunConfig, CacheMode
from crawl4ai.content_filter_strategy import PruningContentFilter, BM25ContentFilter
from crawl4ai.markdown_generation_strategy import DefaultMarkdownGenerator

async def main():
    browser_config = BrowserConfig(
        headless=True,  
        verbose=True,
    )
    run_config = CrawlerRunConfig(
        cache_mode=CacheMode.ENABLED,
        markdown_generator=DefaultMarkdownGenerator(
            content_filter=PruningContentFilter(threshold=0.48, threshold_type="fixed", min_word_threshold=0)
        ),
        # markdown_generator=DefaultMarkdownGenerator(
        #     content_filter=BM25ContentFilter(user_query="WHEN_WE_FOCUS_BASED_ON_A_USER_QUERY", bm25_threshold=1.0)
        # ),
    )
    
    async with AsyncWebCrawler(config=browser_config) as crawler:
        result = await crawler.arun(
            url="https://docs.micronaut.io/4.9.9/guide/",
            config=run_config
        )
        print(len(result.markdown.raw_markdown))
        print(len(result.markdown.fit_markdown))

if __name__ == "__main__":
    asyncio.run(main())
```

</details>

<details>
<summary>🖥️ <strong>执行 JavaScript 并不使用 LLM 提取结构化数据</strong></summary>

```python
import asyncio
from crawl4ai import AsyncWebCrawler, BrowserConfig, CrawlerRunConfig, CacheMode
from crawl4ai import JsonCssExtractionStrategy
import json

async def main():
    schema = {
    "name": "KidoCode Courses",
    "baseSelector": "section.charge-methodology .w-tab-content > div",
    "fields": [
        {
            "name": "section_title",
            "selector": "h3.heading-50",
            "type": "text",
        },
        {
            "name": "section_description",
            "selector": ".charge-content",
            "type": "text",
        },
        {
            "name": "course_name",
            "selector": ".text-block-93",
            "type": "text",
        },
        {
            "name": "course_description",
            "selector": ".course-content-text",
            "type": "text",
        },
        {
            "name": "course_icon",
            "selector": ".image-92",
            "type": "attribute",
            "attribute": "src"
        }
    ]
}

    extraction_strategy = JsonCssExtractionStrategy(schema, verbose=True)

    browser_config = BrowserConfig(
        headless=False,
        verbose=True
    )
    run_config = CrawlerRunConfig(
        extraction_strategy=extraction_strategy,
        js_code=["""(async () => {const tabs = document.querySelectorAll("section.charge-methodology .tabs-menu-3 > div");for(let tab of tabs) {tab.scrollIntoView();tab.click();await new Promise(r => setTimeout(r, 500));}})();"""],
        cache_mode=CacheMode.BYPASS
    )
        
    async with AsyncWebCrawler(config=browser_config) as crawler:
        
        result = await crawler.arun(
            url="https://www.kidocode.com/degrees/technology",
            config=run_config
        )

        companies = json.loads(result.extracted_content)
        print(f"成功提取 {len(companies)} 条数据")
        print(json.dumps(companies[0], indent=2))


if __name__ == "__main__":
    asyncio.run(main())
```

</details>

<details>
<summary>📚 <strong>使用 LLM 提取结构化数据</strong></summary>

```python
import os
import asyncio
from crawl4ai import AsyncWebCrawler, BrowserConfig, CrawlerRunConfig, CacheMode, LLMConfig
from crawl4ai import LLMExtractionStrategy
from pydantic import BaseModel, Field

class OpenAIModelFee(BaseModel):
    model_name: str = Field(..., description="OpenAI 模型名称。")
    input_fee: str = Field(..., description="OpenAI 模型的输入 token 费用。")
    output_fee: str = Field(..., description="OpenAI 模型的输出 token 费用。")

async def main():
    browser_config = BrowserConfig(verbose=True)
    run_config = CrawlerRunConfig(
        word_count_threshold=1,
        extraction_strategy=LLMExtractionStrategy(
            # 您可以使用 Litellm 库支持的任何提供商，例如：ollama/qwen2
            # provider="ollama/qwen2", api_token="no-token", 
            llm_config = LLMConfig(provider="openai/gpt-4o", api_token=os.getenv('OPENAI_API_KEY')), 
            schema=OpenAIModelFee.schema(),
            extraction_type="schema",
            instruction="""从爬取的内容中，提取所有提到的模型名称及其输入和输出 token 的费用。
            不要遗漏整个内容中的任何模型。提取的单个模型 JSON 格式应如下所示：
            {"model_name": "GPT-4", "input_fee": "US$10.00 / 1M tokens", "output_fee": "US$30.00 / 1M tokens"}。"""
        ),            
        cache_mode=CacheMode.BYPASS,
    )
    
    async with AsyncWebCrawler(config=browser_config) as crawler:
        result = await crawler.arun(
            url='https://openai.com/api/pricing/',
            config=run_config
        )
        print(result.extracted_content)

if __name__ == "__main__":
    asyncio.run(main())
```

</details>

<details>
<summary>🤖 <strong>使用自定义用户配置文件的自有浏览器</strong></summary>

```python
import os, sys
from pathlib import Path
import asyncio, time
from crawl4ai import AsyncWebCrawler, BrowserConfig, CrawlerRunConfig, CacheMode

async def test_news_crawl():
    # 创建持久性用户数据目录
    user_data_dir = os.path.join(Path.home(), ".crawl4ai", "browser_profile")
    os.makedirs(user_data_dir, exist_ok=True)

    browser_config = BrowserConfig(
        verbose=True,
        headless=True,
        user_data_dir=user_data_dir,
        use_persistent_context=True,
    )
    run_config = CrawlerRunConfig(
        cache_mode=CacheMode.BYPASS
    )
    
    async with AsyncWebCrawler(config=browser_config) as crawler:
        url = "ADDRESS_OF_A_CHALLENGING_WEBSITE"
        
        result = await crawler.arun(
            url,
            config=run_config,
            magic=True,
        )
        
        print(f"成功爬取 {url}")
        print(f"内容长度：{len(result.markdown)}")
```

</details>

---

> **💡 提示：** 某些网站可能使用 **CAPTCHA** 验证机制来阻止自动化访问。如果您的工作流程遇到此类挑战，可以选择性地集成第三方 CAPTCHA 处理服务，如 <strong>[CapSolver](https://www.capsolver.com/blog/Partners/crawl4ai-capsolver/?utm_source=crawl4ai&utm_medium=github_pr&utm_campaign=crawl4ai_integration)</strong>。他们支持 reCAPTCHA v2/v3、Cloudflare Turnstile、Challenge、AWS WAF 等。请确保您的使用符合目标网站的服务条款和适用法律。

## ✨ 最新更新

<details open>
<summary><strong>版本 0.8.6 — 安全热修复：litellm 供应链修复</strong></summary>

由于 PyPI 供应链遭到入侵影响原始包，已将 `litellm` 依赖替换为 `unclecode-litellm`。如果您使用的是 v0.8.5 或更早版本，请立即升级。

```bash
pip install -U crawl4ai
```

</details>

<details>
<summary><strong>版本 0.8.5 发布亮点 - 反机器人检测、Shadow DOM 与 60+ 项 Bug 修复</strong></summary>

我们自 v0.8.0 以来最大的版本更新。包含代理升级的反机器人检测、Shadow DOM 扁平化、深度爬取取消，以及超过 60 项 Bug 修复。

- **🛡️ 反机器人检测与代理升级**：
  - 三级检测：已知供应商、通用阻断指示器、结构完整性检查
  - 自动重试代理链和回退获取功能
  ```python
  from crawl4ai import CrawlerRunConfig
  from crawl4ai.async_configs import ProxyConfig

  config = CrawlerRunConfig(
      proxy_config=[ProxyConfig.DIRECT, ProxyConfig(server="http://my-proxy:8080")],
      max_retries=2,
      fallback_fetch_function=my_web_unlocker,
  )
  ```

- **🌑 Shadow DOM 扁平化**：
  - 提取隐藏在 shadow DOM 组件内的内容
  ```python
  config = CrawlerRunConfig(flatten_shadow_dom=True)
  ```

- **🛑 深度爬取取消**：
  - 使用 `cancel()` 或 `should_cancel` 回调优雅地停止长时间爬取
  - 支持 BFS、DFS 和 BestFirst 策略

- **⚙️ 配置默认值 API**：
  - BrowserConfig 和 CrawlerRunConfig 上的 `set_defaults()` / `get_defaults()` / `reset_defaults()`

- **🔒 关键安全修复**：
  - Docker `/crawl` 端点中通过反序列化实现的 RCE——已移除 `eval()`，添加白名单
  - Redis CVE-2025-49844（CVSS 10.0）——升级至 7.2.7

- **60+ 项 Bug 修复**，涵盖浏览器管理、代理、深度爬取、提取、CLI 和 Docker

[完整 v0.8.5 发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.8.5.md)

</details>

<details>
<summary><strong>版本 0.8.0 发布亮点 - 崩溃恢复与预取模式</strong></summary>

本版本引入了深度爬取的崩溃恢复、用于快速 URL 发现的新预取模式，以及针对 Docker 部署的关键安全修复。

- **🔄 深度爬取崩溃恢复**：
  - `on_state_change` 回调在每个 URL 之后触发，用于实时状态持久化
  - `resume_state` 参数可从保存的检查点继续
  - 可 JSON 序列化的状态，用于 Redis/数据库存储
  - 支持 BFS、DFS 和最佳优先策略
  ```python
  from crawl4ai.deep_crawling import BFSDeepCrawlStrategy

  strategy = BFSDeepCrawlStrategy(
      max_depth=3,
      resume_state=saved_state,  # 从检查点继续
      on_state_change=save_to_redis,  # 每个 URL 后调用
  )
  ```

- **⚡ 快速 URL 发现的预取模式**：
  - `prefetch=True` 跳过 Markdown、提取和媒体处理
  - 比完整处理快 5-10 倍
  - 完美适用于两阶段爬取：先发现，再选择性处理
  ```python
  config = CrawlerRunConfig(prefetch=True)
  result = await crawler.arun("https://example.com", config=config)
  # 仅返回 HTML 和链接——不生成 Markdown
  ```

- **🔒 安全修复（Docker API）**：
  - 钩子默认禁用（`CRAWL4AI_HOOKS_ENABLED=false`）
  - API 端点上阻止 `file://` URL 以防止 LFI
  - 从钩子执行沙箱中移除 `__import__`

[完整 v0.8.0 发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.8.0.md)

</details>

<details>
<summary><strong>版本 0.7.8 发布亮点 - 稳定性与 Bug 修复版本</strong></summary>

本版本聚焦于稳定性，修复了社区报告的 11 个 Bug。没有新功能，但显著提升了可靠性。

- **🐳 Docker API 修复**：
  - 修复深度爬取请求中 `ContentRelevanceFilter` 的反序列化（#1642）
  - 修复 `BrowserConfig.to_dict()` 中 `ProxyConfig` 的 JSON 序列化（#1629）
  - 修复 Docker 镜像中 `.cache` 文件夹权限（#1638）

- **🤖 LLM 提取改进**：
  - 新增 `LLMConfig` 参数，支持可配置的限速器退避（#1269）：
    ```python
    from crawl4ai import LLMConfig

    config = LLMConfig(
        provider="openai/gpt-4o-mini",
        backoff_base_delay=5,           # 首次重试等待 5s
        backoff_max_attempts=5,          # 最多尝试 5 次
        backoff_exponential_factor=3     # 每次将延迟乘以 3
    )
    ```
  - `LLMExtractionStrategy` 支持 HTML 输入格式（#1178）：
    ```python
    from crawl4ai import LLMExtractionStrategy

    strategy = LLMExtractionStrategy(
        llm_config=config,
        instruction="提取表格数据",
        input_format="html"  # 现支持："html"、"markdown"、"fit_markdown"
    )
    ```
  - 修复原始 HTML URL 变量——提取策略现在接收 `"Raw HTML"` 而非 HTML 块（#1116）

- **🔗 URL 处理**：
  - 修复 JavaScript 重定向后的相对 URL 解析（#1268）
  - 修复提取代码中的导入语句格式化（#1181）

- **📦 依赖更新**：
  - 将已弃用的 PyPDF2 替换为 pypdf（#1412）
  - Pydantic v2 ConfigDict 兼容性——不再有弃用警告（#678）

- **🧠 AdaptiveCrawler**：
  - 修复查询扩展，使其实际使用 LLM 而非硬编码的模拟数据（#1621）

[完整 v0.7.8 发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.7.8.md)

</details>

<details>
<summary><strong>版本 0.7.7 发布亮点 - 自托管与监控更新</strong></summary>

- **📊 实时监控仪表板**：带有实时系统指标和浏览器池可见性的交互式 Web UI
  ```python
  # 访问监控仪表板
  # 访问：http://localhost:11235/dashboard

  # 实时指标包括：
  # - 系统健康状况（CPU、内存、网络、正常运行时间）
  # - 活跃和已完成的请求跟踪
  # - 浏览器池管理（永久/热/冷）
  # - 管理员清理事件
  # - 带完整上下文的错误监控
  ```

- **🔌 全面的监控 API**：用于编程访问所有监控数据的完整 REST API
  ```python
  import httpx

  async with httpx.AsyncClient() as client:
      # 系统健康状况
      health = await client.get("http://localhost:11235/monitor/health")

      # 请求跟踪
      requests = await client.get("http://localhost:11235/monitor/requests")

      # 浏览器池状态
      browsers = await client.get("http://localhost:11235/monitor/browsers")

      # 端点统计
      stats = await client.get("http://localhost:11235/monitor/endpoints/stats")
  ```

- **⚡ WebSocket 流式传输**：每 2 秒实时更新，用于自定义仪表板
- **🔥 智能浏览器池**：三层架构（永久/热/冷），自动提升和清理
- **🧹 管理员系统**：带事件日志记录的自动资源管理
- **🎮 控制操作**：通过 API 进行手动浏览器管理（终止、重启、清理）
- **📈 生产指标**：6 个关键运营卓越指标，支持 Prometheus 集成
- **🐛 关键 Bug 修复**：
  - 修复异步 LLM 提取阻塞问题（#1055）
  - 增强 DFS 深度爬取策略（#1607）
  - 修复 AsyncUrlSeeder 中的站点地图解析（#1598）
  - 解决浏览器视口配置问题（#1495）
  - 修复带指数退避的 CDP 时序问题（#1528）
  - pyOpenSSL 安全更新（>=25.3.0）

[完整 v0.7.7 发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.7.7.md)

</details>

<details>
<summary><strong>版本 0.7.5 发布亮点 - Docker 钩子与安全更新</strong></summary>

- **🔧 Docker 钩子系统**：在 8 个关键节点使用用户提供的 Python 函数实现完整的管道定制
- **✨ 基于函数的钩子 API（新增）**：将钩子编写为带完整 IDE 支持的普通 Python 函数：
  ```python
  from crawl4ai import hooks_to_string
  from crawl4ai.docker_client import Crawl4aiDockerClient

  # 将钩子定义为普通 Python 函数
  async def on_page_context_created(page, context, **kwargs):
      """阻止图片以加快爬取速度"""
      await context.route("**/*.{png,jpg,jpeg,gif,webp}", lambda route: route.abort())
      await page.set_viewport_size({"width": 1920, "height": 1080})
      return page

  async def before_goto(page, context, url, **kwargs):
      """添加自定义请求头"""
      await page.set_extra_http_headers({'X-Crawl4AI': 'v0.7.5'})
      return page

  # 选项 1：使用 hooks_to_string() 工具用于 REST API
  hooks_code = hooks_to_string({
      "on_page_context_created": on_page_context_created,
      "before_goto": before_goto
  })

  # 选项 2：带自动转换的 Docker 客户端（推荐）
  client = Crawl4aiDockerClient(base_url="http://localhost:11235")
  results = await client.crawl(
      urls=["https://httpbin.org/html"],
      hooks={
          "on_page_context_created": on_page_context_created,
          "before_goto": before_goto
      }
  )
  # ✓ 完整的 IDE 支持、类型检查和可复用性！
  ```

- **🤖 增强 LLM 集成**：自定义提供商，支持温度控制和 base_url 配置
- **🔒 HTTPS 保护**：使用 `preserve_https_for_internal_links=True` 安全处理内部链接
- **🐍 Python 3.10+ 支持**：现代语言特性和增强性能
- **🛠️ Bug 修复**：解决了多个社区报告的问题，包括 URL 处理、JWT 认证和代理配置

[完整 v0.7.5 发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.7.5.md)

</details>

<details>
<summary><strong>版本 0.7.4 发布亮点 - 智能表格提取与性能更新</strong></summary>

- **🚀 LLMTableExtraction**：革命性的表格提取，支持智能分块处理超大型表格：
  ```python
  from crawl4ai import LLMTableExtraction, LLMConfig
  
  # 配置智能表格提取
  table_strategy = LLMTableExtraction(
      llm_config=LLMConfig(provider="openai/gpt-4.1-mini"),
      enable_chunking=True,           # 处理超大型表格
      chunk_token_threshold=5000,     # 智能分块阈值
      overlap_threshold=100,          # 在块之间保持上下文
      extraction_type="structured"    # 获取结构化数据输出
  )
  
  config = CrawlerRunConfig(table_extraction_strategy=table_strategy)
  result = await crawler.arun("https://complex-tables-site.com", config=config)
  
  # 表格自动分块、处理和合并
  for table in result.tables:
      print(f"提取的表格：{len(table['data'])} 行")
  ```

- **⚡ 调度器 Bug 修复**：修复 arun_many 中快速完成任务的顺序处理瓶颈
- **🧹 内存管理重构**：将内存工具合并到主工具模块，架构更清晰
- **🔧 浏览器管理器修复**：通过线程安全锁定解决并发页面创建中的竞态条件
- **🔗 高级 URL 处理**：更好地处理 raw:// URL 和基础标签链接解析
- **🛡️ 增强代理支持**：支持 dict 和字符串格式的灵活代理配置

[完整 v0.7.4 发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.7.4.md)

</details>

<details>
<summary><strong>版本 0.7.3 发布亮点 - 多配置智能更新</strong></summary>

- **🕵️ 未检测浏览器支持**：绕过复杂的机器人检测系统：
  ```python
  from crawl4ai import AsyncWebCrawler, BrowserConfig
  
  browser_config = BrowserConfig(
      browser_type="undetected",  # 使用未检测 Chrome
      headless=True,              # 可以无头模式隐身运行
      extra_args=[
          "--disable-blink-features=AutomationControlled",
          "--disable-web-security"
      ]
  )
  
  async with AsyncWebCrawler(config=browser_config) as crawler:
      result = await crawler.arun("https://protected-site.com")
  # 成功绕过 Cloudflare、Akamai 和自定义机器人检测
  ```

- **🎨 多 URL 配置**：在一个批次中为不同 URL 模式使用不同策略：
```python
from crawl4ai import CrawlerRunConfig, MatchMode, CacheMode
  
  configs = [
      # 文档站点——积极缓存
      CrawlerRunConfig(
          url_matcher=["*docs*", "*documentation*"],
          cache_mode=CacheMode.WRITE_ONLY,
          markdown_generator_options={"include_links": True}
      ),
      
      # 新闻/博客站点——新鲜内容
      CrawlerRunConfig(
          url_matcher=lambda url: 'blog' in url or 'news' in url,
          cache_mode=CacheMode.BYPASS
      ),
      
      # 其他所有内容的回退
      CrawlerRunConfig()
  ]
  
  results = await crawler.arun_many(urls, config=configs)
  # 每个 URL 自动获得最佳配置
  ```

- **🧠 内存监控**：在爬取期间跟踪和优化内存使用：
  ```python
  from crawl4ai.memory_utils import MemoryMonitor
  
  monitor = MemoryMonitor()
  monitor.start_monitoring()
  
  results = await crawler.arun_many(large_url_list)
  
  report = monitor.get_report()
  print(f"峰值内存：{report['peak_mb']:.1f} MB")
  print(f"效率：{report['efficiency']:.1f}%")
  # 获取优化建议
  ```

- **📊 增强表格提取**：直接从网页表格转换为 DataFrame：
  ```python
  result = await crawler.arun("https://site-with-tables.com")
  
  # 新方式——直接访问表格
  if result.tables:
      import pandas as pd
      for table in result.tables:
          df = pd.DataFrame(table['data'])
          print(f"表格：{df.shape[0]} 行 × {df.shape[1]} 列")
  ```

- **💰 GitHub 赞助商**：四级赞助系统，保障项目可持续发展
- **🐳 Docker LLM 灵活性**：通过环境变量配置提供商

[完整 v0.7.3 发布说明 →](https://github.com/unclecode/crawl4ai/blob/main/docs/blog/release-v0.7.3.md)

</details>

<details>
<summary><strong>版本 0.7.0 发布亮点 - 自适应智能更新</strong></summary>

- **🧠 自适应爬取**：您的爬虫现在可以自动学习和适应网站模式：
  ```python
  config = AdaptiveConfig(
      confidence_threshold=0.7, # 停止爬取的最低置信度
      max_depth=5, # 最大爬取深度
      max_pages=20, # 最大爬取页面数
      strategy="statistical"
  )
  
  async with AsyncWebCrawler() as crawler:
      adaptive_crawler = AdaptiveCrawler(crawler, config)
      state = await adaptive_crawler.digest(
          start_url="https://news.example.com",
          query="最新新闻内容"
      )
  # 爬虫学习模式并随时间改进提取效果
  ```

- **🌊 虚拟滚动支持**：从无限滚动页面完整提取内容：
  ```python
  scroll_config = VirtualScrollConfig(
      container_selector="[data-testid='feed']",
      scroll_count=20,
      scroll_by="container_height",
      wait_after_scroll=1.0
  )
  
  result = await crawler.arun(url, config=CrawlerRunConfig(
      virtual_scroll_config=scroll_config
  ))
  ```

- **🔗 智能链接分析**：三层评分系统，实现智能链接优先排序：
  ```python
  link_config = LinkPreviewConfig(
      query="机器学习教程",
      score_threshold=0.3,
      concurrent_requests=10
  )
  
  result = await crawler.arun(url, config=CrawlerRunConfig(
      link_preview_config=link_config,
      score_links=True
  ))
  # 按相关性和质量排名的链接
  ```

- **🎣 异步 URL 播种器**：在几秒内发现数千个 URL：
  ```python
  seeder = AsyncUrlSeeder(SeedingConfig(
      source="sitemap+cc",
      pattern="*/blog/*",
      query="python 教程",
      score_threshold=0.4
  ))
  
  urls = await seeder.discover("https://example.com")
  ```

- **⚡ 性能提升**：通过优化的资源处理和内存效率提速最高 3 倍

阅读我们的 [0.7.0 发布说明](https://docs.crawl4ai.com/blog/release-v0.7.0)的完整详情，或查看 [CHANGELOG](https://github.com/unclecode/crawl4ai/blob/main/CHANGELOG.md)。

</details>

## Crawl4AI 的版本编号

Crawl4AI 遵循标准 Python 版本编号惯例（PEP 440），帮助用户了解每个版本的稳定性和功能。

<details>
<summary>📈 <strong>版本号说明</strong></summary>

我们的版本号遵循以下模式：`MAJOR.MINOR.PATCH`（例如 0.4.3）

#### 预发布版本
我们使用不同的后缀来表示开发阶段：

- `dev`（0.4.3dev1）：开发版本，不稳定
- `a`（0.4.3a1）：Alpha 版本，实验性功能
- `b`（0.4.3b1）：Beta 版本，功能完整但需要测试
- `rc`（0.4.3rc1）：发布候选版本，潜在的最终版本

#### 安装
- 常规安装（稳定版本）：
  ```bash
  pip install -U crawl4ai
  ```

- 安装预发布版本：
  ```bash
  pip install crawl4ai --pre
  ```

- 安装特定版本：
  ```bash
  pip install crawl4ai==0.4.3b1
  ```

#### 为什么使用预发布版本？
我们使用预发布版本来：
- 在真实场景中测试新功能
- 在正式发布前收集反馈
- 确保生产用户的稳定性
- 允许早期用户尝试新功能

对于生产环境，我们建议使用稳定版本。如需测试新功能，可使用 `--pre` 标志选择预发布版本。

</details>

## 📖 文档与路线图

> 🚨 **文档更新通知**：我们将在下周进行重大文档修订，以反映近期更新和改进。请关注更全面、更新的指南！

有关当前文档，包括安装说明、高级功能和 API 参考，请访问我们的[文档网站](https://docs.crawl4ai.com/)。

查看我们的开发计划和即将推出的功能，请访问[路线图](https://github.com/unclecode/crawl4ai/blob/main/ROADMAP.md)。

<details>
<summary>📈 <strong>开发待办事项</strong></summary>

- [x] 0. 图爬虫：使用图搜索算法进行智能网站遍历，实现全面的嵌套页面提取
- [x] 1. 基于问题的爬虫：自然语言驱动的网络发现和内容提取
- [x] 2. 知识最优爬虫：在最小化数据提取的同时最大化知识的智能爬取
- [x] 3. 智能体爬虫：用于复杂多步骤爬取操作的自主系统
- [x] 4. 自动模式生成器：将自然语言转换为提取模式
- [x] 5. 领域特定抓取器：针对常见平台（学术、电子商务）的预配置提取器
- [x] 6. 网络嵌入索引：爬取内容的语义搜索基础设施
- [x] 7. 交互式操作台：用于测试和比较策略的 Web UI，支持 AI 辅助
- [x] 8. 性能监控：爬虫操作的实时洞察
- [ ] 9. 云集成：跨云提供商的一键部署解决方案
- [x] 10. 赞助计划：具有分级福利的结构化支持系统
- [ ] 11. 教育内容："如何爬取"视频系列和交互式教程

</details>

## 🤝 贡献

我们欢迎开源社区的贡献。请查看我们的[贡献指南](https://github.com/unclecode/crawl4ai/blob/main/CONTRIBUTORS.md)获取更多信息。

## 📄 许可证与署名

本项目采用 Apache License 2.0 授权，建议通过以下徽章进行署名。详情请参阅 [Apache 2.0 许可证](https://github.com/unclecode/crawl4ai/blob/main/LICENSE)文件。

### 署名要求
使用 Crawl4AI 时，您必须包含以下署名方式之一：

<details>
<summary>📈 <strong>1. 徽章署名（推荐）</strong></summary>
在您的 README、文档或网站中添加以下徽章之一：

| 主题 | 徽章 |
|-------|-------|
| **Disco 主题（动画）** | <a href="https://github.com/unclecode/crawl4ai"><img src="./docs/assets/powered-by-disco.svg" alt="Powered by Crawl4AI" width="200"/></a> |
| **Night 主题（暗色+霓虹）** | <a href="https://github.com/unclecode/crawl4ai"><img src="./docs/assets/powered-by-night.svg" alt="Powered by Crawl4AI" width="200"/></a> |
| **Dark 主题（经典）** | <a href="https://github.com/unclecode/crawl4ai"><img src="./docs/assets/powered-by-dark.svg" alt="Powered by Crawl4AI" width="200"/></a> |
| **Light 主题（经典）** | <a href="https://github.com/unclecode/crawl4ai"><img src="./docs/assets/powered-by-light.svg" alt="Powered by Crawl4AI" width="200"/></a> |

添加徽章的 HTML 代码：
```html
<!-- Disco 主题（动画） -->
<a href="https://github.com/unclecode/crawl4ai">
  <img src="https://raw.githubusercontent.com/unclecode/crawl4ai/main/docs/assets/powered-by-disco.svg" alt="Powered by Crawl4AI" width="200"/>
</a>

<!-- Night 主题（暗色+霓虹） -->
<a href="https://github.com/unclecode/crawl4ai">
  <img src="https://raw.githubusercontent.com/unclecode/crawl4ai/main/docs/assets/powered-by-night.svg" alt="Powered by Crawl4AI" width="200"/>
</a>

<!-- Dark 主题（经典） -->
<a href="https://github.com/unclecode/crawl4ai">
  <img src="https://raw.githubusercontent.com/unclecode/crawl4ai/main/docs/assets/powered-by-dark.svg" alt="Powered by Crawl4AI" width="200"/>
</a>

<!-- Light 主题（经典） -->
<a href="https://github.com/unclecode/crawl4ai">
  <img src="https://raw.githubusercontent.com/unclecode/crawl4ai/main/docs/assets/powered-by-light.svg" alt="Powered by Crawl4AI" width="200"/>
</a>

<!-- 简单盾牌徽章 -->
<a href="https://github.com/unclecode/crawl4ai">
  <img src="https://img.shields.io/badge/Powered%20by-Crawl4AI-blue?style=flat-square" alt="Powered by Crawl4AI"/>
</a>
```

</details>

<details>
<summary>📖 <strong>2. 文字署名</strong></summary>
在您的文档中添加以下行：
```
本项目使用 Crawl4AI（https://github.com/unclecode/crawl4ai）进行网络数据提取。
```
</details>

## 📚 引用

如果您在研究或项目中使用了 Crawl4AI，请引用：

```bibtex
@software{crawl4ai2024,
  author = {UncleCode},
  title = {Crawl4AI: Open-source LLM Friendly Web Crawler & Scraper},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub Repository},
  howpublished = {\url{https://github.com/unclecode/crawl4ai}},
  commit = {请使用您正在使用的提交哈希}
}
```

文字引用格式：
```
UncleCode. (2024). Crawl4AI: Open-source LLM Friendly Web Crawler & Scraper [Computer software]. 
GitHub. https://github.com/unclecode/crawl4ai
```

## 📧 联系方式

如有问题、建议或反馈，欢迎联系：

- GitHub：[unclecode](https://github.com/unclecode)
- Twitter：[@unclecode](https://twitter.com/unclecode)
- 网站：[crawl4ai.com](https://crawl4ai.com)

爬取愉快！🕸️🚀

## 🗾 使命

我们的使命是通过将数字足迹转化为结构化、可交易的资产，释放个人和企业数据的价值。Crawl4AI 通过开源工具赋能个人和组织提取和结构化数据，促进共享数据经济的形成。

我们设想一个未来，在那里 AI 由真实的人类知识驱动，确保数据创造者直接从其贡献中受益。通过数据民主化和推动道德数据共享，我们正在为真实 AI 进步奠定基础。

<details>
<summary>🔑 <strong>关键机遇</strong></summary>
 
- **数据资本化**：将数字足迹转化为可量化的有价值资产。  
- **真实 AI 数据**：为 AI 系统提供真实的人类洞察。  
- **共享经济**：创建一个公平的数据市场，让数据创造者受益。  

</details>

<details>
<summary>🚀 <strong>发展路径</strong></summary>

1. **开源工具**：用于透明数据提取的社区驱动平台。  
2. **数字资产结构化**：组织和评估数字知识价值的工具。  
3. **道德数据市场**：一个安全、公平的结构化数据交换平台。  

更多详情，请参阅我们的[完整使命声明](./MISSION.md)。
</details>

## 🌟 当前赞助商

### 🏢 企业赞助商与合作伙伴

我们的企业赞助商和技术合作伙伴帮助 Crawl4AI 扩展为生产级数据管道提供动力。

| 公司 | 简介 | 赞助等级 |
|------|------|----------|
| <a href="https://www.thordata.com/?ls=github&lk=crawl4ai" target="_blank"><img src="https://gist.github.com/aravindkarnam/dfc598a67be5036494475acece7e54cf/raw/thor_data.svg" alt="Thor Data" width="120"/></a>  | 利用 Thordata 确保与任何 AI/ML 工作流和数据基础设施无缝兼容，以 99.9% 的正常运行时间大规模访问网络数据，并提供一对一客户支持。 | 🥈 银牌 |
| <a href="https://app.nstproxy.com/register?i=ecOqW9" target="_blank"><picture><source width="250" media="(prefers-color-scheme: dark)" srcset="https://gist.github.com/aravindkarnam/62f82bd4818d3079d9dd3c31df432cf8/raw/nst-light.svg"><source width="250" media="(prefers-color-scheme: light)" srcset="https://www.nstproxy.com/logo.svg"><img alt="nstproxy" src="ttps://www.nstproxy.com/logo.svg"></picture></a>  | NstProxy 是一家可信赖的代理提供商，拥有超过 1.1 亿真实住宅 IP，支持城市级定向，99.99% 正常运行时间，低至 $0.1/GB 的价格，提供无与伦比的稳定性、规模和成本效益。 | 🥈 银牌 |
| <a href="https://app.scrapeless.com/passport/register?utm_source=official&utm_term=crawl4ai" target="_blank"><picture><source width="250" media="(prefers-color-scheme: dark)" srcset="https://gist.githubusercontent.com/aravindkarnam/0d275b942705604263e5c32d2db27bc1/raw/Scrapeless-light-logo.svg"><source width="250" media="(prefers-color-scheme: light)" srcset="https://gist.githubusercontent.com/aravindkarnam/22d0525cc0f3021bf19ebf6e11a69ccd/raw/Scrapeless-dark-logo.svg"><img alt="Scrapeless" src="https://gist.githubusercontent.com/aravindkarnam/22d0525cc0f3021bf19ebf6e11a69ccd/raw/Scrapeless-dark-logo.svg"></picture></a>  | Scrapeless 为爬取、自动化和 AI 智能体提供生产级基础设施，提供抓取浏览器、4 种代理类型和通用抓取 API。 | 🥈 银牌 |
| <a href="https://dashboard.capsolver.com/passport/register?inviteCode=ESVSECTX5Q23" target="_blank"><picture><source width="120" media="(prefers-color-scheme: dark)" srcset="https://docs.crawl4ai.com/uploads/sponsors/20251013045338_72a71fa4ee4d2f40.png"><source width="120" media="(prefers-color-scheme: light)" srcset="https://www.capsolver.com/assets/images/logo-text.png"><img alt="Capsolver" src="https://www.capsolver.com/assets/images/logo-text.png"></picture></a> | AI 驱动的 Captcha 解决服务。支持所有主流 Captcha 类型，包括 reCAPTCHA、Cloudflare 等 | 🥉 铜牌 |
| <a href="https://kipo.ai" target="_blank"><img src="https://docs.crawl4ai.com/uploads/sponsors/20251013045751_2d54f57f117c651e.png" alt="DataSync" width="120"/></a> | 帮助工程师和采购商在几秒内找到、比较和采购电子及工业零件，提供规格、定价、交货期和替代品。 | 🥇 金牌 |
| <a href="https://www.kidocode.com/" target="_blank"><img src="https://docs.crawl4ai.com/uploads/sponsors/20251013045045_bb8dace3f0440d65.svg" alt="Kidocode" width="120"/><p align="center">KidoCode</p></a> | Kidocode 是一所面向 5-18 岁儿童的混合式技术与创业学校，提供在线和校园教育。 | 🥇 金牌 |
| <a href="https://www.alephnull.sg/" target="_blank"><img src="https://docs.crawl4ai.com/uploads/sponsors/20251013050323_a9e8e8c4c3650421.svg" alt="Aleph null" width="120"/></a> | 总部位于新加坡的 Aleph Null 是亚洲领先的教育科技中心，致力于以学生为中心、AI 驱动的教育——赋能学习者在快速变化的世界中茁壮成长。 | 🥇 金牌 |



### 🧑‍🤝 个人赞助商

衷心感谢我们的个人支持者！每一份贡献都帮助我们保持开源使命的活力与发展！

<p align="left">
  <a href="https://github.com/hafezparast"><img src="https://avatars.githubusercontent.com/u/14273305?s=60&v=4" style="border-radius:50%;" width="64px;"/></a>
  <a href="https://github.com/ntohidi"><img src="https://avatars.githubusercontent.com/u/17140097?s=60&v=4" style="border-radius:50%;"width="64px;"/></a>
  <a href="https://github.com/Sjoeborg"><img src="https://avatars.githubusercontent.com/u/17451310?s=60&v=4" style="border-radius:50%;"width="64px;"/></a>
  <a href="https://github.com/romek-rozen"><img src="https://avatars.githubusercontent.com/u/30595969?s=60&v=4" style="border-radius:50%;"width="64px;"/></a>
  <a href="https://github.com/Kourosh-Kiyani"><img src="https://avatars.githubusercontent.com/u/34105600?s=60&v=4" style="border-radius:50%;"width="64px;"/></a>
  <a href="https://github.com/Etherdrake"><img src="https://avatars.githubusercontent.com/u/67021215?s=60&v=4" style="border-radius:50%;"width="64px;"/></a>
  <a href="https://github.com/shaman247"><img src="https://avatars.githubusercontent.com/u/211010067?s=60&v=4" style="border-radius:50%;"width="64px;"/></a>
  <a href="https://github.com/work-flow-manager"><img src="https://avatars.githubusercontent.com/u/217665461?s=60&v=4" style="border-radius:50%;"width="64px;"/></a>
</p>

> 想要加入他们？[赞助 Crawl4AI →](https://github.com/sponsors/unclecode)

## Star 历史

[![Star History Chart](https://api.star-history.com/svg?repos=unclecode/crawl4ai&type=Date)](https://star-history.com/#unclecode/crawl4ai&Date)

# In-Memory Search Engine

[![Java](https://img.shields.io/badge/Java-17-blue.svg)](https://www.oracle.com/java/)
[![Build](https://img.shields.io/badge/Build-Passing-brightgreen.svg)]()
[![Tests](https://img.shields.io/badge/Tests-106%20passed-success.svg)]()

一个基于内存的英文全文检索搜索引擎，使用倒排索引技术实现高效文本检索。本项目是华中科技大学《Java语言程序设计》课程的课程设计成果。

## ✨ 功能特性

-   **📂 文档索引**: 支持扫描指定目录下的 `.txt` 文本文件并构建内存倒排索引
-     **🔤 智能分词**: 内置文本内容切分、大小写转换和词汇过滤功能
-     **🗃️ 序列化支持**: 索引对象可序列化到文件/从文件反序列化，支持持久化存储
-     **🔍 高级搜索**:
    -   单关键词全文检索
    -   双关键词与/或逻辑查询
    -   双单词短语检索（相邻位置匹配）
-     **📊 结果排序**: 基于词频计算文档相关性得分，并按得分排序
-       **💻 控制台交互**: 提供完整的控制台输出和结果展示

## 🏗️ 系统架构

### 核心模块
| 模块 | 功能描述 |
| :--- | :--- |
| **索引构建 (Index Building)** | 文档读取、分词、过滤、倒排索引建立 |
| **文本处理 (Text Processing)** | 字符串分割、停用词过滤、长度过滤、模式过滤 |
| **搜索查询 (Search Query)** | 单词查询、多词逻辑查询、短语查询、结果排序 |

### 设计模式应用
-   **装饰者模式 (Decorator Pattern)**: 用于过滤器链 (`StopWordFilter` → `LengthFilter` → `PatternFilter`)
-   **策略模式 (Strategy Pattern)**: 用于排序算法，支持自定义评分策略


## 🚀 快速开始

### 环境要求
-   **JDK版本**: Java 17
-   **操作系统**: 任何支持Java的平台（Windows/Linux/macOS）
-   **开发工具**: Visual Studio Code 或 IntelliJ IDEA

### 构建和运行

1.  **克隆项目**
    ```bash
    git clone <repository-url>
    cd SearchEngineForStudent
    ```

2.  **编译项目**
    ```bash
    javac -d bin src/hust/cs/javacourse/search/**/*.java
    ```

3.  **构建索引**
    ```bash
    java -cp bin hust.cs.javacourse.search.run.TestBuildIndex
    ```

4.  **执行搜索**
    ```bash
    java -cp bin hust.cs.javacourse.search.run.TestSearchIndex
    ```

### 使用示例

#### 单关键词搜索
程序会自动提示输入搜索词：
Enter a single keyword to search: country

#### 双关键词逻辑搜索
Enter two keywords for AND/OR search:
Keyword1: coronavirus
Keyword2: country
Select logic (AND/OR): AND

#### 短语搜索
Enter two words for phrase search:
Word1: novel
Word2: coronavirus


## ⚙️ 配置参数

在 `Config` 类中可调整以下参数：

| 参数 | 默认值 | 描述 |
| :--- | :--- | :--- |
| `TERM_FILTER_PATTERN` | `"[a-zA-Z]+"` | 单词匹配正则表达式 |
| `TERM_FILTER_MINLENGTH` | `3` | 单词最小长度 |
| `TERM_FILTER_MAXLENGTH` | `20` | 单词最大长度 |
| `IGNORE_CASE` | `true` | 是否忽略大小写 |
| `STRING_SPLITTER_REGEX` | `"[^a-zA-Z0-9]+"` | 文本分割正则表达式 |

## 🧪 测试结果

项目已通过全面测试，106个测试用例全部通过：

| 测试模块 | 通过数 | 时间(ms) |
| :--- | :--- | :--- |
| `TermTest` | 9/9 | 40 |
| `PostingTest` | 16/16 | 17 |
| `DocumentTest` | 12/12 | 9 |
| `IndexTest` | 10/10 | 168 |
| `HitTest` | 16/16 | 27 |
| **总计** | **106/106** | **823** |

## 📊 性能特点

-   **高效索引**: 使用 `HashMap` 实现快速词汇查找，时间复杂度 O(1)
-   **智能过滤**: 支持停用词、长度、正则表达式多重过滤
-   **灵活搜索**: 支持多种搜索模式和相关度排序
-   **持久化存储**: 索引序列化支持快速加载和保存

## 👨‍💻 开发者

-   **叶润莹** - *计算机科学与技术2305班* - `U202315573`
-   **指导教师**: 纪俊文 老师

## 📝 课程信息

-   **课程名称**: Java 语言程序设计
-   **所属院校**: 华中科技大学计算机科学与技术学院
-   **完成日期**: 2025年4月29日

## 📄 许可证

本项目仅用于教学目的，保留所有权利。

---

<div align="center">
    <b>🔍 探索文本世界 · 体验搜索魅力 🔍</b>
</div>

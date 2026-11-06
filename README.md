# 一天重塑人生 · 精读学习指南 v2（数据驱动版）

Fix Your Life in One Day — Bilingual Study Guide, data-driven

基于 Dan Koe 在 X 上发表的长文《How to fix your entire life in 1 day》（2026-01-13）制作的**精读学习指南**，不是原文转载。

原文：https://x.com/thedankoe/status/2010751592346030461

## 结构：内容与网页分离

```
index.html                  网页壳：样式 + 交互，只负责读取和渲染，不放正文
data/
  meta.json                 书名、副标题、原文链接、使用方法、章节索引
  chapters/
    ch01.json … ch07.json   每章一个文件：标题、核心句、逐段中英对照、词汇、图表数据
  vocab.json                闪卡（9 张高频词）
  quiz.json                 小测验（6 道题）
```

改内容不用改网页：改对应的 JSON 文件，刷新即可。想分批处理 / 逐章校对，就一次只改一个 `chXX.json`。

每章 JSON 的字段：

```json
{
  "id": "ch01", "num": 1,
  "label": "Chapter 01 · 身份先行",
  "title_en": "…", "title_zh": "…",
  "core_en": "…", "core_zh": "…",
  "paragraphs": [{ "en": "…", "zh": "…" }],
  "vocab": [{ "word": "…", "phonetic": "…", "pos": "n.",
              "def_zh": "…", "example_en": "…", "example_zh": "…" }],
  "diagram": { "type": "words-actions|identity-loop|levels|cybernetics|game",
               "caption_zh": "…" }
}
```

第 6 章另有 `morning`（上午挖掘）、`alarms`（白天闹钟）、`evening`（晚上综合）三个结构化字段；第 4 章的 `levels` 是九层心智列表；第 7 章的 `game_parts` 是六个游戏组件。

新增一章：在 `data/chapters/` 加一个文件，并在 `data/meta.json` 的 `chapters_index` 里加一行，网页会自动收录到目录和进度里。

## 本地预览

必须用 HTTP 打开（`fetch` 不能直接读 `file://` 的 JSON）：

```bash
python3 -m http.server 8000
# 打开 http://localhost:8000/
```

## 发布

GitHub Pages：仓库 Settings → Pages → Deploy from branch → `main` / `/ (root)`，访问 `https://ooking-ai.github.io/fix-life-in-one-day-v2/`

## 版权说明

观点归原作者 Dan Koe 所有。本页为学习笔记与概括：英文段落是用更简单的英文重新讲述的改写版，配中文翻译，不转载原文全文；英文释义与例句为本页原创编写。引用原文请以 X 原帖链接为准。

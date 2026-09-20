# Alan's Blog

這是我的個人部落格與技術筆記網站，使用 [Astro](https://astro.build/) 與 [AstroPaper](https://github.com/satnaing/astro-paper) 主題建置，並透過 GitHub Actions 自動部署至 GitHub Pages。

🌐 **線上網站**：[https://alan1113.github.io/blog/](https://alan1113.github.io/blog/)

---

## 專案特色

- **純靜態渲染**：極速載入、SEO 友善、輕量純淨
- **現代化 CI/CD**：GitHub Actions 自動執行排版檢查 (Lint / Prettier) 與一鍵部署
- **完整功能**：內建淺色/深色模式、Pagefind 全文檢索、標籤分類、RSS 訂閱
- **AI 結對開發**：結合 GitHub Copilot 行內寫作輔助與 Antigravity Agent 架構維護

---

## 部落格內容維護指南 (Content Guide)

### 1. 如何撰寫新文章

所有文章皆存放在 `src/content/posts/` 目錄下，檔案支援 `.md` 或 `.mdx` 格式。

#### 步驟：

1. 在 `src/content/posts/` 建立新檔案（檔名即為文章網址 Slug，例如 `my-learning-notes.md`）。
2. 在文章最頂部填寫 **Frontmatter** 詮釋資料：

```markdown
---
author: Alan
pubDatetime: 2026-09-20T17:30:00+08:00
title: "我的文章標題"
featured: false # 是否置頂於首頁精選 (true / false)
draft: false # 是否為草稿 (若設為 true 則不會發布到線上網站)
tags:
  - tech
  - note
description: "這是一篇關於技術學習與心得分享的文章簡介。"
---

這裡開始撰寫您的 Markdown 內文...
```

#### 常用欄位說明：

| 欄位          | 類型     | 說明                                              |
| :------------ | :------- | :------------------------------------------------ |
| `title`       | 字串     | 文章標題                                          |
| `pubDatetime` | ISO 日期 | 發布時間（建議格式：`YYYY-MM-DDTHH:mm:ss+08:00`） |
| `description` | 字串     | 文章簡介（會顯示於文章列表與 SEO 預覽）           |
| `tags`        | 陣列     | 標籤分類（自動生成標籤頁面 `/tags/[tag]`）        |
| `featured`    | 布林值   | 是否在首頁精選推薦顯示                            |
| `draft`       | 布林值   | `true` 時僅本地開發可見，線上不會公開             |

---

### 2. 如何修改「關於我」頁面

- **檔案位置**：`src/content/pages/about.md`
- 直接使用 Markdown 編輯文字內容，儲存後網站上的 `/about/` 頁面即會同步更新。

---

### 3. 如何修改網站設定 (名稱、社群連結等)

- **檔案位置**：`astro-paper.config.ts`
- 常見設定項：
  - `site.title`：部落格主標題（目前為 `Alan's Blog`）
  - `site.description`：網站 Meta 描述
  - `site.author`：作者名稱
  - `site.profile`：作者個人網站或 GitHub 連結
  - `posts.perPage`：文章列表每頁顯示數量
  - `socials`：頁尾社群圖示連結（可自由新增或調整）

---

### 4. AI 協作寫作技巧

- **GitHub Copilot**：在編輯器開啟 `.md` 檔案撰寫內文或程式碼時，Copilot 會自動根據上下文提供行內文字補全。
- **Antigravity (Agent)**：
  - 文章寫完後，可吩咐 Antigravity：「_請幫我自動排版並檢查格式_」，Agent 會自動執行 `npx prettier --write .`。
  - 需要加新功能或調整樣式時，直接詢問 Agent，免去查閱繁雜設定檔的負擔。

---

## 本地開發與測試

確保本地環境具備 Node.js >= 22：

```bash
# 安裝依賴
npm install

# 啟動本地即時預覽伺服器 (http://localhost:4321)
npm run dev

# 檢查程式碼排版與型別
npm run format:check
npm run lint

# 本地完整建置測試 (模擬 CI 行為)
npm run build
```

---

## 發布流程 (Pull Request Workflow)

推薦使用 Branch + PR 流程確保發布品質：

1. **開立分支**：
   ```bash
   git checkout -b post/new-article
   ```
2. **撰寫文章並排版**：
   ```bash
   npx prettier --write .
   ```
3. **提交並推送**：
   ```bash
   git add .
   git commit -m "docs: add new article"
   git push -u origin post/new-article
   ```
4. **在 GitHub 發起 Pull Request**：
   - GitHub Actions 的 `CI` 工作流程會自動檢查格式、Lint 與建置。
5. **合併 (Merge)**：
   - 檢查確認為綠燈後，點擊 **Merge Pull Request**。
   - `Deploy to GitHub Pages` 工作流程會自動接手並於 1 分鐘內發布上線！

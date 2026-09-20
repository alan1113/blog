# Alan's Blog

這是我的個人部落格與技術筆記網站，使用 [Astro](https://astro.build/) 與 [AstroPaper](https://github.com/satnaing/astro-paper) 主題建置，並透過 GitHub Actions 自動部署至 GitHub Pages。

🌐 **線上網站**：[https://alan1113.github.io/blog/](https://alan1113.github.io/blog/)

## 專案特色

- **純靜態渲染**：效能優秀、載入速度快
- **自動化 CI/CD**：透過 GitHub Actions 在發布 Pull Request 或推送到 `main` 時自動檢查與部署
- **深淺色主題切換**：內建淺色與深色模式
- **文章搜尋**：整合 Pagefind 實現純靜態全文檢索
- **Markdown / MDX 支援**：方便快速撰寫包含程式碼區塊與數學公式的技術文章

## 本地開發

確保本地環境具備 Node.js >= 22：

```bash
# 安裝依賴
npm install

# 啟動本地開發伺服器 (http://localhost:4321)
npm run dev

# 檢查程式碼排版與型別
npm run format:check
npm run lint

# 本地建置
npm run build
```

## 發布流程 (Pull Request Workflow)

1. 建立新分支：`git checkout -b post/new-article`
2. 在 `src/content/posts/` 撰寫文章
3. 推送分支並在 GitHub 建立 Pull Request
4. GitHub Actions (CI) 自動執行排版與建置檢查
5. 合併 (Merge) 至 `main` 分支後自動發布至 GitHub Pages

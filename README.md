# Bookmark Landing Page(Frontend Mentor Challenge)

繁體中文 | English

## 繁體中文版

## Bookmark 擴充功能一頁式產品官網

這是來自Frontend Mentor的挑戰專案，這個專案重點在於建立一個完整的一頁式產品官網，須具備導航欄、頁首、內容、頁尾及電子信箱訂閱與驗證等基礎功能。

作品連結：

---

## 簡介

### 專案架構

```text
bookmark-landing-page/
 ├── .github/workflows/   # CI/CD 自動化部署設定
 │    └── deploy.yml      # GitHub Actions 腳本
 ├── .vscode/             # 編輯器專屬擴充與設定
 ├── src/
 │    ├── assets/         # 靜態資源（圖片、圖標）
 │    │    └── images/
 │    ├── components/     # 可複用組件
 │    │    ├── layout/    # 頁面大區塊主要佈局
 │    │    │    ├── TheHeader.vue
 │    │    │    ├── HeroSection.vue
 │    │    │    ├── FeatureSection.vue
 │    │    │    ├── FAQSection.vue
 │    │    │    ├── DownloadSection.vue
 │    │    │    └── TheFooter.vue
 │    │    └── ui/        # 獨立功能性 UI 元件
 │    │         ├── BgBlueRect.vue
 │    │         ├── FeatureTab.vue
 │    │         ├── FQAToggle.vue
 │    │         └── DownloadCards.vue
 │    ├── style/          # 樣式資料夾
 │    ├── App.vue         # 根組件
 │    ├── main.ts         # 程式進入點（TypeScript）
 │    ├── style.css       # 全域樣式設定（Tailwind 導入）
 │    └── vite-env.d.ts   # TypeScript 環境宣告
 ├── index.html           # 網頁入口 HTML
 ├── tsconfig.json        # TypeScript 編譯配置
 └── vite.config.ts       # Vite 建置配置與環境設定
```

### 技術棧

* 核心框架：Vue3 (Composition API)
* 開發語言：TypeScript, JavaScript(ES6+)
* 建置工具：Vite
* 樣式處理：Tailwind CSS v4
* 部屬與自動化：GitHub Pages, GitHub Actions

---

## 說明

### 主要功能

* RWD響應式設計：針對不同裝置進行佈局最佳化，提供行動端與桌機端更流暢、舒適的瀏覽體驗。
* 響應式導覽列：在電腦上顯示完整導覽列，換到手機時則為漢堡選單，自動偵測螢幕尺寸，為不同的裝置提供更舒適的導覽體驗。
* 動態產品優勢：點選不同頁籤時，下方的產品優勢介紹（圖片與文字）會瞬間流暢切換，不需要重新整理或等待載入網頁。
* 微互動彈跳動畫：於瀏覽器下載引導區塊注入動態特效，為一頁式產品主頁增添活潑的視覺層次與回饋感。
* 手風琴摺疊面板：常見問題區塊採用手風琴設計，點擊即可展開或收合答案。讓畫面保持乾淨清爽，大幅優化閱讀體驗。
* 即時Email表單驗證：在輸入當下同步進行格式校對與即時錯誤提示，減少提交失敗的重複修正率，優化使用者體驗。

### 技術亮點

### 問題挑戰與解決方案


---

## 結語

## 安裝流程


##### 回到最上面

<!-- 架構
大標題

中英文切換標籤錨點

(以下中英文都一樣，先寫中文再寫英文)
次標題
    一句話簡述+作品連結
簡介
    專案架構
    技術棧
說明
    主要功能
    技術亮點
    穩提挑戰與解決方案
結語

安裝流程

回到最上面(標籤錨點)-->

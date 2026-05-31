# Bookmark Landing Page(Frontend Mentor Challenge)

[繁體中文](#繁體中文版) | [English](#english-version)

## 繁體中文版

## Bookmark 擴充功能一頁式產品官網

這是來自Frontend Mentor的挑戰專案，這個專案重點在於建立一個完整的一頁式產品官網，須具備導航欄、頁首、內容、頁尾及電子信箱訂閱與驗證等基礎功能。

作品連結：<https://tina801005.github.io/bookmark-landing-page/>

---

## 📍簡介

### 📂專案架構

```markdown
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

### 📎技術棧

* 核心框架：Vue3 (Composition API)
* 開發語言：TypeScript, JavaScript(ES6+)
* 建置工具：Vite
* 樣式處理：Tailwind CSS v4
* 部屬與自動化：GitHub Pages, GitHub Actions

---

## 📋說明

### 🎯主要功能

* **RWD響應式設計**：針對不同裝置進行佈局最佳化，提供行動端與桌機端更流暢、舒適的瀏覽體驗。
* **響應式導覽列**：在電腦上顯示完整導覽列，換到手機時則為漢堡選單，自動偵測螢幕尺寸，為不同的裝置提供更舒適的導覽體驗。
* **動態產品優勢**：點選不同頁籤時，下方的產品優勢介紹（圖片與文字）會瞬間流暢切換，不需要重新整理或等待載入網頁。
* **微互動彈跳動畫**：於瀏覽器下載引導區塊注入動態特效，為一頁式產品主頁增添活潑的視覺層次與回饋感。
* **手風琴摺疊面板**：常見問題區塊採用手風琴設計，點擊即可展開或收合答案。讓畫面保持乾淨清爽，大幅優化閱讀體驗。
* **即時Email表單驗證**：在輸入當下同步進行格式校對與即時錯誤提示，減少提交失敗的重複修正率，優化使用者體驗。

### 💡技術亮點

* **自動化部屬工作流(CI/CD)**：配置GitHub Action自動化腳本，實現自動化部屬與測試，大幅提升交付效率。
* **無障礙網頁規範(Accessibility / A11y)**：全頁面落實HTML5語義化標籤並遵守WAI-ARIA規則，確保鍵盤導覽與螢幕閱讀器友善。
* **資料驅動與高度可重複性組件**：組件和數據資料解耦，全部透過Vue 3 props 進行資料驅動渲染。搭配TypeScript嚴謹型別維護，大幅提升系統的擴充性及易維護性。

### 🔍問題挑戰與解決方案

* 【問題】git push上去後CI/CD沒反應
  * 【解決方案】解決方法：一一排查。
    1. 檢查github設定檔 setting>actions>general，確認Actions permissions 是否為Allow all actions and reusable workflows；確認Workflow permissions是否為Read and write permissions
    2. 檢查資料夾及檔名是否有拼錯。正確應為.github/workflows/deploy.yml
    3. 檢查vscode是否已登入github帳戶
    4. 檢查deploy.yml中的branches是否為正確的分支名稱
    5. 檢查分支名稱
  * 最後檢查出是分支名稱寫錯了，修正後CI/CD正常啟動🎉

* 【問題】Tailwind CSS安裝後沒反應
  * 【解決方案】
    * 原因：Tailwind CSS v4 語法重大變革 ，一開始沿用v3的 @tailwind base; 指令會導致樣式完全失效 。
    * 求助Copilot後得知v4的指令變成`@import "tailwindcss";` 。進入style.css裡修正後恢復正常

* 【問題】Tailwind CSS v4 與postCSS的適配問題
  * 【解決方案】
    * 原因：Tailwind v4 將 PostCSS 插件移至獨立套件 @tailwindcss/postcss。
    * 解決：補裝套件並更新 postcss.config.js 配置。

* 【問題】本地與遠端分支的 Git 歷史紀錄衝突（因手動切換與調整分支導致），導致普通 Push 被拒絕
  * 【解決方案】
    * 先用" git push origin master --force "強制推送新的修正並重新調整commit紀錄。
    * 日後作品發布成網頁後，任何bug都必須用以下方法紀錄並push到master分支。不需要去更改網頁分支(不需要把gh-pages改成master避免造成CI/CD混亂)
      1. 確保自己在 master 分支>> `git checkout master`
      2. 存檔所有修改 >> `git add .`
      3. 紀錄我修了什麼 >> `git commit -m "fix: 修正了某某樣式 bug"`
      4. 推送上去（不需要 --force 了，用普通的 push 即可！）>> `git push origin master`

* 【問題】BgBlueRect在HeroSection和FeatureTab的尺寸與定位
  * 【解決方案】
    * 原因：設計稿中「大型藍色圓角裝飾背景」同時出現在兩個不同區塊，Hero為右側/左圓角；Feature為左側/右圓角，導致代碼中出現大量重複的Tailwind CSS樣式，且必須同時符合在不同螢幕斷點下的適配性。
    * 解決：經初期分析設計稿後決定將其獨立抽離為`BgBlueRect.vue`核心組件裝飾，並採用尺寸內聚，定位外包的設計：
      1. **本體尺寸內聚**：因兩者唯一不同的是定位而寬高都是一樣的，所以決定將寬高統一封裝在`BgBlueRect.vue`，這樣做不僅可以維持單一數據源，對後期維護也相對有利。
      2. **動態定位外包**：利用Vue3的屬性透傳機制，將特定圓角方向(`rounded-l-full` / `rounded-r-full`)與各段點的絕對定位(`top` / `bottom` / `left` / `right`的百分比位移)交給父組件配置。
      3. **防止視口溢出與消除橫向滾動條**：因裝飾色塊在部分斷點採用了向外延伸的絕對定位（如 `right-[-20%]`），會導致網頁總寬度超出瀏覽器視口（Viewport），進而產生無意義的橫向滾動條。為了解決此視覺瑕疵，在全域（如 `body` 或外層大框架）注入 `overflow-x-hidden` 進行防禦性剪裁，確保超出螢幕的裝飾塊能完美隱藏，維持網頁垂直瀏覽的純粹與流暢度。
    * 【後續改善方向】目前雖然透過各斷點的百分比與固定值完成了RWD呈現，但定位本質上仍高度依賴外層視窗寬度，在極端大螢幕或者超小螢幕下仍存在裝飾塊過度飄移或不如預期的效果等風險。
      * **預期最佳解法**：未來預期將定位基準從視窗改為內部的`container`。讓裝飾色塊改以container的左右邊界為錨點進行動態相對位移，這應該會是全螢幕尺寸下最穩定、不容易崩潰的網頁布局方案。

* 【問題】靜態資源動態路徑丟失（Dynamic Asset Handling）
  * 【解決方案】"本專案採用方法A用import預先導入"
    * 方法A：使用 import 預先導入（適合圖片數量少時）。

        ```typescript
        //方法A：用FeatureTab.vue做舉例
        //先在 script中將靜態圖片當成模組導入（Import）為變數，再將該變數直接放入陣列資料中。
        // 1. import導入圖片資源，這裡使用相對路徑來確保在構建過程中能正確解析
        import featuresTab1Url from "../../assets/images/illustration-features-tab-1.svg";
        // 2. 定義每一項的資料類型
        interface Feature {
            id:number;
            imgSrc: string;
        }
        // 3. 將功能特色標籤的資料獨立成一個陣列，方便後續維護和擴展
        const features: Feature[] = [
            {
                id:1,
                imgSrc: featuresTab1Url
            }]
        // 4. 將陣列中的資料渲染進頁面中
        <div v-if="activeFeature">
            <img :src="activeFeature.imgSrc">
        </div>
        ```

    * 方法B：利用 new URL 動態解析（適合圖片數量多、使用 v-for 循環時）

        ```typescript
        //把圖片的相對路徑打包成函式，再用v-for方式渲染進img裡
        // 1. 定義動態路徑轉換函式
        const getImageUrl = (name: string) => {
        return new URL(`./assets/${name}`, import.meta.url).href
        }
        // 2. 陣列中只需儲存純「檔案名稱」（例如：logo-chrome.svg）
        const 陣列名 = [
        { id: 1, title: '文字標題', imgName: '圖片檔名(xxx.svg,xxx.png,xxx.jpg)' }, // 只留檔名
        ]
        // 3. Template 渲染： <img :src="getImageUrl(item.imgName)" />
        <img :src="getImageUrl(card.imgName)" :alt="card.title" />

        ```

---

## 😊結語

這個專案記錄了很多的第一次，第一次使用TypeScript、Tailwind CSS、CI/CD以及A11y。雖然製作時程有點長🫣但也讓我有更多時間可以思考怎麼做會更好，且也發現在要符合A11y的條件下，分析設計稿變得格外的重要。在分析的同時必須先考慮這個部分是否需要提示，是否需要加上focus，同時也安裝了NVDA實際體驗一下視障者在使用螢幕閱讀器時"聽到"的資訊有多麼混亂，這時候"減法"就非常重要，必須引導的地方才讓螢幕讀出來，其餘不必要的就讓其安靜減少干擾，才能讓視障者更好地聚焦在自己需要的資訊上。這個專案除了讓我練習到landing page的排版布局外，更重要的是讓我學到如何換位思考，開發出適合一般人也適合視障者的web，讓視障朋友們不會覺得自己是被忽略或特殊對待的群體。

## 🧩安裝流程

以下為本專案的本地開發與部屬安裝流程：

1. 先確認已安裝 Node.js（建議 Node 18 以上）
2. 進入專案目錄

    ```bash
    cd bookmark-landing-page
    ```

3. 安裝專案依賴

    ```bash
    npm install
    ```

4. 啟動本地開發伺服器

    ```bash
    npm run dev
    ```

5. 建置 production 版本

    ```bash
    npm run build
    ```

6. 若要在本地預覽 production 版

    ```bash
    npm run preview
    ```

7. 部屬說明

  本專案使用 GitHub Pages 進行自動部署；當 `master` 分支收到推送時，GitHub Actions 將自動建置並發佈站點。
> 如果在安裝過程中遇到 Tailwind CSS v4 相關問題，請確認 `style.css` 已改為 `@import "tailwindcss";`，且 `postcss.config.js` 已安裝並正確配置 `@tailwindcss/postcss` 插件。

---

### [🔝 回到最上面](#bookmark-landing-pagefrontend-mentor-challenge)

---

## English Version

## Bookmark Landing Page

This is a Frontend Mentor challenge project focused on creating a complete one-page product website with basic features such as a navigation bar, header, content section, footer, and email subscription/verification.

Link: <https://tina801005.github.io/bookmark-landing-page/>

## 📍Introduction

### 📂Project Structure

```markdown
bookmark-landing-page/
 ├── .github/workflows/   # CI/CD automated deployment configuration
 │    └── deploy.yml      # GitHub Actions workflow script
 ├── .vscode/             # Editor workspace extensions and settings
 ├── src/
 │    ├── assets/         # Static assets (images, icons)
 │    │    └── images/
 │    ├── components/     # Reusable Vue components
 │    │    ├── layout/    # Major page layout sections
 │    │    │    ├── TheHeader.vue
 │    │    │    ├── HeroSection.vue
 │    │    │    ├── FeatureSection.vue
 │    │    │    ├── FAQSection.vue
 │    │    │    ├── DownloadSection.vue
 │    │    │    └── TheFooter.vue
 │    │    └── ui/        # Independent functional UI components
 │    │         ├── BgBlueRect.vue
 │    │         ├── FeatureTab.vue
 │    │         ├── FQAToggle.vue
 │    │         └── DownloadCards.vue
 │    ├── style/          # Styles directory
 │    ├── App.vue         # Root component
 │    ├── main.ts         # Application entry point (TypeScript)
 │    ├── style.css       # Global styles (Tailwind CSS initialization)
 │    └── vite-env.d.ts   # TypeScript environment declarations
 ├── index.html           # HTML entry point
 ├── tsconfig.json        # TypeScript compiler configuration
 └── vite.config.ts       # Vite build and environment configuration
 ```

### 📎Tech Stack

* Framework: Vue3 (Composition API)
* Development Language: TypeScript, JavaScript(ES6+)
* Build Tool: Vite
* Styling: Tailwind CSS v4
* Deployment and automation: GitHub Pages, GitHub Actions

---

## 📋Features

### 🎯Main Features

* **RWD responsive design**: optimized layout for different devices, providing smoother and more comfortable browsing experiences for both mobile and desktop.
* **Responsive navigation bar**: Shows the full navigation menu on desktop and switches to a hamburger menu on mobile. The layout adapts automatically to different screen sizes for a more comfortable navigation experience.
* **Dynamic product feature section**: Clicking different tabs instantly and smoothly switches the product feature content below (images and text) without a page refresh or loading delay.
* **Micro-interactive pop-up animations**: Dynamic effects are added in the download guide section, providing lively visual layers and feedback on the one-page product site.
* **Accordion panel**: The FAQ section uses an accordion design that lets users expand or collapse answers, keeping the interface clean and improving readability.
* **Real-time email form validation**: Inputs are validated immediately and error messages appear in real time, reducing repeated corrections from failed submissions and improving the user experience.

### 💡Technical Highlights

* **Automated deployment workflow (CI/CD)**: GitHub Actions scripts are configured to automate deployment and testing, greatly improving delivery efficiency.
* **Accessibility (A11y)**: Implements HTML5 semantic tags across all pages and complies with WAI-ARIA rules to ensure navigation and reader-friendly interfaces.
* **Data-driven and reusable components**: Components and data are decoupled and rendered using Vue 3 props. Combined with TypeScript's strict typing, this greatly improves scalability and maintainability.

### 🔍Challenges & Solutions

* 【Issue】 CI/CD not triggering after git push
  * 【Solution】Troubleshooting steps performed:
    1. Checked GitHub repository settings under Settings > Actions > General. Verified that "Actions permissions" was set to Allow all actions and reusable workflows, and "Workflow permissions" was set to Read and write permissions.
    2. Checked for folder or filename typos. Verified the correct path should be .github/workflows/deploy.yml.
    3. Verified that VS Code was successfully logged into my GitHub account.
    4. Checked if the target branch configured in deploy.yml matched the actual deployment branch.
    5. Double-checked the actual branch name.
  * Root cause: It turned out to be a typo in the branch name. After correcting it, the CI/CD pipeline triggered and ran perfectly! 🎉

* 【Issue】Tailwind CSS styling has no effect after installation
  * 【Solution】
    * Root Cause: Tailwind CSS v4 introduced major syntax changes. Initially relying on the v3 `@tailwind base` directives caused the styles to fail completely.
    * Resolution: Consulted Copilot and learned that the v4 syntax has changed to `@import "tailwindcss";`. After updating this inside `style.css`, everything went back to normal.

* 【Issue】Compatibility issues between Tailwind CSS v4 and PostCSS
  * 【Solution】
    * Root Cause: Tailwind v4 moved its PostCSS plugin into a separate package: `@tailwindcss/postcss`.
    * Resolution: Installed the missing package and updated the configuration inside `postcss.config.js`.

* 【Issue】Git history conflict between local and remote branches (caused by manual branch switching and adjustments), resulting in normal pushes being rejected
  * 【Solution】
    * Used `git push origin master --force` to force-push the new updates and clean up the commit history.
    * For future reference, once the site is deployed, any bug fixes must be recorded and pushed directly to the `master` branch using the following workflow. No need to modify the deployment branch manually (avoid changing `gh-pages` to `master` to prevent disrupting the CI/CD pipeline):
      1. Ensure you are on the master branch >> `git checkout master`
      2. Stage all modifications >> `git add .`
      3. Record what I fixed >> `git commit -m "fix: resolve styling bug in some component"`
      4. Push it up (no --force needed, just a regular push!) >> `git push origin master`

* 【Issue】Dimensions and positioning of BgBlueRect inside HeroSection and FeatureTab
  * 【Solution】
    * Root Cause: In the design mockups, the "large blue rounded background decoration" appears in two different sections (Hero uses a right-aligned shape with left-rounded corners; Feature uses a left-aligned shape with right-rounded corners). This initially led to a large amount of duplicate Tailwind CSS classes and made responsiveness across different viewport breakpoints difficult to manage.
    * Resolution: After an initial analysis of the design, I decided to extract this into a reusable core decorative component called `BgBlueRect.vue`, applying a design philosophy of "encapsulate dimensions, delegate positioning":
      1. **Encapsulate Dimensions (Internalized)**: Since the height and width are identical for both sections and only the position differs, I encapsulated the sizing classes inside `BgBlueRect.vue`. This maintains a single source of truth and makes future maintenance much easier.
      2. **Delegate Positioning (Externalized)**: Utilized Vue 3's attribute fallthrough (`v-bind="$attrs"`) to pass section-specific classes like rounded corner directions (`rounded-l-full` / `rounded-r-full`) and absolute position percentages (`top` / `bottom` / `left` / `right`) directly from the parent components.
      3. **Prevent Viewport Overflow & Eliminate Horizontal Scrollbars**: Because the decorative shapes are absolutely positioned and extend outwards at certain breakpoints (e.g., `right-[-20%]`), they expanded the total page width beyond the browser viewport, creating an annoying and unnecessary horizontal scrollbar. To fix this visual defect, I applied `overflow-x-hidden` as a defensive clipping mechanism globally (on the `body` or wrapper frame) to cleanly hide the protruding decorative graphics and keep vertical scrolling perfectly smooth.
    * 【Future Improvements】While the layout currently renders perfectly across RWD breakpoints using hardcoded percentages and offsets, the positioning still relies heavily on the viewport width. This presents a minor risk of the decoration drifting awkwardly on extreme 2K/4K monitors or ultra-small screens.
      * **Target Strategy**: In the next iteration, I plan to switch the positioning anchor from the viewport window to the inner content `container`. Having the decoration dynamically offset relative to the left/right boundaries of the layout `container` will provide the most resilient and bulletproof layout scheme for all screen sizes.

* 【Issue】Missing dynamic asset paths during build (Dynamic Asset Handling)
  * 【Solution】**This project adopts Method A: Pre-importing assets for deployment.**
    * Method A: Pre-importing assets via import (Best suited when the asset count is small).

      ```typescript
        // Method A: Example using FeatureTab.vue
        // Pre-import static images as modules in the <script> setup, then reference the variables inside your data arrays.

        // 1. Import image assets using relative paths to ensure correct resolution during the Vite build process
        import featuresTab1Url from "../../assets/images/illustration-features-tab-1.svg";

        // 2. Define the TypeScript interface for data items
        interface Feature {
            id: number;
            imgSrc: string;
        }

        // 3. Separate the data into an array for cleaner future scalability
        const features: Feature[] = [
            {
                id: 1,
                imgSrc: featuresTab1Url
            }
        ];

        // 4. Render the data variable dynamically into the template
        // <div v-if="activeFeature">
        //     <img :src="activeFeature.imgSrc">
        // </div>
      ```

    * Method B: Dynamic resolution utilizing `new URL()` (Best suited for large numbers of assets rendered through a `v-for` loop).

      ```typescript
        // Wrap relative asset paths in a helper function and bind them inside v-for loops

        // 1. Define the dynamic path resolution helper
        const getImageUrl = (name: string) => {
          return new URL(`./assets/${name}`, import.meta.url).href;
        };

        // 2. Store only the raw filenames in the array data (e.g., 'logo-chrome.svg')
        const cardList = [
          { id: 1, title: 'Card Title', imgName: 'logo-chrome.svg' }, // Filename only
        ];

        // 3. Template binding syntax:
        // <img :src="getImageUrl(card.imgName)" :alt="card.title" />
      ```

### 😊Conclusion

This project recorded many firsts, including the first use of TypeScript, Tailwind CSS, CI/CD, and A11y. Although the production schedule was a bit long, it gave me more time to think about how to do it better, and I also realized that analyzing the design draft became especially important when meeting A11y's requirements. While analyzing, you must first consider whether a hint is needed for this part, whether focus should be added, and even installed the NVDA screen reader myself to personally experience how chaotic the auditory information can be for visually impaired users. This realization highlighted the true value of 'subtraction' in web design: only explicit guide paths should be read aloud: only the guiding areas are read by the screen, while unnecessary parts are quieted to reduce distractions, allowing the visually impaired person to better focus on the information they need. This project not only helped me practice the layout of landing pages, but more importantly, it taught me how to think from others' perspectives and developed a web suitable for both the general public and the visually impaired, so that visually impaired friends wouldn't feel ignored or treated as a special group.

---

## 🧩Installation Steps

Below is the local development and installation process for this project:

1. First, make sure Node.js is installed (Node 18 or above recommended).
2. Enter the project directory.

    ```bash
    cd bookmark-landing-page
    ```

3. Install project dependencies

    ```bash
    npm install
    ```

4. Start the local development server

    ```bash
    npm run dev
    ```

5. Build the production version

    ```bash
    npm run build
    ```

6. To preview the production build locally

    ```bash
    npm run preview
    ```

7. Deployment Guidelines
  This project uses GitHub Pages for automatic deployment; when the `master` branch receives a push, GitHub Actions will build and publish the site automatically.
    > If you encounter Tailwind CSS v4-related issues during installation, make sure [style.css](style.css) uses `@import "tailwindcss";`, and that `@tailwindcss/postcss` is installed and properly configured in [postcss.config.js](postcss.config.js).

---

### [🔝 Back to top](#bookmark-landing-pagefrontend-mentor-challenge)

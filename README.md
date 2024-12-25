# ECharts 與 Vue 3 整合示例專案

這是一個展示如何在 Vue 3 中正確使用 ECharts 的示範專案，特別關注於常見問題的處理方式。

## 功能展示

此專案包含多個 ECharts 整合的範例元件，每個元件展示不同的實作方式及其考量：

### 1. 記憶體洩漏處理 (MemoryLeak.vue)

- 展示如何正確處理 ECharts 實例的生命週期
- 在元件卸載時適當釋放資源
- 使用 `onUnmount` 清理 ECharts 實例

### 2. 資料更新處理方式

這裡提供範例包含 

- ErrorNotRender.vue 錯誤未成功渲染
- WatchRerender.vue 使用 watch 觸發渲染
- ResponseSetOption.vue 在回應後使用 setOption 更新圖表
- Error.vue 來自 https://github.com/apache/echarts/issues/13943 的錯誤範例實驗

## 最佳實踐建議

1. 務必在元件卸載時清理 ECharts 實例
2. 避免使用響應式資料直接綁定圖表實例
3. 使用 `setOption` 方法更新圖表
4. 確保 DOM 元素已經準備就緒才初始化圖表

## Tech Stack

- Vue 3
- Vite
- Pinia (狀態管理)
- Vue Router
- TailwindCSS
- SASS
- ESLint + Prettier (程式碼品質工具)
- Stylelint
- 套件自動引入工具 (unplugin-auto-import)
- ECharts 5.5+

## 建議的開發環境設定

- [VSCode](https://code.visualstudio.com/) 
- [Vue -Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss#review-details)

- Node.js 20+ 版本
- pnpm 9+ 版本

## 專案設定

安裝依賴：
```sh
pnpm install
```

### 開發指令

開發環境運行（支援熱重載）：
```sh
pnpm dev
```

建置生產版本：
```sh
pnpm build
```

預覽建置結果：
```sh
pnpm preview
```

### 程式碼格式化

執行程式碼格式化：
```sh
pnpm format
```

執行 ESLint 檢查與自動修復：
```sh
pnpm lint
```


## 專案結構說明

- `/src` - 原始碼目錄
- `/public` - 靜態資源目錄

## 相關文件

- [ECharts 官方文件](https://echarts.apache.org/zh/index.html)
- [Vite 設定參考](https://vitejs.dev/config/)
- [Vue 3 文件](https://vuejs.org/)
- [Pinia 文件](https://pinia.vuejs.org/)
- [TailwindCSS 文件](https://tailwindcss.com/docs)
- [Stylelint 文件](https://stylelint.io/)
- [ESLint 文件](https://eslint.org/)
- [Prettier 文件](https://prettier.io/)


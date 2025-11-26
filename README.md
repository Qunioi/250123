# BBINPartner2.0 Project (250123)

## 環境需求

> Node.js v20.0.0

## 專案指令

### 安裝依賴

```bash
npm install
```

### 啟動開發伺服器

```bash
npm run dev
```

### 打包生產環境

```bash
npm run build
```

## ThemeManager 編輯器設定

本專案包含一個 `ThemeManager` 主題編輯器，用於即時調整網站樣式與浮動圖。

### 如何開啟/關閉 ThemeManager

`ThemeManager` 的開關位於 `src/App.vue` 文件中。

1. 打開 `src/App.vue`。
2. 找到 `enableThemeManager` 變數。
3. 將其設為 `true` 以開啟編輯器，或設為 `false` 以關閉（生產環境通常建議關閉）。

```javascript
// src/App.vue

<script setup>
// ... 其他 import

// 控制 ThemeManager 開關
const enableThemeManager = ref(false) // true: 開啟, false: 關閉
provide('enableThemeManager', enableThemeManager)
</script>
```

### 功能說明

開啟 `ThemeManager` 後，您可以在頁面右側看到編輯面板，功能包括：
- **顏色主題切換**：選擇不同的配色方案。
- **浮動圖管理**：上傳、更換、排序左右兩側的浮動圖片（支援拖曳排序）。
- **預覽與匯出**：即時預覽效果並匯出設定檔。

## 配色方案使用狀態

| 主題代碼 | 主色 (Primary) | 副色 (Secondary) | 使用日期 | 狀態 |
| :--- | :--- | :--- | :--- | :--- |
| 2501231 | #080F22 | #D2D3D8 | - | 未使用 |
| 2501232 | #1D0241 | #BBB5F8 | - | 未使用 |
| 2501233 | #D9DFFA | #425181 | - | 未使用 |
| 2501234 | #FAD9DF | #814251 | - | 未使用 |

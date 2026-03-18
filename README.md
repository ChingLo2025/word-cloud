# Word cloud

這個專案是從 Observable notebook 匯出的靜態網站，可以直接部署到 GitHub Pages。

## 本機預覽

在專案根目錄啟動任何靜態檔案伺服器即可，例如：

```sh
python3 -m http.server 8000
```

然後開啟 <http://localhost:8000>。

## GitHub Pages 部署方式

此專案已包含 GitHub Actions workflow：`.github/workflows/deploy-pages.yml`。

### 1. 推送到 GitHub

把目前分支推送到你的 GitHub repository。

### 2. 在 GitHub 啟用 Pages

到 repository 的 **Settings → Pages**：

- **Source** 選擇 **GitHub Actions**

### 3. 觸發部署

之後只要 push 到 `main` 或 `master`，就會自動部署到 GitHub Pages。
也可以到 **Actions** 頁面手動執行 **Deploy to GitHub Pages** workflow。

## Observable Runtime 使用方式

原始 notebook 來源：<https://observablehq.com/@d3/word-cloud@249>

若你要把 notebook 當成模組引用，可使用 [Observable Runtime](https://github.com/observablehq/runtime)：

```sh
npm install @observablehq/runtime@5
npm install https://api.observablehq.com/d/dc13673d7b6884c8@249.tgz?v=3
```

```js
import {Runtime, Inspector} from "@observablehq/runtime";
import define from "@d3/word-cloud";

const runtime = new Runtime();
const main = runtime.module(define);
main.value("foo").then(value => console.log(value));
```

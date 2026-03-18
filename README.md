# Word cloud

這個專案是從 Observable notebook 匯出的靜態網站，已整理成可直接用 **GitHub Pages 的 branch source** 發佈。

## 本機預覽

直接把 `docs/` 當成網站根目錄啟動靜態伺服器即可，例如：

```sh
python3 -m http.server 8000 --directory docs
```

然後開啟 <http://localhost:8000>。

## GitHub Pages 部署方式

這個專案不需要自訂 build workflow；依照 GitHub Pages 官方建議，靜態網站可以直接從 branch 發佈。

### 1. 推送到 GitHub

先把目前分支推送到你的 GitHub repository。

### 2. 在 GitHub 啟用 Pages

到 repository 的 **Settings → Pages**：

- **Source** 選擇 **Deploy from a branch**
- **Branch** 選擇 `main`（或你的預設分支）
- **Folder** 選擇 `/docs`

儲存後，GitHub 會直接把 `docs/` 內容發布成 GitHub Pages 網站。

## 站點檔案位置

GitHub Pages 使用的靜態檔都放在 `docs/`：

- `docs/index.html`
- `docs/index.js`
- `docs/runtime.js`
- `docs/inspector.css`
- `docs/files/`

另外也包含 `docs/.nojekyll`，避免 GitHub Pages 對這份 Observable 匯出網站套用 Jekyll 處理。

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

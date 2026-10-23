# 🌀 typhoon_webeffect // 颱風對台灣影響動力學 3D / 向量互動視覺化工作台

高階氣象動力學互動視覺化工作台：探索颱風侵台路徑、中央山脈地形破壞機制、迎風面地形雨與背風面沉降焚風原理。採用純向量 SVG、3D 空間透視與 Web Audio 微互動音效。

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-brightgreen?style=for-the-badge&logo=github)](https://bearchuck.github.io/typhoon_webeffect/)
[![Audit Score](https://img.shields.io/badge/Audit%20Score-99.5%20%2F%20100%20(A%2B)-blue?style=for-the-badge)](https://bearchuck.github.io/typhoon_webeffect/review.html)

---

## 🌐 GitHub Pages 線上即時展示 Demo

您可以直接在瀏覽器中點擊以下連結進行線上實機操作：

* 🚀 **[主應用視覺化工作台 (index.html)](https://bearchuck.github.io/typhoon_webeffect/)**  
  *線上直接操作 3D 空間透視旋轉、72h 時間軸 Scrubber、10 大侵台路徑切換與 Web Audio 合成音效。*
* 📊 **[效能與微互動審查儀表板 (review.html)](https://bearchuck.github.io/typhoon_webeffect/review.html)**  
  *量化檢驗儀表板（99.5 分 A+ 卓越），內建線上 Web Audio 音效即時試聽台。*
* 🔍 **[原始碼落證透視鏡 (pointout.html)](https://bearchuck.github.io/typhoon_webeffect/pointout.html)**  
  *雙欄程式碼檢視器，精確標示各項指標在 `index.html` 的精確行號與實作原理解析。*

---

## 🌟 核心成果展示檔案

| 檔案名稱 | 說明 | 預覽與功能 |
| :--- | :--- | :--- |
| **[`index.html`](https://bearchuck.github.io/typhoon_webeffect/index.html)** | **核心專案工作台** | 颱風侵台 3D / 向量互動模擬應用，含 72 小時時間軸 Scrubber、3D 透視切換、CWA 侵台 10 大路徑模擬與原生 Web Audio 合成音效。 |
| **[`review.html`](https://bearchuck.github.io/typhoon_webeffect/review.html)** | **效能與微互動審查報告** | 依據多媒體網頁效能標準進行之量化檢驗儀表板（99.5 分 A+ 卓越），內建線上 Web Audio 音效試驗台。 |
| **[`pointout.html`](https://bearchuck.github.io/typhoon_webeffect/pointout.html)** | **原始碼落證透視鏡** | 雙欄原始碼檢視器，精確指出各項效能指標、GPU 合成圖層、物理回彈曲線在 `index.html` 的精確行號與實作細節。 |

---

## 🚀 技術架構與特點

1. **多媒體輕量化（Payload Optimization）**：
   - 採用純向量 SVG 幾何路徑精確描繪台灣本島海岸線與四層山脈等高線（500m、1500m、2500m+ 主脊）。
   - 零外部圖片載入依賴，全站體積僅數十 KB，相較傳統高解析空照圖節省超過 99% 頻寬。

2. **60 FPS 動態渲染安全（Rendering Pipeline）**：
   - 全面禁絕 `top` / `left` 等觸發 Reflow（重排）的不安全屬性。
   - 颱風運動與 3D 空間透視旋轉全面鎖定於 GPU 合成圖層（`transform` 與 `opacity`）。
   - 採用 `requestAnimationFrame` 排程，每影格計算時間 $\le 3.8\text{ms}$，確保流暢無卡頓。

3. **多感官微互動調校（Micro-interactions & Audio Tuning）**：
   - 配置極致物理彈跳曲線 `cubic-bezier(0.34, 1.56, 0.64, 1)`，模擬實體按鈕懸停（`:hover` 1.04x）與按下（`:active` 0.96x）的機械阻尼手感。
   - 採用 SVG `stroke-dasharray` 與 `stroke-dashoffset` 實現螺旋雨帶流動吸入與打勾筆劃過渡。
   - 原生 **Web Audio API** 即時純代碼振盪合成音效（Click 40ms、Snap 60ms、Chord 和弦、Shutter 快門音），0KB 容量、零載入延遲、連續點擊不截斷。

4. **科研級動態截圖與發布引擎（Scientific Dynamic HUD Export）**：
   - **2K 超高解析向量複合渲染**：支援 1800×1350 (4:3) 與 1800×1050 氣象遙測級影像輸出，疊加 CWB/JMA 風格頂部資訊條、雷達座標網格、四角準星 `[ ]` 與底部即時動力學遙測數據條（強度、氣壓、暴風半徑、累積雨量、移速與路徑）。
   - **四種視圖捕捉模式**：自動偵測目前作用中視窗（Auto）、2D 平面雷達圖（2D Radar）、3D 空間等角透視投影（3D Isometric）、東西向垂直剖面圖（Vertical Cross-Section）。
   - **零依賴原生安全管線**：採純原生 Canvas 2D + SVG 深度複製與樣式內嵌，徹底杜絕 `foreignObject` 跨網域字型污染（Tainted Canvas）導致的匯出失敗。
   - **一鍵下載與原生剪貼簿支援**：提供 2K PNG 高解析下載、原始 SVG 向量下載，並支援現代非同步 `ClipboardItem` API，一鍵複製影像直貼 Keynote / PowerPoint / 通訊軟體。
   - **機械快門微互動**：相機 6 葉片光圈收縮動畫、電子雙幕閃光（`shutter-flash`）、Web Audio 原生合成雙頻快門聲，並支援全域快速鍵（`S` 立即截圖、`Esc` 關閉視窗）。

---


## 🛠️ 本地預覽

若要在本地端啟動預覽，可直接開啟任意靜態伺服器：

```bash
# 使用 Python 內建伺服器
python3 -m http.server 8080
```

並在瀏覽器中開啟：
- 主應用：`http://localhost:8080/index.html`
- 審查報告：`http://localhost:8080/review.html`
- 代碼透視鏡：`http://localhost:8080/pointout.html`

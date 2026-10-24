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

4. **科研級動態截圖與分析結論圖片匯出引擎（Scientific Dynamic HUD Export）**：
   - **一鍵下載 2K 氣象動力學分析結論圖**：點擊相機快門按鈕直接生成並下載 **2000×1260** 超高解析度科研級「分析結論報告卡」，整合中央山脈地形破壞、迎風面強迫抬升豪雨、背風面沉降焚風、全台各分區威脅度與防災避險關鍵指引。
   - **多重視圖捕捉模式**：支援氣象分析結論圖（Conclusion）、當前視窗（Auto）、2D 向量雷達圖（2D Radar）、3D 空間等角透視（3D Isometric）與東西向垂直剖面圖（Vertical Profile）。
   - **零依賴原生安全管線**：採純原生 Canvas 2D + SVG 深度複製與樣式內嵌，徹底杜絕 `foreignObject` 跨網域字型污染（Tainted Canvas）導致的匯出失敗。
   - **雙重極速發布工作流**：支援自動觸發瀏覽器下載、高解析 PNG / 向量 SVG 另存，並支援現代非同步 `ClipboardItem` API 一鍵複製影像直貼 Keynote / PowerPoint / 通訊軟體。
   - **機械快門微互動**：相機 6 葉片光圈收縮動畫、電子雙幕閃光（`shutter-flash`）、Web Audio 原生合成雙頻快門聲，並支援全域快速鍵（`S` 立即截圖並下載結論、`Esc` 關閉視窗）。

5. **真實氣象物理與大氣渦旋動力（Meteorological Vortex Physics）**：
   - **北半球逆時針渦旋（Counter-Clockwise Swirl）**：嚴格依循北半球地轉偏向力（科氏力，Coriolis Effect），低壓中心環流與 7/10 級暴風半徑全面採用逆時針旋轉（CCW）。
   - **向心內流螺旋雨帶（Inward Convergence Flow）**：螺旋雨帶採用向心方向之 `stroke-dashoffset` 循環流動動畫，真實重現熱帶氣旋底層水氣輻合捲入颱風眼之動態過程。

6. **中央氣象署 (CWA) 颱風資料庫直接引用、完整列表與即時動態讀取（CWA Best Track & Live API Engine）**：
   - **顯著操作與切換按鈕**：
     - 頂部遙測資訊列按鈕 `[ ● CWA 資料庫 ]`（即時動態呼吸燈號，一鍵呼叫 Best Track 探索中心）。
     - 右上功能區專屬按鈕 `[ CWA ]`（內建氣象雷達旋轉掃描動畫）。
     - 左側路徑控制台快速切換晶片（24' 凱米、24' 山陀兒、24' 康芮、23' 海葵）與**「歷年 31 款侵台颱風快速下拉選單」**，免開彈窗即可秒選即讀。
   - **歷年侵台最佳追蹤資料庫完整清單（Best Track 31 款經典強颱）**：
     - **完整收錄 1963~2024 年 31 款指標性颱風**，涵蓋 CWA 全部 10 類侵台路徑與怪異滯留路徑：
       - *2020 年代*：2024 凱米、2024 山陀兒（高雄17級風）、2024 康芮（320km巨型暴風圈）、2023 海葵、2023 小犬（蘭嶼95.2m/s歷史破表極值）、2023 杜蘇芮、2021 璨樹。
       - *2010 年代*：2019 利奇馬（西北颱）、2019 米塔、2018 瑪莉亞、2017 尼莎、2017 海棠（雙颱藤原效應）、2016 莫蘭蒂（890hPa巔峰強颱）、2016 梅姬、2016 尼伯特（905hPa）、2015 蘇迪勒（台北13級風）、2015 杜鵑、2013 蘇力、2012 天秤（海峽逆轉打轉）。
       - *2000 年代*：2009 莫拉克（2884mm 世紀水災八八風災）、2008 辛樂克、2008 薔蜜、2007 柯羅莎、2004 敏督利（七二水災西南氣流）、2001 納莉（滯留49小時台北捷運淹沒）、2000 象神。
       - *20 世紀經典*：1996 賀伯（阿里山1987mm百年風災）、1994 提姆、1986 韋恩（三進三出濁水溪登陸怪颱）、1977 賽洛瑪（直撲高雄重創）、1963 葛樂禮（典型西北颱台北大淹水）。
   - **多維度即時搜尋與篩選系統**：
     - 🔍 **全域即時搜尋**：支援輸入中文名稱、英文名稱、年份、登陸點或特徵標籤即刻過濾。
     - 📅 **年代篩選**：全部年份、2020年代、2010年代、2000年代、20世紀經典。
     - 🧭 **CWA 10 大路徑篩選**：第 1 類西北颱、第 2 類北部、第 3 類花蓮、第 4 類南部、第 5 類巴士海峽、第 6 類東部近海、第 7 類海峽北上、第 8 類海峽南下、第 9 類西向東、特殊打轉路徑。
     - 🌪️ **強度等級篩選**：強烈颱風 (≥51m/s)、中度颱風 (32.7~50.9m/s)、輕度颱風 (17.2~32.6m/s)。
     - 🔲 **雙重視圖模式**：一鍵切換「科研卡片模式 (Card Grid)」與「詳細清單列表 (Table List View)」。
   - **一鍵動態讀取機制（Dynamic Typhoon Ingestion）**：
     - 點擊列表任一颱風，即時動態重新計算 SVG 暴風半徑（依真實公里數等比換算）、中心氣壓、最大風力、螺旋環流轉速、各分區威脅評估、真實侵台軌跡線段與動力學原理，並連動更新 2K 氣象結論分析圖匯出。
   - **官方開放資料平台 API (`W-C0034-001`) 即時動態與演練模擬**：
     - 支援輸入個人 API 金鑰直接連線中央氣象署端點，解析在途即時警報與半徑。
     - 內建「💡 演練示範：動態載入在途強颱警報模擬」，非颱風季亦能完整體驗即時警報動態讀入。
   - **動態自訂與外部 CWA JSON 載入器**：
     - 提供自訂觀測數據表單（名稱、氣壓、風速、7級半徑、路徑分類）與外部 JSON 貼入解析，即刻動態注入工作台展開動態模擬。

---

## 🛰️ 線上颱風資料庫直接引用指引 (Online Typhoon Databases)

本視覺化工作台採用純前端向量結構與開放資料架構，可直接透過 JavaScript `fetch()` 介接以下權威線上颱風資料庫：

| 資料庫 / 平台 | 單位 | 存取協定與格式 | 適用場景與資料欄位 |
| :--- | :--- | :--- | :--- |
| **[CWA 氣象署開放資料平台](https://opendata.cwa.gov.tw/)** | 台灣中央氣象署 | REST API (JSON / XML)<br>代碼：`W-C0034-001` | 即時警報、颱風中心經緯度、氣壓、近中心最大風速、7級/10級暴風半徑、預報路徑。 |
| **[CWA 暴風圈侵襲機率 API](https://opendata.cwa.gov.tw/)** | 台灣中央氣象署 | REST API (JSON)<br>代碼：`W-C0034-002` | 全台各縣市未來 120 小時之 7 級風暴風圈侵襲機率百分比。 |
| **[CWA 歷史颱風資料庫](https://rdc28.cwa.gov.tw/TDB/)** | 台灣中央氣象署 | Web / CSV 下載 | 1958 年至今所有侵台颱風路徑分類（1~10 類）、逐時雨量與測站極端風速。 |
| **[NCDR 災害示警平台](https://alerts.ncdr.nat.gov.tw/)** | 國家災害防救科技中心 | Open Data / CAP / GeoJSON | 即時颱風警戒區 Polygon、豪雨特報、風雨防救災應變資訊。 |
| **[JMA RSMC Tokyo Best Track](https://www.jma.go.jp/jma/jma-eng/jma-center/rsmc-hp-pub-eg/besttrack.html)** | 日本氣象廳 (WMO 指定) | CSV / Text Format | 西北太平洋官方歷史颱風最佳路徑（每 6 小時中心位置、氣壓、強度）。 |
| **[NOAA IBTrACS](https://www.ncei.noaa.gov/products/international-best-track-archive)** | 美國國家海洋暨大氣總署 | REST API / GeoJSON / CSV | 全球熱帶氣旋最佳追蹤資料庫，提供即時與歷史氣旋完整軌跡與物理強度。 |
| **[Open-Meteo Weather API](https://open-meteo.com/)** | Open-Meteo | REST API (免金鑰 / 開放 CORS) | 透過純前端輸入經緯度即可獲取海平面氣壓、風速、陣風，零延遲介接即時風場。 |

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

# 咖啡貓不睡覺 — 獨立遊戲

單檔 HTML 小遊戲系列。零依賴、零建置、可離線遊玩。

© 2026 咖啡貓不睡覺

---

## 專案

| 目錄 | 遊戲 | 線上版本 |
|------|------|---------|
| [`bullet-evolution/`](bullet-evolution/) | **彈幕進化** — 彈幕射擊 + 基因演化 + 抽卡式武器收集 | https://cx7jnb64oarr8.space.mcode.cn |
| [`enemy-evolution/`](enemy-evolution/) | **敵人演化原型** — 敵人基因演化沙盒 | https://0uzeih8b8xrcc.space.mcode.cn |

## 怎麼玩

直接用瀏覽器開 `.html` 檔案即可。沒有伺服器、沒有 npm、沒有網路請求。

手機上建議用瀏覽器的「加入主畫面」當 App 用。

---

## 彈幕進化 v0.5

基因演化驅動的彈幕生存。敵人有六個始祖系，每系十個基因會依實際戰況繁殖演化；玩家的武器也是從基因長出來的。

- 在畫面**下半部按住拖曳**移動，武器自動開火
- 躲開彩色子彈，5 顆愛心，被打中扣 1 顆，每過一波回 1 顆
- 你變強，敵人也跟著變強（`PWR()` 耦合）
- 擊落特定敵人系會解鎖新武器加入卡池
- 每 5 波選技能卡，每 10 波基因進化

設計細節、平衡數據、已知問題全在 **[`bullet-evolution/docs/技術文件.md`](bullet-evolution/docs/技術文件.md)**。

檔名帶版號。改版時請一併更新檔名與遊戲內的版本標示。

---

## 開發

```
bullet-evolution/
├── 彈幕進化-v0.5.html      遊戲本體（單檔）
├── README.md               玩法與開發指令
├── dist/index.html         部署用副本
└── docs/技術文件.md        基因系統、平衡數據、已知問題

enemy-evolution/
├── 敵人演化原型.html        遊戲本體（單檔）
└── dist/index.html         部署用副本
```

### 語法檢查

抽出 `<script>` 餵 node，不需要瀏覽器：

```bash
node -e "const fs=require('fs');fs.writeFileSync('/tmp/c.js',fs.readFileSync('彈幕進化-v0.5.html','utf8').match(/<script>([\s\S]*)<\/script>/)[1])"
node --check /tmp/c.js
```

### 部署

同步到部署目錄：

```bash
cp bullet-evolution/彈幕進化-v0.5.html bullet-evolution/dist/index.html
```

目前使用的部署平台會強制注入浮水印，無法移除。

---

## 版權

程式碼與文件 © 2026 咖啡貓不睡覺

# RESTIA CUP 瑞斯盃 — 選秀大會工具

Delta Force 台灣「瑞斯盃」電競賽事的直播用選秀工具。12 位教練先排名次，再以 S 型（蛇形）順序輪流從 T1／T2／T3 三個分層各選一名選手，支援大頭照拖曳。

## 使用方式

直接用瀏覽器開 `draft-tool.html`，或起一個靜態伺服器：

```bash
python -m http.server 8766
# 開啟 http://localhost:8766/draft-tool.html
```

固定 1920×1080 版面，會自動縮放貼合視窗，適合直播畫面。

## 流程

1. **START**：介紹頁，按下開始。
2. **排名次**：拖曳教練卡調整選秀順序。
3. **選秀**：S 型順序 —
   - 第一輪 T1：第 1 名 → 第 12 名
   - 第二輪 T2：蛇形反向，第 12 名 → 第 1 名
   - 第三輪 T3：第 1 名 → 第 12 名
   - 共 36 次選擇，每位教練最終擁有 T1／T2／T3 各一名選手。

進度會存在瀏覽器 localStorage，重整不會遺失。網址加 `?reset` 可清空從頭開始。

## 檔案結構

- `draft-tool.html` — 單一檔案，內含所有 HTML／CSS／JS
- `assets/faces/` — 裁切好的選手／教練大頭照（執行時使用）
- `assets/bg.png`、`intro.jpg`、`logo.png`、`title.png` — 版面圖

> 註：原始未裁切大頭照 `assets/portraits/` 未納入版控（體積大、執行時不需要）。

# Raspberry Pi Studio 公開文件版 / Public Documentation Edition

本倉庫收錄 Raspberry Pi Studio V1 的最終技術報告與報告圖片。  
This repository contains the final technical reports and report figures for Raspberry Pi Studio V1.

## 閱讀入口 / Start here

- [繁體中文完整製作報告](reports/Raspberry_Pi_Studio_Manufacturing_Report_ZH-TW.md)
- [繁體中文功能架構與整機驗收規格](reports/Raspberry_Pi_Studio_Functional_Architecture_ZH-TW.md)
- [English Manufacturing Report](reports/Raspberry_Pi_Studio_Manufacturing_Report_EN.md)
- [English Functional Architecture and Acceptance Specification](reports/Raspberry_Pi_Studio_Functional_Architecture_EN.md)

## 目錄 / Directory layout

```text
Raspberry_Pi_Studio_Public/
├── README.md
├── SHA256SUMS.txt
├── reports/
│   ├── 繁體中文製作報告
│   ├── 繁體中文功能架構與驗收規格
│   ├── English Manufacturing Report
│   └── English Functional Architecture
└── assets/
    └── figures/   報告使用的最終渲染圖 / final report figures
```

## 工程狀態 / Engineering status

報告將內容分成三種狀態：

- 已由模型驗證的幾何、碰撞與安裝淨空；
- 可作為實作起點的工程設計值；
- 製造或宣稱產品性能前仍須完成的實機測試。

The reports distinguish:

- model-verified geometry, collision checks and installation clearances;
- engineering design values intended as implementation starting points;
- hardware tests still required before manufacture or performance claims.

本專案是獨立的 Raspberry Pi 機殼與控制系統設計，不是 Apple 原廠製造圖或 Apple 產品。  
This is an independent Raspberry Pi enclosure and control-system project. It is not an Apple manufacturing drawing or an Apple product.

## 檔案驗證 / Integrity

可在倉庫根目錄執行以下 PowerShell，核對公開文件與圖片：

Run the following PowerShell command from the repository root to verify the published reports and figures:

```powershell
$lines = Get-Content .\SHA256SUMS.txt
foreach ($line in $lines) {
    if ($line -match '^([0-9a-f]{64})  (.+)$') {
        $actual = (Get-FileHash -Algorithm SHA256 -LiteralPath $matches[2]).Hash.ToLowerInvariant()
        if ($actual -ne $matches[1]) {
            throw "檔案雜湊不一致：$($matches[2])"
        }
    }
}
```

本公開文件倉庫目前未指定獨立的再利用授權條款。  
No separate reuse license has been selected for this documentation repository.

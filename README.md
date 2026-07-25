# Raspberry Pi Studio — Public Documentation Edition

> **PUBLIC DOCUMENTATION EDITION / 公開文件版**
>
> This repository intentionally contains final reports and the figures embedded in those reports only. It does not contain CAD, printable meshes, source models, backups, build scripts, audit internals or supplied reference assets.
>
> 本倉庫刻意只公開最終報告與報告內使用的圖片，不包含 CAD、可列印網格、來源模型、備份、建模腳本、稽核內部資料或使用者提供的參考素材。

## Start here / 閱讀入口

- [繁體中文完整製作報告](reports/Raspberry_Pi_Studio_Manufacturing_Report_ZH-TW.md)
- [English Manufacturing Report](reports/Raspberry_Pi_Studio_Manufacturing_Report_EN.md)
- [繁體中文功能架構與整機驗收規格](reports/Raspberry_Pi_Studio_Functional_Architecture_ZH-TW.md)
- [English Functional Architecture and Acceptance Specification](reports/Raspberry_Pi_Studio_Functional_Architecture_EN.md)
- [Bill of Materials / BOM](reports/Raspberry_Pi_Studio_BOM.csv)
- [Raspberry Pi 5 I/O Pin Map](reports/Raspberry_Pi_Studio_IO_Pin_Map.csv)
- [Power Budget](reports/Raspberry_Pi_Studio_Power_Budget.csv)

## Public scope / 公開範圍

Included:

- final Traditional Chinese and English reports;
- procurement, GPIO/I²C/UART and power-budget tables;
- six derived final-render figures referenced by the manufacturing reports;
- a SHA-256 manifest for the public files.

Explicitly excluded:

- `.blend`, `.stl`, `.glb`, `.usdz`, STEP, 3MF and other model files;
- original reference models and reference photographs;
- private backups, Blender rebuild scripts, logs and raw audit packages;
- the history of the private development repository.

The public repository has an independent Git history. It is not a filtered branch or clone of the private model repository.

## Directory layout

```text
Raspberry_Pi_Studio_Public/
├── README.md
├── SHA256SUMS.txt
├── reports/
│   ├── bilingual manufacturing reports
│   ├── bilingual functional architecture reports
│   ├── BOM
│   ├── I/O pin map
│   └── power budget
└── assets/
    └── figures/   final report figures only
```

## Engineering status

The enclosure geometry and model-level collision/clearance checks were completed in the private development project. The public documents clearly separate:

- model-verified geometry;
- engineering design values;
- hardware tests still required before manufacture or product claims.

This is an independent Raspberry Pi enclosure project and is not an Apple manufacturing drawing or an Apple product.

## Integrity

Run the following from the repository root to verify public files:

```powershell
$lines = Get-Content .\SHA256SUMS.txt
foreach ($line in $lines) {
    if ($line -match '^([0-9a-f]{64})  (.+)$') {
        $actual = (Get-FileHash -Algorithm SHA256 -LiteralPath $matches[2]).Hash.ToLowerInvariant()
        if ($actual -ne $matches[1]) { throw "Hash mismatch: $($matches[2])" }
    }
}
```

No separate reuse license has been selected for this public documentation repository.

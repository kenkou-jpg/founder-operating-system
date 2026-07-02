# Project Registry

> Founder Operating System のマルチプロダクト対応レイヤー。
> 各プロジェクト固有の情報をここで管理し、Common OS への書き込みを禁止する。

---

## 基本思想

Founder Operating System は **Common OS** である。
プロジェクト固有の情報（PR 履歴・責務履歴・KPI）は、このディレクトリ配下の **Project Registry** で管理する。

```
Founder Operating System（Common OS）
  ↓ 固有情報はここへ
Project Registry
  ├── ippo/
  ├── fasting/（将来）
  ├── imaging-agriculture/（将来）
  └── [future-app]/（拡張可能）
```

---

## ディレクトリ構成

```
project-registry/
├── README.md                     ← このファイル
├── PROJECT_REGISTRY_POLICY.md    ← 分離ポリシー定義
│
├── ippo/
│   ├── README.md                 ← IPPO Registry 概要
│   ├── PROJECT_PROGRESS.md       ← PR 進捗・Milestone 履歴
│   ├── RESPONSIBILITY_HISTORY.md ← PR 単位の責務・Scope 履歴
│   └── WEEKLY_METRICS.md         ← 週次 KPI・Velocity
│
└── [future-app]/                 ← 同構造で追加可能
```

---

## 新プロジェクト追加方法

1. `project-registry/[app-name]/` ディレクトリを作成する
2. `ippo/` の4ファイルを複製してプロジェクト名を書き換える
3. `FOUNDER_OS_REFERENCE.md` の Project Registry Mapping に追加する
4. Common OS には一切書かない

---

## 参照先

- `PROJECT_REGISTRY_POLICY.md` — 分離ルール定義
- `FOUNDER_OS_REFERENCE.md` — External Repository Mapping

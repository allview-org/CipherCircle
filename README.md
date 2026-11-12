<!-- 產品／專案：CipherCircle｜法人／事業體：AllView／全視界（完整法定名稱 [待確認]）｜日期：2026-11-11（Asia/Taipei）｜草稿 v0.3 -->
# CipherCircle
C2-AV-FHS 密圈 CipherCircle FHE 密文防護之偽匿名社群 for 思想領袖、敏感議題討論群體
# AllView Anonymous & Non-Repudiable Social Network (`allview-fhe-social-app`)

[![PMO Category: Functional Technology](https://img.shields.io/badge/PMO-Category%203%20(Functional)-blue.svg)](#pmo-governance)
[![Repo ID: C3-AV-FHS-F](https://img.shields.io/badge/Repo%20ID-C3--AV--FHS--F-green.svg)](#pmo-governance)
[![Security Level: E2EE + FHE + Audit](https://img.shields.io/badge/Security-Signal%20Protocol%20%7C%20FHE%20%7C%20Audit%20Chain-red.svg)](#security-architecture)
[![QA Readiness: Gate 1-3](https://img.shields.io/badge/QA%20Gates-Scope%20%7C%20Design%20%7C%20Build-orange.svg)](#qa-acceptance--testing)

結合 **Telegram / Pixelfed 級極致視覺化體驗** 與 **Signal 級端對端加密安全**，並透過 **FHE（Fully Homomorphic Encryption，全同態加密）** 實現密文運算，同時具備「全域匿名操作」與「授權方不可否認證據鏈」的新世代社群與知識交流平台。

---

## 📑 目錄 (Table of Contents)
1. [系統願景與核心價值](#系統願景與核心價值)
2. [與整體大系統的關聯 (System Context)](#與整體大系統的關聯-system-context)
3. [核心功能模組 (Feature Matrix)](#核心功能模組-feature-matrix)
4. [技術架構與混合安全模型](#技術架構與混合安全模型)
5. [資料流與典型使用者旅程](#資料流與典型使用者旅程)
6. [專案目錄結構 (Repository Structure)](#專案目錄結構-repository-structure)
7. [快速開始與本地開發 (Getting Started)](#快速開始與本地開發-getting-started)
8. [QA 驗收標準與測試計畫 (QA Acceptance)](#qa-驗收標準與測試計畫-qa-acceptance)
9. [治理、權限與 PMO 規範 (PMO Governance)](#治理權限與-pmo-規範-pmo-governance)

---

## 1. 系統願景與核心價值

本專案旨在解決現代社群網路於「隱私保護」與「可信任問責」之間的根本衝突：
- **極致易用性**：提供如 Instagram / Pixelfed 的動態牆、短影音、故事、階層論壇與直播授課，免除加密工具傳統的生硬學習門檻。
- **公開環境偽匿名**：對一般使用者與公開檢索環境完全隱匿真實身分，以長期加密公私鑰對與零知識證明（ZKP）進行合法成員驗證。
- **授權方不可否認（Non-Repudiation）**：所有互動（發表、點擊、閱讀、資料調用）皆即時生成可驗證收據（Receipt），寫入 Merkle 證據鏈，防範竄改與事後否認。
- **全同態加密（FHE）運算**：平台在無法解密原始資料的前提下，執行推薦演算法、互動指標聚合、匿名投票與私密過濾。

---

## 2. 與整體大系統的關聯 (System Context)

本軟體隸屬於 **「四即一、一即四」全域事業體架構**，具體協同關係如下：
* **四之一：AllView (`allview.today`)**：本專案為 AllView 文化傳播、宗教與知識論壇的核心數位空間載體。
  * 對應預售專案：`allview-fhe-social-presale` (`C2-AV-FHS`)
  * 本功能實作專案：`allview-fhe-social-app` (`C3-AV-FHS-F`)
* **四之二：AEGIS (`aegis.expert`)**：底層共用 FHE 密碼學核心函式庫及硬體加速介面支援（`platform-he-fhe-core`）。
* **一／四之四：Wonderland Center (`wonderland.center`)**：作為全域阿米巴組織、群眾發包、義工動員與資源點數調度（`platform-resource-points-conversion`）之入口。

```
+--------------------------------------------------------------------------+
|                     Allview.today Corporate (C1-AV-CORP)                 |
+--------------------------------------------------------------------------+
       |                                                    |
       v                                                    v
[Presale / Crowdfunding]                             [Functional Engine]
allview-fhe-social-presale                          allview-fhe-social-app
       |                                                    |
       +--------------------+-------------------------------+
                            |
       +--------------------+-------------------------------+
       |                                                    |
       v                                                    v
[AEGIS FHE Core]                                     [Platform Engine]
platform-he-fhe-core (OpenFHE / SEAL)                platform-resource-points-conversion
```

---

## 3. 核心功能模組 (Feature Matrix)

### A. 視覺化內容與社群層 (UX & Social Layer)
* **動態牆與限時動態**：多圖文、短影音、Stories / Reels 風格流暢排版。
* **社群互動**：點讚、表情回饋、轉發、私密收藏、主題標籤（Hashtags）。
* **探索與過濾**：跨裝置同步（Mobile First / Responsive Web），支援低學習成本探索頁面。

### B. 端對端安全通訊 (Signal Protocol Messaging)
* **X3DH + Double Ratchet**：提供嚴密的前向保密（PFS）與後向保密（PCS）。
* **多方通訊**：加密群聊、語音/視訊串流通話與螢幕共享。
* **自毀機制**：限時閱後即焚、本機受控金鑰備份。

### C. 論壇、演講與課程模組 (Knowledge & Forum)
* **階層式論壇**：主題串討論、精華置頂、權限式討論版塊。
* **直播演講與授課**：端對端加密串流（E2EE Live Stream），支援預約演講。
* **課程與教材管理**：課堂講義發布、作業加密繳交、測驗與成果進度追蹤。

### D. 匿名認證與 ZK 機制 (Anonymity & ZK Proofs)
* **偽匿名身分體系**：基於 Ed25519 / Dilithium 金鑰對生成匿名公眾身分。
* **零知識證明（ZKP）**：證明特定組織身分、會員資格或閱讀權限，而不揭露個人真實帳號。

### E. FHE 密文運算 (Confidential Computing)
* **私密推薦與標籤匹配**：在密文狀態下比對使用者興趣與文章向量。
* **密文統計與匿名投票**：同態加法累計投票數，避免計票方提前獲悉個體傾向。

### F. 證據鏈與可驗證審計 (Audit Chain & Receipts)
* **不可否認閱讀收據**：每次調用或閱讀內容皆產生簽章收據（Read Receipt）。
* **Merkle Tree 歷史封裝**：將收據定期打包並生成 Merkle Root，確保存證不可竄改。
* **條件式調閱介面**：僅當司法仲裁或授權門檻金鑰（Threshold Signatures）湊齊時方可檢驗證據鏈。

---

## 4. 技術架構與混合安全模型

為兼顧**低延遲體驗**與**高強度密碼學運算**，系統嚴格採取混合切割策略：

```
+-----------------------------------------------------------------------------+
|                           Client Application Layer                          |
|         (Flutter / React / Tauri Native Desktop + Secure Storage)           |
+-----------------------------------------------------------------------------+
            | (E2EE Signal Protocol)                 | (FHE Ciphertexts & ZKP)
            v                                        v
+-----------------------------+        +--------------------------------------+
|   Real-time Comms Gateway   |        |        FHE & Analytics Service       |
|    - libsignal / X3DH       |        |        - OpenFHE / TFHE-rs           |
|    - WebRTC SFU (E2EE Call) |        |        - Homomorphic Ranking         |
+-----------------------------+        +--------------------------------------+
            |                                        |
            +--------------------+-------------------+
                                 |
                                 v
+-----------------------------------------------------------------------------+
|                        Audit & Non-Repudiation Layer                        |
|  - Cryptographic Receipts (Ed25519 Signatures + RFC 3161 Timestamps)         |
|  - Merkle Tree State Ledger / Append-only Storage Engine                     |
+-----------------------------------------------------------------------------+
```

| 架構分層 | 技術選型 | 承擔角色與設計邊界 |
| :--- | :--- | :--- |
| **前端 UX** | Flutter / React (Next.js) | 參考 Pixelfed 設計語言；保持 60fps 體驗，不直接跑重度 FHE。 |
| **即時通訊** | `libsignal` (Rust / C bindings) | 負責所有一對一私訊、群聊與 E2EE 通話信令。 |
| **身分與 ZK** | Circom + SnarkJS / Halo2 | 負責匿名資格驗證，保護使用者真實 IP 及長期身分。 |
| **FHE 密文運算** | OpenFHE / TFHE-rs / SEAL | 離線/批次執行密文推薦、特徵相似度計算與投票聚合。 |
| **證據鏈日誌** | Rust Append-only Engine + Merkle | 儲存不可竄改收據，鏈上/分散式存儲只放 Opaque Root Hash。 |
| **儲存底層** | S3 相容物件存儲 + SQL (Postgres) | 嚴格執行信封加密（Envelope Encryption），密鑰完全由客戶端持有。 |

---

## 5. 資料流與典型使用者旅程

```
[使用者 A: 匿名發布]
   │
   ├── 1. 生成內容 ──> 客戶端對稱加密 (AES-GCM-256)
   ├── 2. 動作簽名 ──> 產生 Action Receipt (Ed25519)
   └── 3. 提取特徵 ──> FHE 加密特徵向量 ──> 上傳至後端 (密文儲存)
                                                   │
[使用者 B: 匿名檢索與閱讀]                         │
   │                                               ▼
   ├── 4. 取得內容 ──> 本地解密檢視          [Evidence Ledger]
   └── 5. 回傳收據 ──> 產生 Read Receipt ───> 寫入 Merkle 證據鏈 (不可否認)
                                                   ▲
[審計 / 爭端驗證方 (仲裁門檻金鑰)]                 │
   │                                               │
   └── 6. 提交授權憑證 ───────────────────────────┴─> 驗證特定閱讀/發表證據鏈
```

---

## 6. 專案目錄結構 (Repository Structure)

```text
allview-fhe-social-app/
├── .github/
│   ├── CODEOWNERS                      # 權限邊界維護團隊
│   ├── pull_request_template.md        # PR 檢驗樣板 (包含 QA Gate 檢查)
│   └── workflows/
│       ├── ci.yml                      # Build, Lint, Unit Test
│       └── security-scan.yml           # SAST, FHE memory leak 檢測
├── docs/
│   ├── ARCHITECTURE.md                 # 細部架構與威脅模型
│   ├── CRYPTO-SPEC.md                  # FHE 參數、Signal Ratchet 與 ZK 電路規格
│   ├── DATA-MODEL.md                   # 資料庫與證據鏈結構
│   └── THREAT-MODEL.md                 # STRIDE 威脅模型與信任邊界分析
├── src/
│   ├── client/                         # 前端 UI (Flutter / Web)
│   ├── core-signal/                    # Signal Protocol 封裝與金鑰輪替邏輯
│   ├── core-fhe/                       # FHE 運算 Kernel (OpenFHE / TFHE-rs)
│   ├── zk-proofs/                      # 零知識成員驗證電路 (Circom / Halo2)
│   ├── audit-ledger/                   # Merkle Tree、收據簽署與驗證引擎
│   └── server/                         # 業務閘道 (API Gateway, Storage Adaptor)
├── tests/
│   ├── unit/                           # 單元測試
│   ├── integration/                    # 整合測試
│   ├── crypto/                         # 密碼學一致性與已知解答測試 (KAT)
│   └── qa-e2e/                         # 端到端驗收測試自動化腳本
├── QA-ACCEPTANCE.md                    # QA 驗收清單與測試案例對照表
├── REQUIREMENTS.md                     # 功能 (FR) 與非功能需求 (NFR) 清單
├── SECURITY.md                         # 資安通報機制與密鑰外洩因應流程
├── CONTRIBUTING.md                     # 開發協作標準
└── README.md                           # 本文件
```

---

## 7. 快速開始與本地開發 (Getting Started)

### 環境前置需求
- **Rust**: `1.78+` (用於核心密碼學與 Audit Ledger 模組)
- **C++ 工具鏈**: `CMake 3.22+`, `Clang 15+` / `GCC 11+` (編譯 OpenFHE)
- **Node.js**: `v20+` / **Flutter SDK**: `3.19+` (前端客戶端)
- **Docker & Docker Compose**: `24.0+`

### 1. 取得專案原始碼
```bash
git clone https://github.com/allview-today/allview-fhe-social-app.git
cd allview-fhe-social-app
```

### 2. 初始化核心加密子模組
```bash
# 建置與編譯 FHE 及密碼學安全元件
cargo build -p core-fhe -p core-signal
```

### 3. 啟動本機測試節點網路
```bash
# 啟動本地端模擬之活動串流與證據鏈審計存儲
docker compose -f docker/docker-compose.dev.yml up -d
```

### 4. 執行全域密碼學基準測試
```bash
# 確保密碼學元件運算時間符合 UX SLA
cargo test --test crypto_benchmark -- --nocapture
```

---

## 8. QA 驗收標準與測試計畫 (QA Acceptance)

本專案納入 PMO **七道品質閘門（7-Gate QA Governance）**，所有 Pull Request 必須由 QA 依據 `REQUIREMENTS.md` 與 `QA-ACCEPTANCE.md` 逐項核可：

| 需求代碼 | 模組類別 | 驗收規範 (Acceptance Criteria) | 自動化測試項目 | 通過門檻 |
| :--- | :--- | :--- | :--- | :--- |
| **FR-UX-01** | 使用者體驗 | 動態牆載入、捲動與圖片/影片解密渲染順暢。 | `tests/qa-e2e/test_feed_scroll.spec.ts` | 60 FPS，首屏 < 1.2s |
| **FR-SEC-01** | 通訊安全 | Signal 雙棘輪交握完成，支援前向保密與閱後即焚。 | `tests/crypto/test_ratchet_pfs.rs` | 100% 密鑰不重複使用 |
| **FR-FHE-01** | 密文運算 | 推薦模型在未解密向量下完成 Top-K 候選推薦。 | `tests/crypto/test_fhe_ranking.rs` | 批次延遲 < 800ms |
| **FR-AUD-01** | 證據鏈不可否認 | 點閱與存取皆觸發簽章收據，Merkle 樹可重現路徑。 | `tests/integration/test_receipt_merkle.rs` | 驗證成功率 100% |
| **NFR-SEC-01** | 資料保護 | 服務端資料庫與硬碟映像檔中不得含有明文 PII。 | `tests/qa-e2e/test_db_leak_scan.py` | 零明文個資外洩 |

---

## 9. 治理、權限與 PMO 規範 (PMO Governance)

依照組織 **PMO 控制表** 規範，本專案實施嚴格的角色權限分離原則：

### A. 角色信箱與責任分工 (Aliases & Responsibility)
* **Dev Lead**: `dev-allview-fhe-social-app@allview.today`（核心架構與程式碼交付）
* **Collaborator**: `collab-allview-fhe-social-app@allview.today`（跨模組開發與審查）
* **QA Lead**: `qa-allview-fhe-social-app@allview.today`（品質閘門審查與 E2E 簽核）
* **Repo Admin**: `admin-allview-fhe-social-app@allview.today`（權限治理與合規發布）

### B. 分支與合併政策 (Branching & Merge Gates)
1. `main` 分支設定為受保護分支（Protected Branch），禁止直接推送。
2. 任何合併均需取得：
   - 至少 1 名 Dev Lead 批准。
   - 至少 1 名 QA Lead 針對 `QA-ACCEPTANCE.md` 的測試報告簽核。
   - CI 所有 Status Checks 通過（包括 SAST 安全掃描與 FHE 回歸測試）。
3. 嚴禁將客戶私鑰、AES DEK、未經遮罩之測試資料提交至儲存庫中。

---

> **專案聯絡與安全回報**：  
> 若發現任何密碼學實作缺陷或安全隱患，請立即通知 `github-security@wonderland.center`，請勿公開提交 Issue。


## v0.3 變更註記（2026-11-11，Asia/Taipei）

僅修正本次涉及之品牌顯示名稱、網域文字及與 t12u 直接衝突的法人關係段落；repo／org、技術代碼、URL、路徑、分支及 email local part 均未變更。品牌與網域確認不代表內容核准；本文件為草稿 v0.3，其他來源規格僅供參考，未驗證的功能、效能、時程及合規不得視為核准。

### 人工審核清單

- 完整法定名稱、登記資訊、設立沿革、網域持有人與技術協作／託管契約仍以已確認錨點為限，其他 [待確認] 標註維持。
- 既有版權權利人與授權條款未由本次品牌修訂推定變更；請確認 README 的版權行及 LICENSE 第 189 行 `Copyright [yyyy] [name of copyright owner]` 範本尚未填寫之權利人與年份。
- 保留的技術 URL／徽章／代碼若含歷史文字，並非現行品牌或法人歸屬聲明；如需替換 URL 或改名須另行確認。
- 其餘效能、法遵、交付與產品主張未經核驗，均待人工審核，不因本次修字或 PR 合併視為核准。

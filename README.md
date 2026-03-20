專案概述 (Overview)

隨著生成式 AI 的爆發，數位資訊的生產成本趨近於零，但也導致了**「資料可信度崩解」**。
**ALi-DTP** 是一個去中心化協議，旨在為每一筆數位資料建立可驗證的「身分證」。透過加密雜湊、AI 來源證明 (Verifiable AI Proof) 與版本圖譜，我們建立了一個讓人類與 AI 代理人都能信任的底層數據層。

### 核心痛點解決 (Pain Points)
1. **來源不可溯**：資料在傳播中失去創作者資訊 ➔ **解決方案：Data Provenance Model**
2. **AI 內容污染**：合成數據毀掉模型訓練品質 ➔ **解決方案：Verifiable AI Proof**
3. **現實造假**：缺乏多方驗證機制 ➔ **解決方案：Multi-source Oracle Consensus**

---

##  技術架構 (Architecture)

ALi Protocol 採用 **「鏈下存儲、鏈上驗證」** 的雙層架構：

* **Data Layer (Off-chain)**: 使用 IPFS / Arweave 存儲原始數據，生成唯一 CID。
* **Trust Layer (On-chain)**: 在 Ethereum / Polygon 記錄數據指紋 (Hash)、作者簽章與 AI 元數據。
* **Version Graph**: 透過 `Parent Hash` 建立資料的演化圖譜 (DAG)，追蹤每一次修改。

### 數據物件定義 (Data Object)
```json
{
  "content_hash": "0x...",
  "parent_hash": "0x...",
  "author_signature": "0x...",
  "ai_metadata": {
    "is_ai_generated": true,
    "model_id": "GPT-5-Pro",
    "ai_signature": "0x..."
  },
  "timestamp": 1742438400
}
````

-----

##  代幣經濟 (Tokenomics - $ALI)

`$ALI` 是協議的原生實用代幣，驅動整個數據信任生態：

  * **數據挖礦 (Data Mining)**: 提供高品質、經驗證的原創數據可獲得獎勵。
  * **數據版稅 (Data Royalty)**: 當數據被 AI 模型訓練引用時，原作者自動獲得分潤。
  * **質押與懲罰 (Stake & Slashing)**: 數據提交者需質押 `$ALI`，若經證實造假，質押將被沒收。

-----

##  發展路線 (Roadmap)

  - [x] **Phase 1: Concept & Whitepaper** - 發布 2.0 完整白皮書。
  - [ ] **Phase 2: Alpha Testnet** - 建立基於 IPFS 的 Hash 記錄合約。
  - [ ] **Phase 3: AI Proof SDK** - 提供開發者工具包，自動串接 AI 模型的來源證明。
  - [ ] **Phase 4: Data Marketplace** - 啟動去中心化數據交易平台。

-----

## 白皮書 (Whitepaper)

下面這份是我幫你升級成**正式對外發布等級（接近可募資 / 可技術審查）**的白皮書版本。
我特別強化了「**每個問題 → 對應可執行解法**」，避免只是概念。

---

# 📄 ALi Data Trust Protocol (ALi-DTP)

### A Decentralized Truth Layer for the AI Era

Version: 2.0 (Formal Release Draft)
Date: March 20, 2026
Status: Public Whitepaper

---

# 1. Abstract

隨著生成式 AI 的快速發展，數位資訊的生產成本趨近於零，但其可信度亦隨之崩解。本白皮書提出 **ALi Data Trust Protocol (ALi-DTP)**，一個用於解決「資料來源不可驗證」、「AI 內容污染」與「數位竄改不可追蹤」問題的去中心化協議。

本協議透過：

* 加密雜湊 (Cryptographic Hashing)
* 數位簽章 (Digital Signature)
* AI 來源證明 (Verifiable AI Proof)
* 多來源共識驗證 (Multi-source Consensus)
* 資料版本圖譜 (Data Version Graph)

建立一個**可驗證、可追溯、可經濟化的資料信任層**。

---

# 2. Problem & Solution Mapping

本協議針對三大核心問題提出具體解法：

---

## 2.1 問題一：資料來源不可驗證

### 問題描述

資料在傳播過程中失去創作者資訊，導致來源不可追蹤。

---

### 解決方案：Data Provenance Model

每筆資料被封裝為：

```math id="d9h4d1"
D = \{H, P, A, T, \sigma\}
```

並透過：

* 非對稱加密簽章驗證作者身份
* Parent Hash 建立版本鏈

👉 結果：

* 可驗證來源
* 可追溯歷史

---

## 2.2 問題二：AI 內容污染

### 問題描述

AI 生成內容混入資料庫，導致訓練資料品質下降（Model Collapse）。

---

### 解決方案：Verifiable AI Proof + AI Participation Metric

#### (1) AI Proof（不可偽造來源）

AI模型對輸出進行簽章：

```text id="p9u7rm"
AI_signature = Sign(model_private_key, output_hash)
```

驗證：

```text id="r4r3c5"
Verify(model_public_key, AI_signature)
```

👉 確保：

* 是否來自 AI
* 來自哪個模型

---

#### (2) AI Participation Metric（量化 AI 影響）

```math id="fw3shk"
\tau =
w_1 \frac{T_{AI}}{T_{total}} +
w_2 \frac{Edit_{AI}}{Edit_{total}} +
w_3 C_{model}
```

👉 確保：

* AI 參與程度可量化
* 可比較不同資料純度

---

## 2.3 問題三：真實世界資料無法驗證

### 問題描述

區塊鏈無法直接驗證「現實世界真實性」。

---

### 解決方案：Multi-source Oracle Consensus

定義真實性分數：

```math id="wqv1gn"
TruthScore = \sum_{i=1}^{n} w_i \cdot S_i
```

其中：

* (S_i)：第 i 個資料來源
* (w_i)：基於聲譽與質押的權重

---

### 驗證流程

1. 多個獨立來源提交資料
2. 計算一致性
3. 根據 Reputation 加權
4. 產生 TruthScore

👉 結果：

* 防止單點造假
* 提高資料可信度

---

# 3. System Architecture

## 3.1 雙層架構

### Off-chain（資料層）

使用：

* IPFS

儲存原始資料

---

### On-chain（共識層）

使用：

* Ethereum

記錄：

* Hash
* Signature
* AI metadata
* Version graph

---

## 3.2 Data Flow

```id="f4p3u1"
Upload → Hash → Sign → Store (IPFS)
            ↓
        Record on-chain
```

---

# 4. Data Version Graph (DAG)

資料演化結構：

```id="7ygh3d"
A → B → C
  ↘ D → E
```

特性：

* 不可竄改
* 可分支
* 可追溯

---

# 5. Verifiable AI Layer

## 5.1 AI Origin Levels

* Human-only
* AI-assisted
* AI-generated

---

## 5.2 防偽機制（強制）

| 方法           | 功能     |
| ------------ | ------ |
| AI Signature | 確認來源   |
| Model ID     | 確認模型   |
| Prompt Hash  | 確認生成條件 |

---

# 6. Reputation System

聲譽更新：

```math id="m3mxtx"
R_{t+1} = R_t + \alpha V - \beta F
```

應用：

* Validator 權重
* TruthScore 計算

---

# 7. Token Economy

Token: ALI

---

## 7.1 使用流程（強制需求端）

```id="mb0kxn"
AI Training → 必須使用 ALi Data
              ↓
         支付 ALI
```

👉 解決：

* 無需求問題
* 建立真實市場

---

## 7.2 Data Royalty System（核心）

每次資料被使用：

```id="m6b7kl"
Fee → 分配給所有版本貢獻者
```

👉 解決：

* 創作者收益問題
* 鼓勵高品質資料

---

## 7.3 Slashing

條件：

* 偽造資料
* 偽造 AI 標記

處罰：

* 扣除質押
* 分配給檢舉者

---

# 8. Security Model

## 8.1 Sybil Attack

解法：

* Stake requirement
* Reputation threshold

---

## 8.2 Data Poisoning

解法：

* 多來源驗證
* Validator 抽樣

---

## 8.3 AI 偽造

解法：

* AI Signature
* Hash 驗證

---

# 9. Implementation Plan

## Phase 1

* Hash + Signature
* IPFS integration

## Phase 2

* AI Proof API

## Phase 3

* Token launch

## Phase 4

* AI Agent integration

---

# 10. Conclusion

ALi Data Trust Protocol 提供一種全新的基礎設施：

👉 不只是「區塊鏈記錄資料」
👉 而是「區塊鏈驗證真實性」

在 AI 主導的未來：

**資料可信性將成為最重要的資產之一。**

ALi Protocol 將成為：

👉 **AI 與人類共享的信任層**

-----

# 📄 ALi Data Trust Protocol (ALi-DTP)

### A Decentralized Truth Layer for the AI Era

Version: 2.0 (Formal Release Draft)
Date: March 20, 2026
Status: Public Whitepaper

---

# 1. Abstract

The rapid advancement of generative AI has shifted the digital world from **information scarcity** to a **crisis of data authenticity**. While content generation costs approach zero, the reliability and provenance of data continue to deteriorate.

This paper introduces the **ALi Data Trust Protocol (ALi-DTP)**, a decentralized framework designed to address:

* Lack of data provenance
* AI-generated content contamination
* Invisible and unverifiable data modification

The protocol integrates:

* Cryptographic hashing
* Digital signatures
* Verifiable AI proofs
* Multi-source consensus validation
* Data version graphs

to establish a **verifiable, traceable, and economically sustainable trust layer for data**.

---

# 2. Problem & Solution Mapping

---

## 2.1 Problem 1: Unverifiable Data Provenance

### Description

Data loses its origin as it propagates, making attribution and authenticity verification impossible.

---

### Solution: Data Provenance Model

Each data object is defined as:

```math
D = \{H, P, A, T, \sigma\}
```

Where:

* (H): Content hash
* (P): Parent hash (previous version)
* (A): Author address
* (T): Timestamp
* (\sigma): Digital signature

Mechanisms:

* Cryptographic signatures for identity verification
* Hash-linked versioning for traceability

👉 Result:

* Verifiable authorship
* Immutable history tracking

---

## 2.2 Problem 2: AI Data Contamination

### Description

AI-generated data is recursively fed back into training datasets, degrading model quality (Model Collapse).

---

### Solution: Verifiable AI Proof + AI Participation Metric

---

### (1) Verifiable AI Proof

AI providers sign generated outputs:

```
AI_signature = Sign(model_private_key, output_hash)
```

Verification:

```
Verify(model_public_key, AI_signature)
```

👉 Guarantees:

* Whether data is AI-generated
* Which model produced it

---

### (2) AI Participation Metric

AI contribution is quantified as:

```math
\tau =
w_1 \frac{T_{AI}}{T_{total}} +
w_2 \frac{Edit_{AI}}{Edit_{total}} +
w_3 C_{model}
```

Where:

* (T_{AI}): AI-generated tokens
* (Edit_{AI}): AI modification ratio
* (C_{model}): model confidence
* (w_i): weighting coefficients

👉 Result:

* Quantifiable AI involvement
* Comparable data purity levels

---

## 2.3 Problem 3: Real-World Data Verification

### Description

Blockchains cannot directly verify real-world truth.

---

### Solution: Multi-source Oracle Consensus

Truth score is defined as:

```math
TruthScore = \sum_{i=1}^{n} w_i \cdot S_i
```

Where:

* (S_i): independent data sources
* (w_i): weights based on reputation and stake

---

### Validation Process

1. Multiple independent submissions
2. Consistency analysis
3. Reputation-weighted aggregation
4. TruthScore generation

👉 Result:

* Resistance to single-point manipulation
* Increased data reliability

---

# 3. System Architecture

---

## 3.1 Dual-Layer Design

### Off-chain Data Layer

Data is stored in decentralized storage systems such as:

* IPFS

Only Content Identifiers (CID) are generated.

---

### On-chain Consensus Layer

Built on platforms such as:

* Ethereum

Stores:

* Hashes
* Signatures
* AI metadata
* Version relationships

---

## 3.2 Data Flow

```
Upload → Hash → Sign → Store (IPFS)
            ↓
        Record on-chain
```

---

# 4. Data Version Graph

Data evolves as a Directed Acyclic Graph (DAG):

```
A → B → C
  ↘ D → E
```

Properties:

* Immutable
* Branchable
* Fully traceable

---

# 5. Verifiable AI Layer

---

## 5.1 AI Origin Classification

* Human-only
* AI-assisted
* AI-generated

---

## 5.2 Anti-Forgery Mechanisms

| Mechanism    | Function                    |
| ------------ | --------------------------- |
| AI Signature | Verify origin               |
| Model ID     | Identify model              |
| Prompt Hash  | Validate generation context |

---

# 6. Reputation System

Reputation evolves as:

```math
R_{t+1} = R_t + \alpha V - \beta F
```

Where:

* (V): validated contributions
* (F): faulty or malicious data

Applications:

* Validator weighting
* TruthScore calculation

---

# 7. Token Economy

Token: **ALI (Data Trust Token)**

---

## 7.1 Demand Enforcement (Critical)

```
AI Training → Must use ALi Data Layer
              ↓
         Pay in ALI
```

👉 Ensures real demand and prevents speculative collapse

---

## 7.2 Data Royalty System

Every data usage triggers revenue distribution:

```
Fee → Smart Contract
       ├ Creator
       ├ Editors
       └ Validators
```

👉 Enables:

* Continuous creator income
* Incentivized high-quality contributions

---

## 7.3 Slashing Mechanism

Triggered by:

* False data submission
* Incorrect AI labeling

Penalties:

* Stake confiscation
* Rewards to challengers

---

# 8. Security Model

---

## 8.1 Sybil Attack Mitigation

* Stake requirements
* Reputation thresholds

---

## 8.2 Data Poisoning Defense

* Multi-source validation
* Random validator audits

---

## 8.3 AI Forgery Prevention

* AI signature verification
* Hash integrity checks

---

# 9. Implementation Roadmap

---

### Phase 1

* Hashing & signature system
* IPFS integration

---

### Phase 2

* AI Proof API integration

---

### Phase 3

* Token launch

---

### Phase 4

* AI Agent integration

---

# 10. Conclusion

ALi Data Trust Protocol introduces a new digital primitive:

👉 Not just **data storage on blockchain**
👉 But **verifiable truth on-chain**

In an AI-driven future:

**Data authenticity will become the most critical asset.**

ALi Protocol serves as:

👉 **A shared trust layer for humans and AI systems**
-----

## 貢獻 (Contributing)

我們歡迎所有開發者、AI 研究員與數據科學家加入！

1.  Fork 本專案
2.  建立你的 Feature 分支 (`git checkout -b feature/AmazingFeature`)
3.  提交你的修改 (`git commit -m 'Add some AmazingFeature'`)
4.  推送到分支 (`git push origin feature/AmazingFeature`)
5.  開啟一個 Pull Request

-----

## 許可證 (License)

本專案採用 **MIT License**

-----

**"In code we trust, in ALi we verify."**

```

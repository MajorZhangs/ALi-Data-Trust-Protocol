 ALi Data Trust Protocol (ALi-DTP)
A Decentralized Truth Layer for the AI Era
Version: 2.0 (Formal Release Draft)
Date: March 20, 2026
Status: Public Whitepaper
________________________________________
1. Abstract
隨著生成式 AI 的快速發展，數位資訊的生產成本趨近於零，但其可信度亦隨之崩解。本白皮書提出 ALi Data Trust Protocol (ALi-DTP)，一個用於解決「資料來源不可驗證」、「AI 內容污染」與「數位竄改不可追蹤」問題的去中心化協議。
本協議透過：
	加密雜湊 (Cryptographic Hashing)
	數位簽章 (Digital Signature)
	AI 來源證明 (Verifiable AI Proof)
	多來源共識驗證 (Multi-source Consensus)
	資料版本圖譜 (Data Version Graph)
建立一個可驗證、可追溯、可經濟化的資料信任層。
________________________________________
2. Problem & Solution Mapping
本協議針對三大核心問題提出具體解法：
________________________________________
2.1 問題一：資料來源不可驗證
問題描述
資料在傳播過程中失去創作者資訊，導致來源不可追蹤。
________________________________________
解決方案：Data Provenance Model
每筆資料被封裝為：
D={H,P,A,T,σ}
並透過：
	非對稱加密簽章驗證作者身份
	Parent Hash 建立版本鏈
結果：
	可驗證來源
	可追溯歷史
________________________________________
2.2 問題二：AI 內容污染
問題描述
AI 生成內容混入資料庫，導致訓練資料品質下降（Model Collapse）。
________________________________________
解決方案：Verifiable AI Proof + AI Participation Metric
(1) AI Proof（不可偽造來源）
AI模型對輸出進行簽章：
AI_signature = Sign(model_private_key, output_hash)
驗證：
Verify(model_public_key, AI_signature)
確保：
	是否來自 AI
	來自哪個模型
________________________________________
(2) AI Participation Metric（量化 AI 影響）
τ=w_1  T_AI/T_total +w_2  (Edit_AI)/(Edit_total )+w_3 C_model
確保：
	AI 參與程度可量化
	可比較不同資料純度
________________________________________
2.3 問題三：真實世界資料無法驗證
問題描述
區塊鏈無法直接驗證「現實世界真實性」。
________________________________________
解決方案：Multi-source Oracle Consensus
定義真實性分數：
TruthScore=∑_(i=1)^n▒w_i ⋅S_i
其中：
	(S_i)：第 i 個資料來源
	(w_i)：基於聲譽與質押的權重
________________________________________
驗證流程
	多個獨立來源提交資料
	計算一致性
	根據 Reputation 加權
	產生 TruthScore
👉 結果：
	防止單點造假
	提高資料可信度
________________________________________
3. System Architecture
3.1 雙層架構
Off-chain（資料層）
使用：
	IPFS
儲存原始資料
________________________________________
On-chain（共識層）
使用：
	Ethereum
記錄：
	Hash
	Signature
	AI metadata
	Version graph
________________________________________
3.2 Data Flow
Upload → Hash → Sign → Store (IPFS)
            ↓
        Record on-chain
________________________________________
4. Data Version Graph (DAG)
資料演化結構：
A → B → C
  ↘ D → E
特性：
	不可竄改
	可分支
	可追溯
________________________________________
5. Verifiable AI Layer
5.1 AI Origin Levels
	Human-only
	AI-assisted
	AI-generated
________________________________________
5.2 防偽機制（強制）
方法	功能
AI Signature	確認來源
Model ID	確認模型
Prompt Hash	確認生成條件
________________________________________
6. Reputation System
聲譽更新：
R_(t+1)=R_t+αV-βF
應用：
	Validator 權重
	TruthScore 計算
________________________________________
7. Token Economy
Token: ALI
________________________________________
7.1 使用流程（強制需求端）
AI Training → 必須使用 ALi Data
              ↓
         支付 ALI
解決：
	無需求問題
	建立真實市場
________________________________________
7.2 Data Royalty System（核心）
每次資料被使用：
Fee → 分配給所有版本貢獻者
解決：
	創作者收益問題
	鼓勵高品質資料
________________________________________
7.3 Slashing
條件：
	偽造資料
	偽造 AI 標記
處罰：
	扣除質押
	分配給檢舉者
________________________________________
8. Security Model
8.1 Sybil Attack
解法：
	Stake requirement
	Reputation threshold
________________________________________
8.2 Data Poisoning
解法：
	多來源驗證
	Validator 抽樣
________________________________________
8.3 AI 偽造
解法：
	AI Signature
	Hash 驗證
________________________________________
9. Implementation Plan
Phase 1
	Hash + Signature
	IPFS integration
Phase 2
	AI Proof API
Phase 3
	Token launch
Phase 4
	AI Agent integration
________________________________________
10. Conclusion
ALi Data Trust Protocol 提供一種全新的基礎設施：
不只是「區塊鏈記錄資料」
而是「區塊鏈驗證真實性」
在 AI 主導的未來：
資料可信性將成為最重要的資產之一。
ALi Protocol 將成為：
AI 與人類共享的信任層


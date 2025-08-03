#### AWS Artifact

用於按需訪問 AWS 的安全與合規報告，以及某些線上協議。它旨在幫助客戶了解 AWS 雲的安全態勢和合規性，
並驗證他們的雲環境是否符合各種法規、行業標準和內部審計要求。

#### AWS Audit Manager

持續審計您的 AWS 使用情況，以便輕鬆評估您的雲端運營是否符合監管和行業標準。

 AWS Artifact 是提供 AWS 本身的安全合規報告（AWS 作為雲提供商的合規性證明），
 AWS Audit Manager 則是幫助您作為客戶，自動收集和管理證據，以證明您在雲中運行的應用程式和工作負載符合特定的合規標準。


### Partial dependence plots

Partial Dependence Plots（部分依賴圖，簡稱 PDP）是用來解釋機器學習模型中 特定特徵對預測結果的影響 的視覺化工具，常見於解釋 非線性模型

觀察每一個自變數的變化是如何影響預測表現，它可以快速地分析自變數與目標變數之間的關係

### 機器學習模型的準確率（Accuracy in AWS ML services）

訓練模型的「準確率（Accuracy）」，那它是衡量分類模型預測正確率的指標，計算公式如下：

<img width="303" height="61" alt="image" src="https://github.com/user-attachments/assets/0020a1d9-3ccf-4d0a-a4e7-e678102286d4" />

AWS SageMaker 在訓練模型後可以自動產出如：

Accuracy

Precision / Recall

F1 Score

Confusion Matrix（混淆矩陣）




### 
Transparency 透明度
Explainability 可解釋性

Model convergence tables 模型收斂表
用於評估模型訓練過程是否穩定，以及模型是否達到最佳狀態。

Partial Dependence Plots (PDPs) 
提供了一種視覺化的方式來展示一個或兩個特徵如何影響模型的預測。它們可以幫助利害關係人理解：
- 哪些特徵對預測的影響最大。
- 這些特徵的變化如何導致預測的變化。
- 模型的行為是否符合直覺或業務邏輯。


Decision trees 決策樹
- 分類能力：決策樹是一種強大的分類演算法，非常適合將資料分類到多個類別（如 20 種類別）。
- 可解釋性：決策樹以其高可解釋性而聞名。你可以將決策樹的結構直接視覺化出來，它顯示了一系列「如果...那麼...」的規則，從根節點到葉節點的路徑就是模型做出特定分類決策的邏輯。這種基於規則的結構使得其內部機制如何影響輸出變得非常清晰和容易理解，即使是非技術人員也能相對容易地掌握。這完全符合「文件化模型內部機制如何影響輸出」的要求。

Linear regression (線性迴歸)：
- 分類能力：線性迴歸是用於預測連續數值的迴歸演算法，而非分類演算法。它無法直接將基因分為 20 種類別。

Logistic regression (邏輯迴歸)：
- 分類能力：邏輯迴歸是一種分類演算法，可以用於二元分類，也可以擴展到多元分類（如 20 種類別）。
- 可解釋性：邏輯迴歸也具有一定的可解釋性，透過檢視每個特徵的係數，可以了解該特徵對預測類別機率的影響方向和強度。然而，相較於決策樹提供的直接、層次分明的決策路徑，邏輯迴歸的解釋更多是關於特徵權重的統計意義，對於完全理解「內部機制如何導致特定輸出」可能不如決策樹那樣直觀和直接。

Neural networks (神經網路)：
- 分類能力：神經網路，特別是深度學習模型，在複雜的分類任務上表現卓越，可以輕鬆處理 20 種類別的分類。
- 可解釋性：然而，神經網路通常被視為「黑箱模型」。它們的內部結構（數百萬甚至數十億個權重和偏差）非常複雜，很難直接解釋或文件化其內部機制如何影響每個特定的輸出。雖然存在一些事後解釋性技術 (e.g., SHAP, LIME)，但它們無法提供像決策樹那樣清晰、內建的決策路徑解釋。

Amazon SageMaker

進行機器學習推論的需求，其特點是：
- 生產環境 (Production environment)
- 大型輸入數據 (Input data sizes up to 1 GB)
- 長時間處理 (Processing times up to 1 hour)
- 近乎即時的延遲 (Near real-time latency)

Use transfer learning 遷移學習
取一個已經在大型數據集（通常是通用領域）上訓練好的模型（預訓練模型），然後將其用於一個新的、但相關的任務。通常會透過以下方式實現：
- 將預訓練模型的學習到的特徵提取器部分保留下來。
- 移除模型的輸出層，並添加一個新的輸出層，針對新任務的類別或目標進行訓練。
- 選擇性地對預訓練模型的部分或全部層進行微調 (fine-tuning)，使其更好地適應新任務的數據。
- 這種方法可以顯著減少訓練時間和所需的數據量，因為模型已經從大量的通用數據中學習了許多有用的特徵。這完全符合「避免從頭開始創建新模型」和「適應預訓練模型以用於新的、相關任務」的要求。

Human-in-the-loop, HITL
人機協同驗證。對於需要高準確度並最大程度減少錯誤的任務，人工審核和驗證是至關重要的品質控制環節

Amazon SageMaker Ground Truth Plus：
這是一個全託管服務，提供專業的人工團隊來執行數據標註和驗證工作，專為獲取高品質的標註數據而設計。

Data augmentation
這是一種擴充訓練數據集的技術，例如旋轉圖像、增加雜訊等，旨在提高模型泛化能力。它本身不是一種生成新圖像的工具，也無法直接「最小化錯誤標註」。
 
 Amazon Bedrock knowledge base：這是為大型語言模型 (LLM) 提供檢索增強生成 (RAG) 功能的，主要用於文字，與圖像生成和標註無關。

Amazon Rekognition 進行圖像識別

Amazon QuickSight Q 進行數據彙總
 是一個商業智慧 (BI) 服務，允許用戶透過自然語言查詢數據並獲得可視化的彙總。這與圖像生成或錯誤標註的風險完全無關

a foundation model (FM) 

Amazon Bedrock
Amazon S3 bucket

Amazon S3 managed keys (SSE-S3)

small language models (SLMs) on edge devices

 large language models (LLMs) on edge devices

Amazon SageMaker Feature Store 特徵商店
- 特徵商店 (Feature Store) 是一個集中式的儲存庫，用於儲存、管理和共享機器學習模型的特徵 (features)。
- 它允許不同的團隊輕鬆地發現、存取和重複使用已經建立好的特徵，而無需重複開發。
- 它提供版本控制、元數據管理、線上/離線存取等功能，方便多個團隊協作和管理特徵。
- 完全符合需求：特徵商店是專為解決跨團隊共享和管理機器學習特徵而設計的。


Amazon SageMaker Data Wrangler
 - 準備和轉換數據的工具，例如數據清理、特徵工程、數據可視化等。它主要用於數據預處理階段，而不是用於共享和管理已經建立好的特徵。

Amazon SageMaker Clarify
 - 檢測和減輕機器學習模型的偏差 (bias)，並提供模型可解釋性 (explainability) 的洞察。


Amazon SageMaker Model Cards
 - 用於記錄機器學習模型元數據（例如模型目的、訓練數據、性能指標）的標準化格式。雖然它有助於模型的可追溯性和透明度，但它不是用於共享和管理模型開發中使用的變數（特徵）。


Amazon SageMaker








 

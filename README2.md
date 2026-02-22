```mermaid
graph TB
    %% =====================================================================================
    %% --- GitHub 絕對穩定版樣式定義 (移除圓角以避免崩潰錯誤) ---
    %% =====================================================================================
    
    %% timeline: 時間軸節點 - 清透的科學藍，標準矩形，粗邊框
    %% 【修正】移除了 rx, ry 和 font-weight 以確保相容性
    classDef timeline fill:#e3f2fd,stroke:#1565c0,stroke-width:3px,color:#0d47a1;
    
    %% sampling: 採樣動作節點 - 代表生物樣本的淡紅/粉色，紅色虛線邊框，標準矩形
    %% 【修正】移除了 rx, ry 和 font-weight
    classDef sampling fill:#ffebee,stroke:#c62828,stroke-width:2px,stroke-dasharray: 5 5,color:#b71c1c;
    
    %% sop: 基礎文件節點 - 代表規範的淡綠色，標準矩形
    %% 【修正】移除了 rx, ry
    classDef sop fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#1b5e20;
    
    %% linkStyle: 定義連接線的樣式
    linkStyle 0,1,2,3,4 stroke:#1565c0,stroke-width:4px,fill:none;
    linkStyle 5,6,7,8,9,10 stroke:#c62828,stroke-width:2px,stroke-dasharray: 5 5,fill:none;

    %% =====================================================================================
    %% --- 節點定義 ---
    %% =====================================================================================

    %% --- 主標題 ---
    %% 【修正】將 fill:none 改為白色，避免選取不到物件的錯誤
    Title["(1) 臨床流程與樣本採集標準作業 (SOP) 建立"]:::titleBox
    classDef titleBox fill:#ffffff,stroke:none,color:#333;

    %% --- 藍色時間軸節點 (右側) ---
    T1("基線<br/>Baseline"):::timeline
    T2("NIC Cycle 1 後<br/>Post-C1"):::timeline
    T3("術前<br/>Pre-op"):::timeline
    T4("手術/術後<br/>Post-op"):::timeline
    T5("追蹤期<br/>Follow-up"):::timeline

    %% --- 紅色採樣動作節點 (左側) ---
    S1("採血 &<br/>組織切片"):::sampling
    S2("採血 &<br/>組織切片"):::sampling
    S3("採血"):::sampling
    S4("採血 &<br/>潛在採檢"):::sampling
    S5("採血 &<br/>手術檢體"):::sampling
    S6("系列採血"):::sampling

    %% --- 綠色 SOP 基礎節點 (最左側) ---
    SOP_Node["建立標準作業流程 (SOP) 基礎<br/>(涵蓋：採血 / 組織 / 運送 / 病理處理流程<br/>以及 倫理 / IRB / 匿名化管理機制)"]:::sop

    %% =====================================================================================
    %% --- 流程連接 ---
    %% =====================================================================================

    %% 1. 主時間軸流程 (粗藍線)
    T1 --> T2 --> T3 --> T4 --> T5

    %% 2. 時間點對應採樣動作 (紅色虛線)
    T1 -.-|> S1
    T2 -.-|> S2
    T3 -.-|> S3
    T4 -.-|> S4
    T4 -.-|> S5
    T5 -.-|> S6

    %% 3. 佈局輔助
    SOP_Node ~~~ S1
```

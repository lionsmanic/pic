```mermaid
graph TB
    %% --- 定義樣式 ---
    classDef timeline fill:#e1f5fe,stroke:#0288d1,stroke-width:2px,color:#01579b,font-weight:bold,rx:8,ry:8;
    classDef sampling fill:#ffe0b2,stroke:#f57c00,stroke-width:2px,stroke-dasharray: 8 5,rx:8,ry:8;
    classDef sop fill:#fff9c4,stroke:#fbc02d,stroke-width:1px,rx:0,ry:0;
    classDef container fill:#fffde7,stroke:#c0ca33,stroke-width:2px;

    %% --- 主容器 ---
        direction TB

        %% --- 時間軸流程 (藍色區塊) ---
        T1("基線 Baseline"):::timeline --> T2("NIC Cycle 1 後"):::timeline --> T3("術前 Pre-op"):::timeline --> T4("手術/術後 Post-op"):::timeline --> T5("追蹤期 Follow-up"):::timeline

        %% --- 採樣動作 (橘色虛線區塊) ---
        %% 透過連結將採樣區塊掛在對應的時間點下方
        T1 --- S1("採血 & 組織切片"):::sampling
        T2 --- S2("採血"):::sampling
        T3 --- S3("採血 & 潛在組織採檢"):::sampling
        T4 --- S4("採血 & 手術組織檢體"):::sampling
        T5 --- S5("系列採血"):::sampling

        %% --- SOP 基礎建設 (黃色區塊) ---
        %% 使用隱藏連結 (~~~) 將其定位於整體流程的右下方
        SOP_Docs["建立採血/組織/運送/病理 SOP <br/> 倫理/IRB/匿名化管理"]:::sop
        T4 ~~~ SOP_Docs
        T5 ~~~ SOP_Docs

    end
    %% 應用最外層容器樣式
    class MainContainer container
```

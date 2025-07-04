---
tags: programming, preprocessor, C
alias: []
created: 2025-07-04
updated:
source:
---
# 前置處理器 (Preprocessor)

前置處理器是 C 編譯過程中的**第一個階段**。在真正的編譯（將 C 程式碼轉換為機器碼）開始之前，前置處理器會掃描你的原始碼，執行以 `#` 符號開頭的特殊指令。這些指令被稱為**預處理器指令**或**宏指令**。

**前置處理器的主要任務包括：**

- **文件包含 (File Inclusion)**：處理 `#include` 指令，將指定檔案的內容（通常是標頭檔 `.h`）插入到當前檔案中。這讓你可以在不同的原始檔中共享宣告和定義。
    
    - 例如：`#include <stdio.h>` 會將 `stdio.h` 的內容複製到你的程式碼中。
        
- **宏展開 (Macro Expansion)**：處理 `#define` 指令，將宏名稱替換為其定義的文字內容。
    
    - 例如：`#define PI 3.14159` 會將程式碼中所有 `PI` 都替換成 `3.14159`。
        
- **條件編譯 (Conditional Compilation)**：處理 `#ifdef`, `#ifndef`, `#if`, `#elif`, `#else`, `#endif` 等指令。這些指令允許你根據條件來包含或排除部分程式碼，例如針對不同的作業系統或偵錯模式編譯不同的功能。
    
    - 例如：
        
        ```clike
        #ifdef DEBUG
            printf("Debug info here.\n");
        #endif
        ```
        
        只有在定義了 `DEBUG` 宏時，這行 `printf` 程式碼才會被編譯。
        
- **其他指令**：例如 `#undef` (撤銷宏定義)、`#error` (發出編譯錯誤)、`#pragma` (提供編譯器特定的指令)。
    
**總結**：前置處理器是一個**文字替換器**和**程式碼篩選器**，它在實際編譯發生之前修改你的原始碼。
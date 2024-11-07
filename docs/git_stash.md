# Git Stash

用於暫存 Staging area 的修改，可於之後再取出至 Staging area。  

使用情境：  
1. 臨時要切換到另一個 branch 進行開發，但是要保留目前 branch 的進度
2. 已經做了一些編輯，才發現忘記切換至原本預計要編輯的 branch

## 指令
- 保存一份 stash
    - ```bash
        git stash
        ```
- 查看目前的所有 stash
    - ```bash
        git stash list
        ```
- 選擇器
    - 預設（不指定）：最後保存的一份 stash
    - 舉例：選擇編號為「2」的 stash
        - `stash@{2}`
- 取出 stash
    - ```bash
        git stash apply
        ```
- 刪除 stash
    - ```bash
        git stash drop
        ```
- 取出並刪除 stash
    - ```bash
        git stash pop
        ```

## 注意事項與小知識
- 保存 stash 前，要確認編輯的檔案已在 Staging area。
- stash 無法 push 到 remote repo。
- 可以在 master branch 保存 stash、再 checkout 到 develop branch 取出，達成解決「忘記切換 branch」的目的。


#### 參考資料
[【狀況題】手邊的工作做到一半，臨時要切換到別的任務](https://gitbook.tw/chapters/faq/stash)
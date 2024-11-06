# Git Tag 與 GitHub Release

## Git Tag
- 將某個 commit 加上 tag
    - 舉例：將 hash 為「abc1234」的 commit 加上
    「v1.0」的 tag
        - ```bash
            git tag v1.0 abc1234
            ```
    - commit hash 也可以使用 `HEAD~3` 等等選擇。
    - 若無輸入 commit hash，是選擇目前 `HEAD` 指向的 commit。
- 查看目前 repo 裡的所有 tag
    - ```bash
        git tag
        ```
- 將 tag push 到 remote repo
    - push 單一 tag
        - 舉例：push「v1.0」這個 tag
            - ```bash
                git push origin v1.0
                ```
    - push 所有 tag
        - ```bash
            git push --tags
            ```

## GitHub Release
1. 在 GitHub repo 頁面，點擊 Branches 旁邊的［Tags］
2. 點進要製成 Release 的 Tag
3. 點擊右上方的［Create release from tag］
4. 輸入資訊、（optional）上傳輸出檔案
5. 點擊［Publish release］

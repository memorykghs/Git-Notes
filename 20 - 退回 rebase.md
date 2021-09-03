# 20 - 退回 rebase
有時候拉完 `dev` 並切回自己的分支做 rebase 後，會發現沒有辦法 auto-merge 或是多了一堆不是自己的 commit。這時候特別需要一個可以退回 rebase 的方法，像 ctrl+Z 一樣回到 rebase 前的狀態。

在這個情況下，可以先下 `git reflog` 來查看分支異動的歷史，包括 `rebase`、`commit` 或是 `checkout` 等等，每一個步驟都有 hashCode 及流水號。可以依據這個歷史來找我們想要恢復到哪個步驟。
![](/images/20-1.png)

大括號內的流水編號，跟 `stash` 一樣，數字越小越新。另外，你比較謹慎的話，可以先下 `git log HEAD@{3}` 確認那個時間點的檔案是不是你要的。最後，假設想要回到 ，只要下 `git reset --hard HEAD@{2}` 就可以回到 rebase 之前了!就不用想方設法的重新建分支然後把改好的扣複製過去了!
![](/images/20-2.png)

p.s. 在 windows 下有可能需要對指令加上 `""`：`git reset --hard "HEAD@{3}"`

## 參考
* http://jiduanyaoji.logdown.com/hints/2015/07/10/github-you-rebase-but-found-the-wrong-going-to-respond
* https://stackoverflow.com/questions/134882/undoing-a-git-rebase
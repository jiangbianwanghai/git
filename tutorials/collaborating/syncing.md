![同步](https://www.atlassian.com/git/images/tutorials/collaborating/syncing/hero.svg "同步")

#同步

SVN使用一个单一的中央信息库，作为开发商的通信枢纽和协作通过将开发人员的工作副本与中央存储库之间的变更发生。这是Git的合作模式，这给每个开发自己的资源库中的副本，完成了自己当地的历史和分支结构不同。用户通常需要共享一系列的提交而不是单一的变更。相反犯从工作副本变更到中央存储库，Git的让你分享存储库之间的整个分支。

下面介绍的命令，让你管理与其他存储库连接，通过“推”分支到其他存储库发布当地的历史，看看别人怎么被“揪”分支到本地存储库作出了贡献。

###git more

git的远程命令允许您创建，查看和删除其他资源库的连接。远程连接更喜欢的书签，而不是直接链接到其他库。相反到另一个仓库提供实时的访问，他们服务可用于引用不那么方便的网址为便于记忆的名称。

例如，下面的图显示了从回购到中央回购和其他开发人员的回购两个远程连接。相反，其完整的URL引用它们，你可以通过原产地和约翰快捷方式到其他Git命令。

![配图01](https://www.atlassian.com/git/images/tutorials/collaborating/syncing/01.svg "配图01")

####用法

<pre><code>git remote</code></pre>

列出你有其他存储库的远程连接。

<pre><code>git remote -v</code></pre>

同上面的命令，而是包括每个连接的URL。

<pre><code>git remote add &lt;name&gt; &lt;url&gt;</code></pre>

创建到远程仓库一个新的连接。添加远程之后，您就可以在其他的Git使用<名>作为一种方便快捷的<网址>命令。

<pre><code>git remote rm &lt;name&gt;</code></pre>

删除名为<名>远程仓库的连接。

<pre><code>git remote rename &lt;old-name&gt; &lt;new-name&gt;</code></pre>

重命名<旧名称>到<新名称>的远程连接。

####讨论

Git是设计给每个开发人员完全隔离的开发环境。这意味着，信息不会自动来回传递库之间。相反，开发人员需要手动拉上游提交到他们的本地仓库或手动把他们的本地提交备份到中央存储库。 git的远程命令实际上只是一个到URL传递给这些“共享”命令更简单的

#####The origin Remote

当你克隆一个仓库使用Git克隆，它会自动创建一个名为起源指回克隆库的远程连接。这对于开发者创建一个中央资料库的本地副本非常有用，因为它提供了一种简单的方法来拉动上游的变化或发布本地提交。这种行为也是为什么大多数基于Git的项目叫他们的中央存储库的起源。

#####Repository URLs

Git的支持许多方法来引用远程存储库。来访问远程回购的最简单的方法有两个是通过HTTP和SSH协议。 HTTP是一种简单的方法，让到存储库匿名只读访问。 例如：

<pre><code>http://host/path/to/repo.git</code></pre>

但是，它一般不可能推到提交HTTP地址（你不会希望允许匿名推送反正）。对于读写访问，您应该使用SSH代替：

<pre><code>ssh://user@host/path/to/repo.git</code></pre>

你需要在主机上的有效SSH帐户，但除此之外，得到了支持通过SSH认证的访问开箱。

####例子

施氮原点，它往往是方便的，以你的队友“仓库的连接。例如，如果你的同事，约翰，保持在dev.example.com/john.git可公开访问的存储库，可以按如下方式添加一个连接：

<pre><code>git remote add john http://dev.example.com/john.git</code></pre>

有了这种访问个别开发商的库使得有可能进行合作的中央存储库之外。这对于小型团队在一个大型的项目非常有用的。

###git fetch

git的获取命令导入从远程仓库到本地的回购承诺。由此产生的提交存储为远程分支，而不是我们一直使用正常的地方分支机构。这给你一个机会，使他们融入你的项目的副本之前查看变化。

####用法

<pre><code>git fetch &lt;remote&gt;</code></pre>

获取所有从库中的分支机构。这也下载所有从其他存储库所需的提交和文件。

<pre><code>git fetch &lt;remote&gt; &lt;branch&gt;</code></pre>

同上面的命令，但只取指定的分支。

####讨论

抓取是当你想看看其他人一直在你做什么。由于获取的内容表示为远程分支，它在您的本地开发工作绝对没有影响。这使得获取安全的方式将它们与本地存储库整合之前检查的提交。这是类似，它可以让你看到中央历史进展如何SVN更新，但它不会强迫你改变实际合并到你的资料库。

#####Remote Branches

远程分支就像当地的分支机构，但它们代表了从别人的库提交。您可以检查出一个远程分支就像一个地方之一，但是这让你在一个分离的头状态（就像检查出一个老提交）。你可以认为他们是只读的分支机构。要查看远程分支，简单地传递-r标志git的分支命令。远程分支机构通过它们属于这样你就不会与他们当地的分支机构混淆远程前缀。例如，下面的代码片段显示了从原点远程获取后，你可能会看到分支：

<pre><code>git branch -r
# origin/master
# origin/develop
# origin/some-feature</code></pre>

同样，你可以检查与通常的git的结帐和git日志命令这些分支。如果批准远程分支包含了修改，就可以将其合并成一个普通的Git合并本地分支。因此，与SVN，使用远程存储库同步你的本地库实际上是一个过程分为两个步骤：取，然后合并。 git的拉命令是这一过程更为便捷。

####例子

这个例子遍历与中央存储库主分支同步您的本地仓库的典型工作流程。

<pre><code>git fetch origin</code></pre>

这将显示已下载的分支：

<pre><code>a1e8fb5..45e66a4 master -> origin/master
a1e8fb5..9e8ab1c develop -> origin/develop
* [new branch] some-feature -> origin/some-feature</code></pre>

从这些新的远程分支提交显示为正方形而非圆形下图所示。正如你所看到的，混帐取，您可以访问到另一个仓库的整个分支结构。

![配图02](https://www.atlassian.com/git/images/tutorials/collaborating/syncing/02.svg "配图02")

要查看提交已被添加到上游主，您可以使用原产地/主作为过滤器运行git的日志

<pre><code>git log --oneline master..origin/master</code></pre>

批准更改并将其合并到本地的master分支用下面的命令：

<pre><code>git checkout master
git log origin/master</code></pre>

然后我们可以使用git合并产地/主

<pre><code>git merge origin/master</code></pre>

起源/主和主分支现在都指向同一个commit，而你与上游的发展同步。

###git pull

合并上游变成你的本地库是基于Git的协作工作流程的共同任务。我们已经知道如何用git取指令之后的Git合并做到这一点，但混帐拉卷成一个单一的命令这一点。

####用法

<pre><code>git pull &lt;remote&gt;</code></pre>

取当前分支中指定的远程复制，并立即将它并入本地副本。这是一样的git的取指<远程>其次是git的合并产地/<当前分支>。

<pre><code>git pull --rebase &lt;remote&gt;</code></pre>

同上面的命令，但而不是用git合并与当地一个远程分支整合，使用git底垫。

####讨论

你能想到的git拉为SVN更新的Git版本。这是你的本地仓库与上游的更改同步的简单方法。下面的图说明了牵拉过程的每一个步骤。

![配图03](https://www.atlassian.com/git/images/tutorials/collaborating/syncing/03.svg "配图03")

你开始思考你的资料库是同步的，但随后的git获取显示，自上次检查了它主人的原始版本已取得进展。然后git的合并整合，立即远程主到本地之一：

#####Pulling via Rebase

该--rebase选项可用于通过防止不必要的合并提交，以确保线性的历史。许多开发者更喜欢衍合过合并，因为这等于是说，“我希望把我对别人都做了顶部。改变”在这个意义上，用git与--rebase标志拉动更喜欢比一个SVN更新普通的git拉。

事实上，随着--rebase拉动是这样一个共同的工作流程，有它的专用配置选项：

<pre><code>git config --global branch.autosetuprebase always</code></pre>

运行命令后，所有的git pull命令将通过整合的Git变基，而不是混帐合并。

####例子

下面的例子演示了如何与中央存储库主分支同步：

<pre><code>git checkout master
git pull --rebase origin</code></pre>

这只是移动你的本地修改到的别人都已经贡献了顶部。

###git push

推的是如何从您的本地存储库转移到提交远程回购。这是对口的git取，但取而进口致力于当地的分支机构，推动出口承诺远程分支机构。这有覆盖变化的潜力，所以你需要你如何使用它要小心。这些问题将在下面讨论。

####用法

<pre><code>git push &lt;remote&gt; &lt;branch&gt;</code></pre>

按指定的分支<远程>，所有必要的提交和内部对象的一起。这会在目标资源库的本地分支。为了防止您覆盖提交，Git不会让你推，当它导致在目标资源库非快进合并。

<pre><code>git push &lt;remote&gt; --force</code></pre>

与上述相同的命令，但强制推即使它会导致在非快进合并。除非你绝对相信你知道自己在做什么，否则不要使用--force标志。

<pre><code>git push &lt;remote&gt; --all</code></pre>

推动所有本地分支到指定的远程。

<pre><code>git push &lt;remote&gt; --tags</code></pre>

标签，当你推一个分支或使用--all选项不会自动压入。该--tags标志将所有本地标签到远程存储库。

####讨论

最常见的用例混帐推是发布本地更改到一个中央存储库。你已经积累了数本地提交，并准备与团队的其他成员分享之后，（可选）清理它们与互动变基，然后将它们推到中央存储库。

![配图04](https://www.atlassian.com/git/images/tutorials/collaborating/syncing/04.svg "配图04")

上图显示了当本地主已进展过去中央信息库掌握和发布运行git推起源大师的变化会发生什么。注意混帐推如何在本质上是一样的远程仓库内运行的git合并大师。

#####Force Pushing

Git的防止你拒绝推送请求时，导致非快进合并覆盖中央存储库的历史。所以，如果远程历史从历史分歧，你需要拉远程分支和合并到你本地，然后尝试再次推。这类似于SVN如何让你犯了变更前经SVN更新的中央存储库同步。

该--force标志覆盖此行为，并使得远程仓库分支匹配您的本地之一，删除自上次拉时可能发生的任何上游的变化。你曾经需要强制推送的唯一情况是，当你意识到你刚刚共享的提交是不完全正确，你固定它们与git的承诺--amend或交互式衍合。但是，你必须绝对肯定没有你的队友都使用--force选项前拉着这些提交。

#####Only Push to Bare Repositories

此外，你应该只推到已与--bare标志创建存储库。由于推混乱与远程分支结构，它永远不会推到其他开发人员的信息库是非常重要的。但由于裸回购没有工作目录，这是不可能打断任何人的发展。

####例子

下面的例子描述了发布到中央存储库本地的捐款标准方法之一。首先，它可以确保你的本地主达最新的获取由中央仓库的副本，并在上面衍合的变化。互动变基也分享他们之前清理你提交一个很好的机会。然后，混帐推命令将所有提交的在您的本地师傅到中央存储库。

<pre><code>git checkout master
git fetch origin master
git rebase -i origin/master
# Squash commits, fix up commit messages etc.
git push origin master</code></pre>

既然我们已经确信本地主升最新的，这将导致一个快进合并，混帐推不应该抱怨上述任何非快进的问题。

原文：[Syncing](https://www.atlassian.com/git/tutorials/syncing "Syncing")
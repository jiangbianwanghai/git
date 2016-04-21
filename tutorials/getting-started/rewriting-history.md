![改写历史](https://www.atlassian.com/git/images/tutorials/getting-started/rewriting-history/hero.svg "改写历史")

#改写历史

###简介

Git的主要工作是确保你永远不会失去一个坚定的变化。但是，它的设计也让您对您的开发工作流程的完全控制。这包括让你定义到底是什么项目历史类似;然而，它也造成失去提交的潜力。 Git提供了使用它们可能导致丢失内容免责声明下，它的历史重写的命令。

本教程介绍了一些最常见的原因为覆盖致力于快照，并告诉您如何避免这样做的缺陷。

###git commit --amend

该git的承诺--amend命令来修复最近提交的便捷方式。它可以让你把演出与以往提交的变化，而不是提交它作为一个全新的快照。它也可以使用而不改变其快照只需编辑先前提交信息。

![配图01](https://www.atlassian.com/git/images/tutorials/getting-started/rewriting-history/01.svg "配图01")

但是，修正并不仅仅改变最近一次提交，这完全替换它。到Git，它看起来像一个全新的承诺，这是可视化与上面的图中星号（*）。它与公共仓库工作时，记住这一点很重要。

####用法

<pre><code>git commit --amend</code></pre>

结合与以前的暂存的变更提交和取代以前用产生的快照提交。运行这个时候没有什么演出，可以编辑先前提交信息而不改变其快照。

####讨论

过早提交发生在日常发展的过程中所有的时间。人们很容易忘记上演文件或进行格式化提交信息的错误的方式。该--amend标志就是修正这些小错误的便捷方式。

#####不修改公开承诺

在git的重置页面，我们谈论你如何不应该重置已经与其他开发者共享的提交。这同样适用于修正：修正从未已经推送到公共仓库的更新。

修订提交实际上是全新的提交，之前的承诺是从项目历史中删除。这与重置公共快照，导致同样的后果。如果你修改提交，其他开发人员根据他们的工作，它看起来像他们工作的基础上，从项目历史消失了。这对于开发商是在一个混乱的局面，它的复杂歇着。

####例子

下面的例子演示了基于Git的开发一个常见的场景。我们编辑，我们希望在一个单一的快照提交一些文件，但我们忘记了周围添加一个文件的第一次。修复错误仅仅是分期等文件，并用--amend旗犯的问题：

<pre><code># Edit hello.py and main.py
git add hello.py
git commit

# Realize you forgot to add the changes from main.py
git add main.py
git commit --amend --no-edit</code></pre>

编辑器将随消息填充从以前的承诺和包括--no编辑标志将让你做出修正你的提交不改变其提交信息。如有必要，你可以改变它，否则只是保存并关闭文件如常。由此产生的提交将取代不完整的一个，它看起来像我们提交更改单个快照hello.py和main.py。

###git rebase

衍合是一个分支移动到新基提交的过程。一般过程可以看作如下：

![配图02](https://www.atlassian.com/git/images/tutorials/getting-started/rewriting-history/02.svg "配图02")

就内容而言，垫底真的只是移动一个分支从一个提交到另一个。但在内部，Git会通过创造新提交并将它们应用到指定的基它的字面意思重写你的项目的历史实现这一目的。要明白，这是非常重要的，即使分支看起来是一样的，它是由全新的提交。

####用法

<pre><code>git rebase &lt;base&gt;</code></pre>

重订当前分支到<基>，它可以是任何形式的承诺引用（一个ID，一个分行名称，标签或相对引用HEAD）。

####讨论

对于垫底的主要原因是为了保持线性项目历史。例如，考虑在那里，因为你开始一项功能的工作主分支已取得进展的情况：

![配图03](https://www.atlassian.com/git/images/tutorials/getting-started/rewriting-history/03.svg "配图03")

您有您的整合功能到主分支两种选择：直接合并或重订基，然后合并。在3路合并，并在合并前一种选择的结果犯，而在快进合并后的结果和一个完美的线性历史。下图演示了如何衍合到主便于快进合并。

![配图04](https://www.atlassian.com/git/images/tutorials/getting-started/rewriting-history/04.svg "配图04")

重订基期是整合上游变成你的本地库的常用方法。在一个多余的合并与混帐合并结果的变化上游拉动提交您想了解项目的进展每次。在另一方面，垫底就像是说，“我想我的基础变化是什么大家都已经做了。”

#####Don’t Rebase Public History

正如我们与git的承诺--amend和git复位讨论，你千万不要衍合那些已经推送到公共仓库的更新。底垫将更换新的旧的提交，它看起来像你的项目那段历史突然消失了。

####例子

下面的例子结合的git使用git合并变基到保持线性项目历史。这是一个快速简便的方法，以确保您的合并将是快进。

<pre><code># Start a new feature
git checkout -b new-feature master
# Edit files
git commit -a -m "Start developing a feature"</code></pre>

在我们的功能的中间，我们意识到有一个安全漏洞，在我们的项目

<pre><code># Create a hotfix branch based off of master
git checkout -b hotfix master
# Edit files
git commit -a -m "Fix security hole"
# Merge back into master
git checkout master
git merge hotfix
git branch -d hotfix</code></pre>

合并入此修复程序后主人，我们有一个叉形项目历史。相反，一个普通的Git合并，我们将关注的分支与变基保持线性的历史整合：

<pre><code>git checkout new-feature
git rebase master</code></pre>

这会将新特性掌握的技巧，它可以让我们从主做一个标准的快进合并：

<pre><code>git checkout master
git merge new-feature</code></pre>

###git rebase -i

运行混帐-i标志底垫开始一个交互式衍合会话。相反，盲目地移动所有提交的新基地，交互式衍合让您有机会来改变在这个过程中个人提交。这使您可以通过删除，分割和改变现有的一系列提交清理历史。这就像git的承诺--amend类固醇。

####用法

<pre><code>git rebase -i &lt;base&gt;</code></pre>

重订当前分支到<基>，但使用交互式衍合会话。这将打开一个编辑器，您可以输入每个命令（如下所述）承诺将重订。这些命令确定提交如何个体将被转移到新的基地。还可以重新排列提交列出改变提交本身的顺序。

####讨论

互动垫底让您对您的项目的历史是什么样子完全控制。这提供了一个很大的自由去发展，因为这让他们犯了“混乱”的历史，当他们专注于写代码，然后回去和事后清理。

大多数开发人员喜欢使用一个交互式的rebase它合并到主代码库之前，擦亮一个特性分支。这给了他们机会壁球微不足道的提交，删除过时的，并承诺对“官方”项目历史前确保一切是为了。为了大家一样，它看起来就像整个功能是在一个单一的一系列精心策划的提交发达。

####例子

发现下面的例子是从非交互式的git底垫页的一个的互动适应。

<pre><code># Start a new feature
git checkout -b new-feature master
# Edit files
git commit -a -m "Start developing a feature"
# Edit more files
git commit -a -m "Fix something from the previous commit"

# Add a commit directly to master
git checkout master
# Edit files
git commit -a -m "Fix security hole"

# Begin an interactive rebasing session
git checkout new-feature
git rebase -i master</code></pre>

最后一个命令将打开填充了新功能，这两个提交一个编辑器，具有一定的指导：

<pre><code>pick 32618c4 Start developing a feature
pick 62eed47 Fix something from the previous commit</code></pre>

您可以更改挑命令之前，每次提交，以确定它如何被变基中移动。在我们的例子，我们只是一个壁球命令将二者结合起来提交：

<pre><code>pick 32618c4 Start developing a feature
squash 62eed47 Fix something from the previous commit</code></pre>

保存并关闭开始变基的编辑器。这将打开另一个编辑器要求为组合快照提交信息。定义提交信息后，底垫是完整的，你应该能够看到你的git的日志输出压扁提交。这整个过程可以被可视如下：

![配图05](https://www.atlassian.com/git/images/tutorials/getting-started/rewriting-history/05.svg "配图05")

请注意，压扁犯有不同的ID或者比原来的提交，它告诉我们，这确实是一个全新的提交。

最后，你可以做一个快进合并到抛光特性分支整合到主代码库：

<pre><code>git checkout master
git merge new-feature</code></pre>

交互式衍合的实际功率可以在生成主分支额外62eed47的历史可以看出承诺是无处可寻。为了其他人，它看起来像你是谁与完美量实现的新功能的开发光辉围绕提交的第一次。这是交互式的衍合如何保持项目的历史干净意义。

###git reflog

Git的跟踪更新使用一种称为引用日志机制分支机构的一角。这可以让你回去，即使他们不被任何分支或标记中引用的变更。改写历史后，引用日志包含有关树枝的老态信息，并允许您在必要时回到那个状态。

####用法

<pre><code>git reflog</code></pre>

显示为本地资源库的引用日志。

<pre><code>git reflog --relative-date</code></pre>

显示相对最新的信息（例如，2个星期前）引用日志的。

####讨论

每当当前磁头被更新（通过切换分支，在新的变化拉动，重写历史或简单地通过添加新提交）一个新条目将被添加到该引用日志。

####例子

要了解git的引用日志，让我们通过一个实例运行。

<pre><code>0a2e358 HEAD@{0}: reset: moving to HEAD~2
0254ea7 HEAD@{1}: checkout: moving from 2.2 to master
c10f740 HEAD@{2}: checkout: moving from master to 2.2</code></pre>

上面的引用日志显示了由主到2.2分支和背部检出。从那里，有一个硬复位到旧提交。最新的活动是在顶部标有HEAD@ {0}表示。

如果事实证明你不小心搬回，reflog就会将包含在提交师傅指着（0254ea7）之前，你accidentially下跌2提交。

<pre><code>git reset --hard 0254ea7</code></pre>

使用Git复位，然后就可以改变主回提交以前。这提供了病历的安全网被意外更改。

要注意，如果修改已经提交到本地存储库中的引用日志只是提供了一个安全网，它仅跟踪的运动是很重要的。

原文：[Rewriting history](https://www.atlassian.com/git/tutorials/rewriting-history")
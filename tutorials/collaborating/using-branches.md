![Using Branches](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/hero.svg "Using Branches")

#使用分支

本教程是一个全面的介绍的Git分支。首先，我们将看看创建新的分支，这就好比要求一个新的项目的历史。然后，我们将看到如何结帐的git可以用来选择一个分支。最后，我们将学习如何混帐合并可以整合独立分支的历史。

当你阅读，请记住，Git的分支不像SVN分支。而SVN分支仅用来捕捉偶尔大规模发力，Git的分支是你的日常工作流程中不可或缺的一部分。

###git branch

分支表示发展的一个独立的线路。分行作为编辑/阶段的抽象/提交在Git中基础知识，这个系列的第一个模块中讨论的过程。你可以把它们作为一种请求一个全新的工作目录中，临时区域和项目的历史。新提交被记录在历史记录当前分支，从而导致该项目历史上的一个叉。

git的分支命令可以让你创建，列出，重命名和删除分支。它不会让你分支机构之间进行切换，或再次把分叉的历史重新走到一起。出于这个原因，git的分支紧密地与git的结帐和Git整合合并的命令。

####用法

<pre><code>git branch</code></pre>

列出所有的分支机构在你的资料库。

<pre><code>git branch &lt;branch&gt;</code></pre>

创建一个名为<枝>新的分支。这不签出新的分支。

<pre><code>git branch -d &lt;branch&gt;</code></pre>

删除指定的分支。这在Git的一个“安全”的操作会阻止您删除分支，如果有未合并的变化。

<pre><code>git branch -D &lt;branch&gt;</code></pre>

强制删除指定的分支，即使它有未合并的变化。这就是，如果你想永久扔掉所有发展的特定行相关的提交的使用命令。

<pre><code>git branch -m &lt;branch&gt;</code></pre>

重命名当前分支<分公司>。

####讨论

在Git，分支是你的日常开发过程中的一部分。当你想添加一个新功能或修复一个bug，无论多么大或多么小，你生成一个新的分支来封装更改。这可以确保不稳定的代码永远不会提交到主要的代码库，它为您提供了其合并到主分支之前清理功能的历史的机会。

![配图01](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/01.svg "配图01")

例如，上图中用可视化开发两个隔离线，一个是小功能，一个用于较长的运行特征库。通过在分行开发它们，它不仅可以并行地对他们两人的工作，但它也保持主主分支从可疑代码的自由。

#####分支提示

Git的分支背后的实现比SVN模型更加轻巧。而不是从目录到目录中复制文件，存储的Git分支，以提交的参考。在这个意义上说，一个分支表示一系列的尖端提交-它不是提交的容器。一个分支的历史是通过提交推断的关系。

这对Git的融合模式产生了巨大影响。而在SVN合并是一个文件的基础上进行，Git的，您可以在提交的更抽象的层次工作。实际上，你可以看到该项目历史上合并作为一个连接两个独立提交历史的。

####例子

#####创建分支

要明白，分支机构只是指向承诺是很重要的。当你创建一个分支，所有的Git需要做的是建立一个新的指针，它不会改变库以任何其他方式。所以，如果你开始看起来像这样一个存储库：

![配图02](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/02.svg "配图02")

然后，您使用以下命令创建一个分支：

<pre><code>git branch crazy-experiment</code></pre>

这个仓库的历史将保持不变。你得到的是一个新的指针到当前提交：

![配图03](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/03.svg "配图03")

注意，这只是创建新的分支。要开始添加提交给它，你需要用git checkout来选择它，然后使用标准添加的git和git commit命令。请参阅本模块的git的结帐部分获取更多信息。

#####删除分支

一旦you'be处理完一个分支，并把它合并到主代码库，你可以自由地删除分支，而不会丢失任何历史：

<pre><code>git branch -d crazy-experiment</code></pre>

但是，如果分支尚未合并，上面的命令将输出一个错误信息：

<pre><code>error: The branch 'crazy-experiment' is not fully merged.
If you are sure you want to delete it, run 'git branch -D crazy-experiment'.</code></pre>

这可以保护你失去参考那些提交，这意味着你将失去有效的发展是整个线路接入。如果你真的想删除的分支（例如，这是一个失败的实验），你可以利用资本-D标志：

<pre><code>git branch -D crazy-experiment</code></pre>

不论其地位和没有警告这将删除分支，所以明智地使用它。

###git checkout

Git的checkout命令，您可以通过git的分支建立分支机构之间进行导航。检查出一个分支更新的工作目录与存储在该分支的版本的文件，它会告诉的Git来记录这个分支所有新的提交。你可以把它作为一种方法来选择你的工作在其发展路线。

在前面的模块中，我们看到了结账混帐如何可以用于查看旧的提交。检查出的分支是在工作目录进行更新以匹配所选分支/修订相近;然而，新的变化将保存在项目历史，也就是说，它不是一个只读操作。

####用法

<pre><code>git checkout &lt;existing-branch&gt;</code></pre>

退房的规定分支，它应该已经可以用git branch创建。这使得<现有分支>当前分支，并更新工作目录相匹配。

<pre><code>git checkout -b &lt;new-branch&gt;</code></pre>

创建并检查了<新枝>。 -b选项是一个方便的标志，告诉混帐混帐运行结帐<新枝>之前运行git分支<新枝>。 git的结帐-b<新枝><现有分支>

同上调用，而是立足新的分支关闭<现有分支>而不是当前分支。

####讨论

git的结帐工作手牵手与git的分支。当你想开始一个新的功能，你创建的Git分支的一个分支，然后检查出来用git结帐。您可以在多个功能在一个单一的存储库与git的结帐它们之间切换工作。

![配图04](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/04.svg "配图04")

其每一个新功能的专用分支是从传统的工作流程SVN一个戏剧性的转变。这使得它可笑容易尝试新的实验，在不破坏现有功能的恐惧，它使得在许多不相关的功能在同一时间工作。此外，树枝也便于几个合作工作流程。

####Detached HEADs

现在，我们已经看到git的结帐的三个主要用途，我们可以谈论“分离的头：”我们以前的模块中遇到。

请记住，HEAD是神的指的是当前快照方式。在内部，通过git checkout命令仅更新了HEAD以指向指定的分支或提交。当它指向一个分支，Git不会抱怨，但是当你检查出提交，就切换到了“分离的头”状态。

![配图05](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/05.svg "配图05")

这是告诉你，你所做的一切，从项目发展的其他“超然”的警告。如果你要开始开发，而在一个分离的头状态的功能，就不会有分支让你回去吧。当你不可避免地结帐另一个分支（例如，合并在您的功能），就没有办法引用您的功能：

![配图06](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/06.svg "配图06")

问题是，你的开发应始终发生在一个分支从来没有在一个分离的头。这可以确保你总是有你的新提交的参考。但是，如果你只是在寻找一个古老的承诺，它并没有真正，如果你在一个分离的头的状态还是不很重要。

####例子

下面的例子演示了基本的Git分支过程。当你想开始一个新的功能时，您创建一个专用分支交换机到其中：

<pre><code>git branch new-feature
git checkout new-feature</code></pre>

然后，你可以提交就像我们在前面的模块已经看到了新的快照：

<pre><code># Edit some files
git add &lt;file&gt;
git commit -m "Started work on a new feature"
# Repeat</code></pre>

所有这些被记录在新的特征，这是完全从主隔离。你可以在这里添加尽可能多的提交根据需要而不必担心在你的分支的其他部分发生了什么事情。当它的时间要回“官方”的代码库，只需签出master分支：

<pre><code>git checkout master</code></pre>

这说明你的仓库的状态你开始你的功能之前。从这里，你必须完成的功能进行合并，岔开一个全新的，不相关的功能，或者做一些工作，你的项目的稳定版本的选项。

###git merge

合并是上帝把一个分叉的历史重新结合在一起的方式。 git的合并命令可以把发展由混帐分支创建独立的行，并将它们整合成一个单一的分支。

请注意，所有下面提出的命令合并到当前分支。当前分支将被更新，以反映该合并，但目标分支将完全不受影响。同样，这意味着混帐合并是结合经常使用Git的结账选择当前分支和Git分支-d删除过时的目标分支。

####用法

<pre><code>git merge &lt;branch&gt;</code></pre>

合并指定分支到当前分支。 GIT中会自动确定合并算法（下面讨论）。

<pre><code>git merge --no-ff &lt;branch&gt;</code></pre>

合并指定分支到当前分支，但总是产生一个合并提交（即使它是一个快进合并）。这是记录发生在你的仓库所有合并有用。

####讨论

一旦你完成开发在一个孤立的分支功能，它能够把它找回来到主代码库是非常重要的。根据存储库的结构，Git有几种不同的算法来实现这一目标：一个快进合并或3路合并。

当存在来自当前分支尖端到目标分支的线性路径，可能会发生的快速进合并。而不是“实际上是”合并分支机构，所有Git有做整合历史是移动（即“快进”）当前分支倾斜到目标分支的顶端。这有效地结合了历史，因为所有从目标分支到达的提交现在都可以通过当前。例如，某些特征的快进合并到主看起来像下面这样：

![配图07](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/07.svg "配图07")

然而，如果分支已发散一个快进合并是不可能的。当没有目标分支的线性路径，GIT中没有选择，但通过3路合并来组合它们。 3路合并采用专用提交的两个历史联系在一起。的命名来自于Git使用三个提交生成合并提交的事实：这两个分支的技巧和他们的共同祖先。

![配图08](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/08.svg "配图08")

虽然你可以使用这些合并的策略，许多开发人员喜欢使用快进合并（通过重订基期促进）为小功能和bug修正，同时保留3路合并为长时间运行功能的集成。在后一种情况下，所产生的合并提交用作符号接合两个分支。

#####解决冲突

如果你试图合并这两个两个分支改变了同一个文件的同一部分，Git会无法弄清楚使用哪个版本。当这种情况发生时，它就停在之前合并提交，以便您可以手动解决冲突。

Git的合并过程的很大一部分是它使用熟悉的编辑/台/提交的工作流程解决合并冲突。当你遇到一个合并冲突，在运行的git status命令显示哪些文件需要解决。例如，如果两个分支修改hello.py的同一节，你会看到类似以下内容：

<pre><code># On branch master
# Unmerged paths:
# (use "git add/rm ..." as appropriate to mark resolution)
#
# both modified: hello.py
#</code></pre>

然后，你可以去和修复了合并，以自己的喜好。当你准备好完成合并，所有你需要做的就是运行git对冲突的文件（S）添加到通知Git他们解决。然后，运行正常的git的承诺产生合并提交。这是完全相同的进程犯一个普通的快照，这意味着它很容易为普通开发人员能够管理自己的合并。

需要注意的是合并冲突只会发生在一个3路合并的事件。它是不可能有一个快进合并更改冲突。

####例子

#####快进式合并

第一个例子演示了一个快进合并。下面的代码创建一个新的分支，增加了两个来提交，然后将其集成到采用快进合并的主线。

<pre><code># Start a new feature
git checkout -b new-feature master

# Edit some files
git add <file>
git commit -m "Start a feature"

# Edit some files
git add <file>
git commit -m "Finish a feature"

# Merge in the new-feature branch
git checkout master
git merge new-feature
git branch -d new-feature</code></pre>

这对于使用多为比长时间运行特点的组织工具，一个孤立的发展短命的特性分支常见的工作流程。

还要注意的是混帐不应该抱怨Git的分支-d，因为新的功能现在从主分支访问。

#####3-Way Merge

下一个例子很相似，但需要一个3路合并，因为主人的进展，而该功能正在进行。这是一个大的特点，或当几个开发者在一个项目中同时工作一个常见的场景。

<pre><code># Start a new feature
git checkout -b new-feature master

# Edit some files
git add <file>
git commit -m "Start a feature"

# Edit some files
git add <file>
git commit -m "Finish a feature"

# Develop the master branch
git checkout master

# Edit some files
git add <file>
git commit -m "Make some super-stable changes to master"

# Merge in the new-feature branch
git merge new-feature
git branch -d new-feature</code></pre>

请注意，这是不可能的Git执行快进合并，因为没有办法移动掌握了新的特征，而不回溯。

对于大多数工作流程，新功能将是一个更大的功能，花了很长时间来开发，这将是新的，为什么会提交上出现主在此期间。如果你的特性分支竟是小如一个在上面的例子中，你可能会更好过重订基它放到主，做一个快进合并。这可以防止多余的合并塞满了项目的历史承诺。

原文：[Using Branches](https://www.atlassian.com/git/tutorials/using-branches "Using Branches")
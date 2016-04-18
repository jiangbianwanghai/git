![查看老提交配图](https://www.atlassian.com/git/images/tutorials/getting-started/viewing-old-commits/hero.svg "查看老提交配图")

#查看老提交

###git checkout

Git的checkout命令有三个不同的功能：检查出文件，签出的提交，并检查了分支机构。在此模块中，我们只关注前两种配置。

签出承诺使得该提交整个工作目录匹配。这可以用来观看项目的老态，而不以任何方式改变你目前的状态。签出文件，您可以看到一个老版本的特定文件，让你的工作目录的其余部分不变。

####用法

<pre><code>git checkout master</code></pre>

返回到主分支。树枝上挂满了下一个模块的深度，但现在，你可以认为这是一种方式来获得回项目的“当前”的状态。

<pre><code>git checkout &lt;commit&gt; &lt;file&gt;</code></pre>

签出文件的以前版本。这将打开<文件>驻留在工作目录进入一个完全相同的副本，从<提交>，并将其添加到临时区域。

<pre><code>git checkout &lt;commit&gt;</code></pre>

更新工作目录设置为指定提交的所有文件。您可以使用一个哈希提交或变量作为<提交>参数。这将让你在一个分离的头状态。

####讨论

之后的任何版本控制系统的整体思路是将存储项目的“安全”的副本，让你永远不必担心无可挽回破坏你的代码库。一旦你建立了一个项目的历史，混帐结账是一个简单的方法来“加载”这些保存快照到开发计算机上。

签出一个旧提交的是一个只读操作。这是不可能伤害你的资料库，同时查看旧版本。项目的“当前”的状态保持在主分支不变（详见分行模块）。在开发过程中的正常过程中，头部通常指向掌握或其他一些当地的分行，但是当你看看以前的承诺，HEAD不再指向一个分支，它指向直接提交。这被称为“分离的头”状态，并且它可以被可视化为如下：

![配图01](https://www.atlassian.com/git/images/tutorials/getting-started/viewing-old-commits/01.svg "配图01")

在另一方面，检查出旧文件会影响您的存储库的当前状态。您可以在一个新的快照，你会任何其他文件重新提交旧版本。所以，实际上，混帐结账这种用法作为一种方法来恢复到旧版本的个人文件。

![配图02](https://www.atlassian.com/git/images/tutorials/getting-started/viewing-old-commits/02.svg "配图02")

####例子

#####Viewing an Old Revision

这个例子假设你已经开始开发一个疯狂的实验，但你不知道，如果你想保持这一点。为了帮助你决定，你想看看该项目的状态，你开始实验前。首先，你需要找到你想看的修订的ID。

<pre><code>git log --oneline</code></pre>

比方说，你的项目的历史看起来像下面这样：

<pre><code>b7119f2 Continue doing crazy things
872fa7e Try something crazy
a1e8fb5 Make some important changes to hello.py
435b61d Create hello.py
9773e52 Initial import</code></pre>

您可以使用git checkout来查看“使一些进口变为hello.py”承诺如下：

<pre><code>git checkout a1e8fb5</code></pre>

这使得你的工作目录匹配a1e8fb5的确切状态提交。你可以看一下文件，编译项目，运行测试，并且无需担心失去该项目的当前状态，甚至编辑文件。你在这里做什么都不将被保存在您的存储库。要继续发展，就需要回到你的项目的“当前”的状态：

<pre><code>git checkout master</code></pre>

这是假设你在默认的主分支，这将在分行模块进行深入讨论发展。

一旦你回到主分支，您可以使用git的恢复或混帐复位撤消不期望的变化。

####Checking Out a File

如果你只在一个文件感兴趣，你也可以使用git结帐获取旧版本的它。例如，如果你只是想看看从旧的hello.py文件提交，你可以使用下面的命令：

<pre><code>git checkout a1e8fb5 hello.py</code></pre>

请记住，不像检查出一个提交，这会影响你的项目的当前状态。旧的文件修订将显示为一个“更改为承诺”，让您有机会恢复到以前版本的文件。如果您决定不希望保留旧版本，你可以检查出的最新版本具有以下：

<pre><code>git checkout HEAD hello.py</code></pre>


原文：[Inspecting a repository](https://www.atlassian.com/git/tutorials/inspecting-a-repository)
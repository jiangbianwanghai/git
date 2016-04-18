![检查存储库配图](https://www.atlassian.com/git/images/tutorials/getting-started/inspecting-a-repository/hero.svg "检查存储库配图")

#检查存储库

###git status

git的状态命令显示工作目录和暂存区域的状态。它可以让你看到哪些变化相继上演，其中有没有，哪些文件没有被跟踪的Git。状态输出不告诉你关于承诺的项目历史的任何信息。对于这一点，你需要使用git日志。

####用法

<pre><code>git status</code></pre>

列出哪些文件上演，不分级，并不露痕迹。

####讨论

git的状态的命令是一个相对简单的命令。它只是向您展示了已经持续使用Git添加和git的承诺。状态消息还包括分期/ unstaging文件的相关说明。呈现出的git状态调用的三个主要类别样本输出包含如下：

<pre><code># On branch master
# Changes to be committed:
# (use "git reset HEAD <file>..." to unstage)
#
#modified: hello.py
#
# Changes not staged for commit:
# (use "git add <file>..." to update what will be committed)
# (use "git checkout -- <file>..." to discard changes in working directory)
#
#modified: main.py
#
# Untracked files:
# (use "git add <file>..." to include in what will be committed)
#
#hello.pyc</code></pre>

####Ignoring Files

未跟踪文件通常分为两类。他们是刚刚被添加到项目和尚未提交任何文件，或者他们虽然这是绝对有益的，包括在GIT原编译像.pyc文件，OBJ，.EXE等可执行文件状态输出，后者则可以使它很难看到在你的仓库实际发生的。

为此，Git的，您可以通过放置在路径被称为的.gitignore一个特殊的文件完全忽略的文件。你想忽略的任何文件应包含在单独一行，而*符号可以用作通配符。例如，添加以下到项目的根将防止出现在git的状态编译Python模块.gitignore文件以：

<pre><code>*.pyc</code></pre>

####例子

这是很好的做法来检查提交修改之前版本库的状态，使用户不小心犯一些你不故意的。这个例子显示之前和分期，并承诺快照后的版本库的状态：

<pre><code># Edit hello.py
git status
# hello.py is listed under "Changes not staged for commit"
git add hello.py
git status
# hello.py is listed under "Changes to be committed"
git commit
git status
# nothing to commit (working directory clean)</code></pre>

第一个状态输出将显示该文件作为不分级。 git的补充作用将体现在第二git的状态，最终状态输出会告诉你，没有什么承诺，工作目录匹配最近的提交。有些Git命令（例如，混帐合并）要求工作目录是干净的，这样你就不会意外覆盖的变化。

###git log

git log命令显示犯下快照。它可以让你列出该项目的历史，进行过滤和搜索特定的变化。虽然git的状态，您可以检查工作目录和临时区域，git的日志只能对承诺的历史。

![配图01](https://www.atlassian.com/git/images/tutorials/getting-started/inspecting-a-repository/01.svg "配图01")

日志输出可以以多种方式进行定制，从简单的滤波提交到在完全用户定义的格式显示它们。一些git的日志的最常见的配置的介绍如下。

####用法

<pre><code>git log</code></pre>

显示整个使用默认的格式提交历史。如果输出占用超过一个屏幕，你可以使用空格键来滚动和q退出。

<pre><code>git log -n &lt;limit&gt;</code></pre>

通过<限制>限制提交的数目。例如，git的日志-n3将只显示3提交。

<pre><code>git log --oneline</code></pre>

凝聚各承诺一行。这是获得该项目历史的高度概述有用。

<pre><code>git log --stat</code></pre>

随着普通GIT中的日志信息，包括哪些文件被改变，加入或删除从他们每个人的所有行的相对数。

<pre><code>git log -p</code></pre>

显示表示每次提交补丁。这显示了完整的diff每次提交，这是你可以有你的项目历史上最详细视图。

<pre><code>git log --author="&lt;pattern&gt;"</code></pre>

特定作者搜索提交。在<模式>参数可以是一个普通字符串或正则表达式。

<pre><code>git log --grep="&lt;pattern&gt;"</code></pre>

搜索与匹配提交信息<模式>，它可以是一个普通字符串或正则表达式的提交。

<pre><code>git log &lt;since&gt;..&lt;until&gt;</code></pre>

仅显示之间发生的<自> <直至>提交。这两个参数可以是一个提交ID，一个分支名，HEAD，或任何其他类型的修订参考。

<pre><code>git log &lt;file&gt;</code></pre>

只显示提交包含指定的文件。这是查看特定文件的历史记录的简单方法。

<pre><code>git log --graph --decorate --oneline</code></pre>

一些有用的选项来考虑。该旗 - 图会画上提交信息的左侧提交的基于文本的图表。 -decorate增加分支机构或显示在提交的变量的名称。 -on线显示在提交一览在一行使它更容易地浏览提交的信息。

####讨论

git log命令是Git的探索存储库的历史的基本工具。这是当你需要找到一个项目的特定版本或弄清楚什么样的变化将在一个特性分支合并介绍你用什么。

<pre><code>commit 3157ee3718e180a9476bf2e5cab8e3f1e78a73b7
Author: John Smith</code></pre>

这其中大部分是非常简单的;然而，第一行值得一些解释。 40个字符的字符串提交后的提交的内容的SHA-1校验和。这有两个目的。首先，它确保的完整性的提交 - 如果它是有史以来损坏，提交将产生不同的校验和。其次，它充当提交的唯一ID。

这个ID可以像git的日志命令使用<自> .. <直至>指特定的提交。例如，git的日志3157e..5ab91将显示ID的3157e和5ab91在提交的一切。除了校验，分支名称（中科模块讨论）和HEAD关键字是指个人提交的其他常用方法。 HEAD总是指当前犯，无论是分支机构或一个特定的提交。

〜字符是制作相对引用到的提交父有用。例如，3157e〜1指的是提交3157e面前，HEAD〜3是当前的曾祖提交。

背后所有这些识别方法的想法是让您执行基于特定提交的行动。 git log命令通常是对这些相互作用的起点，因为它可以让你找到你想要一起工作的提交。

####例子

用法部分提供git的日志的例子很多，但要记住这几个选项可以合并成一个单一的命令：

<pre><code>git log --author="John Smith" -p hello.py
</code></pre>

这将显示所有的变化约翰·史密斯到文件hello.py做了充分的差异。

..语法的是比较分支非常有用的工具。下一个例子显示所有在一些特征不在掌握所有提交的简要概述。

<pre><code>git log --oneline master..some-feature</code></pre>


原文：[Inspecting a repository](https://www.atlassian.com/git/tutorials/inspecting-a-repository)
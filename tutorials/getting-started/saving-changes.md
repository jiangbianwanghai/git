![保存更改](https://www.atlassian.com/git/images/tutorials/getting-started/saving-changes/hero.svg "保存更改")

#保存更改

###git add

git命令添加一个改变工作目录添加到暂存区域。它告诉Git,你想包括在下一次提交更新到一个特定的文件。然而,git存储库添加并不影响在任何重大way-changes没有记录,直到你跑git提交。

结合这些命令,你还需要git状态查看工作目录的状态和暂存区域。

####用法

<pre><code>git add &lt;file&gt;</code></pre>

阶段的所有更改在&lt;file&gt;提交。

<pre><code>git add &lt;directory&gt;</code></pre>

阶段的所有更改为&lt;directory&gt;下一个承诺。

<pre><code>git add -p</code></pre>

开始交互式临时会话,让你选择部分文件添加到下一个承诺。这将给你一个块的变化,提示您的命令。块使用y阶段,n忽略块,把它分成小块,e手动编辑块,和q退出。

####讨论

<code>git add</code> 和 <code>git commit</code> 命令组成基本git工作流。这些两个命令每一个Git用户需要理解,不管他们的团队的协作模型。他们的手段记录版本的项目进入库的历史。

开发一个项目围绕着基本的编辑/ /提交模式阶段。首先,你编辑你的工作目录中的文件。当你准备保存项目的当前状态的一个副本,你和git添加阶段变化。你满意了快照后,您提交的项目与git提交历史。

![配图01](https://www.atlassian.com/git/images/tutorials/getting-started/saving-changes/01.svg "配图01")

git添加命令不应混淆svn添加,将一个文件添加到存储库。相反,git添加工作在更抽象的层面上的变化。这意味着git添加需要叫你每次修改一个文件,而svn添加每个文件只需要调用一次。这听起来可能有点多余,但这个工作流程使得它更容易保持一个项目组织。

####暂存区

暂存区域是Git的更独特的特性,它可以花些时间来充实你的大脑,如果你来自一个SVN(甚至是水银)背景。它有助于把它看作一个工作目录和项目历史之间的缓冲。

而不是提交所有的更改你自从上次提交,舞台让你组相关变化成高度集中实际上快照之前提交项目历史。这意味着你可以做各种各样的编辑无关的文件,然后回去把他们分成逻辑提交通过添加相关的变化阶段,提交他们的乐队。在任何版本控制系统,重要的是要创造原子提交,这样很容易跟踪bug和恢复的变化对其他项目的影响微乎其微。

####例子

当你开始一个新项目,git添加为svn进口起着相同的作用。创建一个初始提交的当前目录,使用以下两个命令:

<pre><code>git add .
git commit</code></pre>

一旦你有你的项目安装,可以通过添加新文件的路径git添加:

<pre><code>git add hello.py
git commit</code></pre>

上面的命令也可以用来记录更改现有的文件。再次,Git没有区分暂存新文件的变化和改变文件已经添加到存储库中。

###git commit

git commit命令提交了项目历史快照。承诺的快照可以被认为是“安全”版本的project-Git永远不会改变他们,除非你明显地问。与git添加,这是最重要的一个git命令。

虽然它们共享相同的名称,但这一点也不像svn commit命令。快照提交到本地存储库,这需要绝对没有交互与其他Git存储库。

####用法

<pre><code>git commit</code></pre>

提交了快照。这将启动一个文本编辑器提示您提交消息。当你进入了一个信息,保存文件并关闭编辑器来创建实际的承诺。git commit - m”<message>”

提交了快照,而推出的一个文本编辑器,使用<消息>提交消息。

<pre><code>git commit -a</code></pre>

提交一个快照的所有更改工作目录。这只包括修改跟踪文件(那些添加了git添加在他们的历史中)。

####讨论

快照总是致力于本地存储库。这是完全不同的从SVN,其中工作副本致力于中央存储库。相比之下,Git没有迫使你与中央存储库交互,直到你准备好了。正如暂存区域之间缓冲工作目录和项目历史,每个开发人员的本地存储库是他们的贡献和中央存储库之间的缓冲。

这种变化的基本发展模式Git用户。相反的变化,它直接提交到中央回购,Git开发人员有机会积累提交当地的回购。这SVN-style合作相比,具有很多优点:它可以更容易地将一个功能分解成原子提交,保持相关提交组合在一起,在出版之前清理当地的历史到中央存储库中。它还允许开发人员在一个孤立的环境中工作,直到他们推迟集成在一个方便的断点。

#####快照,而不是差异

除了实际区分SVN和Git,其底层实现也遵循完全不同的设计哲学。而SVN跟踪文件的差异,Git版本控制模型是基于快照。举个例子,一个SVN commit由diff相比原始文件添加到存储库中。Git,另一方面,记录每个提交每个文件的全部内容。

![配图02](https://www.atlassian.com/git/images/tutorials/getting-started/saving-changes/02.svg "配图02")

这使得许多比SVN Git操作要快得多,因为一个特定版本的文件不需要“组装”从其diffs-the完整的每个文件的修订立即从Git的内部数据库。

Git的快照模型有一个深远的影响其版本控制模型的几乎每一个方面,影响从其分支和合并工具协作工作流。

####例子

下面的示例假设您已经编辑的一些内容在文件称为你好。py并准备提交项目的历史。首先,您需要舞台与git添加文件,然后您可以提交了快照。

<pre><code>git add hello.py
git commit</code></pre>

这将打开一个文本编辑器(通过git配置可定制)要求提交消息,连同一个列表的承诺:

<pre><code># Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
# Changes to be committed:
# (use "git reset HEAD <file>..." to unstage)
#
#modified: hello.py</code></pre>

Git不需要提交消息遵循任何特定的格式限制,但规范化格式总结整个提交第一行不到50个字符,留下一个空行,然后详细解释的被改变了。例如:

<pre><code>Change the message displayed by hello.py

- Update the sayHello() function to output the user's name
- Change the sayGoodbye() function to a friendlier message</code></pre>

注意,很多开发人员还想使用现在时态的提交消息。这使得它们读更像动作库,这使得许多history-rewriting操作更直观。

原文：[Saving changes](https://www.atlassian.com/git/tutorials/saving-changes "Saving changes")
![撤销更改](https://www.atlassian.com/git/images/tutorials/getting-started/undoing-changes/hero.svg "撤销更改")

#撤销更改

本教程提供所有必要的技能，软件项目的早期版本的工作。首先，它表明你如何发掘老提交，然后将它解释了项目历史与重置本地计算机上做过修改恢复公众提交的区别。

###git checkout

Git的checkout命令有三个不同的功能：检查出文件，签出的提交，并检查了分支机构。在此模块中，我们只关注前两种配置。

签出承诺使得该提交整个工作目录匹配。这可以用来观看项目的老态，而不以任何方式改变你目前的状态。签出文件，您可以看到一个老版本的特定文件，让你的工作目录的

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

![配图01](https://www.atlassian.com/git/images/tutorials/getting-started/undoing-changes/01.svg "配图01")

在另一方面，检查出旧文件会影响您的存储库的当前状态。您可以在一个新的快照，你会任何其他文件重新提交旧版本。所以，实际上，混帐结账这种用法作为一种方法来恢复到旧版本的个人文件。

![配图02](https://www.atlassian.com/git/images/tutorials/getting-started/undoing-changes/02.svg "配图02")

####例子

#####查看旧版本

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

#####签出文件

如果你只在一个文件感兴趣，你也可以使用git结帐获取旧版本的它。例如，如果你只是想看看从旧的hello.py文件提交，你可以使用下面的命令：

<pre><code>git checkout a1e8fb5 hello.py</code></pre>

请记住，不像检查出一个提交，这会影响你的项目的当前状态。旧的文件修订将显示为一个“更改为承诺”，让您有机会恢复到以前版本的文件。如果您决定不希望保留旧版本，你可以检查出的最新版本具有以下：

<pre><code>git checkout HEAD hello.py</code></pre>

###git revert

git的还原命令撤销一个坚定的快照。但是，而不是删除该项目历史上提交，它的数字如何撤消提交引入的变化，并与追加所产生的内容的新承诺。这可以防止从Git的历史损失，这是你的修订历史记录的完整性和可靠的合作非常重要。

![配图03](https://www.atlassian.com/git/images/tutorials/getting-started/undoing-changes/03.svg "配图03")

####用法

<pre><code>git revert &lt;commit&gt;</code></pre>

生成一个新的提交了撤销所有的<提交>引入的变化，然后将其应用到当前的分支。

####讨论

还原时，应使用要删除从项目历史上的整个提交。这可能是有用的，例如，如果你跟踪一个bug，发现它是由一个单一的引进提交。不用手动进去，修复它，并提交新的快照，你可以使用git恢复到自动完成这一切为您服务。

#####Reverting vs. Resetting

理解git的复归是很重要的撤销单个提交 - 它通过删除所有后续提交不“恢复”回一个项目的以前的状态。在Git，这实际上是所谓的复位，而不是还原。

![配图04](https://www.atlassian.com/git/images/tutorials/getting-started/undoing-changes/04.svg "配图04")

复归拥有超过复位两个重要的优势。首先，它不改变项目的历史，这使得它对于已经发布到共享存储库提交一个“安全”的操作。有关为何改变共同的历史是很危险的详情，请参阅git的重置页面。

其次，混帐复归是能够针对个人承诺在历史上的任意一点，而git的复位只能向后工作从目前提交。例如，如果你想撤销一个旧犯了git的复位，你就必须删除所有发生后的目标承诺，删除了提交的，然后重新提交所有后续提交的。不用说，这不是一个优雅撤消溶液。

####例子

下面的例子是混帐复归一个简单的演示。它要求一个快照，然后立即用还原撤销它。

<pre><code># Edit some tracked files

# Commit a snapshot
git commit -m "Make some changes that will be undone"

# Revert the commit we just created
git revert HEAD</code></pre>

这可以被可视化为如下：

![配图05](https://www.atlassian.com/git/images/tutorials/getting-started/undoing-changes/05.svg "配图05")

注意，第4犯仍然是在恢复后的项目历史。而不是删除它，混帐复归增加了新的承诺，撤消它的变化。其结果是，第3和第5提交代表完全相同的代码库，而第4犯仍是我们的历史，以防万一，我们要回到它的道路。

###git reset

如果混帐复归是一个“安全”的方式撤消更改，你能想到的git重置为危险的方法。当你使用git复位撤消（和提交的任何参考或引用日志将不再引用），有没有办法恢复原始拷贝它是一个永久撤销。使用这个工具的时候，因为它是有失去工作的潜力唯一的Git命令之一必须小心。

像git的结帐，git的复位与许多配置一个通用的命令。它可用于去除致力于快照，虽然它更经常用于撤消在暂存区和工作目录的更改。在这两种情况下，它应该只用于撤消本地更改，你永远不应该重置已经与其他开发者共享快照。

####用法

<pre><code>git reset &lt;file&gt;</code></pre>

拆除临时区域指定的文件，但保留工作目录不变。这unstage文件而不覆盖任何更改。

<pre><code>git reset</code></pre>

重置暂存区，以配合最新的承诺，但是离开工作目录保持不变。这unstage所有文件，而不会覆盖任何更改，让您有机会从头开始，重新打造上演快照。

<pre><code>git reset --hard</code></pre>

重置暂存区和工作目录，以匹配最新的提交。除了unstaging变化，--hard标志告诉Git的覆盖在工作目录中的所有变化了。换句话说：这抹杀所有未提交的修改，所以请确保你真的想使用它之前扔掉你的地方发展。

<pre><code>git reset &lt;commit&gt;</code></pre>

移动当前分支尖端向后<提交>，重设临时区域相匹配，但先不谈工作目录。因为所做的所有修改<提交>将驻留在工作目录，它可以让你使用CCleaner的，更多的原子快照重新提交该项目的历史。

<pre><code>git reset --hard &lt;commit&gt;</code></pre>

向后移动当前分支尖端<提交>和复位两个临时区域和工作目录相匹配。这不仅抹杀未提交的变化，但<提交>毕竟犯，以及。

####讨论

上述所有调用的是用来清除从存储库的变化。如果没有--hard标志，git的复位是清理不分级通过改变或uncommitting一系列快照，并重新建立他们从头开始的储存库的方式。该--hard标志就派上用场了，当一个实验已经可怕的错误，你需要一个干净的石板一起工作。

而恢复可以安全地撤消公开承诺，git的复位的目的是撤消本地更改。由于其独特的目标，这两个指令的实现方式不同：完全复位删除一个变更，而恢复保持原有变更，并使用新的提交申请撤消。

![配图06](https://www.atlassian.com/git/images/tutorials/getting-started/undoing-changes/06.svg "配图06")

#####不要重置公共历史

你不应该使用git复位<提交>当后<提交>的任何快照已推送到公共仓库。发布提交后，你必须假设其他开发商都在它的依赖。

删除提交的其他团队成员继续发展带来了合作的严重问题。当他们尝试用你的资料库进行同步时，它看起来就像突然消失了项目历史的一大块。下面的序列说明当您尝试重置公开承诺会发生什么。起源/ master分支是你本地的master分支的中央存储库的版本。

![配图07](https://www.atlassian.com/git/images/tutorials/getting-started/undoing-changes/07.svg "配图07")

只要你在复位后添加新的提交，Git会认为你当地的历史已经从原产/主发散，且合并提交需要同步您的仓库很可能会混淆视听，阻挠你的团队。

重点是，确保你使用的git复位<提交>在本地的实验，出了问题，而不是发布的更改。如果你需要修复公共提交，git的恢复命令被用于此目的而设计的。

####例子

#####Unstaging a File

在准备上演快照的git的复位命令是经常遇到的。下一个例子假设您有两个文件叫你已经添加到仓库hello.py和main.py。

<pre><code># Edit both hello.py and main.py

# Stage everything in the current directory
git add .

# Realize that the changes in hello.py and main.py
# should be committed in different snapshots

# Unstage main.py
git reset main.py

# Commit only hello.py
git commit -m "Make some changes to hello.py"

# Commit main.py in a separate snapshot
git add main.py
git commit -m "Edit main.py"</code></pre>

正如你所看到的，git的复位可以帮助您保持，让你不相关下提交unstage改变你的提交高度关注。

#####删除本地提交

接下来的例子展示了一个更高级的使用情况。它表明，当你已经工作了一段新的实验，但决定犯了一些快照后彻底扔掉它会发生什么。

<pre><code># Create a new file called `foo.py` and add some code to it

# Commit it to the project history
git add foo.py
git commit -m "Start developing a crazy feature"

# Edit `foo.py` again and change some other tracked files, too

# Commit another snapshot
git commit -a -m "Continue my crazy feature"

# Decide to scrap the feature and remove the associated commits
git reset --hard HEAD~2</code></pre>

git的复位HEAD〜2命令通过两次提交向后移动当前分支，有效地消除我们刚刚从项目历史创建的两个快照。请记住，这种复位只应在未公布的提交使用。如果你已经推你的提交到共享存储库从未进行上述操作。

###git clean

git的clean命令从工作目录中删除未跟踪文件。这的确是一个更方便的命令，因为它是琐碎的，看看哪些文件是不露痕迹用git状态和手动删除它们。像一个普通的rm命令，git的清洁不能撤消，所以一定要确保你真的想你运行它之前删除未跟踪文件。

git的清洁命令经常与git的复位 - 硬联合执行。请记住，重置仅影响跟踪文件，因此需要清理那些未追踪一个单独的命令。相结合，这两个命令让你回到工作目录到特定提交的确切状态。

####用法

<pre><code>git clean -n</code></pre>

执行混帐干净的“预演”。这将告诉你哪些文件会不会实际上做它移走。

<pre><code>git clean -f</code></pre>

从当前目录中删除未跟踪文件。除非clean.requireForce配置选项设置为false（默认情况下它是真的）是必需的-f（强制）标记。这不会删除由指定的.gitignore未跟踪的文件夹或文件。

<pre><code>git clean -f &lt;path&gt;</code></pre>

删除未跟踪的文件，但是操作限制在指定的路径。

<pre><code>git clean -df</code></pre>

从当前目录中删除未跟踪文件和未跟踪目录。

<pre><code>git clean -xf</code></pre>

从当前目录中删除无路径的文件以及任何文件,Git通常忽略了。

####讨论

git的复位 - 硬和git干净-f命令是你最好的朋友，你已经在你的本地库取得了一些令人尴尬的发展，并要刻录的证据后。同时运行它们会使你的工作目录匹配最新的提交，给你一个干净的石板一起工作。

git的清洁命令也可以是一个生成后清理工作目录是有用的。例如，它可以很容易地除去的.o及由C编译器产生的.exe二进制文件。这是偶尔打包项目发布前的必要步骤。 -x选项是为此特别方便。

请记住，用git复位一起，git的清洁是必须永久删除提交的潜力唯一的Git命令之一，所以要小心。事实上，它是如此容易失去Git的维护者需要连最基本的操作-f标志的重要补充。这可以防止不小心用天真的git洁调用字句。

####例子

下面的例子中抹杀工作目录中的所有变化，包括已添加新文件。它假定你已经犯了一些快照，并与一些新的发展正在试验。

<pre><code># Edit some existing files
# Add some new files
# Realize you have no idea what you're doing

# Undo changes in tracked files
git reset --hard

# Remove untracked files
git clean -df</code></pre>

运行此复位/洁净序列后，工作目录以及暂存区域看起来酷似最近提交和git的状态将报告一个干净的工作目录。现在，您可以重新开始。

需要注意的是，不同于git的复位第二个例子中，新的文件是_不_添加到库中。其结果是，他们可能不会受到影响的git的复位 - 硬，并要求混帐干净删除它们。

原文：[Undoing Changes](https://www.atlassian.com/git/tutorials/undoing-changes "Undoing Changes")
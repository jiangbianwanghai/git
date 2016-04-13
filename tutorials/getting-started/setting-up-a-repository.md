![建立一个资料库](https://www.atlassian.com/git/images/tutorials/getting-started/setting-up-a-repository/hero.svg "建立一个资料库")

#建立一个资料库

本教程提供了最重要的Git命令的简要概述。首先，建立一个信息库部分解释了所有的你需要开始一个新的版本控制项目的工具。然后，剩下的部分介绍您的日常Git命令。

该模块的最后，你应该能够创建一个Git仓库，你的项目保管记录快照，并查看项目的历史。

###git init

git的init命令创建一个新的Git仓库。它可以用于现有的，未版本控制的项目转换为Git仓库或初始化一个新的空库。大多数其他Git命令都没有初始化的库外提供，因此这通常是你将在一个新的项目中运行的第一个命令。

执行git的初始化会在项目的根，它包含了所有回购所需的元数据的git的子目录。除了.git目录，现有项目保持不变（不同于SVN，Git的并不需要在每个子目录中的git的文件夹）。

####用法

<pre><code>git init</code></pre>

转换当前目录成一个Git仓库。这增加了的.git夹到当前目录并且使得能够启动该项目的记录的版本。

<pre><code>git init <directory> </code></pre>

创建在指定目录的空Git仓库。运行此命令将创建一个名为<目录包含无非是git的子目录新文件夹。

<pre><code>git init --bare <directory></code></pre>

初始化一个空的Git仓库，但省略了工作目录。共享库中，应当始终与--bare标志创建（参见下文）。按照惯例，仓库用的.git的--bear标志结束初始化。例如，一个存储库的裸版叫我的项目应该被存储在一个名为my-project.git目录。

####讨论

相比于SVN，git的init命令来创建新的版本控制项目的一个非常简单的方法。 Git不会要求您创建一个存储库，导入文件，并检查了工作副本。所有你需要做的是cd到项目文件夹，并运行git的init，你就会有一个功能齐全的Git仓库。

然而，对于大多数项目的git的init只需要执行一次创建一个中央存储库，开发人员一般不使用git init以建立自己的本地存储库。相反，他们通常会使用git克隆到现有的存储库复制到本地计算机。

####裸库

该--bare标志创建不具有工作目录库，因此无法编辑文件并提交该资料库的变化。因为树枝推到非纯仓库有覆盖变化的潜在中央库中，应当始终创建裸存储库。 --bare看作一种方式来标记存储库作为储存设施，而不是一个开发环境。这意味着几乎所有的Git的工作流程，在中央存储库是光秃秃的，和开发商本地资源库都是非光秃秃的。

![配图01](https://www.atlassian.com/git/images/tutorials/getting-started/setting-up-a-repository/01.svg "配图01")

####例如

由于git的克隆是创建一个项目的本地拷贝一个更便捷的方式，最常见的用例的git的init是创建一个中央存储库：

<pre><code>ssh <user>@<host>
cd path/above/repo 
git init --bare my-project.git</code></pre>

首先,您的SSH到服务器,它将包含您的中央存储库。然后,您导航到无论你想存储项目。最后,您使用——光标记创建一个中央存储库。开发人员将(克隆)(/教程/ setting-up-a-repository / git clone)我的项目。git开发机器上创建一个本地副本。

###git clone

git克隆命令拷贝现有的git存储库。这是有点像svn checkout,除了“工作副本”是一个成熟的Git repository-it有它自己的历史,管理自己的文件,从原来的库是一个完全隔离环境。

便利,克隆会自动创建一个远程连接称为原点指向回到原来的库。这使得它很容易与一个中心存储库。

####用法

<pre><code>git clone <repo> </code></pre>

克隆存储库位于<回购>到本地机器上。原来的库可以位于本地文件系统或远程机器上通过HTTP或SSH访问。

<pre><code>git clone <repo> <directory></code></pre>

克隆存储库位于<回购>到文件夹名为<目录>在本地机器上。

####讨论

如果一个项目已经设置在一个中央存储库,git克隆命令是最常见的方式让用户获得发展。git init、克隆通常是一次性操作开发人员取得工作副本,所有版本控制操作通过本地存储库管理和协作。

####Repo-To-Repo协作

重要的是要了解Git的“工作副本”的想法非常不同于你的工作副本通过检查代码从一个SVN储存库。不像SVN,Git没有区别工作副本和中央repository-they都成熟的Git存储库。

这使得与Git合作比与SVN根本不同。而SVN取决于中央存储库之间的关系和工作副本,Git的协作模型是基于repository-to-repository交互。而不是检查工作副本到SVN的中央存储库,你推或拉从一个存储库提交到另一个。

![配图03](https://www.atlassian.com/git/images/tutorials/getting-started/setting-up-a-repository/03.svg "配图03")

![配图02](https://www.atlassian.com/git/images/tutorials/getting-started/setting-up-a-repository/02.svg "配图02")

当然,没有什么阻止你给某些Git回购特别的意义。例如,通过指定一个Git存储库的“中央”存储库,可以使用Git复制一个集中式工作流。关键是,这是通过约定而不是根植到风险投资本身。

####例如

下面的例子演示了如何获得一个本地副本的存储在一个中央存储库使用SSH服务器可访问example.com的用户名约翰:

<pre><code>git clone ssh://john@example.com/path/to/my-project.git 
cd my-project
# Start working on the project</code></pre>

第一个命令初始化一个新的Git存储库在本地机器上我的项目文件夹和填充中央存储库的内容。然后,您可以cd到项目并开始编辑文件,提交快照,与其他存储库交互。也注意。git扩展是省略了从克隆存储库。这反映了non-bare本地副本的状态。

###git config

git配置命令允许您配置您的git安装从命令行(或单个存储库)。这个命令可以定义从用户信息存储库的行为偏好。下面列出了几种常见的配置选项。

####用法

<pre><code>git config user.name <name></code></pre>

作者名字定义为用于所有提交当前库中。通常,您会希望使用——全球标志为当前用户设置配置选项。

<pre><code>git config --global user.name <name></code></pre>

作者的名字定义为用于所有提交当前用户。

<pre><code>git config --global user.email <email></code></pre>

定义作者电子邮件被当前用户用于所有提交。

<pre><code>git config --global alias.<alias-name> <git-command></code></pre>

Git命令创建一个快捷方式。

<pre><code>git config --system core.editor <editor></code></pre>

定义命令所使用的文本编辑器如git提交当前机器上的所有用户。<编辑>参数应该命令启动所需的编辑器(例如,vi)。

<pre><code>git config --global --edit</code></pre>

在文本编辑器中打开全局配置文件进行手工编辑。

####讨论

所有的配置选项都存储在纯文本文件,因此git配置命令只是一个方便的命令行界面。通常情况下,你只需要配置一个Git安装你第一次开始工作在一个新的发展机器,和几乎所有情况下,您会希望使用——全球国旗。

Git存储的配置选项在三个独立的文件,它允许您选择范围单个存储库,用户,或整个系统:

* <回购> /。git / config - Repository-specific设置。
* ~ /。gitconfig——特定于用户的设置。这就是选择设置存储——全球的旗帜。
* (前缀)/ etc /美元gitconfig——系统范围的设置。

当选择在这些文件冲突,当地设置覆盖用户设置覆盖系统。如果你打开这些文件,您将看到类似以下:

<pre><code>[user] 
name = John Smith
email = john@example.com
[alias]
st = status
co = checkout
br = branch
up = rebase
ci = commit
[core]
editor = vim</code></pre>

您可以手动编辑这些值作为git配置完全相同的效果。

####例如

你要做的第一件事在安装Git是告诉它你的名字/电子邮件和定制的一些默认设置。一个典型的初始配置可能类似于以下几点:

<pre><code># Tell Git who you are
git config --global user.name "John Smith"
git config --global user.email john@example.com</code></pre>

<pre><code># Select your favorite text editor
git config --global core.editor vim</code></pre>

<pre><code># Add some SVN-like aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.up rebase
git config --global alias.ci commit</code></pre>

这将产生~ /。从一节gitconfig文件。

原文：[Setting up a repository](https://www.atlassian.com/git/tutorials/setting-up-a-repository "Setting up a repository")
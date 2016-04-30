![比较工作流](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/hero.svg "比较工作流")

#比较工作流

数组的工作流可以很难知道从哪里开始在实现Git在工作场所。这个页面提供了一个起点,为企业团队测量最常见的Git工作流。

当你阅读时,记住这些工作流设计为指导方针,而不是具体的规则。我们想告诉你什么是可能的,所以你可以混合和匹配方面从不同的工作流来满足您的个人需求。

##集中式工作流

![配图01](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/01.svg "配图01")

过渡到一个分布式的版本控制系统似乎是一项艰巨的任务,但你不需要改变你现有的工作流利用Git。您的团队可以开发项目以完全相同的方式,因为他们与颠覆。

然而,使用Git权力开发工作流提供了几个优势SVN。首先,它给整个项目的每个开发人员自己的本地副本。这个孤立的环境让每个开发人员独立工作项目时,他们可以添加的其他更改提交到本地库,完全忘记上游发展,直到它很方便。

第二,它允许您访问Git的健壮的分支和合并模型。与SVN,Git分支被设计成一个故障安全机制集成代码和共享存储库之间的变化。

###它是如何工作的

像Subversion,集中式工作流使用一个中央存储库作为所有更改项目的统一。树干,而是默认开发分支被称为大师,所有更改提交到这个分支。此工作流不需要任何其他分支除了主人。

开发人员开始通过克隆中央存储库。在他们自己的项目的本地副本,他们编辑文件和提交修改SVN;然而,这些新提交存储他们是完全孤立的中央存储库。这使得开发者可以推迟同步上游,直到他们在方便的断点。

官方发布更改项目,开发商“推”当地的主分支中央存储库。这相当于svn commit,除了它增加了所有的本地提交不已经在中央主分支。

![配图02](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/02.svg "配图02")

####管理冲突

中央存储库代表官方项目,所以它的提交历史应该被视为神圣的和不可改变的。如果一个开发人员的本地提交偏离中央存储库,Git将拒绝把自己的变更,因为这将覆盖正式提交。

![配图03](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/03.svg "配图03")

之前,开发人员可以发表他们的特性,他们需要获取更新中心提交和变基的变化上。这就像说,“我想添加更改其他人已经做了什么。“结果是一个完美的线性历史,就像在传统的SVN工作流。

如果本地更改直接与上游有冲突,Git将暂停垫底术过程,给你一个机会来手动解决冲突。Git的优点是它使用相同的Git地位和Git添加命令生成提交并解决合并冲突。这使得新开发人员更容易管理自己的合并。另外,如果他们给自己带来麻烦,Git使得它很容易中止整个变基,再试一次(或去找帮助)。

###例子

让我们一步一步看一个典型的小团队将如何使用这个工作流协作。我们将看到如何两个开发人员,约翰和玛丽,可以工作在不同的特性,通过分享他们的贡献一个集中的存储库。

#####一个初始化中央存储库

![配图04](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/04.svg "配图04")

首先,人需要在服务器上创建一个中央存储库。如果这是一个新的项目,你可以初始化一个空的存储库。否则,您将需要导入现有的Git或SVN储存库。

中央存储库应该总是裸存储库(他们不应该有一个工作目录中),可以创建如下:

ssh user@host git init --bare /path/to/repo.git

一定要使用一个有效的SSH用户名的用户,您的服务器的域名或IP地址的主机,和你想要的位置存储/路径/ / repo.git回购。注意,。git扩展通常添加到存储库名称表明这是一个裸存储库。

#####每个人都克隆中央存储库

![配图05](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/05.svg "配图05")

接下来,每个开发人员创建一个本地副本的整个项目。这是通过git克隆命令完成:

git clone ssh://user@host/path/to/repo.git

Git克隆存储库时,自动添加一个叫做起源的快捷方式,点“父”库中,假设你想要与之交互的道路上走的更远。

#####约翰在他的特性

![配图06](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/06.svg "配图06")

约翰在他的本地存储库,可以使用标准的开发特性Git提交流程:编辑阶段,提交。如果你不熟悉暂存区域,这是一种准备提交无需包括工作目录的每一个变化。这允许您创建高度集中提交,即使你做了很多当地的变化。

<pre><code>git status # View the state of the repo
git add <some-file> # Stage a file
git commit # Commit a file&lt;/some-file&gt;
</code></pre>

记住,这些命令创建本地提交以来,John可以多次重复这个过程他希望不用担心发生了什么在中央存储库中。这可能是非常有用的对于大型特性需要被分解成更简单、更原子块。

#####玛丽工作特性

![配图07](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/07.svg "配图07")

与此同时,玛丽正在自己的特性在自己的本地存储库使用相同的编辑/阶段提交进程。像约翰一样,她不关心发生了什么在中央存储库,和她真的不在乎约翰在做什么在他的本地存储库,因为所有局部存储库。

#####约翰出版他的特性

![配图08](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/08.svg "配图08")

Once John finishes his feature, he should publish his local commits to the central repository so other team members can access it. He can do this with the git push command, like so:

<pre><code>git push origin master</code></pre>

Remember that origin is the remote connection to the central repository that Git created when John cloned it. The master argument tells Git to try to make the origin’s master branch look like his local master branch. Since the central repository hasn’t been updated since John cloned it, this won’t result in any conflicts and the push will work as expected.

#####Mary tries to publish her feature

![配图09](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/09.svg "配图09")

Let’s see what happens if Mary tries to push her feature after John has successfully published his changes to the central repository. She can use the exact same push command:

<pre><code>git push origin master</code></pre>

But, since her local history has diverged from the central repository, Git will refuse the request with a rather verbose error message:

<pre><code>error: failed to push some refs to '/path/to/repo.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
hint: before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
</code></pre>

This prevents Mary from overwriting official commits. She needs to pull John’s updates into her repository, integrate them with her local changes, and then try again.

#####Mary rebases on top of John’s commit(s)

![配图10](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/10.svg "配图10")

Mary can use git pull to incorporate upstream changes into her repository. This command is sort of like svn update—it pulls the entire upstream commit history into Mary’s local repository and tries to integrate it with her local commits:

<pre><code>git pull --rebase origin master</code></pre>

The --rebase option tells Git to move all of Mary’s commits to the tip of the master branch after synchronising it with the changes from the central repository, as shown below:

![配图11](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/11.svg "配图11")

The pull would still work if you forgot this option, but you would wind up with a superfluous “merge commit” every time someone needed to synchronize with the central repository. For this workflow, it’s always better to rebase instead of generating a merge commit.

#####Mary resolves a merge conflict

![配图12](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/12.svg "配图12")

Rebasing works by transferring each local commit to the updated master branch one at a time. This means that you catch merge conflicts on a commit-by-commit basis rather than resolving all of them in one massive merge commit. This keeps your commits as focused as possible and makes for a clean project history. In turn, this makes it much easier to figure out where bugs were introduced and, if necessary, to roll back changes with minimal impact on the project.

If Mary and John are working on unrelated features, it’s unlikely that the rebasing process will generate conflicts. But if it does, Git will pause the rebase at the current commit and output the following message, along with some relevant instructions:

<pre><code>CONFLICT (content): Merge conflict in &lt;some-file&gt;</code></pre>

![配图13](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/13.svg "配图13")

The great thing about Git is that anyone can resolve their own merge conflicts. In our example, Mary would simply run a git status to see where the problem is. Conflicted files will appear in the Unmerged paths section:

<pre><code># Unmerged paths:
# (use "git reset HEAD &lt;some-file&gt;..." to unstage)
# (use "git add/rm &lt;some-file&gt;..." as appropriate to mark resolution)
#
# both modified: &lt;some-file&gt;</code></pre>

Then, she’ll edit the file(s) to her liking. Once she’s happy with the result, she can stage the file(s) in the usual fashion and let git rebase do the rest:

<pre><code>git add &lt;some-file&gt;
git rebase --continue</code></pre>

And that’s all there is to it. Git will move on to the next commit and repeat the process for any other commits that generate conflicts.

If you get to this point and realize and you have no idea what’s going on, don’t panic. Just execute the following command and you’ll be right back to where you started before you ran 

\[git pull --rebase\]\(/tutorials/syncing/git-pull\):

<pre><code>git rebase --abort</code></pre>

#####Mary successfully publishes her feature

![配图14](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/centralized-workflow/14.svg "配图14")

After she’s done synchronizing with the central repository, Mary will be able to publish her changes successfully:

<pre><code>git push origin master</code></pre>

####Where To Go From Here

As you can see, it’s possible to replicate a traditional Subversion development environment using only a handful of Git commands. This is great for transitioning teams off of SVN, but it doesn’t leverage the distributed nature of Git.

If your team is comfortable with the Centralized Workflow but wants to streamline its collaboration efforts, it's definitely worth exploring the benefits of the Feature Branch Workflow. By dedicating an isolated branch to each feature, it’s possible to initiate in-depth discussions around new additions before integrating them into the official project.

##Feature Branch Workflow

![配图01](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/feature-branch-workflow/01.svg "配图01")

Once you've got the hang of the Centralized Workflow, adding feature branches to your development process is an easy way to encourage collaboration and streamline communication between developers.

The core idea behind the Feature Branch Workflow is that all feature development should take place in a dedicated branch instead of the master branch. This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the master branch will never contain broken code, which is a huge advantage for continuous integration environments.

Encapsulating feature development also makes it possible to leverage pull requests, which are a way to initiate discussions around a branch. They give other developers the opportunity to sign off on a feature before it gets integrated into the official project. Or, if you get stuck in the middle of a feature, you can open a pull request asking for suggestions from your colleagues. The point is, pull requests make it incredibly easy for your team to comment on each other’s work.

###它是怎么工作的

The Feature Branch Workflow still uses a central repository, and master still represents the official project history. But, instead of committing directly on their local master branch, developers create a new branch every time they start work on a new feature. Feature branches should have descriptive names, like animated-menu-items or issue-#1061. The idea is to give a clear, highly-focused purpose to each branch.

Git makes no technical distinction between the master branch and feature branches, so developers can edit, stage, and commit changes to a feature branch just as they did in the Centralized Workflow.

In addition, feature branches can (and should) be pushed to the central repository. This makes it possible to share a feature with other developers without touching any official code. Since master is the only “special” branch, storing several feature branches on the central repository doesn’t pose any problems. Of course, this is also a convenient way to back up everybody’s local commits.

####Pull Requests

Aside from isolating feature development, branches make it possible to discuss changes via pull requests. Once someone completes a feature, they don’t immediately merge it into master. Instead, they push the feature branch to the central server and file a pull request asking to merge their additions into master. This gives other developers an opportunity to review the changes before they become a part of the main codebase.

Code review is a major benefit of pull requests, but they’re actually designed to be a generic way to talk about code. You can think of pull requests as a discussion dedicated to a particular branch. This means that they can also be used much earlier in the development process. For example, if a developer needs help with a particular feature, all they have to do is file a pull request. Interested parties will be notified automatically, and they’ll be able to see the question right next to the relevant commits.

Once a pull request is accepted, the actual act of publishing a feature is much the same as in the Centralized Workflow. First, you need to make sure your local master is synchronized with the upstream master. Then, you merge the feature branch into master and push the updated master back to the central repository.

Pull requests can be facilitated by product repository management solutions like Bitbucket Cloud or Bitbucket Server. View the Bitbucket Server pull requests documentation for an example.

####例子

The example included below demonstrates a pull request as a form of code review, but remember that they can serve many other purposes.

#####Mary begins a new feature

![配图02](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/feature-branch-workflow/02.svg "配图02")

Before she starts developing a feature, Mary needs an isolated branch to work on. She can request a new branch with the following command:

<pre><code>git checkout -b marys-feature master</code></pre>

This checks out a branch called marys-feature based on master, and the -b flag tells Git to create the branch if it doesn’t already exist. On this branch, Mary edits, stages, and commits changes in the usual fashion, building up her feature with as many commits as necessary:

<pre><code>git status
git add &lt;some-file&gt;
git commit</code></pre>

#####Mary goes to lunch

![配图03](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/feature-branch-workflow/03.svg "配图03")

Mary adds a few commits to her feature over the course of the morning. Before she leaves for lunch, it’s a good idea to push her feature branch up to the central repository. This serves as a convenient backup, but if Mary was collaborating with other developers, this would also give them access to her initial commits.

<pre><code>git push -u origin marys-feature</code></pre>

This command pushes marys-feature to the central repository (origin), and the -u flag adds it as a remote tracking branch. After setting up the tracking branch, Mary can call git push without any parameters to push her feature.

#####Mary finishes her feature

![配图04](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/feature-branch-workflow/04.svg "配图04")

When Mary gets back from lunch, she completes her feature. Before merging it into master, she needs to file a pull request letting the rest of the team know she's done. But first, she should make sure the central repository has her most recent commits:

<pre><code>git push</code></pre>

Then, she files the pull request in her Git GUI asking to merge marys-feature into master, and team members will be notified automatically. The great thing about pull requests is that they show comments right next to their related commits, so it's easy to ask questions about specific changesets.

#####Bill receives the pull request

![配图05](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/feature-branch-workflow/05.svg "配图05")

Bill gets the pull request and takes a look at marys-feature. He decides he wants to make a few changes before integrating it into the official project, and he and Mary have some back-and-forth via the pull request.

#####Mary makes the changes

![配图06](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/feature-branch-workflow/06.svg "配图06")

To make the changes, Mary uses the exact same process as she did to create the first iteration of her feature. She edits, stages, commits, and pushes updates to the central repository. All her activity shows up in the pull request, and Bill can still make comments along the way.

If he wanted, Bill could pull marys-feature into his local repository and work on it on his own. Any commits he added would also show up in the pull request.

#####Mary publishes her feature

![配图07](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/feature-branch-workflow/07.svg "配图07")

Once Bill is ready to accept the pull request, someone needs to merge the feature into the stable project (this can be done by either Bill or Mary):

<pre><code>git checkout master
git pull
git pull origin marys-feature
git push</code></pre>

First, whoever’s performing the merge needs to check out their master branch and make sure it’s up to date. Then, git pull origin marys-feature merges the central repository’s copy of marys-feature. You could also use a simple git merge marys-feature, but the command shown above makes sure you’re always pulling the most up-to-date version of the feature branch. Finally, the updated master needs to get pushed back to origin.

This process often results in a merge commit. Some developers like this because it’s like a symbolic joining of the feature with the rest of the code base. But, if you’re partial to a linear history, it’s possible to rebase the feature onto the tip of master before executing the merge, resulting in a fast-forward merge.

Some GUI’s will automate the pull request acceptance process by running all of these commands just by clicking an “Accept” button. If yours doesn’t, it should at least be able to automatically close the pull request when the feature branch gets merged into master

#####Meanwhile, John is doing the exact same thing

While Mary and Bill are working on marys-feature and discussing it in her pull request, John is doing the exact same thing with his own feature branch. By isolating features into separate branches, everybody can work independently, yet it’s still trivial to share changes with other developers when necessary.

###Where To Go From Here

For a walkthrough of feature branching on Bitbucket, check out the Using Git Branches documentation. By now, you can hopefully see how feature branches are a way to quite literally multiply the functionality of the single master branch used in the Centralized Workflow. In addition, feature branches also facilitate pull requests, which makes it possible to discuss specific commits right inside of your version control GUI.

The Feature Branch Workflow is an incredibly flexible way to develop a project. The problem is, sometimes it’s too flexible. For larger teams, it’s often beneficial to assign more specific roles to different branches. The Gitflow Workflow is a common pattern for managing feature development, release preparation, and maintenance.

##Gitflow Workflow

![配图01](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/01.svg "配图01")

The Gitflow Workflow section below is derived from Vincent Driessen at nvie.

The Gitflow Workflow defines a strict branching model designed around the project release. While somewhat more complicated than the Feature Branch Workflow, this provides a robust framework for managing larger projects.

This workflow doesn’t add any new concepts or commands beyond what’s required for the Feature Branch Workflow. Instead, it assigns very specific roles to different branches and defines how and when they should interact. In addition to feature branches, it uses individual branches for preparing, maintaining, and recording releases. Of course, you also get to leverage all the benefits of the Feature Branch Workflow: pull requests, isolated experiments, and more efficient collaboration.

###它是如何工作的

The Gitflow Workflow still uses a central repository as the communication hub for all developers. And, as in the other workflows, developers work locally and push branches to the central repo. The only difference is the branch structure of the project.

###Historical Branches

Instead of a single master branch, this workflow uses two branches to record the history of the project. The master branch stores the official release history, and the develop branch serves as an integration branch for features. It's also convenient to tag all commits in the master branch with a version number.

![配图02](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/02.svg "配图02")

The rest of this workflow revolves around the distinction between these two branches.

###Feature Branches

Each new feature should reside in its own branch, which can be pushed to the central repository for backup/collaboration. But, instead of branching off of master, feature branches use develop as their parent branch. When a feature is complete, it gets merged back into develop. Features should never interact directly with master.

![配图03](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/03.svg "配图03")

Note that feature branches combined with the develop branch is, for all intents and purposes, the Feature Branch Workflow. But, the Gitflow Workflow doesn’t stop there.

###Release Branches

![配图04](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/04.svg "配图04")

Once develop has acquired enough features for a release (or a predetermined release date is approaching), you fork a release branch off of develop. Creating this branch starts the next release cycle, so no new features can be added after this point—only bug fixes, documentation generation, and other release-oriented tasks should go in this branch. Once it's ready to ship, the release gets merged into master and tagged with a version number. In addition, it should be merged back into develop, which may have progressed since the release was initiated.

Using a dedicated branch to prepare releases makes it possible for one team to polish the current release while another team continues working on features for the next release. It also creates well-defined phases of development (e.g., it‘s easy to say, “this week we’re preparing for version 4.0” and to actually see it in the structure of the repository).

Common conventions:

* branch off: develop
* merge into: master
* naming convention: release-* or release/\*

####Maintenance Branches

![配图05](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/05.svg "配图05")

Maintenance or “hotfix” branches are used to quickly patch production releases. This is the only branch that should fork directly off of master. As soon as the fix is complete, it should be merged into both master and develop (or the current release branch), and master should be tagged with an updated version number.

Having a dedicated line of development for bug fixes lets your team address issues without interrupting the rest of the workflow or waiting for the next release cycle. You can think of maintenance branches as ad hoc release branches that work directly with master.

###例子

The example below demonstrates how this workflow can be used to manage a single release cycle. We’ll assume you have already created a central repository.

####Create a develop branch

![配图06](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/06.svg "配图06")

The first step is to complement the default master with a develop branch. A simple way to do this is for one developer to create an empty develop branch locally and push it to the server:

<pre><code>git branch develop
git push -u origin develop</code></pre>

This branch will contain the complete history of the project, whereas master will contain an abridged version. Other developers should now clone the central repository and create a tracking branch for develop:

<pre><code>git clone ssh://user@host/path/to/repo.git
git checkout -b develop origin/develop</code></pre>

Everybody now has a local copy of the historical branches set up.

#####Mary and John begin new features

![配图07](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/07.svg "配图07")

Our example starts with John and Mary working on separate features. They both need to create separate branches for their respective features. Instead of basing it on master, they should both base their feature branches on develop:

<pre><code>git checkout -b some-feature develop</code></pre>

Both of them add commits to the feature branch in the usual fashion: edit, stage, commit:

<pre><code>git status
git add &lt;some-file&gt;
git commit</code></pre>

#####Mary finishes her feature

![配图08](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/08.svg "配图08")

After adding a few commits, Mary decides her feature is ready. If her team is using pull requests, this would be an appropriate time to open one asking to merge her feature into develop. Otherwise, she can merge it into her local develop and push it to the central repository, like so:

<pre><code>git pull origin develop
git checkout develop
git merge some-feature
git push
git branch -d some-feature</code></pre>

The first command makes sure the develop branch is up to date before trying to merge in the feature. Note that features should never be merged directly into master. Conflicts can be resolved in the same way as in the Centralized Workflow.

#####Mary begins to prepare a release

![配图09](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/09.svg "配图09")

While John is still working on his feature, Mary starts to prepare the first official release of the project. Like feature development, she uses a new branch to encapsulate the release preparations. This step is also where the release’s version number is established:

<pre><code>git checkout -b release-0.1 develop</code></pre>

This branch is a place to clean up the release, test everything, update the documentation, and do any other kind of preparation for the upcoming release. It’s like a feature branch dedicated to polishing the release.

As soon as Mary creates this branch and pushes it to the central repository, the release is feature-frozen. Any functionality that isn’t already in develop is postponed until the next release cycle.

#####Mary finishes the release

![配图10](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/10.svg "配图10")

Once the release is ready to ship, Mary merges it into master and develop, then deletes the release branch. It’s important to merge back into develop because critical updates may have been added to the release branch and they need to be accessible to new features. Again, if Mary’s organization stresses code review, this would be an ideal place for a pull request.

<pre><code>git checkout master
git merge release-0.1
git push
git checkout develop
git merge release-0.1
git push
git branch -d release-0.1</code></pre>

Release branches act as a buffer between feature development (develop) and public releases (master). Whenever you merge something into master, you should tag the commit for easy reference:

<pre><code>git tag -a 0.1 -m "Initial public release" master
git push --tags</code></pre>

Git comes with several hooks, which are scripts that execute whenever a particular event occurs within a repository. It’s possible to configure a hook to automatically build a public release whenever you push the master branch to the central repository or push a tag.

#####End-user discovers a bug

After shipping the release, Mary goes back to developing features for the next release with John. That is, until an end-user opens a ticket complaining about a bug in the current release. To address the bug, Mary (or John) creates a maintenance branch off of master, fixes the issue with as many commits as necessary, then merges it directly back into master.

<pre><code>git checkout -b issue-#001 master
# Fix the bug
git checkout master
git merge issue-#001
git push</code></pre>

Like release branches, maintenance branches contain important updates that need to be included in develop, so Mary needs to perform that merge as well. Then, she’s free to delete the branch:

<pre><code>git checkout develop
git merge issue-#001
git push
git branch -d issue-#001</code></pre>

###Where To Go From Here

By now, you’re hopefully quite comfortable with the Centralized Workflow, the Feature Branch Workflow, and the Gitflow Workflow. You should also have a solid grasp on the potential of local repositories, the push/pull pattern, and Git's robust branching and merging model.

Remember that the workflows presented here are merely examples of what’s possible—they are not hard-and-fast rules for using Git in the workplace. So, don't be afraid to adopt some aspects of a workflow and disregard others. The goal should always be to make Git work for you, not the other way around.

##Forking Workflow

The Forking Workflow is fundamentally different than the other workflows discussed in this tutorial. Instead of using a single server-side repository to act as the “central” codebase, it gives every developer a server-side repository. This means that each contributor has not one, but two Git repositories: a private local one and a public server-side one.

![配图01](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/forking-workflow/01.svg "配图01")

The main advantage of the Forking Workflow is that contributions can be integrated without the need for everybody to push to a single central repository. Developers push to their own server-side repositories, and only the project maintainer can push to the official repository. This allows the maintainer to accept commits from any developer without giving them write access to the official codebase.

The result is a distributed workflow that provides a flexible way for large, organic teams (including untrusted third-parties) to collaborate securely. This also makes it an ideal workflow for open source projects.

###它是如何工作的

As in the other Git workflows, the Forking Workflow begins with an official public repository stored on a server. But when a new developer wants to start working on the project, they do not directly clone the official repository.

Instead, they fork the official repository to create a copy of it on the server. This new copy serves as their personal public repository—no other developers are allowed to push to it, but they can pull changes from it (we’ll see why this is important in a moment). After they have created their server-side copy, the developer performs a git clone to get a copy of it onto their local machine. This serves as their private development environment, just like in the other workflows.

When they're ready to publish a local commit, they push the commit to their own public repository—not the official one. Then, they file a pull request with the main repository, which lets the project maintainer know that an update is ready to be integrated. The pull request also serves as a convenient discussion thread if there are issues with the contributed code.

To integrate the feature into the official codebase, the maintainer pulls the contributor’s changes into their local repository, checks to make sure it doesn’t break the project, merges it into his local master branch, then pushes the master branch to the official repository on the server. The contribution is now part of the project, and other developers should pull from the official repository to synchronize their local repositories.

####The Official Repository

It’s important to understand that the notion of an “official” repository in the Forking Workflow is merely a convention. From a technical standpoint, Git doesn’t see any difference between each developer’s public repository and the official one. In fact, the only thing that makes the official repository so official is that it’s the public repository of the project maintainer.

####Branching in the Forking Workflow

All of these personal public repositories are really just a convenient way to share branches with other developers. Everybody should still be using branches to isolate individual features, just like in the Feature Branch Workflow and the Gitflow Workflow. The only difference is how those branches get shared. In the Forking Workflow, they are pulled into another developer’s local repository, while in the Feature Branch and Gitflow Workflows they are pushed to the official repository.

###例子

####The project maintainer initializes the official repository

![配图02](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/forking-workflow/02.svg "配图02")

As with any Git-based project, the first step is to create an official repository on a server accessible to all of the team members. Typically, this repository will also serve as the public repository of the project maintainer.

Public repositories should always be bare, regardless of whether they represent the official codebase or not. So, the project maintainer should run something like the following to set up the official repository:

<pre><code>ssh user@host
git init --bare /path/to/repo.git</code></pre>

Bitbucket also provides a convenient GUI alternative to the above commands. This is the exact same process as setting up a central repository for the other workflows in this tutorial. The maintainer should also push the existing codebase to this repository, if necessary.

#####Developers fork the official repository

![配图03](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/forking-workflow/03.svg "配图03")

Next, all of the other developers need to fork this official repository. It’s possible to do this by SSH’ing into the server and running git clone to copy it to another location on the server—yes, forking is basically just a server-side clone. But again, Bitbucket let developers fork a repository with the click of a button.

After this step, every developer should have their own server-side repository. Like the official repository, all of these should be bare repositories.

#####Developers clone their forked repositories

![配图04](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/forking-workflow/04.svg "配图04")

Next each developer needs to clone their own public repository. They can do with the familiar git clone command.

Our example assumes the use of Bitbucket to host these repositories. Remember, in this situation, each developer should have their own Bitbucket account and they should clone their server-side repository using:

<pre><code>git clone https://user@bitbucket.org/user/repo.git</code></pre>

Whereas the other workflows in this tutorial use a single origin remote that points to the central repository, the Forking Workflow requires two remotes—one for the official repository, and one for the developer’s personal server-side repository. While you can call these remotes anything you want, a common convention is to use origin as the remote for your forked repository (this will be created automatically when you run git clone) and upstream for the official repository.

<pre><code>git remote add upstream https://bitbucket.org/maintainer/repo</code></pre>

You’ll need to create the upstream remote yourself using the above command. This will let you easily keep your local repository up-to-date as the official project progresses. Note that if your upstream repository has authentication enabled (i.e., it‘s not open source), you’ll need to supply a username, like so:

<pre><code>git remote add upstream https://user@bitbucket.org/maintainer/repo.git</code></pre>

This requires users to supply a valid password before cloning or pulling from the official codebase.

#####Developers work on their features

![配图05](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/forking-workflow/05.svg "配图05")

In the local repositories that they just cloned, developers can edit code, commit changes, and create branches just like they did in the other workflows:

<pre><code>git checkout -b some-feature
# Edit some code
git commit -a -m "Add first draft of some feature"</code></pre>

All of their changes will be entirely private until they push it to their public repository. And, if the official project has moved forward, they can access new commits with git pull:

<pre><code>git pull upstream master</code></pre>

Since developers should be working in a dedicated feature branch, this should generally result in a fast-forward merge.

#####Developers publish their features

![配图06](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/forking-workflow/06.svg "配图06")

Once a developer is ready to share their new feature, they need to do two things. First, they have to make their contribution accessible to other developers by pushing it to their public repository. Their origin remote should already be set up, so all they should have to do is the following:

<pre><code>git push origin feature-branch</code></pre>

This diverges from the other workflows in that the origin remote points to the developer’s personal server-side repository, not the main codebase.

Second, they need to notify the project maintainer that they want to merge their feature into the official codebase. Bitbucket provides a “Pull request” button that leads to a form asking you to specify which branch you want to merge into the official repository. Typically, you’ll want to integrate your feature branch into the upstream remote’s master branch.

#####The project maintainer integrates their features

![配图07](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/forking-workflow/07.svg "配图07")

When the project maintainer receives the pull request, their job is to decide whether or not to integrate it into the official codebase. They can do this in one of two ways:

1. Inspect the code directly in the pull request
2. Pull the code into their local repository and manually merge it

The first option is simpler, as it lets the maintainer view a diff of the changes, comment on it, and perform the merge via a graphical user interface. However, the second option is necessary if the pull request results in a merge conflict. In this case, the maintainer needs to fetch the feature branch from the developer’s server-side repository, merge it into their local master branch, and resolve any conflicts:

<pre><code>git fetch https://bitbucket.org/user/repo feature-branch
# Inspect the changes
git checkout master
git merge FETCH_HEAD</code></pre>

Once the changes are integrated into their local master, the maintainer needs to push it to the official repository on the server so that other developers can access it:

<pre><code>git push origin master</code></pre>

Remember that the maintainer's origin points to their public repository, which also serves as the official codebase for the project. The developer's contribution is now fully integrated into the project.

#####Developers synchronize with the official repository

![配图08](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/forking-workflow/08.svg "配图08")

Since the main codebase has moved forward, other developers should synchronize with the official repository:

<pre><code>git pull upstream master</code></pre>

####Where To Go From Here

If you’re coming from an SVN background, the Forking Workflow may seem like a radical paradigm shift. But don’t be afraid—all it’s really doing is introducing another level of abstraction on top of the Feature Branch Workflow. Instead of sharing branches directly though a single central repository, contributions are published to a server-side repository dedicated to the originating developer.

This article explained how a contribution flows from one developer into the official master branch, but the same methodology can be used to integrate a contribution into any repository. For example, if one part of your team is collaborating on a particular feature, they can share changes amongst themselves in the exact same manner—without touching the main repository.

This makes the Forking Workflow a very powerful tool for loosely-knit teams. Any developer can easily share changes with any other developer, and any branch can be efficiently merged into the official codebase.

原文：[Comparing Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows "Comparing Workflows")
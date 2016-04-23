![Making a Pull Request](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/hero.svg "Making a Pull Request")

#Making a Pull Request

拉请求是一项功能，它使开发人员更容易使用到位桶合作。他们提供了一个用户友好的Web界面将其纳入正式项目之前讨论修改建议。

![配图01](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/01.svg "配图01")

在最简单的形式，拉请求用于开发一种机制来通知，他们已经完成了功能团队成员。一旦他们的特性分支准备就绪，开发文件通过他们的帐户到位桶拉请求。这涉及让大家知道他们需要查看代码，并将其合并到主分支。

但是，拉入请求不仅仅是一个通知，它是讨论拟议功能一个专门的论坛了。如果有与该变化的任何问题，队友所用的拉入请求后反馈，甚至调整通过按压后续提交的功能。所有这些活动都直接拉入请求的内部跟踪。

![配图02](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/02.svg "配图02")

相比其他合作模式，分享这种提交正式的解决方案，使得一个更加简化的工作流程。 SVN和Git既可以自动发送一个简单的脚本通知电子邮件;然而，当涉及到讨论的变化，开发人员通常都依靠电子邮件线程。当后续提交涉及这可以成为杂乱无章，更是如此。拉把所有这些功能成为一个友好的Web界面旁边的到位桶仓库的请求。

###Anatomy of a Pull Request

当您提交请求拉，你正在做的是请求另一个开发者（例如，项目管理员）是直接从你的资料库分支到他们的存储库。这意味着，你需要提供4条信息提交pull请求：源代码库，源科，目标资源库和目标分支。

![配图03](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/03.svg "配图03")

许多这些值将被设置为通过到位桶一个合理的默认。但是，根据您的协作工作流程，你的团队可能需要指定不同的值。上图显示，要求合并一个特性分支进入官主分支拉的要求，但也有许多其他的方式来使用拉请求。

###How it works

拉请求可以与功能科工作流程，该工作流程Gitflow，或分岔流一起使用。但拉请求需要或者两个不同的分支或两个不同的仓库，所以他们不会与集中式工作流程工作。使用上拉请求与每个工作流的稍有不同，但总的过程如下：

1. 开发人员创建在其本地回购专用分支的特征。
2. 开发商推分支到公共库到位桶。
3. 开发商通过文件一到位桶拉请求。
4. 的团队的其他成员中的评论代码，探讨它，并改变它。
5. 该项目的维护者合并功能到官方库并关闭拉请求。

本节的其余部分介绍了如何拉请求可以针对不同工作流程的协作加以利用。

###Feature Branch Workflow With Pull Requests

特性分支使用的工作流程管理的协作共享资源库到位桶，而开发人员创建孤立的分支功能。但是，不是立即将它们合并到主，开发者应该打开一个pull请求启动围绕功能的讨论之前它被集成到主代码库。

![配图04](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/04.svg "配图04")

只有一个在特性分支工作流程公共仓库，所以拉的请求目标资源库和源库将永远是相同的。通常情况下，开发商将指定他们的特性分支作为源分支和主分支作为目标分支。

收到拉入请求后，项目维护者有权决定该怎么做。如果要素是蓄势待发，他们可以简单地把它合并到主关闭拉请求。但是，如果有提议的变更问题，他们可以张贴在拉请求的反馈。后续提交将显示旁边的相关意见。

它也有可能立案一个特点，就是不完整的拉请求。例如，如果一个开发人员有麻烦实施特殊要求，他们可以提交载有他们的工作正在进行中拉请求。然后，其他开发者可以提供建议拉入请求里面，甚至解决问题本身额外的提交。

###Gitflow Workflow With Pull Requests

Git的工作流流程是类似的特性分支工作流程，但定义围绕项目发布设计了一个严格的分支模型。添加拉请求到Gitflow工作流程为开发人员提供一个方便的地方谈论发布分支或维护分支，而他们正在努力。

![配图05](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/05.svg "配图05")
![配图06](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/06.svg "配图06")

在Gitflow工作流引入请求的机制是完全相同的前一节：开发商只是文件的拉请求时功能，释放或修补程序分支需要进行审查，而且球队的其余部分将通过到位桶通知。

特点是一般合并到开发分支，同时释放和修补程序的分支合并到这两个开发和掌握。拉请求可以用来规范地管理所有这些合并的。

###Forking Workflow With Pull Requests

在分叉工作流程，开发商推完成的功能，以自己的公共仓库，而不是共享的。之后，他们提交pull请求，让项目的维护者知道，它已经准备好进行审查。

由于该项目维护者无法知道当其他开发商增加了承诺的到位桶仓库的方式引入请求的通知方面是在这个工作流程特别有用。

![配图07](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/07.svg "配图07")

由于每个开发商都有自己的公共仓库，拉请求源库将其目标库不同。源库是开发商的公共存储库和源科是包含修改建议之一。如果开发商试图功能合并到主代码库，则目标存储库是正式项目和目标分支是高手。

拉请求也可以使用与正式项目以外的其他开发者合作。例如，如果一个开发人员正在研究一种功能与队友，他们可以使用的文件队友的到位桶储存库为目标，而不是正式项目拉请求。然后，他们将使用相同的功能分行源和目标分支。

![配图08](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/08.svg "配图08")

这两个开发人员可以讨论和制定拉动请求里面的功能。当他们完成后，他们中的一个将另一个文件拉入请求，要求到功能合并到官方主分支。这种灵活性使得拉请求在分岔的工作流程非常强大的协作工具。

###例子

下面的例子演示了如何引入请求可以在分岔工作流中使用。这同样适用于小团队和第三方开发者贡献的开源项目的开发人员。

在这个例子中，Mary是一个开发者，和约翰是该项目的维护者。他们都有自己的公共仓库到位桶，和约翰的包含正式项目。

####Mary forks the official project

![配图09](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/09.svg "配图09")

要启动项目时，玛丽首先需要到餐桌约翰的到位桶储存库。她可以通过登录到位桶，导航到约翰的资料库，并单击按钮叉做到这一点。

![配图10](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/10.svg "配图10")

填写名称和说明分叉库后，她将拥有该项目的服务器端副本。

![配图11](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/11.svg "配图11")

接下来，小丽需要克隆，她只是一个分叉库到位桶。这会给她一个项目的工作拷贝她的本地机器上。她可以通过运行以下命令这样做：

<pre><code>git clone https://user@bitbucket.org/user/repo.git</code></pre>

请记住，混帐克隆自动创建一个原点远程指回玛丽的分叉存储库。

####Mary develops a new feature

![配图12](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/12.svg "配图12")

之前，她开始写任何代码，玛丽需要创建一个新的分支为特征。该分支是什么，她将作为上拉请求的源分支使用。

<pre><code>git checkout -b some-feature
# Edit some code
git commit -a -m "Add first draft of some feature"</code></pre>

因为她需要创建功能玛丽可以使用尽可能多的提交。而且，如果该功能的历史是混乱比她愿意，她可以使用一个交互式的rebase删除或壁球不必要的提交。对于较大的项目，清理功能的历史使得它更容易为项目的维护者，看看发生了什么事情在拉请求。

####Mary pushes the feature to her Bitbucket repository

![配图13](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/13.svg "配图13")

她的特点是完成后，小丽推特性分支她自己的到位桶仓库（不是官方资料库），用一个简单的混帐推：

<pre><code>git push origin some-branch</code></pre>

这使得提供给项目的维护者（或者谁可能需要访问他们的任何合作者）她的变化。

####Mary creates the pull request

![配图14](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/14.svg "配图14")

到位桶有她的特性分支后，小丽可以通过导航到她的分叉存储库，并单击右上角的拉请求按钮创建通过她的到位桶账号拉入请求。由此产生的形式自动设置玛丽的存储库作为源存储库，并要求她指定源分支，目标资源库和目标分支。

玛丽希望她的功能合并到主代码库，因此，源科是她的特性分支，目标仓库是John的公共仓库，目标分支是高手。她还需要提供上拉请求的标题和描述。如果有需要谁批准除了约翰代码其他人，她可以在审阅字段中输入他们。

![配图15](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/pull-request-7.png "配图15")

她创建的拉请求后，通知将通过他的到位桶饲料，并通过电子邮件（可选）发送到约翰。

####John reviews the pull request

![配图16](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/pull-request-8.png "配图16")

约翰可以访问所有的人都通过点击自己的到位桶库拉入请求选项卡上提交的拉请求。点击玛丽的拉请求将显示他拉入请求的描述，功能犯下的历史，它包含的所有变化的差异。

如果他认为该功能是准备合并到项目中，所有他所要做的就是打合并按钮批准拉入请求和合并玛丽的功能到他的主分支。

但是，在这个例子中，假设约翰发现了玛丽的代码中的小bug，需要她在合并之前修复它，他可以张贴到拉入请求评论作为一个整体，或者他可以选择在特定的承诺功能历史评论。

![配图17](https://www.atlassian.com/git/images/tutorials/collaborating/making-a-pull-request/pull-request-9.png "配图17")

####Mary adds a follow-up commit

如果玛丽对反馈的任何问题，她可以响应拉入请求里面，把它当作一个讨论的论坛，她的功能。

要纠正错误，玛丽又增加了承诺，她的特性分支并将其推到她的到位桶储存库，就像她周围做了第一次。该承诺将自动添加到原有拉力要求，约翰可以再次查看更改，旁边就是他原来的注释。

####John accepts the pull request

最后，约翰接受的变化，合并特性分支变成主人，并关闭拉请求。该功能现已集成到项目，和任何其他开发商做这个工作，可以把它到采用标准的git pull命令自己的本地存储库。

###Where to go from here

你现在应该有所有你需要开始引入请求集成到现有的工作流程的工具。请记住，拉请求不是任何基于Git的协作工作流的替代品，而是一个方便的除了他们，使协作更容易获得所有的团队成员。

原文：[Making a Pull Request](https://www.atlassian.com/git/tutorials/making-a-pull-request "Making a Pull Request")
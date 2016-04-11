![什么是Git](https://www.atlassian.com/git/images/tutorials/getting-started/what-is-git/hero.svg "什么是Git")

#什么是Git

到目前为止，在当今世界上使用最广泛的现代版本控制系统是Git的。 Git是一个成熟的，积极维护的开源由Linus Torvalds，Linux的操作系统内核的创作者著名在2005年独自开发的项目。软件项目的数量惊人依靠的Git版本控制，包括商业项目以及开源的。谁与Git的开发工作在可用的软件开发人才库是很好的代表，它工作得很好了广泛的操作系统和IDE的（集成开发环境）。

具有分布式体系，Git是一个DVCS（因此分布式版本控制系统）的一个例子。而不是只有一个为软件的完整版本历史记录一个地方因为是像CVS或颠覆（也称为SVN）一度流行的版本控制系统中常见的，在Git中，工作代码的副本每一个开发商也是一个资源库可以包含所有变化的全部历史。

除了被分发，GIT中已被设计时考虑到性能，安全性和灵活性。

###性能

相比于许多选择时的Git的原始性能特点都非常强。提交新的变化，分支，合并和比较过去的版本性能优化所有。里面的Git实现的算法大约需要和什么访问模式是真正的源代码文件树共同的属性，它们是如何修改的，通常在一段时间深入了解的优势。

不像有些版本控制软件，Git是不是由文件的名称确定文件树的存储和版本历史记录应该是什么的时候上当，相反，Git的重点是文件内容本身。毕竟，源代码文件频繁被重命名，拆分和重新排列。的Git仓库文件的对象格式使用增量编码（存储内容的差异），压缩的组合，并明确存储目录内容和版本的元数据对象。

被分配使显著的性能好处。

例如，假设一个开发者，爱丽丝，使得修改源代码，添加功能为即将到来的2.0版本，然后提交与描述性消息的变化。然后，她的作品在第二个特征，这些承诺过的变化。当然这些都存储在版本历史记录的工作独立的部分。爱丽丝然后切换到相同的软件版本1.3的分支来修复仅影响老版本的错误。这样做的目的是为了让Alice的团队出货bug修复版本，1.3.1版本，之前2.0版本已经准备就绪。爱丽丝可以回到2.0分支继续进行新功能的工作2.0和所有这一切都没有任何网络访问可能会发生，因此是快速和可靠。她甚至可以做到在飞机上。当她准备把所有的个人提交更改到远程存储库，爱丽丝可以在一个命令“推”出来。

###安全

混帐的设计与管理的源代码完整性作为首要任务。这些文件的内容以及文件和目录，版本，标签和承诺之间的真实关系，都在Git仓库这些对象的固定一个名为SHA1加密安全散列算法。这可以防止偶然的，恶意的更改代码和更改历史记录，并确保历史是完全可追溯。

使用Git，你可以确保你有你的源代码，一个地道的内容历史。

其他一些版本控制系统都对秘密篡改没有保护在稍后的日期。这对于依赖于软件开发的任何组织严重的信息安全漏洞。

###灵活性

其中一个关键的Git的设计目标是灵活性。 Git是灵活的在几个方面：在各种非线性发展的工作流程，在其效率小型和大型项目，并在其与许多现有系统和协议兼容性支持。

Git的已被设计为支持分支和标记一流的公民（不像SVN）和运营影响分支和标签（如合并或恢复）也被存储为改变历史的一部分。不是所有的版本控制系统采用这个级别的跟踪。

###使用Git版本控制

Git是大多数软件开发团队今天的最佳选择。虽然每个团队都是不同的，应该做自己的分析，这里为什么要优于替代品使用Git版本控制的主要原因：

####Git是好的

Git有功能，性能，安全性和灵活性，大多数团队和个人开发者的需要。 GIT中的这些属性上面详述。在并排侧与大多数其他替代品比较，很多团队发现，Git是非常有利的。

####Git是一个事实上的标准

Git是同类产品中最广泛采用的工具。这使得GIT中的原因如下吸引力。在Atlassian的，几乎我们所有的项目源代码在Git中进行管理。

开发商广大已经有了Git的经验和大学毕业生的比例显著可能有经验，唯一的Git。而从另一个版本控制系统迁移到Git的时候一些组织可能需要爬学习曲线，许多现有的和未来的开发人员不需要对的Git的培训。

除了大量人才的优势，混帐的优势也意味着许多第三方软件工具和服务已经使用Git，包括IDE和我们自己的工具，如DVCS桌面客户端SourceTree，问题和项目跟踪软件，JIRA集成和代码托管服务，到位桶。

如果你想建立的软件开发工具宝贵的技能，当涉及到版本控制一个没有经验的开发商，Git的应该是你的清单上。

####Git是一个优质的开源项目

Git是用在固体管理工作的十年中很好的支持的开源项目。该项目维护者表明适当的判断和成熟的方法来与提高可用性和功能定期发布满足其用户的长远需求。开源软件的质量是很容易审查和无数的企业严重依赖于质量。

Git的享受伟大的社会支持和广阔的用户群。文档是优秀和丰富，包括书籍，教程和专业的网站。也有播客和视频教程。

作为开源降低了爱好者开发商的成本，因为他们可以使用git无需支付费用。对于开源项目使用Git是无疑的继任者成功的开源版本控制系统，SVN和CVS的前几代。

Git的批评

混帐的一个常见的批评是，它可能很难学习。有些Git中的术语将小说新人和其他系统的用户，Git的术语可能会有所不同，例如，在恢复的Git比在SVN或CVS不同的含义。不过，Git是非常有能力，并提供了大量的电力给用户。学习使用这种权力可能需要一些时间，但一旦它已经获悉，功率可以被球队用来提高他们的开发速度。

对于这些球队从非分布式VCS来了，有一个中央储存库似乎是一件好事，他们不希望失去。然而，虽然混帐已被设计成一个分布式版本控制系统（DVCS），使用Git，你仍然可以有一个正式的，规范的储存库，该软件的所有更改必须存储。使用Git，因为每个开发人员的资料库完成后，他们的工作并不需要由“中央”服务器的可用性和性能的限制。在中断或离线时，开发商仍然可以参考整个项目的历史。因为Git是灵活的，以及分发，你可以工作，你是习惯的方式，但获得的Git的额外优惠，其中有些你甚至不知道你错过。

现在你明白什么版本控制，什么Git是，为什么软件团队要使用它，看了就发现Git的好处可以在整个组织提供。

原文：[What is Git](https://www.atlassian.com/git/tutorials/what-is-git "What is Git")
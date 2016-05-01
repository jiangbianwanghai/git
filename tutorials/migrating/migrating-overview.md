![从SVN迁移到Git](https://www.atlassian.com/git/images/tutorials/migrating/migrating-overview/hero.svg "从SVN迁移到Git")

#从SVN迁移到Git

We’ve broken down the SVN-to-Git migration process into 5 simple steps:

* Prepare your environment for the migration.
* Convert the SVN repository to a local Git repository.
* Synchronize the local Git repository when the SVN repository changes.
* Share the Git repository with your developers via Bitbucket.
* Migrate your development efforts from SVN to Git.

The prepare, convert, and synchronize steps take a SVN commit history and turn it into a Git repository. The best way to manage these first 3 steps is to designate one of your team members as the migration lead (if you’re reading this guide, that person is probably you). All 3 of these steps should be performed on the migration lead’s local computer.

![配图01](https://www.atlassian.com/git/images/tutorials/migrating/migrating-overview/01.svg "配图01")

After the synchronize phase, the migration lead should have no trouble keeping a local Git repository up-to-date with an SVN counterpart. To share the Git repository, the migration lead can share his local Git repository with other developers by pushing it to Bitbucket, a Git hosting service.

![配图02](https://www.atlassian.com/git/images/tutorials/migrating/migrating-overview/02.svg "配图02")

Once it’s on Bitbucket, other developers can clone the converted Git repository to their local machines, explore its history with Git commands, and begin integrating it into their build processes. However, we advocate a one-way synchronization from SVN to Git until your team is ready to switch to a pure Git workflow. This means that everybody should treat their Git repository as read-only and continue committing to the original SVN repository. The only changes to the Git repository should happen when the migration lead synchronizes it and pushes the updates to Bitbucket.

This provides a clear-cut transition period where your team can get comfortable with Git without interrupting your existing SVN-based workflow. Once you’re confident that your developers are ready to make the switch, the final step in the migration process is to freeze your SVN repository and begin committing with Git instead.

![配图03](https://www.atlassian.com/git/images/tutorials/migrating/migrating-overview/03.svg "配图03")

This switch should be a very natural process, as the entire Git workflow is already in place and your developers have had all the time they need to get comfortable with it. By this point, you have successfully migrated your project from SVN to Git.

原文：[Migrate to Git from SVN](https://www.atlassian.com/git/tutorials/migrating-overview "Migrate to Git from SVN")
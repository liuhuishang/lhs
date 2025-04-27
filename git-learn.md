# git学习记录
---
[参考廖雪峰git学习教程](https://liaoxuefeng.com/books/git/introduction/index.html)

---
1.git的安装（windows）：[参考详细教程](https://blog.csdn.net/mukes/article/details/115693833)


2.创建github账号：[注册github账号教程](https://blog.csdn.net/m0_67906358/article/details/128808210)


3.创建git本地库：

* `打开gitbash，使用cd导航到相应文件夹`
    
* `使用命令：git init，在本文件夹建立仓库`
    
* `文件夹中会显示.git文件`

  
    
4.使用git与github连接并将文件上传更新

   *1）将git与github进行连接* [参考连接](https://blog.csdn.net/Natsuago/article/details/145647536)

   * `使用指令：git config --global user.name “username”和git config --global user.email “email”，将git与自己的github进行连接。`
    
   * `指令：git config --list可以查看配置信息。`
    
   * `指令：ssh-keygen -t rsa -b 4096 -C "your-email@example.com"生成一个公钥,找到这个公钥复制并在github的设置中建立一个ssh连接，SSH Key 到 GitHub。连接后可以使用：ssh -T git@github.com查看是否连接成功。`
    
   *2）保存git本地库中的文件和将文件上传*[参考链接](https://blog.csdn.net/A496608119/article/details/123566231)

   * `使用：git add .将所有待上传文件加载到缓冲区或者使用：git add 文件 的形式把待上传文件加载到缓冲区。`
    
   * `使用：git commit -m "wrote a readme file"指令将缓冲区的文件上传到指定仓库。`

   * `使用：git remote add origin https://github.com/XX/XXX.git（这里我已经连接成功，所以我使用的指令是：git remote add origin master）便可以将git的本地库中的文件上传到github中。也可以使用git push -u origin master的形式来进行上传文件`


    
5.使用git对文件操作
    
  * `查看运行结果：git status。git status命令可以让我们时刻掌握仓库当前的状态。`

  * `版本控制系统肯定有某个命令可以告诉我们历史记录，在Git中，我们用git log命令查看。如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数。`

  * `把当前版本返回到上一个版本就可以使用git reset --hard HEAD^,也可以指定要回退到某一个版本即git reset --hard 版本号。`

  * `管理修改：使用git add进行上传到暂存区，使用git commit把暂存区上传修改`

  * `撤销的工作原理：使用git checkout -- file，可以让文件撤销到最近一次修改的状态`

  * `用rm命令可以将文件进行删除。从版本库中删除该文件，那就用命令git rm删掉，并且git commit。删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：
git checkout -- file`。


6.分支管理

1）创建合并分支

  * 创建dev分支，然后切换到dev分支：git checkout -b dev  Switched to a new branch 'dev'。git checkout命令加上-b参数表示创建并切换，相当于以下两条命令： git branch dev， git checkout dev  Switched to branch 'dev'，然后，用git branch命令查看当前分支，git branch命令会列出所有分支，当前分支前面会标一个*号。

  * 可以在dev分支上正常提交，把dev分支的工作成果合并到master分支上：使用命令 git merge dev，git merge命令用于合并指定分支到当前分支，合并完成后，就可以放心地删除dev分支了

  * 最新版本的Git提供了新的git switch命令来切换分支：创建并切换到新的dev分支，可以使用：git switch -c dev，直接切换到已有的master分支，可以使用： git switch master

  * 常见的创建合并分支指令：查看分支：git branch，创建分支：git branch <name>，切换分支：git checkout <name>或者git switch <name>，创建+切换分支：git checkout -b <name>或者git switch -c <name>，合并某分支到当前分支：git merge <name>，删除分支：git branch -d <name>。

2）解决冲突

  * 当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。
解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提

用git log --graph命令可以看到分支

3）分支管理

  * 合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。
如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信

4）bug分支

  *  修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；
当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现

在master分支上修复的bug，想要合并到当前dev分支，可以用git cherry-pick <commit>命令，把bug提交的修改“复制”到当前分支，避免重

5）feature分支

  *  添加一个新功能时，你肯定不希望因为一些实验性质的代码，把主分支搞乱了，所以，每添加一个新功能，最好新建一个feature分支，在上面开发，完成后，合并，最后，删除该feature分支。复
6）多人协作

  * 用git remote -v显示更详细的信息，上面显示了可以抓取和推送的origin的地址。如果没有推送权限，就看不到push的地址，推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上： git push origin master，如果要推送其他分支，比如dev，就改成： git push origin dev。

  * 查看远程库信息，使用git remote -v；本地新建的分支如果不推送到远程，对其他人就是不可见的；从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。

7.标签管理

1）创建标签

  * 在Git中打标签非常简单，首先，切换到需要打标签的分支上，然后，敲命令git tag name就可以打一个新标签，可以用命令git tag查看所有标签。

  * 命令git tag tagname用于新建一个标签，默认为HEAD，也可以指定一个commit id；命令git tag -a tagname -m "blablabla..."可以指定标签信息；命令git tag可以查看所有标签。
    
2）操作标签

  * 如果标签打错了，也可以删除：git tag -d ，如果要推送某个标签到远程，使用命令git push origin tagname

  * 命令git push origin tagname可以推送一个本地标签；命令git push origin --tags可以推送全部未推送过的本地标签；命令git tag -d tagname可以删除一个本地标签；命令git push origin :refs/tags/tagname可以删除一个远程标签

    。8  。 合并图。
3.git常见指令：

* `git init                                                  # 初始化本地git仓库（创建新仓库）`
* `git config --global user.name "xxx"                       # 配置用户名`
* `git config --global user.email "xxx@xxx.com"              # 配置邮件`
* `git config --global color.ui true                         # git status等命令自动着色`
* `git config --global color.status auto`
* `git config --global color.diff auto`
* `git config --global color.branch auto`
* `git config --global color.interactive auto`
* `git config --global --unset http.proxy                    # remove  proxy configuration on git`
* `git clone git+ssh://git@192.168.53.168/VT.git             # clone远程仓库`
* `git status                                                # 查看当前版本状态（是否修改）`
* `git add xyz                                               # 添加xyz文件至index`
* `git add .                                                 # 增加当前子目录下所有更改过的文件至index`
* `git commit -m 'xxx'                                       # 提交`
* `git commit --amend -m 'xxx'                               # 合并上一次提交（用于反复修改）`
* `git commit -am 'xxx'                                      # 将add和commit合为一步`
* `git rm xxx                                                # 删除index中的文件`
* `git rm -r *                                               # 递归删除`
* `git log                                                   # 显示提交日志`
* `git log -1                                                # 显示1行日志 -n为n行`
* `git log -5`
* `git log --stat                                            # 显示提交日志及相关变动文件`
* `git log -p -m`
* `git show dfb02e6e4f2f7b573337763e5c0013802e392818         # 显示某个提交的详细内容`
* `git show dfb02                                            # 可只用commitid的前几位`
* `git show HEAD                                             # 显示HEAD提交日志`
* `git show HEAD^                                            # 显示HEAD的父（上一个版本）的提交日志 ^^为上两个版本 ^5为上5个版本`
* `git tag                                                   # 显示已存在的tag`
* `git tag -a v2.0 -m 'xxx'                                  # 增加v2.0的tag`
* `git show v2.0                                             # 显示v2.0的日志及详细内容`
* `git log v2.0                                              # 显示v2.0的日志`
* `git diff                                                  # 显示所有未添加至index的变更`
* `git diff --cached                                         # 显示所有已添加index但还未commit的变更`
* `git diff HEAD^                                            # 比较与上一个版本的差异`
* `git diff HEAD -- ./lib                                    # 比较与HEAD版本lib目录的差异`
* `git diff origin/master..master                            # 比较远程分支master上有本地分支master上没有的`
* `git diff origin/master..master --stat                     # 只显示差异的文件，不显示具体内容`
* `git remote add origin git+ssh://git@192.168.53.168/VT.git # 增加远程定义（用于push/pull/fetch）`
* `git branch                                                # 显示本地分支`
* `git branch --contains 50089                               # 显示包含提交50089的分支`
* `git branch -a                                             # 显示所有分支`
* `git branch -r                                             # 显示所有原创分支`
* `git branch --merged                                       # 显示所有已合并到当前分支的分支`
* `git branch --no-merged                                    # 显示所有未合并到当前分支的分支`
* `git branch -m master master_copy                          # 本地分支改名`
* `git checkout -b master_copy                               # 从当前分支创建新分支master_copy并检出`
* `git checkout -b master master_copy                        # 上面的完整版`
* `git checkout features/performance                         # 检出已存在的features/performance分支`
* `git checkout --track hotfixes/BJVEP933                    # 检出远程分支hotfixes/BJVEP933并创建本地跟踪分支`
* `git checkout v2.0                                         # 检出版本v2.0`
* `git checkout -b devel origin/develop                      # 从远程分支develop创建新本地分支devel并检出`
* `git checkout -- README                                    # 检出head版本的README文件（可用于修改错误回退）`
* `git merge origin/master                                   # 合并远程master分支至当前分支`
* `git cherry-pick ff44785404a8e                             # 合并提交ff44785404a8e的修改`
* `git push origin master                                    # 将当前分支push到远程master分支`
* `git push origin :hotfixes/BJVEP933                        # 删除远程仓库的hotfixes/BJVEP933分支`
* `git push --tags                                           # 把所有tag推送到远程仓库`
* `git fetch                                                 # 获取所有远程分支（不更新本地分支，另需merge）`
* `git fetch --prune                                         # 获取所有原创分支并清除服务器上已删掉的分支`
* `git pull origin master                                    # 获取远程分支master并merge到当前分支`
* `git mv README README2                                     # 重命名文件README为README2`
* `git reset --hard HEAD                                     # 将当前版本重置为HEAD（通常用于merge失败回退）`
* `git rebase`
* `git branch -d hotfixes/BJVEP933                           # 删除分支hotfixes/BJVEP933（本分支修改已合并到其他分支）`
* `git branch -D hotfixes/BJVEP933                           # 强制删除分支hotfixes/BJVEP933`
* `git ls-files                                              # 列出git index包含的文件`
* `git show-branch                                           # 图示当前分支历史`
* `git show-branch --all                                     # 图示所有分支历史`
* `git whatchanged                                           # 显示提交历史对应的文件修改`
* `git revert dfb02e6e4f2f7b573337763e5c0013802e392818       # 撤销提交dfb02e6e4f2f7b573337763e5c0013802e392818`
* `git ls-tree HEAD                                          # 内部命令：显示某个git对象`
* `git rev-parse v2.0                                        # 内部命令：显示某个ref对于的SHA1 HASH`
* `git reflog                                                # 显示所有提交，包括孤立节点`
* `git show HEAD@{5}`
* `git show master@{yesterday}                               # 显示master分支昨天的状态`
* `git log --pretty=format:'%h %s' --graph                   # 图示提交日志`
* `git show HEAD~3`
* `git show -s --pretty=raw 2be7fcb476`
* `git stash                                                 # 暂存当前修改，将所有至为HEAD状态`
* `git stash list                                            # 查看所有暂存`
* `git stash show -p stash@{0}                               # 参考第一次暂存`
* `git stash apply stash@{0}                                 # 应用第一次暂存`
* `git grep "delete from"                                    # 文件中搜索文本“delete from”`
* `git grep -e '#define' --and -e SORT_DIRENT`
* `git gc`
* `git fsck`
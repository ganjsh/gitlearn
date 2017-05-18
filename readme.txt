Git is a distributed version control system
Git is free software 
Git readme

1. git remote add origin git@server-name:path/repo-name.git; // 本地连接到远程仓库
   git push -u origin master; //将最新修改推送到远程服务器
   git clone git@server-name:path/repo-name.git; // 从远程服务器上克隆到本地
2. 分枝管理
   git checkout -b dev; // 创建新的分枝dev
   git branch; // 查看分枝
   git checkout master; // 切换分枝到master
   git merge dev; // 合并某分枝到当前分枝
   git checkout -d dev; // 删除分枝dev
   git merge --no-ff -m "xxxx" dev; // 

   git stash; // 把当前工作现场“储存”起来，等以后恢复现场后继续工作
   git stash list; // 查看工作现场
   git stash pop; // 恢复现场
3. 多人协作工作模式
   首先，可以试图用git push origin branch-name推送自己的修改
   如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并
   如果合并有冲突，则解决冲突，并在本地提交
   没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功

   在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致
	可能会出现错误：fatal: Cannot update paths and switch to branch 'dev' at the same time.
	解决方案：先git fetch; 再git checkout -b branch-name origin/branch-name
   建立分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name
4. 标签管理：标签也是版本库的快照
   git tag <name>; // 创建标签，默认为HEAD，也可以指定commitid
   git tag -a <name> -m "xxx"; // 可以指定标签信息
   git tag -s <name> -m "xxx"; // 可以用PGP签名标签
   git tag; // 查看所有标签   git show <name>; // 显示指定标签的信息
   git push origin <tagname>; // 推送一个本地标签
   git push origin --tags; 可以推送全部未推送过的本地标签
   git tag -d <tagname>; 可以删除一个本地标签
   git push origin :refs/tags/<tagname>; // 可以删除一个远程标签
5. git补丁
   生成补丁：git format-patch -1; 或者 git format-patch HEAD^;
   应用补丁：git apply patch
6. 生成ssh key
   ssh-keygen -t rsa -C "your email";
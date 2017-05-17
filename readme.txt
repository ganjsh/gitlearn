Git is a distributed version control system
Git is free software 
Git readme

1. git remote add origin git@server-name:path/repo-name.git;
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
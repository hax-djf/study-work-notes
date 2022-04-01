### Git基操

#### git bash here命令

- 克隆代码

  ```shell
  # 分支
  git clone --branch <分支名称>  <@git/https地址>
  # 栗子
  git clone --branch notes-test git@github.com:hax-djf/study-work-notes.git
  # 主分支
  git clone <@git/https地址>
  # 栗子
  git clone git@github.com:hax-djf/study-work-notes.git
  ```

- 添加

  ```
  # 添加全部
  git add .
  # 添加某个文件
  git add <文件包名>
  ```

- 提交

  ```shell
  git commit -m 'init-project'
  ```

- 推送

  ```shell
  # 初始化项目第一次推送
  git push -u origin <主/分支name>
  # 正常推送
  git push 
  ```

- 取消暂存区[add]

  ```shell
  # 取消全部
  git restore --staged .
  # 取消部分文件
  git restore --staged <文件包名>
  ```

- 取消提交[commit ]

  ```powershell
  git reset --soft HEAD^
  ```

- 查看日志

  ```shell
  git log
  ```

- 配置与删除与查看远程仓库

  ```powershell
  # 添加 url为远程仓库地址
  git remote add origin <url> 
  # 删除
  git remote rm origin  <url> 
  # 查看
  git remote -v 
  ```

- 初始化本地仓库/取消初始化

  ```shell
  # 初始化
  git init
  # 取消初始化
  rm -rf .git
  ```

- .gitignore规则不生效的解决办法

  ```shell
  git rm -r --cached .
  git add .
  git commit -m 'update .gitignore'
  ```

  ------

  #### git生成 ssh-key

  ```shell
  # 创建文案，设置用户邮件
  mkdir ~/.ssh
  cd ~/.ssh/
  git config --global user.name "hax-djf"
  git config --global user.email "hax-djf@qq.com"
  ssh-keygen -t rsa -C "hax-djf@qq.com"
  # 连续按三次回车，这里设置的密码就为空了，并且创建了key。
  # 找到系统盘，默认位置 C:\Users\米饭饭一族\.ssh,将[id_rsa.pub]公钥copy出来，记住是全部copy 
  ```

  ------

  #### 初始化代码提交到github/gitee

  ```shell
  # 初始化
  git init
  # 提交状态
  git status
  git add .
  git commit -m'init'
  # 如果需要的话，可以重命名主/分支名称
  git branch -M <新的 主/分支名称>
  git remote add origin https://github.com/hax-djf/study-work-notes.git
  git push -u origin <主/分支名称>
  ```

- 注意事项

  问题：如果在创建仓库的，创建了 [README.md](https://github.com/hax-djf/study-work-notes/blob/main/README.md) 文件，本地在提交中包含了 [README.md](https://github.com/hax-djf/study-work-notes/blob/main/README.md)如果内容不一致会引起问题，例如出现如下

  ```shell
  ! [rejected]        master -> master (fetch first)
  error: failed to push some refs to 'http://192.168.144.128:9097/gitbucket/git/root/FlyingBirds-ui.git'
  ```

  处理方式：

  ```shell
  git pull --rebase origin <主/分支名称>
  合并再次提交
  git commit -m 'init'
  git push -u origin <主/分支名称>
  # 还是有错误 case, please try rebase (--continue | --abort | --skip) If that is not the case, please
  跳过合并
  git rebase  --skip
  完成
  git push -u origin <主/分支名称>
  ```

  ------

  #### 创建分支 branch 

  ```shell
  # 新建分支 branch-name 填写你的分支名称
  git branch <branch-name>
  # 查看所有分支
  git branch -a
  # 切换到某一分支
  git checkout <branch-name>
  # 添加修改代码到缓存（注意最后的"."前面有个空格
  git add .
  # 添加提交代码的备注
  git commit -m "init"
  # 提交代码到指定分支
  git push origin <branch-name> 
  # 分支第一次提交的时候需要加上 -u 
  git push -u origin <branch-name>
  ```

  ------

  #### 将origin(本地提交到指定仓库某个分支)

  ```shell
  # 操作origin代码 初始化git
  git init
  # 添加远程仓库地址
  git remote add origin <PATH/TO/REPO>
  # 将远程主分支 拉取下来 
  git fetch
  # 注意如果你的仓库没有add 和 commit 需要提交到暂存区，才能够创建分支
  # 检查代码
  git status 
  git add .
  git commit -m 'init-project'
  # 创建分支
  git branch <分支名称>
  # 指定现在的工作是基于哪个提交的
  git reset <分支名称>
  # 切换到分支
  git checkout <分支名称>
  # 删除初始化 master 分支
  git branch -d master
  # 推送到远程仓库
  git push -u origin <分支名称>
  ```

- 扩展知识 `git pull`和`git fetch`的区别：

  - `git fetch`是将远程主机的最新内容拉到本地，用户在检查了以后决定是否合并到工作本机分支中。

  -  `git pull` 则是将远程主机的最新内容拉下来后直接合并，即：`git pull = git fetch + git merge`，这样可能会产生冲突，需要手动解决 

  

  


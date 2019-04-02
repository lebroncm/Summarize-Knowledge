# <center>常用git命令</center>

<center>Li Junli</center>

<center>Jan 2019</center>

**git clone URL**    克隆远程*Repository*下每一个文件的每一个版本，*git* 支持*HTTPS*, *SSH*等传输协议

**git clone git@github.com:Ljl-Jdsk/Sensitive-field-identification.git**    *SSH*。*HTTPS*就是网址

**git clone URL yourname**    在本地创建的仓库名字自定义为 *yourname*，默认*origin*指代这个远端仓库

**git status**    检查当前文件状态

**git diff**    显示尚未暂存的改动，新建文件没有进行第一次*commit*时是不能显示的，感觉这是个bug

**git diff --cached** 显示已经暂存起来的变化

**git diff HEAD -- readme.md**    如果只想看*readme.md*  尚未暂存的更新

**git add filename**    将修改的文件加入到暂存区

**git add .**    将修改的所有文件加入stoge

**git commit -m "..."**    提交暂存区的所有文件，并加注释

**git commit -a**    自动把所有已经跟踪过的文件暂存起来一并提交，跳过 *git add* 步骤

**git config --list**    查看所有 *git* 当时能找到的配置

**git config  user.name/email**    查看用户名/邮箱

**git init**    把当前目录初始化为仓库，生成隐藏的*.git*的子目录, *.git/config* 里可以修改*origin*的名字，最好不改*.giit*

**git rm -f filename**    从暂存区域移除文件, 已修改的文件需要-f强制删除

**git rm --cached filename**    *git*不再跟踪，但是磁盘里仍保存

**git mv file_from file_to**    重命名

**git log**    查看提交历史  *--pretty=oneline* 可以把一次提交显示在一行

**git log -p -2**    *-p*表示查看差异，*-2*表示只看最近两次提交，还有很多其他有用的参数

**git remote**    查看配置的远程仓库服务器，至少应该能看到 *origin*, 这是*Git* 给你克隆的仓库的默认名

**git remote -v**    会显示需要读写远程仓库使用的 *Git* 保存的简写与其对应的 *URL*

**git remote add yourname URL**    添加一个新的远程 *Git* 仓库，同时自定义*yourname*代表难记的*URL*

**git remote rm remotename**     移除远程分支，比如*origin*   

#### <center>推送local_branch到remote_branch, 并建立关联</center>

**git push origin**    *remote_branch, local_branch* 同名且已关联, 本地也切换到*local_branch*

**git push -u origin/remote_branch**    远程已有，但并未关联本地分支，本地已切换到*local_branch*

​                                                                    -u 关联本地和远程，一次关联就行，以后推送或拉取时可以简化命令

**git push origin local_branch:remote_branch**    远程没有*remote_branch*分支，本地已切换到*local_branch*

​                                                                                       若不改名，可以省略:remote_branch, 例如下面命令：

**git push origin master**    本地*master*推送到*origin* 指的远程仓库的*mater*分支, 没有就新建一个, 省了:*master*



**git branch  branch_name**    查看本地分支, 若加*branch_name*就是新建分支

**git branch -d branch_name**    删除分支

**git branch -a**    查看远程分支

**git checkout branch_name**    切换分支



#### <center>pull拉取远程分支</center>

**git pull <远程仓库名> <远程分支名>:<本地分支名>**    远程指定分支拉取到本地指定分支上

**git pull <远程仓库名> <远程分支名>**    远程指定分支拉取到本地当前分支

**git pull <远程仓库名>**    将与本地当前分支同名的远程分支拉取到本地当前分支上



**git reset --hard HEAD^**    回退到上一版本 *HEAD, HEAD^, HEAD^^, HEAD~100*是当前/上*1*个/*2*个/*100*个版本

**git reset --hard 1092866a**    返回*092866a*版本，版本号写前几位就行

**git reflog**    回退时*git log* 也会回退，若是想恢复却记不住版本*id*, 用此命令可以查看历史版本*id*

**git checkout -- readme.md**    撤销修改，若没添加到暂存区，就回到修改前，否则回到添加到暂存区前

**git reset HEAD readme.txt**    若已添加到暂存区，用此命令回退暂存区的修改，再用上一个命令就回到修改前了



##Blog采用landscape-plus主题
```
更新landscape-plus
git submodule update
```

##关于submodule
```
添加submodule:
git submodule add 仓库地址 路径
注意：路径不能以 / 结尾（会造成修改不生效）、不能是现有工程已有的目录（不能順利 Clone）

初始化
git submodule init

更新
git submodule update

部署
git submodule update --init --recursive
要是加上 --recursive 参数， git clone 也可以把所有一起 clone 过来哦
git clone --recursive 仓库地址

同步
git submodule foreach --recursive git pull origin master

git submodule status

删除
submodule的删除稍微麻烦点：首先，要在“.gitmodules”文件中删除相应配置信息。然后，执行“git rm –cached ”命令将子模块所在的文件从git中删除。
$ git rm --cached node_modules/submodule && rm -rf node_modules/submodule/

下载的工程带有submodule
初始的时候，submodule的内容并不会自动下载下来的，此时，只需执行如下命令：
git submodule update --init --recursive

建议大家:
1. git pull之后，立即执行git status, 如果发现submodule有修改，立即执行git submodule update
2. 尽量不要使用 git commit -a， git add命令存在的意义就是让你对加入暂存区的文件做二次确认，而 git commit -a相当于跳过了这个确认过程。
3. 你需要对submodule做一些修改，默认git submodule update并不会将submodule切到任何branch，所以，默认下submodule的HEAD是处于游离状态的(‘detached HEAD’ state)。所以在修改前，记得一定要用git checkout master将当前的submodule分支切换到master，然后才能做修改和提交。
```
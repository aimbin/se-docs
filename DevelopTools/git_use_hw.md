# GIT日常操作-简化版
环境基本信息：windows10pro-64位，简体中文。原因：习惯，与办公环境同。

## I. 用乌龟本地提交到分支，github网站请求master拉取
1. 安装Git命令行客户端(windows)，再安装乌龟（TortoiseGit），以及中文库。
2. 在github注册账号，创建工程，并且创建分支，“Clone or download” 复制地址。
3. 本地选择目录，右键用乌龟clone分支到本地。
4. 修改文件内容,乌龟commit（只到本地），在github网页的分支里，看不到新内容。
5. 选择需要提交的文件夹，push（推送）到分支。在github的分支能看到新内容，master没有。
6. 在github的分支（branch），点击compare & pull request，将修改请求master拉取新内容。
7. 在github能看到pull requests后面数字为1，选择，点击Merge pull request，
 接着confirm merge。在master则也能看到新提交的内容。

## II. 本地乌龟操作所有
1. 用乌龟的PuTTY Key Generator生成密钥（公钥+私钥）
2. 保存私钥为ppk文件， 复制公钥key到github的settings的SSH and GPG keys。
3. 选择git工程目录，右键-乌龟菜单的设置，Git-->远端-->设置地址和私钥，添加保存。有个passphrase不用设置，如果设置要记住。
4. 将master也clone到本地，添加远端配置。乌龟右键选merge，选择合并的分支。
5. 合并的内容也只是在本地，master一样commit+push。
6. 在github上刷新，可以看到新的内容。

## III 解惑与引用
1. 提交到master时，乌龟的本地merge操作和github的pull request操作不一致的迷惑：
 +  讨论参考[`Github` 上的 `pull request` 与 `Git` 的 `pull` 有关系么？ ](https://segmentfault.com/q/1010000002575139)
 + 结论：github和git命令设计本身还是按照master主控，即branch开发者来请求master
 去pull(拉取)自己的修改。而乌龟的设计，在菜单并没有git request-pull，
 不支持这个过程，需要人工去协调。

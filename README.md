# git-backup

git-backup.

## Install
如果您的hexo版本是2.x.x，则应按如下方式安装：

``` bash
$ npm install hexo-git-backup@0.0.91 --save
```

如果您的hexo版本是2.x.x，则应按如下方式安装：

``` bash
$ npm install hexo-git-backup --save
```

## Update

如果使用--save安装，则在更新时必须先删除:

``` bash
$ npm remove hexo-git-backup
$ npm install hexo-git-backup --save
```

## Configure

您应该在中配置此插件 `_config.yml`.

``` yaml
backup:
    type: git
    repository:
       github: git@github.com:xxx/xxx.git,branchName
       gitcafe: git@github.com:xxx/xxx.git,branchName
```

## Using
```
hexo backup 
```
or
```
hexo b
```
## Options

如果你想备份你的主题，只需添加 `theme: your theme name,your theme name` 在 `_config.yml`.

``` yaml
backup:
    type: git
    theme: coney,landscape,xxx
    repository:
       github: git@github.com:xxx/xxx.git,branchName
       gitcafe: git@github.com:xxx/xxx.git,branchName
```
**注意：如果你这样做 `themes/coney/.git`将会被删除**

如果你想DIY提交消息，只需添加 'message: update xxx'.
``` yaml
backup:
    type: git
    message: update xxx
    repository:
       github: git@github.com:xxx/xxx.git,branchName
       gitcafe: git@github.com:xxx/xxx.git,branchName
```


现在你可以备份所有的博客了！
## Problems

如果你的计算机允许，你可能会遇到一些麻烦

### Error: EISDIR, open
it is caused by permission.
just do 'sudo hexo b' 
```
sudo hexo b
```

问题一：
fatal: 'github' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

出现上面的提示，说明github远端仓库和本地仓库的关联关系没有建立
可以尝试两种方法解决：
方法1：
执行如下命令
git remote add github git@github.com:xxx/xxx.git
hexo b

方法2:
删除本地目录下的 .git 目录
然后执行命令
hexo b
直到看到如下输出：

[new branch] master -> master
Branch master set up to track remote branch master from github.
INFO Backup done: git

才可以关闭命令终端

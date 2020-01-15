![](http://www.ruanyifeng.com/blogimg/asset/2014/bg2014061202.jpg)

## git init
`$ git init`

## git clone
`$ git clone <版本库的网址>`  
`$ git clone <版本库的网址> <本地目录名>`

```
$ git clone http[s]://example.com/path/to/repo.git/
$ git clone ssh://example.com/path/to/repo.git/
$ git clone git://example.com/path/to/repo.git/
$ git clone /opt/git/project.git
$ git clone file:///opt/git/project.git
$ git clone ftp[s]://example.com/path/to/repo.git/
$ git clone rsync://example.com/path/to/repo.git/
```
## get remote

```
$ git remote  
$ git remote -v
$ git remote show <主机名>  
$ git remote add <主机名> <网址>
$ git remote rm <主机名>
$ git remote rename <原主机名> <新主机名>
```

>git remote add origin *https://github.com/billywww/instructor.git*   

## get fetch
一旦远程主机的版本库有了更新（Git术语叫做commit），需要将这些更新取回本地，这时就要用到git fetch命令。  
`$ git fetch <远程主机名>`  

默认情况下，git fetch取回所有分支（branch）的更新。如果只想取回特定分支的更新，可以指定分支名  
`$ git fetch <远程主机名> <分支名>`

## get pull
git pull命令的作用是，取回远程主机某个分支的更新，再与本地的指定分支合并。它的完整格式稍稍有点复杂。  
`$ git pull <远程主机名> <远程分支名>:<本地分支名>`  
如果远程分支是与当前分支合并，则冒号后面的部分可以省略。  

## get push
git push命令用于将本地分支的更新，推送到远程主机。它的格式与git pull命令相仿。  
`$ git push <远程主机名> <本地分支名>:<远程分支名>`  

如果省略远程分支名，则表示将本地分支推送与之存在"追踪关系"的远程分支（通常两者同名），如果该远程分支不存在，则会被新建。  
`$ git push origin master`  

如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。  
```
$ git push origin :master
# 等同于
$ git push origin --delete master
```
如果当前分支与远程分支之间存在追踪关系，则本地分支和远程分支都可以省略。  

如果远程主机的版本比本地版本更新，推送时Git会报错，要求先在本地做git pull合并差异，然后再推送到远程主机。这时，如果你一定要推送，可以使用--force选项。  
`$ git push --force origin `  

最后，git push不会推送标签（tag），除非使用--tags选项
`$ git push origin --tags`

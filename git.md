# Git

我在使用了一段时间的git 之后，还仅停留在简单的git add、git commit、git push三个操作的使用，甚至是每次提交，为了避免产生冲突还会重新git clone 再次修改提交。今天梳理一下基本概念，让git 更加“物尽其用”。

## git clone 仓库地址

git clone 仓库地址，当我们想要获取一个仓库的所有内容时，并对其代码或文件进行操作时，就可以使用git clone 将远程代码获取到本地，这个过程相当于在本地创建一个工作区【这个概念稍后再解释】。

这个操作会在本地当前目录下，创建一个和远程仓库架构相同的工作目录，其中包含.git 的目录，用于保存下载下来的所有版本记录。

![截屏2021-08-30 下午7.25.00](/Users/xiatian/Library/Application Support/typora-user-images/截屏2021-08-30 下午7.25.00.png)

还可以重新命名 ，在命令末尾指定新的名字即可。

![截屏2021-08-30 下午7.25.22](/Users/xiatian/Library/Application Support/typora-user-images/截屏2021-08-30 下午7.25.22.png)

## 创建分支

在本地仓库操作时，每次提交，git都把它们串成一条时间线，这条时间线就是一个分支。

![截屏2021-08-30 下午9.18.18](/Users/xiatian/Library/Application Support/typora-user-images/截屏2021-08-30 下午9.18.18.png)

目前，git 中只有一条时间线，即主分支master分支。可以看到当前只有一个分支。HEAD  严格来说不是指向 每次提交的节点，而是指向master ，master 指向提交，故HEAD 指向当前的分支，每次提交新的修改节点后，matser分支都会向前移动一步。

> git branch 可以查看分支

![截屏2021-08-30 下午9.18.56](/Users/xiatian/Library/Application Support/typora-user-images/截屏2021-08-30 下午9.18.56.png)

还可以新建分支，并选择其他分支进行操作。如果创建新的分支，git就会新建一个指针，例如新建dev，那么指向master 相同的提交节点，再把HEAD指向dev ，就表示当前分支在dev 上。那么以后对于工作区的修改 和提交就是针对dev这个分支上的操作了。matser不受任何影响。

![截屏2021-08-30 下午9.21.47](/Users/xiatian/Library/Application Support/typora-user-images/截屏2021-08-30 下午9.21.47.png)



## 三个工作区

现在我们来解释上文中提到的三个工作区的概念。

![截屏2021-08-30 下午9.05.44](/Users/xiatian/Desktop/截屏2021-08-30 下午9.05.44.png)

#### 工作区

简单理解，就是当前的工作目录，既可以在自己电脑上看到并操作的目录。

上文中我们还提到了git clone 这个操作，它会在本地创建一个.git 文件夹，进行版本控制等操作。

![截屏2021-08-30 下午8.53.50](/Users/xiatian/Library/Application Support/typora-user-images/截屏2021-08-30 下午8.53.50.png)

#### 暂存区

可以在上述.git 文件夹中看到众多文件。index 即为暂存区，实际上就是一个包含文件索引的目录树，像是一个虚拟的工作区。在这个虚拟工作区的目录树中，包含了文件的基本信息，但是文件的内容不存储在这里，而是保存在了.git/objects 中，文件索引建立了文件和对象库中对象实体之间的关系（图中红色虚线）。

#### 版本库

还有一个版本库，可以理解为即是本地的仓库，当git push 时就是把本地的仓库的所有内容提交到远程仓库中。

## git 基本操作

![截屏2021-08-30 下午9.40.37](/Users/xiatian/Library/Application Support/typora-user-images/截屏2021-08-30 下午9.40.37.png)

+ git clone  即获取远程仓库代码到本地，上文中有详细介绍，这里不再概述。

+ git pull 是从远程获取代码并合并到本地的版本中

+ git add files 将工作区文件提交到暂存区中，同时工作区修改的文件内容被写入到对象中，对象的ID被记录在暂存区的文件索引中。

  git add . 表示把工作区所有修改的文件都提交上去

+ git commit 把暂存区中所有修改的内容提交到当前的分支中，即更新到本地仓库

+ git push   将本地仓库的信息提交到远程仓库中

## git 其他操作

+ git log 显示当前分支提交版本库的日志


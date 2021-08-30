## 在Github上删除已有的仓库或者文件

+ 本地仓库的文件和远程仓库的文件同时删除

打开本地仓库的文件夹，利用rm 命令删除文件，rm -rf 命令删除文件夹；然后执行下面的命令即可

```shell
git add *  //把本地仓库的文件上传至缓存
git commit -m "delete file" 
git push //把本地仓库文件上传至远程仓库
```

![截屏2021-08-30 上午10.25.40](/Users/xiatian/Library/Application Support/typora-user-images/截屏2021-08-30 上午10.25.40.png)

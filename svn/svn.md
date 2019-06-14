# SVN Notes



## SVN 冲突

`svn update` 时报

```shell
filePath - Node remains in conflict
```

执行命令

```shell
svn revert --depth=infinity filePath
```


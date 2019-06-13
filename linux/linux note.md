# Linux Note



## find

```shell
find . -name "*.iml" | xargs rm -r    删除当前文件夹的指定类型文件
```



## [curl](https://curl.haxx.se/)

命令行工具和库 用URL传输数据. 翻译: **command line tool and library** for transferring data with URLs.



查看手册, 查看它的示例,便能运用curl

```shell
curl --manual
```

表单文件上传

```shell
curl -F "file=@localfile;filename=nameinpost" example.com
```

下载文件

```shell
curl -O example.com
```

显示头信息

```shell
curl -i https://m.vxiao.cn
```


# Linux Note



## 脚本解释器

```shell
ls -l /bin/*sh
```



## 运行

运行Shell脚本有两种方法：

### 作为可执行程序

```shell
chmod +x test.sh
./test.sh
```



### 作为解释器参数

```sh
sh test.sh
```



## passwd

```shell
#root用户登录修改root密码
passwd root
```



## find

```shell
#删除当前文件夹的指定类型文件
find . -name "*.iml" | xargs rm -r    
#查找文件内容
find .|xargs grep -ri "WifiConfigController" -l
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



## [tr]([http://man.linuxde.net/tr](http://man.linuxde.net/tr))

**tr命令**可以对来自标准输入的字符进行替换、压缩和删除。它可以将一组字符变成另一组字符，经常用来编写优美的单行命令，作用很强大。

在Shell编程中,有了回车符\r的存在,在拼接字符串,字符串会沾在一起.

```shell
a=`printf "123456\r"`
b="${a}789"  
echo $b
#以下是输出
789456
```

`tr -d '\r'` 去除回车符


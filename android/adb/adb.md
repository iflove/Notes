# Adb



## Shell

### pm

```shell
pm list package -f 		列出已安装的apk的包名
```



### getprop

```shell
adb shell getprop ro.product.model

adb shell getprop | grep "model\|version.sdk\|manufacture
r\|hardware\|platform\|revision\|serialno\|product.name\|brand"
```


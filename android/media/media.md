# Media



## MediaScannerConnection

Google的一些开发者给出的方案是：在创建文件的时候，添加一行代码：

```java
MediaScannerConnection.scanFile(this, new String[] { file.getAbsolutePath() }, null, null);
```


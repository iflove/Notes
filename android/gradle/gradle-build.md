

# buildFinished

项目臃肿加上开启`minifyEnabled`, `dump.txt` 文件变得非常大,利用gradle 构建生命周期去删除无用的构建垃圾.

`settings.gradle`

```groovy
gradle.buildFinished {
    println "构建结束..."
    def f = new File("app/build/outputs/mapping")
    delFileFolder(f)

}

def delFileFolder(File f) {
    if (!f.exists()) {
        return
    }
    if (f.isDirectory()) {
        def files = f.listFiles()
        for (File file : files) {
            delFileFolder(file)
        }
    }
    f.delete()
}
```


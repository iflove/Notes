

# 低功率蓝牙

在Android上开发ble总会遇到各种奇怪问题.



## 扫描

不断重复关闭扫描开启扫描,就会出现无法再开启扫描的问题.

```java
BtGatt.GattService: App 'cn.mashang.vbox' is scanning too frequently
```

遇到这种情况,关闭一下蓝牙就OK了.为了避免这样的问题,处理蓝牙相关操作时,稍微停止个2-3秒钟,再操作.

eg: 蓝牙被关闭时,不能马上开启扫描,不然不能100%成功.

```kotlin
val defaultAdapter = BluetoothAdapter.getDefaultAdapter()
if (defaultAdapter.isEnabled.not()) {
    defaultAdapter.enable()
    Thread.sleep(2000)
}
//开始扫描
startScan
```






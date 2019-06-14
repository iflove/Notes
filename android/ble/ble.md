

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





# [BLE mac地址变化](https://blog.csdn.net/shuijianbaozi/article/details/75219530)

```wiki
Q:Android 5 introduces BLE MAC address rotating for increased privacy. Every time when calling BluetoothLeAdvertiser.startAdvertising(), the MAC-address is changed.

Is it possible to disable address rotating, and just use the same MAC address during the entire lifetime of BluetoothLeAdvertiser?

译:Android的5引入BLE MAC地址时附带了一个增加隐私的旋转。每次调用BluetoothLeAdvertiser.startAdvertising（）(开启广播)时，该MAC地址被改变。
```

[禁用BLE隐私功能](https://stackoverflow.com/questions/28602672/android-5-static-bluetooth-mac-address-for-ble-advertising)

You can disable the BLE Privacy Feature to avoid the MAC address rotating, and change the bluedroid source code as [follows](http://androidxref.com/5.1.1_r6/xref/external/bluetooth/bluedroid/include/bt_target.h#1326):

```wiki

* Toggles support for general LE privacy features such as remote address
* resolution, local address rotation etc.
*/

#ifndef BLE_PRIVACY_SPT 
-#define BLE_PRIVACY_SPT         TRUE
+#define BLE_PRIVACY_SPT         FLASE
#endif
```


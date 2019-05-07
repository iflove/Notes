# [了解Android上的颜色（六个字符）](https://stackoverflow.com/questions/5445085/understanding-colors-on-android-six-characters)

Android使用十六进制ARGB值，格式为#AARRGGBB。第一对字母AA代表alpha通道。您必须将十进制不透明度值转换为十六进制值

## **十六进制不透明度值**(alpha通道值)

- 100% — FF
- 95% — F2
- 90% — E6
- 85% — D9
- 80% — CC
- 75% — BF
- 70% — B3
- 65% — A6
- 60% — 99
- 55% — 8C
- 50% — 80
- 45% — 73
- 40% — 66
- 35% — 59
- 30% — 4D
- 25% — 40
- 20% — 33
- 15% — 26
- 10% — 1A
- 5% — 0D
- 0% — 00 



## 代码获取a通道值

java

```java
for (double i = 1; i >= 0; i -= 0.01) {
    i = Math.round(i * 100) / 100.0d;
    int alpha = (int) Math.round(i * 255);
    String hex = Integer.toHexString(alpha).toUpperCase();
    if (hex.length() == 1)
        hex = "0" + hex;
    int percent = (int) (i * 100);
    System.out.println(String.format("%d%% — %s", percent, hex));
}
```

python

```python
>>> hex(round(255*0.75))
'0xbf'
```


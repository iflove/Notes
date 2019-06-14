# Java-api



## java.text

支付场景下做数值计算时,必须得控制计算结果的精度,能用`DecimalFormat` 保留小数点后几位、数字间用`,`分割、四舍五入等场合。

```java
DecimalFormat df = new DecimalFormat("0.0#");
```

## 关键符号

- `0`：以`0` 填充空缺位
- `.`： 小数的分隔符的占位符
- `,`：分组分隔符的占位符 (只能放在整数部分)
- `#`：取整数



## java.math

### [RoundingMode](https://docs.oracle.com/javase/7/docs/api/java/math/RoundingMode.html)

`DecimalFormat` 提供 `RoundingMode` 中定义的**舍入模式进行格式化**。默认情况下，它使用`RoundingMode.HALF_EVEN`。

```java
DecimalFormat df = new DecimalFormat("0.00");
df.setRoundingMode(RoundingMode.HALF_UP);
```



### [BigDecimal](https://docs.oracle.com/javase/7/docs/api/java/math/BigDecimal.html)

商业运算中, 必须计算到选定的精度和舍入模式, 而`BigDecimal`类提供操作用于算术，比例操作，舍入，比较，散列和格式转换。

```java
BigDecimal balanceBigDecimal = new BigDecimal("100");
BigDecimal payAmountBigDecimal = new BigDecimal("0.123");
BigDecimal result = balanceBigDecimal.subtract(payAmountBigDecimal);
 //舍入操作 返回 BigDecimal其值近似（或精确）等于操作数的值
result = result.setScale(2, BigDecimal.ROUND_HALF_EVEN);
System.out.println(result);
//99.88
```


# JNI Note



## NewStringUTF

```java

member reference type 'JNIEnv' (aka '_JNIEnv') is not a pointer; did you mean...

1. //用C语言格式
return (*env)->NewStringUTF(env, "Hello JNI !");

2. //C++格式
return env->NewStringUTF((char *)"Hello JNI !");


```


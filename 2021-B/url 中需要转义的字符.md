## url 中需要转义的字符

**+** URL 中+号表示空格 %2B 

**空格** URL中的空格可以用+号或者编码 %20 

**/** 分隔目录和子目录 %2F 

**?** 分隔实际的 URL 和参数 %3F 

 **%** 指定特殊字符 %25 

**#** 表示书签 %23 

 **&** URL 中指定的参数间的分隔符 %26 

 **=** URL 中指定参数的值 %3D 



## 不想转义？ 

base64编码也是一种解决方案

```
window.btoa("mariadb")
"bWFyaWFkYg=="
window.atob("bWFyaWFkYg==")
"mariadb"
```


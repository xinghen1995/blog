## 主要内容
> #### C语言库函数
> #### 随手记

## C库函数
> ### <time.h>
1) 使用time_t的函数有
```c
time_t time(time_t *tp);  // 获取日历时间
double difftime(time_t time1, time_t time2); // 返回时间差值(sec)
struct tm* localtime(const time_t *tp); // 将日历时间转换为struct tm
strcut tm *gmtime(const time_t *tp); // 转换为UTC
char *ctime(const time_t *tp);
```
2) 使用struct tm的函数有
```c
time_t mktime(struct tm *tp); // 将struct tm的转换为日历时间time_t
char *asctime(struct tm *tp); 
char *strftime(char *s, size_t smax, const char *fmt, const struct tm *tp);
```

## 随手记
1) 流：流是磁盘或其他外围设备相关联的数据的源或目的地。数据的来源或去处。打开一个流就是将一个流和一个设备或文件进行了关联。
2) 
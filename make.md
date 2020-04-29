## 主要内容
> #### make手册阅读笔记
> #### make实践记录

## make手册阅读笔记
1. **Makefile**文件由五部分构成
    - 显式规则
    - 隐式规则
    - 变量
    - 目标
    - 注释
2. 伪目标必须要在<strong>.PHONY</strong>后加':'
```makefile
.PHONY: clean
clean:
    rm -rf *.o
```
3. **make**可以是用'-f'选项指定任何文件作为**Makefile**，而**make**就不会按照'GNUMakefile','makefile','Makefile'的顺序去查找文件
4. **make**可以使用通配符<strong>'%'</strong>，下面代码force会被强制更新，无论是否已经存在。任意目标如果没有被找到，都会去执行%表示的规则
```makefile
foo:
    frobnicate > foo
%: force
    @$(MAKE) -f Makefile $@
force: ;
```

## make实践手册
1. "="和":="的区别:
    + make中的变量是在Makefile文件完全展开后才决定的值
    + "="赋值的变量在Makefile完全解析后才赋值
    + ":-"赋值的变量只和变量的位置相关
```makefile
    x = foo
    y = $(x) bar
    x = abc
```
上述表达式y的值是abc bar，因为在Makefile完全展开后，x的值是abc
```makefile
    x := foo
    y := $(x) bar
    x := abc
```
上述表达式y的值是foo bar，因为":="赋值的变量只和位置有关，所以x的值是foo

2. Makefile中(shell cmd)和@(shell cmd)的区别：
    + shell cmd 显示cmd命令，并打印命令执行结果
    + @(shell cmd)仅显示命令执行结果
```makefile
all:
    # 输出为"echo hello"
    echo "hello" 
    # 输出为"hello"
    @echo "hello"
```
3. make的第二目标：make在执行完编译命令后，会删除所有非目标文件，如.o文件。为了保留.o文件可以用.SECONDARY:$(OBJS)的方式，将中间文件保留
```makefile
.SECONDARY: $(OBJS)
```
4. make中一些特殊的中间变量:
    + $@ : 所有的目标文件
    + $^ : 所有的约束文件
    + $< : 表示第一个约束文件
    + 待补充
5. wildcard命令：正则式(通配符)在变量和约束中不会自动展开，需要使用wildcard声明。
```makefile
SRC := $(wildcard $(SRC_DIR)/*.cpp)
```
## 主要内容
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
%: foo
    @$(MAKE) -f Makefile $@
force: ;
```
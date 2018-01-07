### 一、语法：
#### extern void *malloc (unsigned int num_bytes);
#### 说明：
* 头文件：#include<malloc.h> 或 #include<alloc.h>--(两种方式都是一样的) 
* 功能：分配长度为num_bytes字节的内存块说明：如果分配成功则返回指向被分配内存的指针，否则返回空指针NULL。
* 注意：当内存不再使用时，应使用free（）函数将内存块释放。

#### 示例代码：
```
#include <stdio.h>
#include <stdlib.h>

int main(){

    char *ip;
    ip =(char *) malloc(100);
    
    if (ip){
        printf("指针ip对应的地址值是：%x\n",ip);
        printf("指针ip对应的值是：%x \n",*ip);
    } else{
        printf("内存为空");
    }
    free(ip);

    return 0;
}
```
#### 运行效果：
```
指针ip对应的地址值是：ebc02610指针ip对应的值是：0 
```

### 二、函数声明
#### 语法：void * malloc（int size）
* 说明：malloc向系统申请分配指定size个字节的内存空间。
* 返回值：void*表示未确定类型的指针，void*类型可以强制转换为其他类型是指针


### 三、malloc与new的不同
* new返回指定类型的指针，并且可以自动计算所需大小。
* malloc必须计算好字节数，并且在返回后强制转换为实际类型的指针。

#### new中：
```
int *p;
p = new int;//返回类型为int* 类型（整数型指针），分配大小为sizeof（int）
```
或：
```
int * parr;
parr = new int[100];   //返回类型为int * 类型（整数型指针），分配大小为sizeof（int）*100；
```
#### malloc中：
```
 int * p；
 p = （int * ）malloc（sizeof（int））；
```
#### 说明：
* 1、malloc函数返回值是"void * "类型，如果不加强制类型转换将编译失败。
* 2、函数的实参为sizeof（int），用于指明一个整型数据需要的大小。
* 3、如果写成" int * p = （int * ） malloc（1）；"编译正常，只给*p分配了1个字节导致有3个字节的内容会被清理。
* 4、malloc实现new [ ]效果：
``` 
int * p = (int *) malloc(sizeof(int)*100); //分配可以放下100个整数的内存空间 
```
* 5、malloc只管内存分配，并不能对内存进行初始化，所以得到的一片新内存的值是随机的
* 6、除了分配及最后释放的方法不一样，通过malloc或new得到指针，在其他操作上保持一致。


### 四、总结
* 1、malloc函数其实就是在内存中找到一片指定大小空间，然后将这个空间的首地址范围给一个指针变量。
* 指针变量可以是一个单独的指针，也可以是一个数组的首地址，这要看malloc函数中参数size的具体内容。
* malloc分配的内存空间在逻辑上是连续的（在物理空间是不连续的），开发者关注的是逻辑上的连续因为操作系统会安排内存分配，所以使用起来当成是连续的。





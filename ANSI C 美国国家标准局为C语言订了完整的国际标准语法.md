ANSI C	美国国家标准局为C语言订了完整的国际标准语法

C语言特点：
* 简单
* 快速
* 高性能
* 兼容性好
* 功能强大
* 易于学习

C语言可以做Linux嵌入式（也就是小工具）
ARM嵌入式、单片机、Arduino 都是C语言
C语言有指针，直接和内存打交道
C语言可以做硬件编程

> NGINX=Apache×10
> C					C++

C语言是由UNIX诞生而产生的技术
MAC是用UNIX内核
Windows没办法装UNIX，只能装Linux

AMD64位CPU   Ubuntu先出然后intel出的


 linux最好用的编辑器：emacs、vim

 ~~~
 安装命令：
 sudo apt-get install 软件名称
 sudo apt-get update 更新资源
 cd ~	进入家目录
 pwd	查看当前位置
 ls	查看当前目录包含哪些文件夹、文件
 ls -l	查看文件类型、时间、用户、用户组
 touch 	文件名		创建文件
 rm 文件名				删除文件
 mkdir 目录名		创建一个目录
 cd 目录名				进入一个目录
 ~~~

 ~~~
 vim:
 i当前光标之前插入
 a当前光标之后插入
 shift+a行尾插入
 shift+i行首插入
 o在下一行插入
 shift+o上一行插入
 x删除当前光标
 dd删除当前一行
 ~~~

 ~~~
 LInux中的stdio是标准的输入输出流
 gcc+文件名 编译文件
 ./文件名	打开文件
 ~~~


> :sp		分屏创建文件
> ctrl+ww		切换屏幕
> :set nu		显示行号


两个文件一起编译 gcc file1 file2 -o newfile.out


不会再修改的函数，用的公共框架和公共类，编译生成静态库


gcc hello.c
gcc -c max.c -o max.o
gcc max.o hello.c

### 头文件与函数定义分离
min.c
~~~
#include <stdio.h>

int min(int a,int b)
{
if(a<b){
return a;
}else{
return b;
}
}
~~~
max.c
~~~
#include <stdio.h>

int max(int a,int b)
{
if(a>b){
return a,;
}else{
return b;
}
}
~~~
hello.c
~~~
#include <stdio.h>
#include "max.h"
#include "min.h"

int main()
{
int a1=33;
nt a2=21;
int maxNum=max(a1,a2);
int minNum=min(a1,a2);
printf("the max value is %d\n,the min value is %d\n",maxNum,minNum);
return 0;
}
~~~

make工具可以将大型的开发项目分成若干个模块
make工具可以很清晰和很快捷的整理源文件
make内部也是gcc
apt-get install make安装make


Makefile的编辑
~~~c
#this is make file
hello.out:max.o min.o hello.c
	gcc max.o min.o hello.c -o hello.out
max.o:max.c
	gcc -c max.c -o max.o
min.i:min.c
	gcc -c min.c -o min.o
~~~



main函数中return
gcc main.c -o mian.out && ./main.out

echo $?
输出0就是执行成功
./main.out && ls				如果&&之前输出的是0后面命令就会执行

main函数中的参数
%S表示打印字符串
argv是指针
argc是整数
int main(int argc,char* argv[])

~~~
#include <stdio.h>

int main(int argc,char* argv[])
{
    primtf("argc is %d \n",argc);
    int i;
    for(i=0;i<argc;i++){
    printf("argv[%d] is %s \n",i,argv);
    }
    return 0;
    }
}
}
~~~

Linux的标准输入流、标准输出流、标准错误流
printf标准的输出流
scanf标准的输入流
stderr标准的错误流

~~~
#include <stdio.h>

int main()
{

fprintf(stdout,"please input the value a: \n");
int a;
fscanf(stdin,"%d",&a);
if(a<0){
fprintf(stderr,"the value must > 0 \n");
return 1;
}
return 0;
}
~~~


重定向  >>		>
用法举例：
./a.out >> a.txt
ls /etc/ >> b.txt
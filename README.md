# C-p48-
C语言学习笔记 p48 字符串函数使用和剖析 
#include<stdio.h>
#include<string.h>
#include<assert.h>

int main()
{
    int len=strlen("abcdef");
    //错误示范
    //char arr[]={'a','b','c','d','e','f'};
    //int len=strlen(arr);
    printf("%d\n",len);
    return 0;
}
//实现strlen的方法
//1.计数器的方法
//2.递归
//3.指针-指针

//1.计算器方法
my_strlen(const char* str)
{
    int count=0;
    assert(str!=NULL);
    while(*str!='\0')
    {
        count++;
        str++;
    }
    return count;
}


//size_t==unsigned int
int main()
{
    if(strlen("abc")-strlen("abcdef")>0)
    {
        printf("hehe\n");
    }
    else
    {
        printf("haha\n");
    }
    return 0;
}//此代码输出hehe，这里判断语句的strlen是把代码当成一个无符号数来理解的

//strcpy
//库函数模版：char* strcpy(char* destination,const char* source);
char* my_strcpy(char* dest,const char* src)
{
    assert(dest!=NULL);
    assert(src!=NULL);
    char* ret=dest
    //拷贝src指向的字符串到dest指向的空间，包含'\0'
    while(*dest++=*src++)
    {
        ;
    }
    //返回目的空间的起始地址
    return ret;
}
int main()
{
    char arr1[]="abcdefghi";
    char arr2[]="bit";
    my_strcpy(arr1,arr2);
    printf("%s\n",arr1);
    return 0;
}//注：1.strcpy的src字符串必须要带'\0'，否则会向后越界访问
//2.目标空间必须足够大，以确保能存放原字符串
//3.目标空间不可变
//4.dest字符串不能是常量字符串，常量字符串是不可修改的

//strcat(字符串追加)
//函数库原形：char* strcat(char* destination,const char* source);
my_strcat(char* dest,const char* src)
{
    char* ret=dest;
    assert(dest!=NULL);
    assert(src);
    //1.找到目的字符串的'\0'
    while(*dest!='\0')
    {
        dest++;
    }
    //追加
    while(*dest++=*src++)
    {
        ;
    }
    return ret;
}
int main()
{
    char arr1[30]="hello\0";//这里的空间必须足够大,目的地也必须要带'\0'
    char arr2[]="world";//这里也必须包含'\0'
    my_strcat(arr1,arr2);
    printf("%s\n",arr1);
    return 0;
}

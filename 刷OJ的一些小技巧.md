# 刷OJ的一些小技巧

2017年10月06日 12:47:46

 

_lefer

 

阅读数：331

更多

个人分类： [算法](https://blog.csdn.net/u012987012/article/category/5928433)

1. freopen(“1.txt”,”r”,stdin); //程序运行后系统自动输入此文档里面的内容（不需要进行手动输入） 
   freopen(“1.txt”,”w”,stdout); //程序输出的内容保存在此文件里

   ```
   freopen("C:\\Users\\lefy\\Downloads\\in.txt","r",stdin);1
   ```

2. memset(a,0,sizeof(a)); //数组的初始化。一般定义一个数组都要初始化 
   数组定义int a[10] 为全局变量的话，其全部元素默认赋值为0；整型数据默认为0，字符串默认为空。

3. \#define max 0x0ffffff; //max 为正无穷 
   \#define min -0x0ffffff;

4. 多组测试数据使用 while(n–){ 程序 }

5. 一般用C语言节约空间，要用C++库函数或STL时才用C++; 
   cout、cin和printf、scanf最好不要混用。而且需要注意的是，如果题目是大规模数据的输入输出，尽量使用printf和scanf，数据量一大，速度明显比c++的输入输出快。 输出1000000个数据，cout 大概用6s printf 用了0.562s

6. 有时候int型不够用，可以用long long或`__int64型(两个下划线__)`。 
   值类型表示值介于 -2^63 ( -9,223,372,036,854,775,808) 到2^63-1(+9,223,372,036,854,775,807 )之间的整数。

   ```
   printf("%I64d",a);
   printf("%lld",a);12
   ```

7. OJ判断是只看输出结果的。 
   所以大部分题处理一组数据后可以直接输出，就不需要用数组保存每一个Case的数据。

8. 纯字符串用puts()输出，会增快速度。

9. 先用scanf()，再用gets()会读入回车。scanf(“%c%c”,&c1,&c2) 后者会读入空格和回车；要使用getchar()吸收空格和回车的录入，使用c语言读字符和字符串一定要十分小心。尽量写好就自己输出一下看看是否是自己需要的值被读入。

10. 读到文件的结尾，程序自动结束 
    while( ( scanf(“%d”,&a) ) != -1 ) 
    while( ( scanf(“%d”,&a) ) != EOF) 
    while( ( scanf(“%d”,&a) ) == 1 ) 
    读到一个0时，程序结束 
    while( scanf(“%d”,&a) &&a) 
    读到多个0时，程序结束 
    while( scanf(“%d%d%d”,&a,&b,&c)&&a+b+c )，该方法不能读取负值。

11. 圆周率=cos(-1.0) 自然对数=exp(1.0)

12. 如果要乘或除2^n,用位移运算速度快。`a>>n;a<<n;` 如：求n^m 时间复杂度log(m)

    ```
    int calc(int n,int m){
        int re=1;
        while(m){
           if(m&1)
              re*=n;
           n*=n;
           m>>=1;
        }
        return re;
    }12345678910
    ```

13. 定义数组时，数组大小最好比告诉的最大范围大一点。字符数组大小必须比字符串最大长度大1。

14. 习惯使用三目运算符

    ```
    int max(int a,int b){return a>b?a:b;}
    int gcd(int m,int n){return n?gcd(n,m%n):m;}
    int abs(int a){return a<0?-a:a;}123
    ```

15. 有的题数据范围小但是计算量大可以用打表法，先把结果算出来保存在数组里，要用时直接取出来。

16. 大概的计算自己程序的时间的方法：引入头文件：`#include<time.h>` 主函数末尾添加上一句`cout<<(double)clock()/CLOCKS_PER_SEC;`但是输入必需重定向，不然会计算输入数据等待时间。

17. runtimeerror 一般这种错误都是下标越界或者是未赋值的变量就直接使用这两种情况，一定要好好排查，不仔细一般找不出来。另外还有在函数内开了一个比较大的数组，使堆栈耗尽所以出错。 这个是后来加上的
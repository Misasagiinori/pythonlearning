# python学习第四周  
## 程序分支结构  
- **单分支结构**  
if <条件>：  
&ensp;&ensp;语句块  
实例  
guess = eval(input())
if guess == 99 :
  print("猜对了")
- **二分支结构**  
if <条件>：  
&ensp;&ensp;语句块一  
else:  
&ensp;&ensp;语句块二  
紧凑方式：适用于简单表达式的二分支结构  
<表达式一>if<条件>else<表达式二>  
guess = eval(input())
print("猜{}了".format("对" if guess == 99 else "错"))  
注意：是表达式而非语句，不支持语句，没有复制的过程  
- **多分支结构**  
if <条件>：  
&ensp;&ensp;语句块一  
elif：  
&ensp;&ensp;语句块二  
......  
else:  
&ensp;&ensp;语句块三  
注意多条件之间的包含关系，注意变量取值范围的覆盖  
- **程序的分支结构**  
条件判断的操作符  
用于条件组合的保留字    x and y; x or y; not x;  
- **程序的异常处理**  
num = eval(input("请输入一个整数："))
print (num**2)  
问题在于如果不是输入整数，比如输入一个字符串，便会出现异常，python中提供了异常的处理机制  
  - 异常处理的基本使用  
try:  
&ensp; <语句块一>  
except<异常类型>:  
&ensp;<语句块二>   
上述例子在开头加一行 try:   
except:  
&ensp;print("输入不是整数")  
或者  
except NameError:  
&ensp;print("输入不是整数")  
标注异常类型后，只相应这个异常，异常类型名字是python中预定义的  
  - 异常处理的高级使用  
try:  
&ensp; <语句块一>  
except<异常类型>:  
&ensp;<语句块二>  
else:  
&ensp;<语句块三>  
finally:  
&ensp;<语句块四>  
finally 对应语句块四是一定回去执行的，无论前面是否发生异常  
else对应的语句块三是在不发生异常时执行的  
## 实例5:身体质量指数bmi  
- **bmi问题分析**  
衡量肥胖与健康的指数 BMI= 体重/身高的平方  
- **实例讲解**  
难点在于同时输出国际和国际的对应的分类：思路一分别计算，思路二混合计算  
#CalBMIV3.py
height,weight = eval(input("请分别输入身高(m)体重(kg)，以逗号隔开："))
bmi = weight / pow(height,2)
print ("BMI数值为:{:.2f}".format(bmi))
who,nat = "",""
if bmi < 18.5:
    who,nat = "偏瘦","偏瘦"
elif 18.5<=bmi<24:
    who,nat = "正常","正常"
elif 24<=bmi<25:
    who,nat = "正常","偏胖"
elif 25<=bmi<28:
    who,nat = "偏胖","偏胖"
elif 28<bmi<30:
    who,nat = "偏胖","肥胖"
else:
    who,nat = "肥胖","肥胖"
print ("BMI指标为：国际'{0}',国内'{1}'".format(who,nat))  
- **BMI举一反三**  
关注多分支结构的组合，覆盖是重要的问题，警惕程序可运行，但结果不正确；阅读代码，先看分支  
## 程序的循环结构  
- **遍历循环**  
for <循环结构> in <遍历变量>:  
&ensp; <语句块>  
从遍历变量中逐一提取元素放在循环结构里  
  - 计数循环，计数n次  
for i in range(n):  
&ensp;<语句块>  
遍历由range()函数产生的数字序列，循环变量 i 可使用也可不适用  
for i in range(M,N,K):
  - 字符串遍历循环  
for c in s：  
&ensp;<语句块>    
s是字符串，遍历每个字符  
  - 列表遍历循环 
for c in ls:  
&ensp;<语句块>  
  - 文件遍历循环  
for line in fi:  
fi是文件标识符，遍历其每行，产生循环  
- **无限循环**  
由条件控制的循环运行方式  
while <条件>:  
&ensp;<语句块>  
循环执行永不退出可以用crtl+c  
- **循环控制保留字**  
break; continue  
break指跳出并结束当前整个循环，执行循环后的语句  
continue结束当次循环，并继续执行后续次数的循环  
两者都可以和for和while这样的循环搭配使用  
for c in "python":
  if c == "t":
    continue
  print(c,end = ",")  
break仅跳出当前最内层循环
- **循环的高级用法**  
循环的扩展：循环与else  
for <循环变量> in <遍历结构>:  
&ensp;<语句块一>  
else:  
&ensp;<语句块二>  
或者  
while<条件>:  
&ensp;<语句块一>  
else:  
&ensp;<语句块二>  
当循环没有被else语句退出时，执行else语句块  
else语句作为正常完全循环的一种奖励  
for c in "python":
  if c == "t":
    continue
  print(c,end=" ")
else:
  print("正常退出")  
## 模块三：random库的使用  
- **random库的概述**  
random库是使用随机数的python标准库  
计算机无法产生真正的随机数，但可以产生伪随机数  
伪随机数：采用梅森旋转算法产生的伪随机序列中元素  
random库包括两类函数，常用的有8个：基本随机数函数 seed();random() 扩展随机函数 ranint() getrandbits() uniform() randrange() choice() shuffle()  
- **基本随机函数**  
python中的随机数使用随机数种子产生  
随机数种子通过梅森旋转算法产生确定的随机序列  
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/%E5%9F%BA%E6%9C%AC%E9%9A%8F%E6%9C%BA%E6%95%B0%E5%87%BD%E6%95%B0.jpg?raw=true)  
import random  
random.seed(10)  
random.random()  
0.5714025946899135  
- **扩展随机数函数**  
random()只能产生0到1之间的小数  
randint(a,b)生成一个a到b之间的整数  
randrange(m,n,k)生产一个[m，n]之间以k为步长的随机整数  
getrandbits(k) 生成一个k比特长的随机整数  
uniform(a,b)生成ab之间的随机小数  
choice(seq) 从序列seq中随机选择一个元素  
shuffle(seq) 对序列seq中的元素进行随机排列，返还打乱后的顺序  
 s= [1,2,3,4,5,6,7,8];random.shuffle(s);print(s)  
如果非常有必要将代码放在一行中，代码可以用分号隔开，实际编写中，建议分行  
## 实例6：圆周率的计算  
- **圆周率计算问题分析**  
数学公式  
蒙特卡罗方法：对于一个区域面积进行洒点  
- **圆周率计算实例讲解**  
#CalPiV1.py
pi = 0 
n = 100
for k in range(n):
  pi+=1/pow(16,k)*(\
    4/(8*k+1)-2/(8*k+4)-\
    1/(8*k+5)-1/(8*k+6))
print("圆周率的值是{}".format(pi))  
增加\使代码换行，增加可读性  
#CalPiV2.py
from random import random
from time import perf_counter
n = 100*1000
m = 0.0 
start = perf_counter()
for i  in range(1,n+1):
    x,y = random(),random()
    s = x**2 + y **2
    if s <= 1.0:
        m+=1
pi = m/n*4
print("圆周率的值是{}".format(pi))
print("运行时间是{:.5f}s".format(perf_counter()-start))  
- **圆周率计算的举一反三**  
理解方法思维：数学思维，找到公式，用公式求解。  
计算思维：抽象一种过程，用计算机自动化求解  
谁更准确：四色定理不能用数学思维  
程序运行时间获取以及分析的方法，理解运行时间的分布，80%的时间只消耗在不到10%的代码上，这代码就是循环代码，初步掌握程序性能分析方法。  
计算问题扩展：求解特定图形的面积
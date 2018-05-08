# 函数与代码复用
## 函数的定义及使用
- **函数的理解及定义**  
函数是一段具有特定功能，可重复使用的语句组，一种功能的抽象，表达特定的功能  
两个作用：降低编程难度与代码复用  
def <函数名>(参数0个或多个):  
&ensp;<函数体>  
return <返回值>  
def fact(n)
s =1
for i in range(1,n+1):
  s *=i
return s  
函数在定义时，所给定的参数是一种占位符  
函数定义后，不经调用，在程序中是不会被执行的  
函数在定义时，参数是输入，函数体是处理，结果是输出（IPO），完整代码的一种封装  
- **函数的使用及调用过程**  
调用是运行函数代码的方式，函数调用后得到返回值  
如上面定义的函数调用 fact（10）  
- **函数的参数传递**  
函数可以有参数，也可以没有，但必须要保留()  
可选参数：函数定义时可以为某些参数选定默认值  
def <函数名>(非可选参数，可选参数)  
python要求所有函数定义时，可选参数必须放在非可选参数后面  
可变参数传递：函数定义时可以设计可变数量参数，即不确定参数总数量   
def <函数名>(确定参数，*b):  
用*b，*c，*a等表示不确定参数  
def fact(n,*b)
s =1
for i in range(1,n+1):
  s *=i
for item in *b:
  s*=item
return s  
参数的传递有两种方式  
函数调用时，参数可以按照位置或名称方式传递  
def fact(n,m=1)
s =1
for i in range(1,n+1):
  s *=i
return s//m  
调用时，一种方式fact(5,10)，这种事按照参数的位置来传递；或者fact(m=10,n=5)按照参数的名称来传递  
- **函数的返回值**  
函数可以返回0个或多个结果，使用保留字return来传递返回值  
函数可以有返回值，也可以没有，可以有return，也可以没有  
return可以传递0个，也可以传递多个值  
a,b,c = fact(10,5) 将函数值分别返回给abc三个变量  
- **局部变量与全局变量**  
程序中全局变量，在函数中使用的变量是局部变量  
n,s = 10,100
def fact(n):
    s = 1
    for i in range(1,n+1):
        s*=i
    return s
print(fact(n),s)  
规则一：局部变量与全局变量是不同的变量  
局部变量是函数内部的占位符，即使与全局变量重名，也不同，函数运行结束后，局部变量将被释放，可使用global保留字在函数内部使用全局变量  
n,s = 10,100
def fact(n):
    global s
    for i in range(1,n+1):
        s*=i
    return s
print(fact(n),s)  
规则二：局部变量为组合数据类型，且未创建，等同于全局变量  
列表有一个特点，必须使用[]才能真实地创建  
ls = ["f","F"]
def func(a):
    ls.append(a)
    return
func("c")
print(ls)  
ls在函数中未创建，可以使用函数外的全局变量  
组合数据类型在python中是用指针来体现的，所以函数中如果没有创建，那么，其使用的是指针，其修改的就是全局变量  
- **lambda函数**  
lambda函数返回函数名作为结果  
lambda函数是一种匿名函数，即没有函数的名字  
lambda函数用于简单的，能在一行也表达的函数  
<函数名>=lambda<参数>:<表达式>  
f = lambda x,y:x+y  
f = lambda : "这是lambda函数"  
谨慎使用lambda函数，lambda函数主要用作一些特定的函数或方法的参数；lambda函数有一些固定的使用方式，后面学习。  
## 实例7:七段数码管绘制  
- **问题分析**  
七段小的数码管构成的一个数字8，交通灯  
turtle绘图体系；  
- **实例讲解上**  
步骤一：绘制出单数数字对应的数码管；步骤二：获得一串数字，绘制对应的数码管；步骤三：获得当前系统对应的时间，绘制对应的数码管  
import turtle
def drawline(draw): #绘制单断数码管
    turtle.pendown() if draw else turtle.penup()
    turtle.fd(40)
    turtle.right(90)
def drawdigit(digit): #根据绘制七段数码管
    drawline(True) if digit in [2,3,4,5,6,8,9] else drawline(False)
    drawline(True) if digit in [0,1,3,4,5,6,7,8,9] else drawline(False)
    drawline(True) if digit in [0,2,3,5,6,8,9] else drawline(False)
    drawline(True) if digit in [0,2,6,8] else drawline(False)
    turtle.left(90)
    drawline(True) if digit in [0,4,5,6,8,9] else drawline(False)
    drawline(True) if digit in [0,2,3,5,6,7,8,9] else drawline(False)
    drawline(True) if digit in [0,1,2,3,4,7,8,9] else drawline(False)
    turtle.left (180)
    turtle.penup() #为后续数字确定位置
    turtle.fd(20)  #为后续数字确定位置
def drawdate(date):
    for i in date:
        drawdigit(eval(i)) #通过eval将数字变成整数
def main():
    turtle.setup(800,350,200,200)
    turtle.penup()
    turtle.fd(-300)
    turtle.pensize(5)
    turtle.pencolor('purple')
    drawdate('20181010')
    turtle.hideturtle()
    turtle.done()
main()      
- **实例讲解下**  
步骤三：获得当前系统的时间，绘制对应的数码管  
增加七段数码管之间的线条间隔  
使用time库获得时间  
获得年月日标记，颜色不同  
使用turtle.write()来绘制一个具体的汉字    
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/七段数码管显示.png?raw=true)
- **举一反三**  
理解方法思维：模块化思维，确定模块接口，封装功能；规则化思维，抽象过程为规则，计算机自动化执行；化繁为简，将大功能拆分为小功能，分而治之。  
## 代码复用与函数递归  
- **代码复用与模块化设计**  
代码复用：把代码当成资源抽象，代码资源化，程序代码是一种表达计算的资源；代码抽象化，使用函数赋予代码更高级别的定义；代码复用，同一份代码在需要时可以重复使用  
函数和对象是代码复用的两种主要形式；函数将代码命名，在代码层面建立初步抽象；  
对象：属性和方法 a.b和a.b(),在函数之上再次组织进行抽象  
模块化设计：通过函数或对象分装将程序划分为模块或模块间的表达；具体包括主程序、子程序和子程序之间的关系  
分而治之，一种分而治之、分层抽象、体系化的设计思想  
模块化设计：紧耦合以及松耦合  
模块内部紧耦合，模块之间松耦合  
- **函数递归的理解**  
函数定义中调用函数自身的方式就是递归
n! = n(n-1)!  
两个关键特性：链条和基例  链条：计算过程中存在递归链条 基例：存在一个或多个不需要再次递归的基例  
递归的定义：类似数学归纳法，当n取第一个值n0的时候，命题成立，假使当nk时命题成立，证明当nk+1时，命题也成立，递归是数学归纳法在编程中的体现  
- **递归函数的调用过程**  
函数+分支语句：递归本身就是一个函数，需要函数定义方式描述  
函数内部采用分支语句对输入参数进行判断 
基例和函数分别表达  
def fact(n):
    if n == 0 :
        return 1
    else:
        return n*fact(n-1)
print(fact(5))  
递归的调用过程就是函数的运算过程，函数是一个模版，在对每一个参数运算时，将函数放在内存里，在遇到一个新的函数时，会再开辟一个内存空间，其所调用的函数是自身不同的复制版本。  
- **函数递归实例解析**  
字符串反转，将字符串s反转后输出 s[::-1]  
def rvs(s):
    if s == "":
        return s
    else:
        return rvs(s[1:])+s[0]

print(rvs("edfrg"))  
斐波那契数列  
def feb(n):
    if n ==1 or n == 2:
        return 1
    else:
        return feb(n-1)+feb(n-2)
def nat(s):
    ls = []
    for i in range(1,s+1):
        ls.append(feb(i))
    return ls
       


print(feb(11),nat(11))  
汉诺塔问题：  
小的圆盘必须永远在大的圆盘上面  
count = 0
def hanoi(n,src,dst,mid):
    global count
    if n ==1:
        print("{}:{}->{}".format(n,src,dst))
        count+=1
    else:
        hanoi(n-1,src,mid,dst)
        print("{}:{}->{}".format(n,src,dst))
        count+=1
        hanoi(n-1,mid,dst,src)

hanoi(3,'开始的柱子','最后的柱子','中间的柱子')
print(count)
## 模块4:PyInstaller
- **PyInstaller库的基本介绍**  
将.py源代码转换成无需源代码的可执行文件  
PyInstaller是第三方库，使用前需要额外安装  
pip install pyinstaller  
- **使用**  
-h：查看帮助  
--clean：清除打包过程中的临时文件  
-D --onedir:默认值，生成dist文件夹  
-F --onefile：在dist文件夹中生成独立的打包文件  
-i<图片文件名.ico>：指定打包程序使用的图标文件
pyinstaller -i <> -F  
## 实例8：科赫雪花小包裹
- **问题分析**  
科赫雪花，高大上的分形几何，分形几何是一种具有迭代关系的几何图形，广泛地存在于自然界中。分形几何中有一种特殊的曲线叫做科赫曲线，也叫做雪花曲线  
用python绘制科赫曲线  
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/%E7%A7%91%E8%B5%AB%E6%9B%B2%E7%BA%BF%E7%A4%BA%E6%84%8F%E5%9B%BE.jpg?raw=true)
用python绘制科赫雪花  
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/科赫雪花.png?raw=true)  
- **举一反三**  
修改分形几何的绘制结束  
修改科赫曲线的基本定义及旋转角度  
康托尔集，谢尔宾斯基三角形，门格海绵，龙形曲线，空间填充曲线，函数递归的深入应用



# 第二周课程导学
- **保留字**
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/python%E4%BF%9D%E7%95%99%E5%AD%97.png?raw=true)
# python 基本图形绘制  
- **深入理解python语言**  
- **实例2，python蟒蛇绘制**  
- **模块一：turtle库**  
- **turtle程序语法分析**  
***
# 深入理解python语言
- **计算机技术的演进**  
1946-1981 计算机系统结构时代  第一台计算机到第一台ibm计算机  计算能力问题  
1981-2008 网络和视窗时代 2008安卓操作系统的诞生 由pc向移动时代转换  交互问题  
2008-2016 复杂信息系统时代 计算机打败国际围棋的冠军  数据问题  
2017-人工智能时代 新计算时代 人类问题

- **编程语言的多样初心**    
人生苦短 我学python python归python c归c 比如涉及操作系统 封装打包  
java針對特定開發  
html、css、js 不可替代的前端技术 全栈能力  
R/Go/matlab 特定领域  
*关注工具变革的力量*
- **python语言的特点**  
python语言是通用语言  
python语法具有强制可读性，比如缩进  
较少的底层语法元素  
多种编程方式  
支持中文字符  
代码量是c语言的10% 13w开源库 避免重复造轮子 快速开放 跨平台
- **超级语言的诞生记**  
机器语言 二进制语言  
汇编语言 二进制代码对应的助记符 汇编器 与cpu型号对应  
高级语言 与cpu型号无关 编译后运行  
超级语言 庞大的计算生态 集成开发 如python   
***
# python蟒蛇绘制实例   
- **用程序绘制一条蟒蛇**  
问题一：计算机绘图的基本原理 一段程序为什么能够产生窗体，为什么能够在窗体上绘制图形  
问题二：python蟒蛇绘制从哪里开始？ 如何绘制一条线、弧形、蟒蛇
- **实例二：python蟒蛇绘制**  
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/%E8%9F%92%E8%9B%87%E7%BB%98%E5%88%B6%E7%A8%8B%E5%BA%8F.jpg?raw=true)
import turtle 程序关键 引入海龟库  
- **python蟒蛇绘制举一反三**  
各类图像绘制问题的代表  圆形 五角星 卡通形象 国旗等
# 模块一：turtle库的使用
- **turtle库的概述**  
turtle库是turtle绘图体系的python实现  
turtle：1969年诞生，用于程序设计入门的绘图方式  
标准库和第三方库 库 Library 包 Package 模块 Module，统称模块  
turtle的原理：想象有一只海龟，位于窗体的正中心，在画布上游走，走过的轨迹成绘制的图形
- **turtle绘图窗体布局**  
在窗体中使用的最小单位是像素 电脑左上角是（0，0） 窗体的左上角是turtle绘图体系的坐标原点  
turtle.setup(wifth,height,startx,starty)启动窗体的大小及位置 4个参数中后两个是可选的，不指定会默认该窗口在屏幕的正中心  
- **turtle空间坐标体系**  
绝对坐标：turtle.goto(x,y)让在任何位置的海龟到达某一个坐标位置  
海龟坐标：turtle.fd(d)向海龟正前方向 turtle.bk() turtle.circle(r,angle)以海龟当前位置左侧的某个点为圆心进行曲线运行  
- **turtle角度坐标体系**  
turtle.seth(angle)改变当前海龟的行进角度，只改变行动方向  
turtle.seth(45) 朝向45度  
turtle.right(angle) turtle.left(angle)  
- **RGB色彩体系**  
RGB：红绿蓝三种颜色通道颜色组合 turtle默认使用RGB小数值 turtle.color(mode) 1.0:小数值模式 255：整数模式  
# turtle程序语法元素分析  
- **库引用与import**  
a.b的代码风格  
库引用：扩充python程序功能的方式：使用import保留字  
使用from和import两个保留字来完成，from turtle import* from turtle import <函数名> 不需要再加库名  
两种方法比较：第一种方法不会出现函数名重复的问题，比如程序很长，引用了很多的库  
import更多的方式，使用import和as保留字 import<库名>as<库别名> 给库起个小名
- **turtle画笔控制函数**  
画笔出现后一直有效，一般成对出现  
turtle.penup():别名 turtle.pu() 抬起画笔，海龟在飞行  
turtle.pendown():别名 turtle.pd()落下画笔，海龟在爬行  
海龟用penup飞行到某位置，在通过pd开始绘图  
turlte.pensize(width): 也可以turtle.width(width) 画笔宽度  
turtle.pencolor(color):修改颜色  
color有三种形式：颜色字符串 turtle.pencolor("purple") 字符串形式，小写 RGB的小数值，RGB的元组类型 turtle.pencolor((1.6,1.6,1.6))  
- **turtle运动控制函数**  
控制海龟行进方向，直线或曲线  
turtle,foward(d):别名 turtle.fd(d)  向前行进像素   
turle.circle(r,extend=none):根据半径r绘制extend角度的弧形 默认圆心在海龟左侧r处 extend 绘制角度，默认是360度整圆
- **turtle方向控制函数**  
控制海龟面对方向：绝对角度和海龟角度  只改变方向
turtle.setheading(angle) turtle.seth()  
turtle.left() turtle.right()  
- **循环语句与range函数**  
for<>in range (<>)  
for i in range (5)  
&ensp;&ensp;print (i) 0 1 2 3 4  
print 中间加逗号会有空格 如 print（"hello:",1） hello: 1  
range() 函数产生循环计数序列  
range(N) 产生0到N-1的整数序列，共N个  
range(M,N) 从M开始到N-1的整数序列，共N-M个  
turtle.done()运行后不会退出，需要手工退出

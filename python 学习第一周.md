# python 学习第一周
## 程序设计基本方法
- 计算机和程序设计  
1.功能性  
2.可编程性  
  - 摩尔定律
  - 程序设计语言
   
- 编译和解释  
**源代码**：人类可以阅读
**目标代码**：只有机器可以阅读  
*编译和解释的区别 整体和逐条 静态语言和动态语言 C语言和python java php*
- 程序的基本编写方法  
IPO：input process output  
计算机只能解决计算问题，因此要分析问题的计算部分  
划分问题的功能边界 ipo  
设计算法  
编写程序  
调试测试  
升级维护  
- 计算机编程  
计算思维 区别逻辑思维和实证思维  
解决问题、用户体验和执行效率  
掌握基本语法 思考程序结构 练习实践
## python开发环境配置
**两种编程方式** 交互式和文件式  
绘制同切圆  
import turtle  
turtle.pensize(2)  
turtle.circle(4)  
turtle.circle(8)  
turtle.circle(20)

画五角星  
from turtle import *   导入turtle库  
pensize(2)粗细  
color('red','red')颜色  
begin_fill()  开始填充  
for i in range (5)  划线次数  
&ensp;&ensp;fd(200)  forward画笔向前200像素  
&ensp;&ensp;rt(144)  right顺时针144度  
end_fill()  停止填充  
done()
## 实例1：温度转换
**摄氏度和华氏度**  
理解1：直接将温度数值进行转换  
理解2：将温度的声音或图像进行理解和转换  
理解3：监控温度信息发布渠道，自动获取转换发布

温度体系需要标明温度体系F\C  
#timeconvert  
tempstr = input("please inset:")  python2用raw_input  
if tempstr[-1] in ['F','f']:  
    c = (eval(tempstr[0:-1])-32)/1.8  
    print("the convert is {:.2f}c".format(c))  
elif tempstr[-1] in ['c','C']:  
    f = 1.8*eval(tempstr[0:-1]) +32  
    print("the convert is{:.2f}f".format(f))  
else:  
    print("wrong")  
    
*温度转换是其他转换的代表*

## python程序语法元素分析
**程序的格式框架**  
- 不同的颜色是代码高亮 编程的色彩辅助系统
- 缩进是空白区域，表示格式框架 单层和多层 严格明确 所属关系 长度一致
- 注释，辅助性文字，不被执行，#：单行注释；'''做开头结尾，多行注释  

**命名和保留字**  
- 变量：程序中用于保存和表示数据的占位符号  =赋值符号
- 命名：关联标识符的过程  
  - 大小写字母、数字、下划线和汉字等
  - 注意：大小写敏感，首字母不能是数字，不能与保留字相同
- [保留字](https://raw.githubusercontent.com/Misasagiinori/pythonlearning/master/python%E4%BF%9D%E7%95%99%E5%AD%97.png):被语言内部定义并保留的字符 33个保留字 保留字也大小写敏感，如大写的IF是变量而非保留字，True、False、None首字母是大写的。

**数据类型**
- 数据类型：字符串、整数、浮点数、列表  
- 例如：10，011，101 整数：10011101；字符串：“10，011，101”；列表类型[10,011,101]
- 字符串：由零个或多个字符组成的有序字符序列，以一对单引号或双引号表示，可以对其中的字符进行索引，字符串的索引标号从0开始
- 字符串的序号：正向递增序号和反向递减序号  
  请|输|入|数|字  
  --|--|--|--|--
  0 |1 |2 |3 |4
  -5|-4|-3|-2|-1  
- 使用[]获得字符串中一个或多个字符
  - 索引 <字符串>[M]
  - 切片 <字符串>[M:N]
- 数字类型：整数和浮点数
- 列表类型：[M，N，] 使用保留字in判断元素是否在列表中

**语句与函数**
- 赋值语句：由赋值符号构成的代码 =  类型保留
- 分支语句：判断条件 if elif else 条件判断语句 ifxxx： 冒号是语法的一部分，不能省略
- 函数：input eval print

**python程序的输入输出**
- input()从控制台获得用户输入 timstr = input ("请输入") 括号里是提示性的信息
- print() 输出函数 
   - print("输入格式错误")
   - print()函数***格式化*** print("温度是{:.2f}c".format(c)) {}是槽,{:.2f}将format函数中的变量值填充至此时取到小数点后两位
- eval() 评估函数 去掉参数最外侧引号并执行余下语句 eval（“1”）得1 eval（'"1+2"'） 得1+2
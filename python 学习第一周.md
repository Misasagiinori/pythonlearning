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
## python程序语法元素分析
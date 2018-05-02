# python学习第三周  
## 第三周课程导学  
**基本数据类型**
- 数字类型及其操作  整数浮点数复数
- 实例3天天向上的力量
- 字符串类型及其操作
- 模块2：time 库的使用
- 实例4：文本进度条  

**方法论**  python语言数字及字符串类型  
**实践能力**  初步学会编程进行字符类操作
## 数字类型及其操作
- **整数类型**  
与数学中整数的概念一致 pow(x,y) 计算x的y次方  
4种进制表现形式 十进制 二进制（0b或0B开头） 八进制（0o或0O开头）十六进制（0x或0X开头）  
- **浮点数类型**  
与数学中实数的概念一致  
浮点数取值范围和精度都存在限制，但常规计算可以忽略不计  
取值范围-10^308 - 10^308 精度10^-16  
浮点数间的运算存在不确定尾，不是bug 0.1+0.2 = 0.3000004  
0.1  53位二进制来表示小数部分 无限  
## 实例三：天天向上的力量  
- **天天向上的力量问题分析**  
基本问题：持续的价值  
一年365天，一天进步1%，累计进步多少  
一年365天，一天退步1%，累计退步多少  
需求分析：似乎可以数学公式 退步进步交叉  
- **天天向上的力量第一问**  
一年365天，每天进步1‰，累计进步多少1.001**365  
#DayDayUpQ1.py  
dayup = pow(1.001,365)  
daydown = pow(0.999,365)  
print ("向上：{:.2f},向下：{:.2f}".format(dayup,daydown))  
- **天天向上的力量第二问**  
5‰和1%的力量 定义一个新的变量  
#DayDayUpQ2.py  
dayfactor = 0.005  
dayup = pow(1+dayfactor,365)  
daydown = pow(1-dayfactor,365)  
print("dayup:{:.2f},daydown:{:.2f}".format(dayup,daydown))  
- **天天向上的力量第三问**  
工作日的力量  
#DayDayUpQ3  
dayup = 1.0  
dayfactor = 0.01  
for i in range (365):  
&ensp;if i%7 in [6,0]:  
&ensp;&ensp;dayup = dayup*(1-dayfactor)  
&ensp;else:  
&ensp;&ensp;dayup = dayup*(1+dayfactor)  
print("工作日的力量：{:.2f}".format(dayup))  
- **工作日的努力**  
b君工作日多么努力才能达到a君的效果    
函数，使用保留字def  
#DayDayUpQ4  
def dayUp(df):
    dayup = 1
    for i in range (365):
      if  i%7 in [6,0]:
        dayup = dayup*(1-0.01)
      else:
        dayup = dayup*(1+df)
    return dayup
dayfactor = 0.01  
while dayUp(dayfactor)<37.78:
  dayfactor += 0.001  
print("工作日的努力参数是：{:.3f}".format(dayfactor))
*grit:perservance and passion for long-term goals*  
- **天天向上的力量举一反三的结果**  
试错

## 字符串类型及其操作  
- **字符串类型的表示**  
字符串：由0个或多个字符组成的有序字符序列  
字符串由一对单引号或双引号表示  
有序序列，可对其中字符进行索引  
字符串由两类共四种表示方式  
第一类由一对单引号或双引号表示，仅用于单行字符串  
第二类由一对三引号（单或双）来表示，可表示多行字符串  
其实，在python并没有真正提供多行注释的方式，三单引号构成的就是字符串，其没有给到任何变量，可以当成注释  
如果希望在字符串中既出现单双引号则使用三引号  
字符串的序号：正向递增以及反向递减  
使用[]来获得字符串中一个或多个字符 索引 <字符串>[M] 切片 <字符串>[M:N]  
切片的高级用法 使用[M:N:K]根据步长对字符串进行切片  
M缺失表示至开头，N缺失表示至结尾 [::-1] 步长-1将字符串逆序  
字符串的特殊字符：转义符\表示特许字符的本意"这里有个双引号(\")"  
转义符形成一些组合表达一些不可打印的含义  
"\b"回退 "\n"换行 "\r"回车（光标移动到当前行行首）  
- **字符串操作符**  
x+y 链接两个字符串  
n*x x*n 将字符串x复制n次  
x in s 如果x是s的字串，则返回true，否则返回false  
例子：获取星期字符串，输入1-7的整数  
#WeekNamePrintV1.py
weekStr = "星期一星期二星期三星期四星期五星期六星期日"
weekId = eval(input("请输入星期数字(1-7):"))
pos = (weekId-1)*3
print(weekStr[pos:pos+3])  
或者    
#WeekNamePrintV2.py
weekStr = "一二三四五六日"
weekId = eval(input("请输入星期数字(1-7):"))
print("星期"+weekStr[weekId-1])  
- **字符串处理函数**  
一些以函数形式提供的字符串处理形式  
len(x) 计算字符串长度  
str(x) 转换成字符串类型  
hex(x) oct(x) 形成十六进制或八进制字符串  
chr(u) x为Unicode的编码，返回其对应的字符  
ord(x) x为字符，返回其对应的Unicode编码  
Unicode编码：Python字符串的编码形式，统一字符编码，从0到1114111（0x10FFFF）空间，每个编码对应一个字符，用一套编码纳入世界上所有语言的字符  
>>>"1+1 = 2" + chr(9801)
'1+1 = 2♉'
>>> ord("我")
25105  
- **字符串处理方法**  
方法在编程中时专有名词，特指a.b()风格中的b；方法本是也是函数，只是与a有关,a是对象，面向对象中的专有名词  
str.lower() str.upper()返回字符串的副本，全部字符为大写或小写  
str.split(sep = none)返回一个列表，由str根据被sep分隔的部分组成  
str.count(sub)返回子串sub在字符串中出现的次数  
str.replace(old,new)返回字符串副本，所有old子串被替换成new  
str.center(width,fillchar)字符串str根据位置居中，fillchar可选两边填充  
str.strip(char)去除字符串中左右两侧出现的char中预定义的字符  
str.join(iter)在变量除最后元素外每个元素后面增加一个字符串  
- **字符串类型的格式化**  
格式化是对字符串进行格式表达的方式  
字符串格式化使用.format()方法  
模板字符串.format(逗号分隔的参数)  
槽，相当于占位信息符，用{}表示，  
"{}:计算机的{}是{}".format("2010","answer","15")  
字符串中槽的顺序与format中字符串的顺序一致。  
可以在槽中的数字指定需要添加参数的顺序  
format方法的格式控制  
槽内部对格式化的配置方式  
{参数序号:格式控制标记}  
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/槽内部的格式化配置方式.png?raw=true)  
>>> "{0:=^20}".format("python")
'=======python======='  
上例子即为填充等号居中对齐，20个字符  
## 模块二：time库的使用  
- **time库的使用**  
time库是python中处理时间的标准库  
计算机时间的表达；获取系统时间并格式化输出；系统级精准计时功能，用于程序性能分析  
import time  
time.b()  
time库包括三类函数：时间获取，time() ctime() gmtime();时间格式化：strftime() strptime();程序计时：sleep() perf_counter()  
- **时间获取**  
time():获取当前时间戳，即计算机内部时间值，浮点数,从1970年0点01分，到当前时间点以秒为单位的时间值  
ctime():以易读的方式获取，返回字符串  
gmtime():获取计算机可以处理的时间格式  
>>> time.gmtime()
time.struct_time(tm_year=2018, tm_mon=4, tm_mday=27, tm_hour=14, tm_min=45, tm_sec=12, tm_wday=4, tm_yday=117, tm_isdst=0)  
- **时间格式化**  
类似字符串格式化，需要有格式化模版  
展示模版由特定的格式化控制符组成  
strftime(tpl,ts):tpl是格式化模版字符串，用来定义输出效果，ts是计算机内部时间类型变量  
t= time.gmtime()  
time.strftime("%Y-%M-%D %H:%M:%S",t)  
time.strptime 与strftime是互补的关系 反格式化 
time.strptime(str,"%Y-%M-%D %H:%M:%S")  
- **程序计时应用**  
测量起止动作动作所经历时间的过程  
测量时间 perf_counter()获取cpu级别的精准时间技术值，单位是秒，连续调用计算差值  
 start = time.perf_counter()
 end = time.perf_counter()
 end-start
22.32089270399956  
产生时间 sleep(s) 让程序休眠s秒时间  
def wait():
  time.sleep(3.3)
wait() 程序等待3.3秒再退出  
## 实例四：文本进度条  
- **进度条问题分析**  
文本进度条：采用字符串形式打印可以动态变化的文本进度条  
进度条需要在一行中根据程序运行逐渐变化  
模拟一个持续的进度，与时间关联  
如何获得文本进度条的变化时间：采用sleep()模拟一个持续的进度  
- **文本进度条简单的开始**  
#TextProBarV1.py
import time
scale = 10
print("-----执行开始-----")
for i in range (scale+1):
  a= '*'*i
  b= '.'*(scale-i)
  c= (i/scale)*100
  print("{:^3.0f}%[{}->{}]".format(c,a,b))
  time.sleep(0.1)
print("-----执行结束-----")  
- **文本进度条的单行动态刷新**  
单行动态刷新：刷新的本质是用后打印的字符覆盖之前的字符；不能换行，print()需要被控制；要能回退，打印后光标回到之前的位置\r,刷新的关键是\r  
#TimeProBarV1.py
import time
for i in range (101):
  print("\r{:3}%".format(i),end="")
  time.sleep(0.1)  
print()默认输出字符串后再输出一个换行，由于我们设定end为空字符，因此不会再增加一个换行，只会将光标停留在当前字符串后  
\r则是使打印字符串前，光标退回当前行行首  
在idle环境中所有信息都被展示，而没有刷新，不是程序出错，因其时开发环境，\r被屏蔽了，使用命令行  
- **文本进度条实例完整效果**  
#TextProBarV3.py
import time
scale = 50
print("执行开始".center(scale//2,"-"))
start = time.perf_counter()
for i in range (scale+1):
  a = "*"*i
  b = "."*(scale-i)
  c = (i/scale)*100
  dur = time.perf_counter()-start
  print("\r{:^3.0f}%[{}->{}]{:.2f}s".format(c,a,b,dur),end="")
  time.sleep(0.1)
print("\n"+"执行结束".center(scale//2,"-"))  
- **文本进度条举一反三**  
在任何运行时间较长的程序中，提高用户体验考虑加入进度条，人机交互  
让计算机展示不能进度条  
相比线性展示，开始展示慢些，后续展示效果逐渐增加更符合人类的心理需求  
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/%E6%96%87%E6%9C%AC%E8%BF%9B%E5%BA%A6%E6%9D%A1%E7%9A%84%E4%B8%8D%E5%90%8C%E8%AE%BE%E8%AE%A1%E5%87%BD%E6%95%B0.jpg?raw=true)

# 文件与数据格式化
## 文件的使用  
- **文件的理解**  
文件是数据的抽象与集合，文件是存储在辅助存储器上的数据序列，文件是数据存储的一种形式。  
文件展现形式，文本文件和二进制文件，文本文件和二进制文件只是文件的展示方式，从本质上，所有文件，都是二进制形式存储  
文本文件：由单一特定编码组成的文件，比如UTF-8编码，由于存在着编码，也被看做存储着的长字符串。适用于例如 .txt  .py文件  
二进制文件：直接由比特0和1构成，没有统一的字符编码，一般存在着二进制0和1的结构组织，即文件格式，例如 .png文件 .avi文件  
f.txt存储，"中国是个伟大的国家"  
tf = open("f.txt","rt")
print("tf".readline())
tf.close()  
会输出文件的第一行内容  
bf = open("f.txt","rb")
print("tf".readline())
tf.close()  
二进制形式打开文件第一行对应的二进制存储形式  
- **文件的打开和关闭**  
文件处理步骤：打开-处理-关闭  
文件的存储状态和文件的占用状态，通过 txt= open(,)和a.close()来转换  
a.read(size)  读文件
a.readline(size)  
a.readlines(hint)  
a.write(a)    写文件
a.writelines(lines)  
a.seek(offset)  
文件的打开  
<变量名> = open(<文件名>,<打开模式>)  
文件名包括文件路径及名称，源文件同目录可省路径  
打开模式：文本模式或二进制，只读信息还是可选信息  
变量名，文件句柄  
python中因为斜杠默认为转义，因此要用反斜杠来替代斜杠,或者增加一个斜杠转义 绝对路径
D:\pye\f.txt 要写成 D:/pye/f.txt 或 D:\\pye\\f.txt    
相对路径，打开的文件与当前程序之间的路径  
./pye/f.txt  从当前目录下找起  
打开模式，7种  
r，只读模式，默认值，如果不存在，返回FileNotFoundErroro  
w，覆盖写模式，文件不存在则创建，存在则覆盖  
x，创建写模式，文件不存在则创造，存在则返回FileExistsError  
a，追加写模式，文件不在则创建，存在则在最后追加内容  
b，二进制文件模式  
t，文本文件模式，默认值  
+，与r、r、w、x同时使用，在原功能基础上添加同时读写功能  
<>.close() 如果没写close，在程序关闭的时候，python也，会自动地将打开关闭，尽可能不要忘
- **文本内容的读取**  
f.read(size=-1)读入全部内容，如果给出参数，读入前size长度  
f.readline(size=-1)从文件中读取一行，如果给出参数，读入前size长度  
f.readlines(hint = -1)读入文件所有行，以每行为元素形成列表，如果给出参数，读取前hint行  
方法一 遍历全文本  一次读入，全部处理  
fname = input("请输入文本全名：")
ftxt = open(fname,"r")
f = ftxt.read()
#对txt全文进行处理
ftxt.close()  
对于大文件来讲，一次性地读入文件，代价很大  
方法二，按数量处理，逐步读入  
fname = input("请输入文本全名：")
ftxt = open(fname,"r")
f = ftxt.read(2)
while f!="":
    #对txt全文进行处理
    f = ftxt.read(2)
ftxt.close()  
方法一 逐行遍历文件  一次读入，逐行处理
fname = input("请输入文本全名：")
ftxt = open(fname,"r")
for line in ftxt.readlines():
    print(line)
ftxt.close()  
方法二 分行读入，逐行处理  
fname = input("请输入文本全名：")
ftxt = open(fname,"r")
for line in ftxt():
    print(line)
ftxt.close()
可以直接用for line in txt:  
- **数据的文件写入**  
f.write(s) 向文件写入一个字符串或字节流  
f.writelines(lines) 讲一个元素全为为字符串的列表写入文件，拼接后写入  
f.seek(offset)改变当前文件操作指针的位置，offset意思是，0-是开头，1-当前位置，2-文件结尾f.seek(0) 指针回到文件开头  
fo = open("output.txt","w+",encoding="utf-8")
ls = ["中国","法国","美国"]
fo.writelines(ls)
fo.seek(0) 如果没有这行，光标会从输入的语句后面开始遍历，没有结果
for line in fo:
    print(line)
fo.close()  
注意程序操作过程中，指针所在位置，以及其对程序的影响  
**open存在编码的问题，可用encoding= "utf-8"加以解决**  
## **实例11：自动轨迹绘制**  
需求：根据脚本来绘制图形，不是写代码，而是写数据绘制轨迹，数据脚本是自动化最重要的一步  
- **基本思路**  
步骤一：定义数据文件格式（接口）  
步骤二：编写程序，根据文件接口解析参数绘制图形  
步骤三：编制数据文件  
数据接口定义，非常具有个性色彩，  
300,0,144,1,0,0  
300,1,144,0,1,0  
使用一行表示一次操作,300表示当前位置开始向前行进的距离，第二个数据表示转向判断，如果数据是0，则是左转，1则是右转，第三个参数表示转向的角度，后三个参数代表RGB三个通道颜色  
map(func,ls) 内嵌函数，将第一个参数的功能，作用于第二个参数的每一个元素，第一个参数函数，第二个参数是迭代类型
#AutoTraceDrawV1.py
import turtle as t
t.turtle('自动轨迹绘制') #设置绘制窗口标题栏的信息
t.setup(800,600,0,0)
t.pencolor("red")
t.pensize(5)
#数据读取
detals = []
f = open('data.txt')
for line in f:  #逐行读取，分次处理
  line.replace("/n","")
  detals.append(list(map(eval,line.split(","))))
f.close() #将接口文件信息读入detal列表，而列表的每一个元素也是一个列表
#自动绘制
for i in range(len(detals)):
  t.pencolor(detals[i][3],detals[i][4],detals[i][5])
  t.fd(detals[i][0])
  if detals[i][1]:
    t.right(detals[i][2])
  else:
    t.left(detals[i][2])  
- **举一反三**  
自动化思维：数据和功能分离，数据驱动的自动运行  
接口设计：格式化设计接口，清晰明了  
二维数据应用：应用维度组织数据，二维最常用  
扩展接口设计，增加更多的控制接口，扩展功能设计，扩展应用需求，由轨迹绘制变为动画绘制  
## 一维数据的格式化 
- **数据组织的维度**  
一维数据：由对等关系的有序或无序数据组成，采用线性的方式组织，列表、数组和集合  
二维数据：由多个一个数据构成，是一维数据的组合形式，比如表单，表格  
多维数据：由一维或二维数据在新的维度上的扩展，如表单增加时间维度  
高维数据：仅利用最基本的二元关系展现数据之间的复杂结构，如键值对  
数据的操作周期：存储、表示、操作  
- **一维数据的表示**  
如果数据之间有序，使用列表，使用for循环遍历进而处理  
如果数据之间无序，使用集合类型  
- **一维数据的存储**  
存储方式一：空格分隔，一个或多个空格，不换行，简单，但数据中本身不能存在空格  
二，逗号分隔，不换行，不能由逗号  
其他方法，使用特殊符号，需要根据数据特点来定，通用性差  
- **一维数据的处理**  
一维数据的存储格式和列表或集合表示方式之间的转换，如何将数据读入程序，或将程序写入存储  
txt = open(fname).read() 大字符串  
ls= txt.split() 根据空格分隔  
f.close()  
写入
ls = ["1","2","3"]
f=open(fname,"w")
f.write(" ".join(ls)) 之间增加空格
f.close()  
*join和split方法可以完成文件的写入或读出操作*  
## 二维数据的格式化
- **二维数据的表示**  
使用列表类型，使用二维列表[[3.14，3.15],[3.16，3.17]],使用两个for循环，遍历列表元素  
外层列表中每个元素可以对应列表的一行或者一列，根据具体应用来确定  
csv格式和二维数据存储 comma-seperated values 用逗号来分割值的方式，一般用.csv作为扩展格式，每行一个一维数据，采用逗号分隔，无空行。Excel软件可读入输出，一般编辑软件都可以产生  
如果某个元素缺失，逗号仍要保留；二维数据的表头可以作为数据存储，也可以另行存储。  
逗号采用英文半角逗号，逗号与数据之间没有额外空格  
如果数据中出现逗号，不同软件有不同表示，有的通过在数据两侧增加引号，有的则是通过转义符  
按行存，按列都可以，具体由程序决定，但一般索引习惯是，ls[row][coulumn],先行后列，根据这种习惯，一般外层列表的每个元素是一行，先存行  
- **二维数据的处理**  
从CSV中读取数据：
fo = open(fname)  
ls = []  
for line in fo:  
    line = line.replace("\"," ")   
    ls.append(line.split(","))  
fo.close()  
经过操作ls就是一个包含二维数据的二维列表信息  
将数据协会CSV文件中  
fo = open(fname,"w")  
ls = [[1,2,3],[3,4,5],[5,6,7]]  
for item in ls:  
    fo.write(",".join(item)+"\")  
fo.close  
采用二层循环  
ls = [[],[],[]]
for row in ls:
    for column in row:
        print(ls[row][column])  
## 模块6:wordcloud库的使用  
- **wordcloud库的基本概述**  
优秀的词云展示第三方库，词云以词语为基本单位，更加直观和艺术化地展示文本  
wordcloud库的安装 终端中 pip install wordcloud  
- **wordcloud库的使用说明**  
wordcloud库把词云当成一个WordCloud对象,注意大小写  
wordcloud.WordCloud() 代表一个文本对应的词云  
可根据文本中词语出现的频率等一系列参数绘制词云  
绘制词云的颜色、形状、尺寸、字体等都是可以设定的  
w = wordcloud.WordCloud()  
以WordCloud对象为基础，配置参数、加载文本、输出文件  
w = wordcloud.WordCloud()  
w.generate(txt) 向WordCloud对象w中加载文本txt  
w.to_file(filename) 将词云输出成图像文件，.png或.jpg格式  
- **绘制词云步骤**  
步骤一：配置对象参数  
步骤二：加载词云文本  
步骤三：输出词云文件  
import wordcloud
c = wordcloud.WordCloud()
c.generate("wordcloud by python")
c.to_file("pythonwordcloud.png")  
1,分隔，通过空格分隔单词，2，统计单词出现次数并过滤 3，字体，根据统计配置字号，4，布局，颜色环境尺寸  
- **词云输出效果参数配置**  
w = wordcloud.WordCloud(参数)  
width,height 指定生成图片的宽度和高度  
min_font_size 指定词云中最小字体，默认为4号  
max_font_size 指定词云中最大字体，根据高度调节  
font_step 词云中字体字号的步进间隔，默认为1，与上面两个组合使用  
font_path 指定字体文件的路径，默认为None  
max_words 指定词云显示的最大单词数量，默认为200  
stop_words 指定词云排除词列表，即不显示的词的列表  
w = wordcloud.WordCloud(stop_words = ["python","fucking world"])  
指定词云形状，mask参数的使用模式
form scipy.misc import imread  
mk = imread(".png")  
w = wordcloud.WordCloud(mask = mk)  
import wordcloud
c = wordcloud.WordCloud()
c.generate("wordcloud by python")
c.to_file("pythonwordcloud.png")  
background_color 词云图片的背景颜色，默认为黑色  
用中文形成词云前需要先分词  
import jieba
import wordcloud
txt = "计算机程序设计语言，通常简称为\
       编程语言，是一组用来定义计算机\
       程序的语法规则。它是一种被标准\
       化的交流技巧。"
w = wordcloud.WordCloud(width = 1000,\
                        font_path = "Songti.ttc",height = 700)
w.generate(" ".join(jieba.lcut(txt)))
w.to_file("中文云词.png")
## 实例12:政府工作报告词云  
- **问题分析**  
需求：直观理解政府工作报告  
新时代全面建设中国特色社会注意.txt
实施乡村振兴战略的意见.txt  
- **实例讲解上**  
- #GovRpWordCloudV1.py
import jieba
import wordcloud
with open("实施乡村振兴战略的意见.txt","r",encoding= "utf-8") as f:
    t = f.read()
ls = jieba.lcut(t)
txt = " ".join(ls)
#准备好了准备的字符文本
w = wordcloud.WordCloud( font_path = "Songti.ttc",\
                         width = 1000,height = 700,background_color\
                         = "white",max_words = 15)
w.generate(txt)
w.to_file("gwwordcloud.png")
- **实例讲解下**  
生成更有形的词云，需要先提供背景是白色的五角星或中国地图形状  
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/政府工作报告实例.png?raw=true)
- **举一反三**  
特色词云设计，属于自己的特色词云风格
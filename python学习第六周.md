# 组合数据类型
## 集合类型及操作  
- **集合类型的定义**
集合是多个元素的无序组合，与数学中的定义一致  
集合元素之间无序，每个元素唯一，不存在相同元素  
集合元素不可更改，不能是可变数据类型
因为集合中不能存在相同的元素，因此，如果集合中的元素可以更改，就可能存在相同的元素，与互异性不符
整数、浮点数、复数、字符串、元组
在python中集合用{}表示，元素间用逗号分隔，建立集合类型用{}或者set()，如果希望建立一个空集时，必须使用set()函数  
A={"python",123,('python',123)}  
B=set("python"),字符串中的每个字符单独拆分，变成集合的一个元素，相同的p和y将被去掉，顺序亦会打乱，因无序
- **集合操作符**  
s|t 并运算；s-t差运算；s&t 交运算；s^t 补运算；s<t,s<=t 判断子集关系，返回True/False; s>t,s>=t 判断包含关系，返回True/False  
4个增强操作符：s|=t 更新几何s，包括原有两个几何  
- **集合的处理方法**  
S.add(x):如果x不在集合S中，将x增加到S中  
S.discard(x):移除s中的x元素，如果x不在
s中，不报错  
S.remove(x):也能移除，但额如果x不在S中，会产生keyError异常，可以用try：except：来捕捉异常  
S.clear():移除S中所有元素  
S.pop():随机返回S中的一个元素，更新S，如果S是空集，产生KeyError异常  
S.copy:返回集合S的一个副本  
len(S):返回集合S中的元素个数  
x in S:判断集合S中元素x，如果x在S中，返回True，否则返回False  
x not in S:与上面相反  
set(x):将其他变量x转换为集合类型  
集合的处理方法  
for item in A:  
返回获得的变量定义顺序是不同的，其内部保存虽然有顺序，但程序员不能无法应用  
try:
    while True:
        print(A.pop(),end="")
except:
    pass  
从A中不停地取出元素，当A中的元素为空时，退出  
- **集合类型应用场景**  
包含关系的比较
一个很重要的应用，数据去重，集合所有类型无重复  
ls = [1,2,3,1,4,3]
set(ls)
list(set(ls))  
## 序列类型及操作  
- **序列类型定义**  
序列是具有先后关系的一组元素，序列是一维元素向量，元素类型可以不同，元素间由下标引导，可以通过下标访问序列的特定元素  
序列是一个基类数据类型，基本数据类型，我们一般不会直接使用，而是使用其衍生出来的字符串类型，元组类型，列表类型  
序号定义，正向递增序号，和反向递减序号
- **序列处理函数及方法**  
x in s； x not in s  
s+t s * n    
n * s s[i] s[i:j:k]    
通用函数及方法  
len(s); min(s)和max(s)最小元素和最大元素; 字符串的比较是按照字母序来比较  
s.index(x)或s.index(x,i,j) 返回序列s从i开始到j位置第一次出现元素x的位置  
s.count(x) 返回序列s中出现x的次数  
- **元组类型及操作**  
元组类型是序列类型的一种扩展，一旦创建不能被修改  
创建使用()或tuple(),元素之间用逗号分隔  
在使用的时候，元组可以有小括号，也可以没有  
例如  
def func():
&ensp;return 1,2  
看似返回了两个值，但在python内部，认为返回了一个值，这个值是元组  
元组类型继承了序列类型的全部操作，因创建后不能修改因此没有特殊操作  
- **列表类型及其操作**  
列表是序列类型的一种扩展 ，创建后可以被修改  
使用[]或list()来创建，元素之间用逗号分隔  
lt = ls 通过等号将一个列表赋值给另一个，此时并没有在系统真正生成一个列表，仅仅将同一个列表赋予不同的名字，只有使用[]或list()才是真正的，其中涉及内存和指针  
ls[i] = x 替换列表的第i个元素为x  
ls[i:j:k] = lt 用列表lt替换列表ls切片后所对应元素子列表  
del ls[i] 删除列表ls中的第i个元素  
del ls[i:j:k]删除列表中第i到第j以k为步长的元素  
ls+=lt 将列表lt中的元素增加到列表ls中  
ls*=n 更新列表，其元素重复n次  
ls.append(x) 在列表最后增加元素x  
ls.clear() 清除列表中所有元素  
ls.copy() 生成一个新列表，复制所有原有元素  
ls.insert(i,x) 在i位置增加一个元素x  
ls.pop(i) 取出第i位置的元素  
ls.remove(x) 将ls中出现的第一个x元素删除  
ls.reverse() 元素反转  
- **序列类型应用场景**  
元组用于元素不改变的应用场景，更多用于固定搭配场景，比如函数的返回值return  
列表更加灵活，它是最常用的序列类型  
主要作用，表示一组有序数据，进而去操作它们  
元素遍历 for item in ls:  for item in tp:  
数据保护 如果不希望数据被程序功能修改，可将程序转换为元组  
lt = tuple(ls)  
多人编程，要求接口采用元组传递数据  
## 基本统计值计算  
- **问题分析**  
需求：给出一组数，需要对它们有个概要理解  
总个数、求和、平均值、方差、中位数  
- **实例讲解**  
#CalStatisticsV1.py
def getNums ():
    Nums = []
    iNumStr = input("请输入数字(回车退出)：")
    while iNumStr != "":
        Nums.append(eval(iNumStr))
        iNumStr = input("请输入数字(回车退出)：")
    return Nums
def mean (numbers): #计算平均值
    s = 0.0
    for num in numbers:
        s+=num
    return s/len(numbers)
def dev (numbers,mean):
    d = 0.0
    for num in numbers:
        d = d+(num-mean)**2
    return pow(d/len(numbers),0.5)

def median(numbers):
    numbers.sort()
    size = len(numbers)%2
    if size ==0:
        med = (numbers[len(numbers)//2-1]+numbers[len(numbers)//2])/2
    else:
        med = numbers[len(numbers)//2]
    return med
def main():
    n = getNums()
    m = mean(n)
    print("平均值:{},方差:{},中位数:{}".format(m,dev(n,m),median(n)))
        
main()  
- **基本统计值计算举一反三**  
通过while语句获取用户多个输入的方法  
模块化设计多个函数  
充分利用python内置函数
## 字典类型及其操作  
- **字典类型定义**  
理解映射：映射是一种键（索引）和值（数据）的对应  
序列类型由0到N整数作为数据的默认索引  
映射由用户为数据自定义索引  
字典类型是映射的体现。键值对，键是数据索引的一种扩展，字典是键值对的集合，键值对之间无需  
字典采用{}或者dict()来创建，键值对用冒号：来表示  
在字典变量中，通过键获得值；[]用来索引或向字典变量中增加新的键值对  
type(x) 返回变量的类型  
生成集合类型不能用{}，是因为{}是默认来生成字典类型的  
- **字典处理函数及方法**  
del d[k] 删除字典中键k对应的数据值  
k in d 判断键k是否在字典中，True/False  
d.keys() 返回字典中所有键的信息，并非列表类型  
d.values() 返回字典中所有值的信息  
d.items() 返回字典中所有键值对的信息  
d.get(k,default) 键k存在则返回相应值，不存在则返回default  
d.pop(k,default) 键k存在则取出相应的值，不存在则返回default  
d.popitem() 随机从字典中取出一个键值对，以元组形式返回  
d.clear() 删除字典中所有的键值对  
len(d) 返回字典中元素的个数  
- **字典类型应用场景**  
映射的表达，例如统计数据出现的次数，数据是键，次数是值。最主要作用，表达键值对数据，进而操作它们  
遍历元素 for k in d:  
## 模块5：jieba库的使用  
- **jieba库简要介绍**  
优秀的中文分文第三方库  
中文文本需要通过分词获得单个的词语  
提供三种分词模式，最简单的只要掌握一种函数  
pip install jieba  
通过中文词库来识别分词，计算汉字之间的关联概率，还可以添加自定义词组  
- **jieba库的使用**  
精确模式：把一段文本精确地切分开，不存在冗余单词  
全模式：把文本所有可能的单词扫描出来，有冗余  
搜索引擎模式，在精确模式的基础上，对长词再次切分  
jibe.lcut(s) 精确模式，返回一个列表类型的分词结果  
jieba.lcut(s,cut_all = True) 全模式，返回一个列表类型的分词结果，有冗余  
jieba.lcut_for_search(s) 搜索引擎模式，有冗余  
jieba.add_word(w) 向jeiba分词词典增加新词  
## 实例10:文本词频统计  
- **问题分析**  
文本词频统计，一篇文章，出现了哪些单词，哪些词出现得最多  
文章是英文文本还是中文得，英文文本以hamlet来分析，中文文本则以三国演义分析人物出场次数
- **hamlet英文词频实例讲解**  
第一步：对文本进行噪音处理，规划提取其中的每一个单词  
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/hamlet词频分析.png?raw=true)
- **三国演义人物出场频率讲解**  
中文用jieba，大小写和标点不需要考虑
词频和人物出场的关联，面向问题的需求  
![](https://github.com/Misasagiinori/pythonlearning/blob/master/picture/三国演义实例.png?raw=true)
- **举一反三**  
应用问题扩展，大量词频分析统计  
绘制词云










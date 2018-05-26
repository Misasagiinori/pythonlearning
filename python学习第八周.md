# 程序设计方法  
## 实例13：体育竞技分析  
需求：毫厘是多少？如何用科学方法分析体育竞技？  
输入球员的水平值，输出可预测的比赛成绩  
体育竞技分析：模拟N场比赛  
计算思维：抽象+自动化  
模拟抽象比赛过程+自动执行N场比赛  
当N越大，比赛结果分析会越科学  
比赛规则：双人击球比赛，A&B，回合制 五局三胜  
开始时一方先发球，直至判分，接下来胜者发球  
球员只能在发球局得分，15分胜一局  
- **自顶向下和自底向上**  
自顶向下：将一个总的问题表达为若干小问题组成的形式，使用相同的方法进一步分解小问题，直到小问题可以用计算机简单明了的解决  
自底向下：逐步组建复杂系统，分单元测试，逐步组装  
- **实例讲解**  
步骤一：打印程序的介绍性信息  printInfo()  
步骤二：获得程序运行参数，proA，proB，n，运动员的能力值，以及模拟比赛的场次数量  getInputs()  
步骤三：利用球员A和B的能力值，模拟n场比赛  simNGames()  
步骤四：输出球员获胜的场次及概率 printSummary()  
程序由这四个函数组成  
步骤三模拟n局比赛可以继续分解成模拟一局比赛
simOneGame()  
判断比赛结束可以封装成小模块，gameOver()  
```
from random import random
def printInfo():
    print("这个程序模拟两个选手A和B之间的某种竞技比赛")
    print("请输入A和B的能力值(0到1之间的小数表示)")

def getInputs():
    a=eval(input("请输入选手a的能力值(0,1):"))
    b=eval(input("请输入选手b的能力值(0,1):"))
    n=eval(input("请输入模拟比赛的场次:"))
    return a,b,n

def printSummary(winsA,winsB):
    n=winsA+winsB
    print("竞技分析开始，共模拟{}场比赛".format(n))
    print("选手A获胜{}场，占比{:0.1%}".format(winsA,winsA/n))
    print("选手B获胜{}场，占比{:0.1%}".format(winsB,winsB/n))

def simNGames(n,probA,probB):
    winsA,winsB=0,0
    for i in range(n):
        scoreA,scoreB=simOneGame(probA,probB)
        if scoreA>scoreB:
            winsA+=1
        else:
            winsB+=1
    return winsA,winsB

def simOneGame(probA,probB):
    scoreA,scoreB=0,0
    serving ="A"
    while not gameOver(scoreA,scoreB):
        if serving=="A":
            if random()<probA:
                scoreA+=1
            else:
                serving="B"
        else:
            if random()<probB:
                scoreB+=1
            else:
                serving="A"
    return scoreA,scoreB

def gameOver(a,b):
    return a==15 or b==15 #带入上面即scoreA或者scoreB等于15

def main():
    printInfo()
    probA,probB,n=getInputs()
    winsA,winsB=simNGames(n,probA,probB)
    printSummary(winsA,winsB)

main()
```
- **举一反三**  
自顶向下的设计思维：分而治之
自底向上的执行思维：模块化集成
## python程序设计思维
- **计算思维与程序设计**  
第三种人类思维特征，逻辑思维，推理和演绎 实证思维，实验和验证 计算思维  
计算思维 computational thinking 抽象和自动化  
抽象问题的计算过程，并用计算机自动化求解  
计算思维是基于计算机的思维方式，不关心因果，而是关心过程和设计，抽象计算过程  
编程是将计算思维变成现实的手段
- **计算生态与python语言**  
自由软件运动，开源生态  
开源思想深入和演化，形成了计算生态  
没有顶层设计以功能为单位  
库之间相互关联，依存发展，自然选择，社区庞大，新技术更迭迅速  
API !=生态 ，设计出来的  
学会站在巨人的肩膀上，起点不是算法，而是系统，利用计算生态为主要模式，快速解决问题  
python123 推荐优质的第三库  
- **用户体验与软件产品**  
进度展示：程序需要时间，需要用户等待，或者程序有若干步骤，需要提示用户，程序存在大量次数循环  
异常处理：当获得输入，对合规性检查，或读写文件，进行输入输出  
打印输出：特定位置，输出过程信息  
日志文件：对程序异常和用户使用进行定期记录  
帮助信息：给用户提供帮助信息  
- **基本的程序设计模式**  
从IPO开始，编写程序，测设程序  
自顶向下设计  
模块化设计，分而治之，松耦合，紧耦合  
配置化设计，轨迹自动化实例，将程序变为引擎加配置，将可选参数配置化，关键在于接口设计  
## python第三方库安装  
- **python全球社区**  
https://pypi.org  
PyPi:python package index  
PSF维护的展示全球python计算生态的主战  
实例：开发与区块链相关的程序（三步）  
第一步：搜索blockchain  
第二步：挑选适合开发的第三方库作为基础  
第三步：利用这个库完成需要的功能  
三种安装方法：pip命令，集成安装，文件安装  
- **pip安装**  
常用pip命令  
pip install <第三方库名>  
pip install -U <第三方库名> 更新已安装的第三方库  
pip uninstall <第三方库名>  
pip download <第三方库名> 下载但不安装第三方库  
pip show <第三方库名> 列出指定第三方库的详细信息  
pip search <关键词> 在名称和介绍中搜索第三方库  
pip list 列出当前系统已安装的第三方库  
- **第三方库集成安装方法**  
Anaconda https://www.anaconda.io  
支持近800个第三方库，包含多个主流工具，适合数据计算领域开发  
- **文件安装方法**  
有些第三方库用pip可以下载，但无法安装  
因为某些第三方库pip下载后，需要编译再安装，如果操作系统没有编译环境，则能下载不能安装  
uci页面 https://www.lfd.uci.edu/~gohlke/pythonlibs/  
给出了windows上需要编译后再安装的第三库的直接编译后的版本  
以安装wordcloud为实例  
再uci页面上搜索wordcloud，下载对应版本，使用pip install <文件名>安装  
## 模块7:os库的使用  
- **基本介绍**  
os库提供通用的基本的操作系统交互功能  
os库是python的标准库，包含几百个函数，常用路径操作，进程管理，环境参数等几类  
路径操作：os.path子库，处理文件路径及信息  
进程管理：指启动系统中其他程序  
环境参数：获取系统软硬件信息等环境参数  
- **os库之路径操作**  
os.path以path为入口，用于操作和处理文件路径  
```
os.path.abs(path)返回path在当前系统中的绝对路径
os.path.normpath(path)对path进行归一化操作，统一用\\分隔路径  
os.path.relpath(path)返回当前程序与所调用文件之间的相对路径(relative path)
os.path.dirname(path)返回路径中的目录名字
os.path.basename(path)返回路径中的文件的名字
os.path.join(path,*paths)组合path和paths，返回一个路径字符串
os.path.exists(path)判断path对应的文件或目录是否存在，返回True或False
os.path.isfile(path)判断path对应是否为已存在文件
os.path.isdir(path)判断path所对应是否为已存在目录
os.path.gettime(path)返回文件或目录上一次的访问时间
os.path.getmtime(path)返回文件或目录最近一次的修改时间 
os.path.getctime(path)返回文件或目录的创建时间
os.path.getsize(path)返回path所对应文件的大小，以字节为单位
```
- **os库之进程管理**
```
os.system(command)
执行程序或命令command，在windows中，返回值为cmd的调用返回信息
import os
os.system("C:\\Windows\\System32\\calc.exe") 调出程序，返回一个0

import os
os.system("C:\\Windows\\System32\\mispanit.exe \
          D:\\PYECourse\\grwordcloud.png")
调用其他程序
```
- **环境参数**  
获取或改变系统的环境信息 
```
os.chdir(path)修改当前程序操作的路径
os.getcwd() 返回程序的当前路径
os.getlogin()获取当前系统登陆用户名称
os.cpu_count()获得当前系统的cpu数量
os.urandom(n)获得n字节长度的随机字符串，通常用于加解密运算,由于某些字符串不能被有效打印出来，将用16进制形式来表示
```
## 实例14:第三方库自动安装脚本
- **问题分析**  
需求：批量安装第三方库，自动执行pip逐一根据安装需求安装
- **自动安装脚本**  
```
#BatchInstall.py
import os
libs={"numpy","matplotlib","sklearn","requests",\
      "django","pygame","pandas"}
try:
    for lib in libs:
        os.system("pip install "+lib)
    print("Successful")
except:
    print("Failed Somehow")
    
注意：pip install 后有空格
```
- **举一反三**
编写各类自动化运行程序的脚本，调用已有程序，调用计算器、时间、pip等  
扩展应用：安装更多的第三方库，增加配置文件  
扩展异常检测：捕获更多异常类型，程序更稳定友好

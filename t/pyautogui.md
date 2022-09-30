---
title: 'Pyautogui实现QQ自动点赞（PC版）'
date: 2022-04-29 23:15:35
tags: [Python]
published: true
hideInList: false
feature: 
isTop: false
---

> Tips：本篇文章适合有一定基础的兄弟，大佬直接略过
>           原文在csdn上，但是没有通过审核😭

@[TOC]


# 前言
最近有许多的小伙伴给我QQ名片点赞，但是数量太多了，回赞到手酸＞﹏＜
于是，我找到了[hamibot](https://hamibot.com/)这个自动化脚本软件，可是最近发现自己编写的点赞脚本没反应〒▽〒
因此，我为其编写了自动点赞的代码ヾ(≧▽≦*)o
`Tips：为了方便演示，本文集成开发环境为Pycharm(～￣▽￣)～`


# 一、原理
使用python中的**pyautogui**模块进行模拟鼠标控制，并比对屏幕中指定图片的位置，实现自动点赞功能
[文档链接在这里（￣︶￣）↗　](https://pyautogui.readthedocs.io/en/latest/)

# 二、使用步骤
## 1.引入库
**方法一**
cmd中输入
```shell
pip install pyautogui
```
**方法二**
```python
import pyautogui as gui
```
如果出现红色下划线，就把光标移到那里，点击下面的蓝字
![安装gui](https://img-blog.csdnimg.cn/d6e62ff50b684feea08a2750bd2b7096.png#pic_center)
## 2.打开QQ的点赞界面
**方法一** 手动定位坐标

利用pyautogui点击图标
```python
import pyautogui as gui
gui.click(x ,y)  # QQ在任务栏小图标的位置
```
pyautogui内置一个position()函数，它能获取鼠标的位置，稍加改进，我们便能实时获取鼠标的位置
```python
import pyautogui as gui
while True:
    lp = gui.position()
    if lp != gui.position():
        print(gui.position())
'''
position()能获取鼠标位置
如果鼠标移动，就打印位置
'''
```
输入任务栏QQ图标的坐标，运行一下，成功弹出主界面，然后重复上述操作，获取各个控件的坐标，进入点赞主面板.

![任务栏图标](https://img-blog.csdnimg.cn/1583b7841533473c966d9639f780c19f.png#pic_left)

![点赞主面板](https://img-blog.csdnimg.cn/1e6914e42238408db369e2c4f2c7bc83.png#pic_left)
![点赞主面板](https://img-blog.csdnimg.cn/5e54d7d0976a49199d3f6550a65cde66.png#pic_left)
![点赞主面板](https://img-blog.csdnimg.cn/a165bbd697f6418e99c664f86ee367d0.png#pic_left)
咳咳咳，今天的赞有点少≡(▔﹏▔)≡
```python
# 模板
import time
import pyautogui as gui

gui.click(x1, y1)  # 点击QQ图标
time.sleep(0.5)

gui.click(x2, y2)  # 点击头像
time.sleep(0.5)

gui.click(x3, y3)  # 点击赞标
time.sleep(0.5)
```
`Tip:这里要导入time模块，为QQ提供反应时间；如果反应时间太长，可以适当增加反应时间`

**方法二** 自动截屏定位
pyautogui内置locateOnScreen()函数，它能捕获屏幕，并定位你给它的图片，非常的nice！！
(首先你要截目标按钮的图)

```python
import pyautogui as gui

bl1 = gui.locateOnScreen('p3.png', confidence=0.9)
# print(bl1)  # Box(left=1575, top=1042, width=22, height=28)
bl2 = gui.center(bl1)  # 定位这个区域的中心
# print(bl2)  # Point(x=1586, y=1056)
blx, bly = bl2
gui.click(blx, bly)
```
⇩ 这个就是p3.png
![p3](https://img-blog.csdnimg.cn/a1d148d9f769415e84acce66e0336791.png)
`Tips:用这个功能需要另外两个库支持！`
`①Pillow：这个库用来截图`
`②opencv-python：这个库用来增加容错率[代码中的confidence(自信)参数]`
下载方法同上
这里要强调一下opencv-python这个库：
1.	confindence的值∈(1,-∞)，数值越大，容错率越小，准确率越高
如果≥1，则会报错
2.	尽量把confindence这个参数加上，如果不加，第二天就会发现识别失败
（原文：函数由于像素差异可以忽略不计而无法定位图像）
3.	这个库比较大，后期不建议打包成exe文件（本来10MB的东西直接增加50MB＞︿＜）
当然有需要的打包也可以
5.	另外，这个函数运行时间较长（1-2s），如果加了confidence参数可以缩小到0.5s以内

其实上述代码可以进一步简化[ locateCenterOnScreen() ]，它直接反馈中心坐标

```python
import pyautogui as gui

x1, y1 = gui.locateCenterOnScreen('E:\\py\\exe_test\\qq.png', confidence=0.9)
gui.click(x1, y1)
```
这里我用的是绝对路径，相对路径也可以，具体选择就看个人习惯啦
重复方法一的步骤进入点赞界面即可
在啰嗦一句，这回预留时间很重要！(时间可调整)

```python
# 模板
import pyautogui as gui
import time

x1, y1 = gui.locateCenterOnScreen('图片名1', confidence=0.9)  # 点击Q标
time.sleep(1)
gui.click(x1, y1)
time.sleep(0.5)

x2, y2 = gui.locateCenterOnScreen('图片名2', confidence=0.9)  # 点击头像
time.sleep(1)
gui.click(x2, y2)
time.sleep(0.5)

x3, y3 = gui.locateCenterOnScreen('图片名3', confidence=0.9)  # 点击赞标
time.sleep(1)
gui.click(x3, y3)
time.sleep(0.5)
```
## 3.自动点赞
自动点赞这部分我只推荐用locateCenterOnScreen（）这个方法，代码如下

```python
def selfclick():
    for _ in range(5):
        x1, y1 = gui.locateCenterOnScreen('d2.png', confidence=0.9)
        time.sleep(0.5)
        for _ in range(11):  # 次数可更改(我穷,只能点10个赞;多1个赞防止漏点,会员调成21即可)
            gui.click(x1, y1)
            time.sleep(0.1)
```
⇩ 这个就是d2.png
![d2](https://img-blog.csdnimg.cn/29eb1f4e15a048a7bfbb24da4050dda6.png)
点赞后它会变蓝，剩下的10次点赞还是锁定在原坐标上

## 4.成品展示
稍加修饰，你就得到了它：
`Ps：如果有疑问，那就去附录上看看叭`
```python
import pyautogui as gui
import time
import sys


def selfclick():
    for _ in range(5):
        x3, y3 = gui.locateCenterOnScreen('d2.png', confidence=0.9)
        time.sleep(0.5)
        for _ in range(11):
            gui.click(x3, y3)
            time.sleep(0.1)

if __name__ == '__main__':
	# 点击Q标
    try:
        x1, y1 = gui.locateCenterOnScreen('qq.png', confidence=0.9)
        gui.click(x1, y1)
    except:
        gui.alert(text='找不到企鹅图标', title='警告', button='OK')
        sys.exit()  # 自动推出
    time.sleep(1)
    
	# 点击头像
    gui.click(1345, 85)
    time.sleep(1)
    
	# 点击赞标,进入点赞主面板
    x2, y2 = gui.locateCenterOnScreen('d1.png', confidence=0.9)
    time.sleep(1)
    gui.click(x2, y2)
    time.sleep(0.5)
    
    # 循环点赞
    for _ in range(8):  # 如果好友多,次数就多一点,反之亦然
        try:
            time.sleep(0.5)
            selfclick()
        except:
            time.sleep(0.35)
            gui.scroll(-300)  # 如果好友多,数值就再调小一点,反之亦然
            time.sleep(0.35)
    # 关闭窗口        
    gui.hotkey('alt', 'f4')
    time.sleep(0.1)
    gui.hotkey('alt', 'f4')
    time.sleep(0.1)
    sys.exit()
```
记得要更改一下坐标，图片要自己截哈q(≧▽≦q)

# 三、附录
## 1.实时获取鼠标位置

```python
import pyautogui as gui
while True:
    lp = gui.position()
    if lp != gui.position():
        print(gui.position())
```
## 2.pyautogui的其他功能

```python
import pyautogui as gui

# 发出弹窗
gui.alert(text='找不到企鹅图标', title='警告', button='OK')

# 鼠标滚轮
gui.scorll(-300)  # 默认向上滚动,向下滚动要加负号
# 输入数值的绝对值越大,滚轮滚得越长

# 快捷键
gui.hotkey('alt', 'f4')  # 先按alt键,再按f4,随后顺次松开
# 其他按键也一样 
```
弹窗长这样( •̀ ω •́ )✧
![弹窗
](https://img-blog.csdnimg.cn/33fce0ff47194cf5a478f7011675c6da.png#pic_center)

# 总结
以上就是今天要讲的内容啦，感谢阅读！更多有关pyautogui的用法请前往官网。这是鄙人第一次写文章，可能有许多不足之处，欢迎在评论区提出建议O(∩_∩)O
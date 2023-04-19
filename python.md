### 字符串

#### 函数

##### 字母大小写

titile()   #首字母大写

upper() #全部大写

lowper() #全部小写

##### 去除空格(strip())

```python
str1 = ' abc '
a=str1.strip()
b=str1.rstrip()
c=str1.lstrip()
print(a,b,c,sep="\n")
<<'abc'
<<' abc'
<<'abc '
```

### 列表

####  修改列表

##### 插入列表(insret()，append())

```python
list1 = []
list1.insert(0,'data')
print(list1)
<< ['data']
```

##### 删除列表（del,  pop(),remove())

根据下表删除

```python
list.pop()
del list[0]
```

根据值删除

```python
list = ['data','data1']
list.remove('data')
```

#### 组织列表

##### 排序（sort())

```python
list.sort()#永久排序
list.sort(reverse=True)#逆排
list.sortd()#临时排序
```

##### 倒着打印列表（reverse())

```python
list.reverse()
```

### 字典

#### 遍历字典（keys( ),valus( ))

```python
dict.items()# 
dict1 = {'a':1,'b':2,'c':3}
d1 = dict1.items()#返回类型不为list.不能索引
<<dict_items([('a', 1), ('b', 2), ('c', 3)])
for i,j in d1:
    print(i,j)
<<a 1
<<b 2
<<c 3

print(dict1.keys())#返回类型不为list，不能索引
print(dict1.values())#返回类型不为list，不能索引
<<dict_keys(['a', 'b', 'c'])
<<dict_values([1, 2, 3])
```

### 函数

#### 系统函数

##### 日期函数（datetime）

from datetime import *

##### 数学函数（math）

向上取整 ：math.ceil

向下取整 ：//

#### 固定参数

```python
def describ(pet, animal=" " ):
    if animal:					#animal为位置实参
        return pet+animal		#animal 可以不参与函数
    else:				
        return pet
print(describ('abc'))
print(describ(animal='1',pet='abc'))#可以改变传参位置
<< abc 
<< abc1
```

#### 任意参数

```python
def describ(*toppings ):#任意位置实参和数量参数
def describ(**toppings ):#任意关键字参数（输入为location=‘princet’)
    print (toppings)
describ(location='princet')
<<{'location': 'princet'}
```

### 类

```python
class Car():
    def __init__(self,make,model,year):#实例类 my_car1 = Car('audi','a4',2016)
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0 #赋值 my_car.odometer_reading = 23
    def read_odometer(self):    #my_car.read_odometer()
        print(str(self.odometer_reading))
    def updata_odometer(self,mileage):  # my_car.updata_odometer(100)
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
class Battery():
    def __init__(self,battery_size=70):
        self.battery_size = battery_size
    def desc_battery(self):
        print(self.battery_size)
class ElectricCar(Car):
    def __init__(self,make,model,year): #my_car2 = ElectricCar('audi', 'a4', 2016)
        #初始化ElectricCar
        super().__init__(make,model,year)
        self.battery = Battery() #子类属性 my_car2.battery.desc_battery() 使用Battery()的方法
    def describe_battery(self):
        print(str(self.battery))
```

#### 变量作用域

------

```python
a = 1
def outer(): 
    a = 2
    def inner():
        nonlocal a
        a = 3
        def inner2():
            print(a)
        inner2()
        print(a)
    inner()
    print(a)
outer()
print(a)
#运行结果：
<<3
<<3
<<3
<<1
```

#### 私有属性

##### 访问私有属性

```python
    @property #访问器
    def name(self):
```

##### 改变私有属性

```python
    # 修改器 - setter方法
    @age.setter
    def age(self, age):
        self._age = age
```

#### 

### 文件操作

```python
import json
def get_stord_username():
    filename = 'username.json'
    try:
        with open(filename) as f_obj:
            username = json.load(f_obj)
    except FileNotFoundError:
        return None
    else:
        return username
def get_new_username():
    username = input("name")
    filename = 'username.json'
    with open(filename, 'w') as f_obj:
        json.dump(username, f_obj)
def greet_user():
    username = get_stord_username()
    if username:
        print(username)
    else:
        username = get_new_username()
        print(username)
greet_user()
```

### 输入格式

###### 输入数据类型

默认str

整型int(input())

输入数据格式

input().split() #去除输入空格

### 输出格式

##### 百分号输出：

1.{:.0f}%'.format(100*42/50)

2.{:.0%}'.format(42/50)

### 符号

##### 除法：

/和//:5/2=2.5,5//2=2(向下取整)

##### 引号：

引号中间的内容会当作字符串打印，三引号输出是不会改变输入的格式

![img](https://img-blog.csdnimg.cn/img_convert/661d6ee62cee6b28db45a72f2809da00.png)

当字符串需要加入引号时，可采用单引号与双引号互相嵌套使用

![img](https://img-blog.csdnimg.cn/img_convert/415930359741fb514196157ed6c62d5d.png)

#### 正则表达式

##### 正则表达式符号

|     符号     | 解释                             | 示例             |                                                         说明 |
| :----------: | -------------------------------- | ---------------- | -----------------------------------------------------------: |
|      .       | 匹配任意字符                     | b.t              |                              可以匹配bat / but / b#t / b1t等 |
|      \w      | 匹配字母/数字/下划线             | b\wt             |                      可以匹配bat / b1t / b_t等 但不能匹配b#t |
|      \s      | 匹配空白字符（包括\r、\n、\t等） | love\syou        |                                             可以匹配love you |
|      \d      | 匹配数字                         | \d\d             |                                       可以匹配01 / 23 / 99等 |
|      \b      | 匹配单词的边界                   | \bThe\b          |                                                              |
|      ^       | 匹配字符串的开始                 | ^The             |                                      可以匹配The开头的字符串 |
|      $       | 匹配字符串的结束                 | .exe$            |                                     可以匹配.exe结尾的字符串 |
|      \W      | 匹配非字母/数字/下划线           | b\Wt             |              可以匹配b#t / b@t等 但不能匹配but / b1t / b_t等 |
|      \S      | 匹配非空白字符                   | love\Syou        |                        可以匹配love#you等 但不能匹配love you |
|      \D      | 匹配非数字                       | \d\D             |                                       可以匹配9a / 3# / 0F等 |
|      \B      | 匹配非单词边界                   | \Bio\B           |                                                              |
|      []      | 匹配来自字符集的任意单一字符     | [aeiou]          |                                     可以匹配任一元音字母字符 |
|     [^]      | 匹配不在字符集中的任意单一字符   | [^aeiou]         |                                   可以匹配任一非元音字母字符 |
|      *       | 匹配0次或多次                    | \w*              |                                                              |
|      +       | 匹配1次或多次                    | \w+              |                                                              |
|      ?       | 匹配0次或1次                     | \w?              |                                                              |
|     {N}      | 匹配N次                          | \w{3}            |                                                              |
|     {M,}     | 匹配至少M次                      | \w{3,}           |                                                              |
|    {M,N}     | 匹配至少M次至多N次               | \w{3,6}          |                                                              |
|      \|      | 分支                             | foo\|bar         |                                           可以匹配foo或者bar |
|     (?#)     | 注释                             |                  |                                                              |
|    (exp)     | 匹配exp并捕获到自动命名的组中    |                  |                                                              |
| (?<name>exp) | 匹配exp并捕获到名为name的组中    |                  |                                                              |
|   (?:exp)    | 匹配exp但是不捕获匹配的文本      |                  |                                                              |
|   (?=exp)    | 匹配exp前面的位置                | \b\w+(?=ing)     |                                  可以匹配I'm dancing中的danc |
|   (?<=exp)   | 匹配exp后面的位置                | (?<=\bdanc)\w+\b |              可以匹配I love dancing and reading中的第一个ing |
|   (?!exp)    | 匹配后面不是exp的位置            |                  |                                                              |
|   (?<!exp)   | 匹配前面不是exp的位置            |                  |                                                              |
|      *?      | 重复任意次，但尽可能少重复       | a.*b a.*?b       | 将正则表达式应用于aabab，前者会匹配整个字符串aabab，后者会匹配aab和ab两个字符串 |
|      +?      | 重复1次或多次，但尽可能少重复    |                  |                                                              |
|      ??      | 重复0次或1次，但尽可能少重复     |                  |                                                              |
|    {M,N}?    | 重复M到N次，但尽可能少重复       |                  |                                                              |
|    {M,}?     | 重复M次以上，但尽可能少重复      |                  |                                                              |

**说明：** 如果需要匹配的字符是正则表达式中的特殊字符，那么可以使用\进行转义处理，例如想匹配小数点可以写成\.就可以了，因为直接写.会匹配任意字符；同理，想匹配圆括号必须写成\(和\)，否则圆括号被视为正则表达式中的分组。

##### re模块

Python提供了re模块来支持正则表达式相关操作，下面是re模块中的核心函数。

| 函数                                         | 说明                                                         |
| -------------------------------------------- | ------------------------------------------------------------ |
| compile(pattern, flags=0)                    | 编译正则表达式返回正则表达式对象                             |
| match(pattern, string, flags=0)              | 用正则表达式匹配字符串 成功返回匹配对象 否则返回None         |
| search(pattern, string, flags=0)             | 搜索字符串中第一次出现正则表达式的模式 成功返回匹配对象 否则返回None |
| split(pattern, string, maxsplit=0, flags=0)  | 用正则表达式指定的模式分隔符拆分字符串 返回列表              |
| sub(pattern, repl, string, count=0, flags=0) | 用指定的字符串替换原字符串中与正则表达式匹配的模式 可以用count指定替换的次数 |
| fullmatch(pattern, string, flags=0)          | match函数的完全匹配（从字符串开头到结尾）版本                |
| findall(pattern, string, flags=0)            | 查找字符串所有与正则表达式匹配的模式 返回字符串的列表        |
| finditer(pattern, string, flags=0)           | 查找字符串所有与正则表达式匹配的模式 返回一个迭代器          |
| purge()                                      | 清除隐式编译的正则表达式的缓存                               |
| re.I / re.IGNORECASE                         | 忽略大小写匹配标记                                           |
| re.M / re.MULTILINE                          | 多行匹配标记                                                 |

> **说明：** 上面提到的re模块中的这些函数，实际开发中也可以用正则表达式对象的方法替代对这些函数的使用，如果一个正则表达式需要重复的使用，那么先通过compile函数编译正则表达式并创建出正则表达式对象无疑是更为明智的选择。
>
> ##### 例子

```python
m1 = re.match(r'^[0-9a-zA-Z]{6,20}$',username) #username是否满足0-9a-zA-Z连续的6-20长度的字符串
m2 = re.match(r'^[1-9]/d{4,11}',qq)#qq满足开头是满足[1-9]，后面连续的4,11个数字的字符串
# 创建正则表达式对象 使用了前瞻和回顾来保证手机号前后不应该出现数字
pattern = re.compile(r'(?<=\D)1[34578]\d{9}(?=\D)')  # 前后都不是数字
sentence = '''
总要的事情说8130123456789遍，我的手机号是13512346789这个靓号，
不是15600998765，也是110或119，王大锤的手机号才是15600998765。
'''
# 查找所有匹配并保存到一个列表中
mylist = re.findall(pattern, sentence)
print(mylist)
# 通过迭代器取出匹配对象并获得匹配的内容
for temp in pattern.finditer(sentence):
    print(temp.group()) # group返回分组内容
# 通过search函数指定搜索位置找出所有匹配
m = pattern.search(sentence)
while m:
        print(m.group())
        m = pattern.search(sentence, m.end()) #end()返回返回匹配结束的位置
```

### 进程和线程

------

#### 进程

Unix和Linux操作系统上提供了`fork()`系统调用来创建进程，Windows系统没有`fork()`调用，可以使用multiprocessing模块的`Process`类来创建子进程。必须使用main()，否则会一直创建子进程

```python
    from multiprocessing import Process 
    
    def download(filename):
    	print('开始下载%s...' % filename)
    	time_to_download = randint(5, 10)
    	sleep(time_to_download)
    	print('%s下载完成! 耗费了%d秒' % (filename, time_to_download))
        
def main():        #必须使用main() 
     start = time()
     p1 = Process(target=download_task, args=('杨',))
     p1.start() #进程开始
     p2 = Process(target=download_task, args=('刚',)) #target调用函数， args为函数参数
     p2.start()
     p1.join() #进程结束
     p2.join()
     end = time()
     print('总共耗费了%.2f秒.' % (end - start))
```

#### 线程

​	开发多线程用threading模块的`Thread`类来创建线程,Thread使用和Process一样拥有target，args参数 

```python
from time import sleep
from threading import Thread, Lock


class Account(object):

    def __init__(self):
        self._balance = 0
        self._lock = Lock() #上锁 让资源只能一个用

    def deposit(self, money):
        # 先获取锁才能执行后续的代码
        self._lock.acquire()
        try:
            new_balance = self._balance + money
            sleep(0.01)
            self._balance = new_balance
        finally:
            # 在finally中执行释放锁的操作保证正常异常锁都能释放
            self._lock.release() #解锁

    @property
    def balance(self):
        return self._balance


class AddMoneyThread(Thread):

    def __init__(self, account, money):
        super().__init__()
        self._account = account
        self._money = money

    def run(self):
        self._account.deposit(self._money)


def main():
    account = Account()
    threads = []
    for _ in range(100):
        t = AddMoneyThread(account, 1)
        threads.append(t)
        t.start()
    for t in threads:
        t.join()
    print('账户余额为: ￥%d元' % account.balance)


if __name__ == '__main__':
    main()
```

#### 单线程+异步I/O

单线程+异步I/O的编程模型称为协程

协程最大的优势就是极高的执行效率，因为子程序切换不是线程切换，而是由程序自身控制，因此，没有线程切换的开销

### 网络应用开发

#### 获取Url

requests.get(url)

#### 套接字编程

TCP套接字就是使用TCP协议提供的传输服务来实现网络通信的编程接口

```python
from socket import socket, SOCK_STREAM, AF_INET
    # family=AF_INET - IPv4地址
    # family=AF_INET6 - IPv6地址
    # type=SOCK_STREAM - TCP套接字
    # type=SOCK_DGRAM - UDP套接字
    # type=SOCK_RAW - 原始套接字
#创建套接字对象并指定使用哪种传输服务
server = socket(family=AF_INET, type=SOCK_STREAM)
#绑定IP地址和端口(端口用于区分不同的服务)
server.bind(('192.168.1.2', 6789))
# 参数512可以理解为连接队列的大小
server.listen(512)
while True:
    # 4.通过循环接收客户端的连接并作出相应的处理(提供服务)
    # accept方法是一个阻塞方法如果没有客户端连接到服务器代码不会向下执行
    # accept方法返回一个元组其中的第一个元素是客户端对象
    # 第二个元素是连接到服务器的客户端的地址(由IP和端口两部分构成)
    client, addr = server.accept()
    print(str(addr) + '连接到了服务器.')
    # 5.发送数据
    client.send(str(datetime.now()).encode('utf-8'))
```

#### 实现TCP客户端

```python
from socket import socket
def main():
    # 1.创建套接字对象默认使用IPv4和TCP协议
    client = socket()
    # 2.连接到服务器(需要指定IP地址和端口)
    client.connect(('192.168.1.2', 6789))
    # 3.从服务器接收数据
    print(client.recv(1024).decode('utf-8'))
    client.close()
```

#### 发送电子邮箱

```python
import smtplib
from email.mime.text import MIMEText
from email.header import Header
# 第三方 SMTP 服务
mail_host = "smtp.qq.com"  # 设置服务器
mail_user = "2939816714@qq.com"  # 用户名
mail_pass = "dkspmplkqvhidhbc"  # 授权码
sender = '2939816714@qq.com'
receivers = ['2863433958@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱
message = MIMEText('Python 邮件发送测试...', 'plain', 'utf-8')
message['From'] = Header("PythonSMTP <2939816714@qq.com>") #括号里的对应发件人邮箱昵称（随便起）、发件人邮箱账号
message['To'] = Header("测试", 'utf-8') #括号里的对应收件人邮箱昵称、收件人邮箱账号
subject = 'Python SMTP 邮件测试'
message['Subject'] = Header(subject, 'utf-8')
smtpObj = smtplib.SMTP()
smtpObj.connect(mail_host,465)  # 发件人邮箱中的SMTP服务器，端口是465
smtpObj.login(mail_user, mail_pass)
smtpObj.sendmail(sender, receivers, message.as_string())
print("邮件发送成功")
```

#### 发送短信

在下面的代码中我们使用了[互亿无线](http://www.ihuyi.com/)短信平台

```python
import urllib.parse
import http.client
import json


def main():
    host  = "106.ihuyi.com"
    sms_send_uri = "/webservice/sms.php?method=Submit"
    # 下面的参数需要填入自己注册的账号和对应的密码
    params = urllib.parse.urlencode({'account': '你自己的账号', 'password' : '你自己的密码', 'content': '您的验证码是：147258。请不要把验证码泄露给其他人。', 'mobile': '接收者的手机号', 'format':'json' })
    print(params)
    headers = {'Content-type': 'application/x-www-form-urlencoded', 'Accept': 'text/plain'}
    conn = http.client.HTTPConnection(host, port=80, timeout=30)
    conn.request('POST', sms_send_uri, params, headers)
    response = conn.getresponse()
    response_str = response.read()
    jsonstr = response_str.decode('utf-8')
    print(json.loads(jsonstr))
    conn.close()


if __name__ == '__main__':
    main()
```

### 图片和办公

#### 图片处理

```python
import ImageFilter
from PIL import Image
image = Image.open('../images/image-show.png')
# 剪裁图像
# rect = 80, 20 ,400, 360
# image.crop(rect).show()
# 生成缩略图
# size = 128, 128
# image.thumbnail(size)
# image.show()
#缩放和黏贴图像
# guido_head = image.crop(rect)
# width, height = guido_head.size
# image.paste(guido_head.resize((int(width / 1.5), int(height / 1.5))), (170, 100))
# 旋转和翻转
# image.rotate(180).show()
# image.transpose(Image.FLIP_LEFT_RIGHT).show()
# 操作像素
# for x in range(150,360):
#     for y in range(20,360):
#         image.putpixel((x, y), (128, 128, 128))
# image.show()
# 滤镜效果
# image.filter(ImageFilter.CONTOUR).show()
```

### 生成器和迭代器

#### 迭代器

- `__iter__`和`__next__`魔术方法就是迭代器协议。    

```python
class Fib(object):
    """迭代器"""
    
    def __init__(self, num):
        self.num = num
        self.a, self.b = 0, 1
        self.idx = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.idx < self.num:
            self.a, self.b = self.b, self.a + self.b
            self.idx += 1
            return self.a
        raise StopIteration() # raise 用于抛出异常
```

#### 生成器

生成器是语法简单版迭代器

##### 生成器进化成协程

send()方法将值传入yield

```python
def calc_avg():
    """流式计算平均值"""
    total, counter = 0, 0
    avg_value = None
    while True:
        value = yield avg_value
        total, counter = total + value, counter + 1
        avg_value = total / counter


gen = calc_avg()
next(gen)
print(gen.send(10)) #10
print(gen.send(20)) #15
print(gen.send(30)) #20
```


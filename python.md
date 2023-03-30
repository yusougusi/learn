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

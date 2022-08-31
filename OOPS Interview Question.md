### Class, Object/instance, Method
    l=[1,2,3,4]
    l.append(5)
    Class is list
    Object is l
    append is Method
```python
class Person:
    def __init__(self,first_name,last_name,age):#init method or constructor
        #Self represent object
        #When ever object is created constructor is called
        self.first_name=first_name
        self.last_name=last_name
        self.age=age

p1=Perason('Aman','Singh',19)
p2=Person('Akash','Singh',17)
```

### Method
```python
class Person:
    def __init__(self,first_name,last_name,age):
        self.first_name=first_name
        self.last_name=last_name
        self.age=age
    def full_name(self):
        return f"{self.first_name} {self.last_name}"
    def vote(self):
        return self.age>=18

p1=Person('Ankit','Jha',20)
print(p1.vote())#True
print(Person.vote(p1))#True
print(p1.full_name())#Ankit Jha
```

### Class Variable
```python
class Circle:
    pi=3.14#Class Variable/class attribute
    def __init__(self,radius):
        self.radius=radius
    def cal_circumference(self):
        return 2*self.pi*self.radius
c=Circle(2)
print(c.cal_circumference())#12.56
```

### Important
    Count all objects of a class
  ```python
    class Person:
        counter=0
        def __init__(self,f_name,l_name):
            Person.counter+=1
            self.f_name=f_name
            self.l_name=l_name
    p1=Person('Raj','Singh')
    p2=Person('Aman',"Singh")
    print(Person.counter)#2
```

### Class Method
```python
class Person:
    counter=0
    def __init__(self,first_name,last_name,age):
        Person.counter+=1
        self.first_name=first_name
        self.last_name=last_name
        self.age=age
    @classmethod
    def count_instances(cls):
        return f"You have created {cls.counter} instances"
    def full_name(self):
        return f"{self.first_name} {self.last_name}"
    def vote(self):
        return self.age>=18
p1=Person("Aman","Singh",90)
print(Person.count_instances())
```

### Class Method as a constructor
```python
class Person:
    counter=0
    def __init__(self,first_name,last_name,age):
        Person.counter+=1
        self.first_name=first_name
        self.last_name=last_name
        self.age=age
    @classmethod
    def from_string(cls,string):
        f,l,a=string.split(',')
        return cls(f,l,a)
    @classmethod
    def count_instances(cls):
        return f"You have created {cls.counter} instances"
    def full_name(self):
        return f"{self.first_name} {self.last_name}"
p1=Person("Aman","Singh",90)
p2=Person.from_string('Akash,Singh,8')
print(Person.count_instances())
print(p2.full_name())
```

### Static method
```python
class Person:
    def __init__(self,first_name,last_name,age):
        self.first_name=first_name
        self.last_name=last_name
        self.age=age
    @staticmethod
    def hello():
        print("Static Method called")
    def full_name(self):
        return f"{self.first_name} {self.last_name}"
p1=Person("Aman","Singh",90)
p1.hello()
```

### Encapsulation
```python
class Phone:
    def __init__(self,brand,model_name,price):
        self.brand=brand
        self.model_name=model_name
        self._price=price
    def make_a_call(self):
        print(f"calling {phone_number}....")
    def full_name(self):
        return f"{self.brand} {self.model_name}"
```

- <b>_variable</b> is used to make private name
- <b>__variable</b> is used to make protected name
- <b>__name__</b> Dunder method or magic name

### Important
        __dict__ is used to show the dictionary of the variable used in classs

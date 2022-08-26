Q-1:What kind of language is Python?
Ans:Python is a general purpose ,Scripting Language.It is Dynamically Typed
    Object Oriented which also support Functional Programming.
    -Dynamically Typed :Type of variable and Expression define during run Time.
    -Every things in python is a Object
    -Every things can be divided into small functions hence called as Functional Programming

Q-2:Is Python an Interpreted Language?
Ans:Python Source Code->Compiler->Binary Code->(PVM Python Virtual Machine)Just in time compiler->Machine Code
    Interpreter Convert binary Code into the machine code and wait for next command by operating System.

Q-3:What is the difference between list and tuple?
Ans:In both we can store Heterogeneous, Indexing, Silicing Operator.
    list-[],mutable.more memmory consuming.
    Tuple-(),immutable,(index,count),less memmory consuming.

Q-4:How is memory managed in python?
Ans:Reference Variable in Stack Memory and Object in Private Heap Space
    -Python Memory manager help to assigning the sapace
    -Garbage Collector

Q-5:What is an identity operator?
Ans:is and is not it is used to cheque that different refere contain same Object
    - X=5 and Y=5

Q-6:What is Monkey Patching?
Ans:class Test:
        def __init__(self,x):
            self.a=x
        def get_data(self):
            print("Some Code to Fetch data from databse")
        def f1(self):
            self.get_data()
        def f2(self):
            self.get_data()
    t1=Test(s)
    t1.f1()
    t2.f2()
    def new_get_data(self):
        print("Some code to fetch data from test data")
    Test.get_data=new_get_data
    print("After Monkey Patching")
    t1.f1()
    t2.f2()

Q-7:How to make generator to produce first N Prime numbers?
Ans:Yield

Q-8:How to implement variable length arguments in Python?
Ans:def average(*t):
        avg=sum(t)/len(t)
        print("Average is",avg)
    average(10,15,16)
    average(8,9,90,7,5,6)

Q-9:How to create instance member variables in a python class?
Ans:class Test:
        def __init__(self):
            self.a=5
        def f1(self):
            self.b=10
    t1=Test()#t1 object
    t2=Test()
    t1.f1()
    t1.c=15
    print(t1.__dict__)

Q-10:What is a lambda expression?
Ans:f=lambda a,b:a+b#a,b is argument
    f(3,4)

Q-11:What is a list comprehension?
Ans: l=[expression for e in sequence ]

Q-12:Local Variable vs Global Variable ?
Ans:x=5#global variable
    def f1():
         y=10#local variable
         print("x=%d y=%d"%(x,y))
    f1()
    print(x,y)

Q-13:What is decorator in Python?
Ans:decorator is a function which takes another function as a argument and changes its funcnality.
    def decor_result(result_function):
        def distinction(marks):
            for m in marks:
                if m>=75:
                    print("Distinction")
            result_function(marks)
        return distinction
    @decor_result
    def result(marks):
        for m in marks:
            if m>=33:
                pass
            else:
                print("FAIL")
        else:
            print("PASS")
    result([50,60,70,80,75])

Q-14:What is an Iterator?
Ans:iterable type ka object ka first stating point ko point karta hai
    my_list=[10,20,30,40,50,60]
    it=iter(my_list)
    while True:
        try:
            print(next(it))
        except StopIteration:
            break

Q-15:Does python support function overloading?
Ans:no
    def f1():
        print("Hii")
    def f1(a,b):
        print("Hello")


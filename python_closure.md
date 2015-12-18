#### python closure

closure == lexical	as-first-class-function

###### namespace

local namespace
global namespace
build-in namespace

	s = "string in global"
	num = 99

	def numFunc(a, b):
	    num = 100
	    print "print s in numFunc: ", s

	    def addFunc(a, b):
	        s = "string in addFunc"
	        print "print s in addFunc: ", s
	        print "print num in addFunc: ", num
	        print "locals of addFunc: ", locals()
	        print 
	        return "%d + %d = %d" %(a, b, a + b)

	    print "locals of numFunc: ", locals()
	    print 
	    return addFunc(a, b)

	numFunc(3, 6)    
	print "globals: ", globals()

###### closure

	def greeting_conf(prefix):
	    def greeting(name):
	        print prefix, name
	    return greeting

	mGreeting = greeting_conf("Good Morning")
	mGreeting("Wilber")
	mGreeting("Will")

	print

	aGreeting = greeting_conf("Good Afternoon")    
	aGreeting("Wilber")
	aGreeting("Will")
***
	def greeting_conf(prefix):
        def greeting(name):
        	print prefix, name
        return greeting

	mGreeting = greeting_conf("Good Morning")      

	print dir(mGreeting)
	print mGreeting.__closure__
	print type(mGreeting.__closure__[0])
	print mGreeting.__closure__[0].cell_contents
***
	def greeting_conf(prefix):
    	def greeting(name):
        	print prefix, name
    	return greeting

	mGreeting = greeting_conf("Good Morning")      
	print "function name is:", mGreeting.__name__
	print "id of mGreeting is:", id(mGreeting)

	print

	aGreeting = greeting_conf("Good Afternoon")  
	print "function name is:", aGreeting.__name__
	print "id of aGreeting is:", id(aGreeting)

###### Python中怎么创建闭包

1 闭包函数必须有内嵌函数
2 内嵌函数需要引用该嵌套函数上一级namespace中的变量
3 闭包函数必须返回内嵌函数
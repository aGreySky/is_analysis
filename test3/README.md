周志强的实验报告
============
## 实验三：图书管理系统领域对象建模

|学号|班级|姓名|
|:---------------:|:------------:|:------------:|
|201510511129|软件15-1|周志强|

### 1.图书管理系统类图

**1.1PlantUML源码如下：**
~~~
@startuml

package "图书管理系统类包" #DDDDDD {
  
	class 图书管理员 {
		__ private data __
		 	-String adminId
	     	-String name
	    	-boolean sex
	    	-Date born
	    	-byte[] photo
	 	-- encrypted --
	 	    -String password
		__ public method __
			+维护图书()
			+归还图书()
			+借还图书()
			+维护读者()
	}
	class 超级管理员 {
		__ private data __
		 	-String superAdminId
		    -String name
		    -boolean sex
		    -Date born
		    -byte[] photo
	 	-- encrypted --
	 		-String password
		__ public method __
	 		+维护图书管理员信息()

	}
	class 读者 {
	 	__ private data __
		 	-String readerId;
		    -String name;
		    -boolean sex;
		    -Date born;
		    -String spec;
		    -int num;
		    -byte[] photo;
	 	-- encrypted --
	 		-String password
		__ public method __
			+查询借阅信息()
			+预订图书()
			+取消预订()
		
	}

	class 图书 {
		__ private data __
		 	 -int bookId
		     -String ISBN
		     -String bookName
		     -String author
		     -String publisher
		     -float price
		     -int cnum
		     -int snum
		     -String summary
		     -byte[] photo
	}

	class 借书记录 {
		__ private data __
		 	-Integer id
		    -int bookId
		    -String readerId
		    -String ISBN
		    -Date ltime
		    -boolean lendConfirm
		    -boolean returnRequest
	}

	note  "<color:blue>省略Getter和Setter方法。</color>" as note1

	图书管理员 <|- 超级管理员 : 维护图书管理员信息
	图书管理员 "N" -- "N" 读者 : 维护读者信息
	读者 "1" -- "N" 借书记录 : 借书和还书
	借书记录 "1" -- "1" 图书 : 一一对应
	借书记录 "N" -- "1" 图书管理员 : 登记和归还
	图书管理员 "N" -- "N" 图书 : 维护图书


	

  
}

@enduml
~~~
**1.2类图如下：**

![周志强-图书管理系统的类图](周志强-图书管理系统的类图.png)

### 2.图书管理系统对象图

**2.1图书管理系统对象关系图**

**2.1.1PlantUML源码如下：**
~~~
@startuml

package "图书管理系统类包" #DDDDDD {
  
	object 图书管理员 {
		 "管理员ID" adminId = "root"
		 "管理员密码" password = "123456"
     	 "姓名" name = "zhouzhiqiang"
    	 "性别"  sex = 1
    	 "生日" born = "2018-04-14 01:16:00"
    	 "照片" photo = "??WExif"
	}
	note  "Tip:sex为Boolean类型，1表示男，0表示女\n照片、封面为字节型数组，直接存放在数据库中" as note2
	object 超级管理员 {
		 "超级管理员ID" superAdminId = "superRoot"
		 "超级管理员密码" password = "123456"
     	 "姓名" name = "zhouzhiqiang"
    	 "性别"  sex = 1
    	 "生日" born = "2018-03-14 01:16:00"
    	 "照片" photo = "??WExif"
	}
	
	
	object 读者 {
	 	 "读者ID" readerId = "root"
     	 "姓名" name = "zhouzhiqiang"
     	 "读者密码" password = "123456"
    	 "性别"  sex = 1
    	 "生日" born = "2018-04-14 01:16:00"
    	 "专业" spec = "软工"
    	 "照片" photo = "??WExif"
    	 "借书量" num = 1
	}


	object 图书 {
		"书号" bookId = 1
		"ISBN号" ISBN = "978-986-181-729"
	 	"书名" bookName = "信息系统分析与设计"
	 	"作者" author = "王晓敏"
	 	"简介" summary = "信息系统分析与设计》是2004年西安电子科技大学出版社出版的图书,
	 					 作者是卫红春。主要讲述了信息系统的基本概念、基本理论和基本方法。"
	 	"出版社" publisher = "科学出版社"
	 	"价格" price = "10.1"
	 	"总量" cnum = "500"
	 	"库存" snum = "400"
		"封面" photo = "??WExif"
	}

	object 借书记录 {
		"借书ID" id = 1
		"图书ID" bookId = 2
	 	"读者ID" readerId = "zhouzhiqiang"
	 	"ISBN号" ISBN = "978-986-181-729"
	 	"借出时间" ltime = "2018-4-12"
	 	"归还请求" returnRequest = 1
	 	"归还确认" lendConfirm = 1
	}

	note right : "归还请求、借书确认为Boolean型变量，\n表示读者通过系统自主提交还书请求，\n默认为0，提交请求后用1表示，\n借书确认表示管理员是否受理借书请求，默认为0,处理后为1"


	图书管理员 <|-- 超级管理员 : 维护图书管理员信息
	读者 "1" - "N" 借书记录 : 借书和还书
	借书记录 "1" -- "1" 图书 : 一一对应
	借书记录 "N" -- "1" 图书管理员 : 登记和归还
	图书管理员 "N" - "N" 图书 : 维护图书
	图书管理员 "N" -- "N" 读者 : 维护读者信息

  
}


@enduml
~~~

**2.1.2对象图如下：**

![周志强-图书管理系统的对象图](周志强-图书管理系统的对象图.png)

**2.2图书对象图**

**2.2.1PlantUML源码如下：**
~~~
@startuml

object 图书 {
		"书号" bookId = 1
		"ISBN号" ISBN = "978-986-181-729"
	 	"书名" bookName = "信息系统分析与设计"
	 	"作者" author = "王晓敏"
	 	"简介" summary = "信息系统分析与设计》是2004年西安电子科技大学出版社出版的图书,
	 					 作者是卫红春。主要讲述了信息系统的基本概念、基本理论和基本方法。"
	 	"出版社" publisher = "科学出版社"
	 	"价格" price = "10.1"
	 	"总量" cnum = "500"
	 	"库存" snum = "400"
		"封面" photo = "??WExif"
	}
	note  right : "sex为Boolean类型，1表示男，0表示女\n封面为字节型数组，直接存放在数据库中"
@enduml
~~~

**2.2.2对象图如下：**

![图书的对象图](图书的对象图.png)

**2.3借书记录对象图**

**2.3.1PlantUML源码如下：**
~~~
@startuml

object 借书记录 {
		"借书ID" id = 1
		"图书ID" bookId = 2
	 	"读者ID" readerId = "zhouzhiqiang"
	 	"ISBN号" ISBN = "978-986-181-729"
	 	"借出时间" ltime = "2018-4-12"
	 	"归还请求" returnRequest = 1
	 	"归还确认" lendConfirm = 1
	}

	note right : "归还请求、借书确认为Boolean型变量，\n表示读者通过系统自主提交还书请求，\n默认为0，提交请求后用1表示，\n借书确认表示管理员是否受理借书请求，默认为0,处理后为1"

@enduml
~~~

**2.3.2对象图如下：**

![借书记录的对象图](借书记录的对象图.png)


**2.4图书管理员对象图**

**2.4.1PlantUML源码如下：**
~~~
@startuml

object 图书管理员 {
		 "管理员ID" adminId = "root"
		 "管理员密码" password = "123456"
     	 "姓名" name = "zhouzhiqiang"
    	 "性别"  sex = 1
    	 "生日" born = "2018-04-14 01:16:00"
    	 "照片" photo = "??WExif"
	}
	note  right : "sex为Boolean类型，1表示男，0表示女\n照片为字节型数组，直接存放在数据库中"


@enduml
~~~

**2.4.2对象图如下：**

![图书管理员的对象图](图书管理员的对象图.png)

**2.5超级管理员对象图**

**2.5.1PlantUML源码如下：**
~~~
@startuml

object 超级管理员 {
		 "超级管理员ID" superAdminId = "superRoot"
		 "超级管理员密码" password = "123456"
     	 "姓名" name = "zhouzhiqiang"
    	 "性别"  sex = 1
    	 "生日" born = "2018-03-14 01:16:00"
    	 "照片" photo = "??WExif"
	}

note  right : "sex为Boolean类型，1表示男，0表示女\n照片为字节型数组，直接存放在数据库中"
@enduml

~~~

**2.5.2对象图如下：**

![超级管理员的对象图](超级管理员的对象图.png)

**2.6读者对象图**

**2.6.1PlantUML源码如下：**
~~~
@startuml

object 读者 {
	 	 "读者ID" readerId = "root"
     	 "姓名" name = "zhouzhiqiang"
     	 "读者密码" password = "123456"
    	 "性别"  sex = 1
    	 "生日" born = "2018-04-14 01:16:00"
    	 "专业" spec = "软工"
    	 "照片" photo = "??WExif"
    	 "借书量" num = 1
	}
	note  right : "sex为Boolean类型，1表示男，0表示女\n照片为字节型数组，直接存放在数据库中"

@enduml
~~~

**2.6.2对象图如下：**

![读者的对象图](读者的对象图.png)



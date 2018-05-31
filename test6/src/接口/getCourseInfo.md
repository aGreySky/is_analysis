# 接口：getCourseInfo  [返回](../../README.md)
用例： [查看课程信息](../用例/查看课程信息.md),[修改课程信息](../用例/修改课程信息.md)

- 功能：
    查看指定课程的信息。
    
- 权限：
    学生/老师：查看所修/所任教课程信息，不能查看其他课程的信息。    
    
- API请求地址： 
    接口基本地址/v1/api/getCourseInfo/<course_id>

- 请求方式 ：
    GET
      
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|课程的ID号。对应表COURSES.COURSE_ID的值|
  
- 返回实例：

        {         
            "status": true,
            "info": null,
            "data": {
                "course_id": "055441"
                "course_name": "C语言基础"
                "course_content": "C语言是一门通用计算机编程语言，应用广泛。
                                   C语言的设计目标是提供一种能以简易的方式编
                                   译、处理低级存储器、产生少量的机器码以及不
                                   需要任何运行环境支持便能运行的编程语言。"
                "course_term": "2015-2016学年第1学期"
                "course_major": "软件工程"
                "course_class": "2015-1，2"
            }          
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |data|返回主体信息JSON串|
  |course_id|课程编号|
  |course_name|课程名称|  
  |course_content|课程简介|
  |course_term|开课学期|
  |course_major|开课专业|
  |course_class|开课班级|
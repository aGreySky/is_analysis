# 接口：getCoursesByTec  [返回](../../README.md)
用例： [选择任教课程](../用例/选择任教课程.md)

- 功能：
   根据老师编号显示老师任教的课程列表。
    
- 权限：
    老师。    
    
- API请求地址： 
    接口基本地址/v1/api/getCoursesByTec

- 请求方式：
    GET

- 请求实例：

        {
            "teacher_id": "2122"
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |teacher_id|老师的工号|
  |type|用户类型，学生或者老师|
  * 注：只能由"老师"访问，因为"学生"无场景访问此接口。
  
- 返回实例：

        { 
            "status": true,
            "info": null,
            "data": {
                "courses": [{
                    "course_id": "055441"
                    "course_name": "C语言基础"
                    "course_content": "C语言是一门通用计算机编程语言，应用广泛。
                                       C语言的设计目标是提供一种能以简易的方式编
                                       译、处理低级存储器、产生少量的机器码以及不
                                       需要任何运行环境支持便能运行的编程语言。"
                    "course_term": "2015-2016学年第1学期"
                    "course_major": "软件工程"
                    "course_class": "2015-1，2"
                    "techer_id": "2122"
                },{
                    "course_id": "032411"
                    "course_name": " 高等数学（A）上"
                    "course_content": "主要内容包括：极限、微积分、空间解析几何与
                                       线性代数、级数、常微分方程。"
                    "course_term": "2015-2016学年第1学期"
                    "course_major": "软件工程"
                    "course_class": "2015-1，2"
                    "techer_id": "2122"
                }]   
            }    
        }

- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |data|返回主体信息JSON串|
  |courses|返回符合条件的所有课程集合，若空则返回[]|
  |course_id|课程编号|
  |course_name|课程名称|  
  |course_content|课程简介|
  |course_term|开课学期|
  |course_major|开课专业|
  |course_class|开课班级|
  |teacher_id|老师编号|

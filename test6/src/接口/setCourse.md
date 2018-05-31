# 接口：setCourse  [返回](../../README.md)
用例：[新增课程](../用例/新增课程.md) [修改课程信息](../用例/修改课程信息.md) 

- 功能：
    创建（修改）指定课程的课程信息。
    
- 权限：
    老师。    
    
- API请求地址： 
    接口基本地址/v1/api/setCourse

- 请求方式 ：
    POST

- 请求实例：

        {
            "course_id": "032411",
            "course_name": " 高等数学（A）上",
            "course_content": "主要内容包括：极限、微积分、空间解析几何与
                               线性代数、级数、常微分方程。",
            "course_term": "2015-2016学年第1学期",
            "course_major": "软件工程",
            "course_class": "2015-1，2",
            "techer_id": "2122"
        }    
    
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|课程编号|
  |course_name|课程名称|  
  |course_content|课程简介|
  |course_term|开课学期|
  |course_major|开课专业|
  |course_class|开课班级|
  |teacher_id|老师编号|
  * 注：新建课程无需传入course_id,course_id为数据库主键，创建后无法更改，
  teacher_id由系统关联，同样无法更改。
  
- 返回实例：

        {         
            "status": true,
            "info": null,    

        }
 
- 返回参数说明： 
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|


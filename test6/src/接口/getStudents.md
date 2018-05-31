# 接口：getStudents  [返回](../../README.md)
用例： [显示本课程学生列表](../用例/显示本课程学生列表.md)

- 功能：
   根据课程编号显示本课程学生列表。
    
- 权限：
    老师。    
    
- API请求地址： 
    接口基本地址/v1/api/getStudents

- 请求方式：
    GET

- 请求实例：

        {
            "course_id": "02233"
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|课程编号|
  
- 返回实例：

        { 
            "status": true,
            "info": null,
            "data": {
                "students": [{
                    "student_id": "201510511129",
                    "major": "软件工程",
                    "class": 1,
                    "enrollment_year": 2015,
                    "web_sum": 1,
                    "user": {
                        "user_id": "201510511129",
                        "name": "周志强",
                        "github_username": "aGreySky",
                        "update_date": "2015-11-29 11:46:27"
                    }
                },{
                    ...
                }]   
            }    
        }

- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |data|返回主体信息JSON串|
  |students|返回本课程学生集合，若空则返回[]|
  |student_id|学号|
  |major|专业|  
  |class|班级|
  |enrollment_year|入学年份|
  |web_sum|学生GitHub地址是否正确，1正确，0错误|
  |user|学生关联的用户信息|
  |user_id|用户编号|
  |name|用户姓名|
  |github_username|GitHub用户名|
  |update_date|个人信息更新时间|
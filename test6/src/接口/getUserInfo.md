# 接口：getUserInfo  [返回](../../README.md)
用例： [查看个人信息](../用例/查看个人信息.md),[修改个人信息](../用例/修改个人信息.md)

- 功能：
    查看用户的所有信息。
    
- 权限：
    学生/老师：查看自己的信息，必须先登录，不能查看其他用户的信息。    
    
- API请求地址： 
    接口基本地址/v1/api/getUserInfo/<user_id>

- 请求方式 ：
    GET
      
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |user_id|用户的ID号。对应表USERS.USER_ID的值|
  
- 返回实例1：

        {         
            "status": true,
            "info": null,
            "data": {
                "user_id":"201510511129",    
                "name":"周志强",
                "github_username":"aGreySky",
                "type":"学生",
                "student": {
                    "major": "软件工程",
                    "class": 1,
                    "enrollment_year": 2015,
                    "web_sum": 1
                }  
            }          
        }
        
 - 返回实例2：

        {         
            "status": true,
            "info": null,
            "data": {
                "user_id":"22333",    
                "name":"张三",
                "github_username":"agrey",
                "type":"老师",
                "teacher": {
                    "department": "信息科学与工程学院"
                }  
            }          
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |data|返回主体信息JSON串|
  |user_id|学号或者工号|
  |name|用户的真实姓名|  
  |github_username|gitHub用户名|
  |student|学生信息|
  |major|学生所在专业|
  |class|学生所在班级|
  |enrollment_year|学生入学年份|
  |web_sum|学生GitHub地址是否正确，1正确，0错误|
  |teacher|老师学习|
  |department|老师所在部门|
  * 注：系统根据所查询的user_id对应的type值，传回学生或老师的信息
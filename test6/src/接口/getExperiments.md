# 接口：getExperiments  [返回](../../README.md)
用例： [查看实验列表](../用例/查看实验列表.md)

- 功能：
   根据课程编号返回实验列表。
    
- 权限：
    学生/老师。    
    
- API请求地址： 
    接口基本地址/v1/api/getExperiments

- 请求方式：
    GET

- 请求实例：

        {
            "course_id": "055441"
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|课程编号，对应唯一课程|
  
  
- 返回实例：

        { 
            "status": true,
            "info": null,
            "data": {
                "experiments": [{
                    "experiment_id": "1"
                    "experiment_name": "C语言语法练习"
                    "experiment_content": "熟练运用和掌握C语言的相关语法"
                    "experiment_last_time": "2015-11-29 11:46:27"

                },{
                    "experiment_id": "2"
                    "experiment_name": "C语言数组练习"
                    "experiment_content": "学会使用C语言的数组来表示数据"
                    "experiment_last_time": "2015-11-29 11:46:27"
                }]   
            }    
        }

- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |data|返回主体信息JSON串|
  |experiments|返回课程对应的所有实验集合，若空则返回[]|
  |course_id|课程编号|
  |experiment_id|实验编号|
  |experiment_name|实验名称|  
  |experiment_content|实验内容|
  |experiment_last_time|实验截至时间|

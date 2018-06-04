# 接口：getDetails  [返回](../../README.md)
用例： [查看实验评分点](../用例/查看实验评分点.md)

- 功能：
   根据实验编号和课程编号返回评分点列表。
    
- 权限：
    学生/老师。    
    
- API请求地址： 
    接口基本地址/v1/api/getDetails

- 请求方式：
    GET

- 请求实例：

        {
            "course_id": "055441",
            "experiment_id": 1
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|课程编号，对应唯一课程|
  |experiment_id|实验编号，和课程编号同时对应唯一实验|
  
  
- 返回实例：

        { 
            "status": true,
            "info": null,
            "data": {
                "details": [{
                    "detail_id": 1，
                    "detail_name": "C语言语法练习"，
                    "detail_content": "熟练运用和掌握C语言的相关语法"

                },{
                    "detail_id": 2，
                    "detail_name": "C语言语法练习"，
                    "detail_content": "熟练运用和掌握C语言的相关语法"
                }]   
            }    
        }

- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |data|返回主体信息JSON串|
  |details|返回实验对应的所有评分点集合，若空则返回[]|
  |detail_id|评分点编号|
  |detail_name|评分点名称|  
  |detail_content|评分点内容|

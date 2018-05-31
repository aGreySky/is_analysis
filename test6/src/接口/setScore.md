# 接口：setScore  [返回](../../README.md)
用例： [修改密码](../用例/修改密码.md)

- 功能：
    评定（修改）学生的成绩和评价。
    
- 权限：
    老师。    
    
- API请求地址： 
    接口基本地址/v1/api/setScore

- 请求方式 ：
    POST

- 请求实例：

        {
            "course_id": "055441"
            "student_id": "201510511129"
            "experiment_scores": [{
                "experiment_id": 1
                "experiment_score": 100,
                "experiment_comment": "C语言语法练习认真完成",
                "experiment_update_date": "2015-11-29 11:46:27"
                "detail_scores": [{
                    "detail_id": 1,
                    "detail_score": 100,
                    "detail_comment": "C语言if语句部分：认真完成",
                    "experiment_update_date": "2015-11-29 11:46:27"
                },{
                    "detail_id": 2,
                    "detail_score": 100,
                    "detail_comment": "C语言while语句部分：认真完成",
                    "detail_update_date": "2015-11-29 11:46:27"
                }]
            }]
        }    
    
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|课程编号|
  |student_id|学号|
  |course_score|课程成绩|
  |course_comment|课程评价|
  |course_update_date|课程成绩批改时间|
  |experiment_scores|实验成绩集合|
  |experiment_id|实验编号|
  |experiment_score|某个实验成绩|
  |experiment_comment|某个实验评价|
  |experiment_update_date|某个实验批改时间|
  |detail_scores|评分点成绩集合|
  |detail_id|评分点编号|
  |detail_score|评分点成绩|
  |detail_comment|评分点评价|  
  |detail_update_date|评分点批改时间|
  * 注：未打成绩的项不计入参数列表，例子见请求实例。
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


# 接口：getScores  [返回](../../README.md)
用例： [查看成绩列表](../用例/查看成绩列表.md)

- 功能：
   根据课程编号及学号返回成绩列表。
    
- 权限：
    学生/老师。    
    
- API请求地址： 
    接口基本地址/v1/api/getScores

- 请求方式：
    POST

- 请求实例：

        {
            "course_id": "055441",
            "student_id": "201510511129"
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|课程编号，对应唯一课程|
  |student_id|学号，对应唯一学生|
  
  
- 返回实例：

        { 
            "status": true,
            "info": null,
            "data": {
                "course_id": "055441"
                "student_id": "201510511129"
                "course_score": null,
                "course_comment": null
                "course_web_sum": 1
                "course_update_date": null
                "experiment_scores": [{
                    "experiment_id": 1
                    "experiment_score": 100,
                    "experiment_comment": "C语言语法练习认真完成",
                    "experiment_web_sum": 1
                    "experiment_update_date": "2015-11-29 11:46:27"
                    "detail_scores": [{
                        "detail_id": 1
                        "detail_score": 100,
                        "detail_comment": "C语言if语句部分：认真完成",
                        "experiment_update_date": "2015-11-29 11:46:27"
                    },{
                        "detail_id": 2
                        "detail_score": 100,
                        "detail_comment": "C语言while语句部分：认真完成",
                        "detail_update_date": "2015-11-29 11:46:27"
                    }]
                },{
                    "experiment_id": 2
                    "experiment_web_sum": 0
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
  |student_id|学号|
  |course_score|课程成绩|
  |course_comment|课程评价|
  |course_web_sum|学生课程GitHub地址是否正确，1正确，0错误|
  |course_update_date|课程成绩批改时间|
  |experiment_scores|实验成绩集合|
  |experiment_id|实验编号|
  |experiment_score|某个实验成绩|
  |experiment_comment|某个实验评价|
  |experiment_web_sum|某个实验GitHub地址是否正确，1正确，0错误|
  |experiment_update_date|某个实验批改时间|
  |detail_scores|评分点成绩集合|
  |detail_id|评分点编号|
  |detail_score|评分点成绩|
  |detail_comment|评分点评价|  
  |detail_update_date|评分点批改时间|
  * 注:当有某一级的GitHub地址出现问题时，直接返回该级的编号及"WEB_SUM"状态，
  同时在其子表下的内容将无需查询，并无需返回。<br>
  如：返回实例中，实验二（即"EXPERIMENT_ID": 2）的"EXPERIMENT_WEB_SUM" = 0。
  表示的是该学生实验二的GitHub地址出错，此时系统将无需查询实验二的评分点成绩，直接返回
  实验二编号和"WEB_SUM"参数值。

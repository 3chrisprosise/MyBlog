---
title: JqueryFileUpload
date: 2018-01-05 20:45:29
tags:
---

1. 使用jquery 实现Django 文件上传功能
    
    可以通过文件的 **flie** 属性获取文件对象的值

2. 使用 js 上传文件

```javascript
var postData = new FormData();
                postData.append("single_select_answer", JSON.stringify(single_select_answer));
                postData.append("multi_select_answer", JSON.stringify(multi_select_answer));
                postData.append("judge_answer", JSON.stringify(judge_answer));
                postData.append("fill_in_answer", JSON.stringify(fill_in_answer));
                postData.append("simple_fill_answer", JSON.stringify(simple_fill_answer));
                postData.append("discuess_answer", JSON.stringify(discuess_answer));
                postData.append("noun_analysis_answer", JSON.stringify(noun_analysis_answer));
                postData.append("case_analysis_answer", JSON.stringify(case_analysis_answer));

                $.ajax({
                url: '/exam/start_exam/'+ '{{ Exam.pk }}',
                type: 'POST',
                data: postData,
                cache: false,
                processData: false,
                contentType: false,
                success:function(data){
                    data = JSON.parse(data);
                    if(data.status === 1){
                        $.toptip("提交成功", 'success');
                        window.location.href = '{% url 'exam:index' %}'
                    }else {
                        $.toptip(data.message, 'error');
                        window.location.href = '{% url 'exam:index' %}'
                    }
                },
                error:function () {
                    $.toptip("服务器异常", 'error');
                }
            });
            }, function() {
                $.toptip("取消提交", 'warning');
            });
        });
```
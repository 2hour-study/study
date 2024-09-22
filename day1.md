# 条件查询  
### __语法__：  
select column1,column2,... from table_name where condition;  
查询   列名1,列名2,...     从   数据源     条件为 条件表达式;  
__关键字__：where,in，between(in是集合，between是范围)  
__执行顺序__：from ... where ... select ...
### 日期类型：  
  #### 获取当前时间：  
    sysdate:日期类型  
    systimestamp：时间戳类型  
    select sysdate,systimestamp from dual; 从临时表中获得时间类型和时间戳。
  #### 转换函数  
    __字符串转日期__ : to_date('日期格式的字符串','日期格式')  
      日期格式： 
        yyyy:四位数的年  
        mm  :两位数的月  
        dd  :日  
        select to_date('2023/02/28','yyyy/mm/dd') from dual;
        
    __日期转字符串__ : to_char(日期类型的参数,'日期格式')
        select to_char(to_date('2023/02/28','yyyy/mm/dd'),'yyyy/mm/dd') from dual;
        select to_char(sysdate,'yyyy/mm/dd') from dual;


# Django 存取資料庫

py manage.py migrate (**執行資料庫遷移命令**)

建立內建 APP 所需之資料表


![image](https://github.com/YueYue32/Django_Learning/blob/main/10.%20Django%20%E5%AD%98%E5%8F%96%E8%B3%87%E6%96%99%E5%BA%AB/1.png)


#


進入MYSQL，進去後就會看見多了一些東西


![image](https://github.com/YueYue32/Django_Learning/blob/main/10.%20Django%20%E5%AD%98%E5%8F%96%E8%B3%87%E6%96%99%E5%BA%AB/2.png)


#


改動資料模型 models.py

資料模型預設是以應用程式作為對應的單位，開啟 myapp/models.py

<br>

並且在裡面建立一個資料表，如下

from django.db import models
from django.utils import timezone


    class student(models.Model):
        SEX_CHOICES = [
            ('M', '男'),
            ('F', '女'),
        ]
        cName = models.CharField('姓名',max_length=20, null=False)
        cSex = models.CharField('性別',max_length=1, choices=SEX_CHOICES, default='', null=False)
        cBirthday = models.DateField('生日',null=False)
        cEmail = models.EmailField('Email',max_length=100, blank=True, default='')
        cPhone = models.CharField('手機',max_length=50, blank=True, default='')
        cAddr = models.CharField('地址',max_length=255, blank=True, default='')
        last_modified = models.DateTimeField('最後修改日期', auto_now = True)
        created = models.DateTimeField('保存日期',default = timezone.now)
    
        def __str__(self):
            return self.cName


儲存後，此時已完成異動，也就是發生了更改動作，此時資料庫尚未發生改變


#



![image](https://github.com/YueYue32/Django_Learning/blob/main/10.%20Django%20%E5%AD%98%E5%8F%96%E8%B3%87%E6%96%99%E5%BA%AB/3.png)



#




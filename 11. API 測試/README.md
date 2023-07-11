# API 測試

重要：後面會用到

完成上述 ORM 設定後，Django 會自動產生可用於資料表 CRUD 的 API

![image](https://github.com/YueYue32/Django_Learning/blob/main/11.%20API%20%E6%B8%AC%E8%A9%A6/1.png)


#


以互動模式測試 API

以下述指令進入 Python 的互動模式進行測試

(django) C:\Users\******\django_test\myweb>py manage.py shell

進入後，可輸入以下>>>之後的指令，測試資料庫 API (測試都正常)


    >>> from myapp.models import student
    >>> from django.utils import timezone
    >>> student.objects.all()
    <QuerySet []>
    >>> s1 = student(cName="Kevin", cSex="M", cBirthday='1995-05-23', cEmail="kevin@student.ncut.edu.tw", cPhone="0937-123456", cAddr="臺中市和平街13號", last_modified=timezone.now(),created=timezone.now())
    >>> s1.save()
    >>> s1.id
    1
    >>> s1.cBirthday
    '1995-05-23'
    >>> s1.cName
    'Kevin'
    >>> s1.cName = "John"
    >>> s1.cName
    'John'
    >>> student.objects.order_by('id')
    <QuerySet [<student: Kevin>]>
    >>> s1.save()
    >>> student.objects.order_by('-id')
    <QuerySet [<student: John>]>
    >>>student.objects.get(cName="John")
    <student: John>
    >>> student.objects.filter(cName="John")
    <QuerySet [<student: John>]>
    >>> s1.delete()
    (1, {'myapp.student': 1})

<br>

![image](https://github.com/YueYue32/Django_Learning/blob/main/11.%20API%20%E6%B8%AC%E8%A9%A6/2.png)

<br>

執行完”s1.save()”之後，先進資料庫看看是否有成功寫入(成功)

![image](https://github.com/YueYue32/Django_Learning/blob/main/11.%20API%20%E6%B8%AC%E8%A9%A6/3.png)


#


補充：

把上面指令一條條條分清楚

    
    # import會用到的套件
    >>> from myapp.models import student
    >>> from django.utils import timezone


重點：

        >>> student.objects.all()
        <QuerySet []> #回傳資料類型


object是Manager類型的對象

定義在from django.db import models中，是默認生成的，也就是objects = Modes.Manage() 。用途是數據庫和模型對象交互的接口(api)

<br>


因為這時是透過”Django”連結MYSQL資料庫，所以如果要對資料庫進行操作 查詢、新增、刪除等動作，都需要先經過”Django”的處理，也就是”object”

XXX.objects.all()：

all 會返回 “QuerySet” (<QuerySet []>)

程序並沒有真的在數據庫中執行SQL語句查詢數據

功能為取得所有資料(包含欄位)

“QuerySet”是什麼?

QuerySet在Django框架下，代表的是資料庫裡面的資料集合

比較實際的說法，QuerySet就是對應資料表(Table)上的所有資料紀錄


#


已經使用”object.all()”，透過”django”連結到MYSQL資料庫

接下來就可以開始對資料庫進行操作


        s1 = student(cName="Kevin", 
        cSex="M", 
        cBirthday='1995-05-23', 
        cEmail="kevin@student.ncut.edu.tw", 
        cPhone="0937-123456", 
        cAddr="臺中市和平街13號", 
        last_modified=timezone.now(),
        created=timezone.now())
        
        >>> s1.save()

<br>

student是前面建立資料庫的class 名稱,後面(按照資料庫欄位順序)新增資料

注意：

前面資料欄位的設定，cBirthday = models.DateField('生日',null=False)

設定DateField屬性，填寫格式是西元-月份-日期

例如：'1995-05-23'


![image](https://github.com/YueYue32/Django_Learning/blob/main/11.%20API%20%E6%B8%AC%E8%A9%A6/4.png)


<br>

重要：


        s1.save()


新增完資料之後，一定要儲存(.save())，不然不會寫入資料庫


#






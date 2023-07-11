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


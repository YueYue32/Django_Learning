# API 測試 新增自定義查詢集

原本只有繼承自models.Manager這個預設的管理器類別 objects.get()、objects.filter()等等

如果沒有指定objects的話，Django預設會使用models.Manager來做為該模型的管理器

(就是沒有使用自定義的objects)

如果平時有幾個很常用的查詢條件

那可以建立那些查詢條件的查詢器，這樣就不用每次查詢都要輸入條件式

假設 很常查詢student資料中，誰是男生

那麼條件式就會是student.objects.filter(`cSex__contains = "M"`)

假設 很常查詢student資料中，誰住台北

那麼條件式就會是student.objects.filter(`cAddr__contains = '台北'`)

每次都要輸入一堆，很麻煩


#


那來定義一個專門用來查詢性別(cSex)、查詢住址(cAddr)的查詢指令

C:\Users\ ****\django_test\myweb\myapp\models.py

 新增在 class student(models.Model): 的前面 

第8~23行

    # 自定義查詢 search_cSex
    # get_queryset 是繼承models.Manager內的指令，不能亂改
    # super()呼叫父類別search_cSex
    # 後面再銜接get_queryset.filter(條件)
    class search_cSex(models.Manager):
        def get_queryset(self):
            return super(search_cSex,self).get_queryset().filter(cSex__contains = "M")
    
    
    # 自定義查詢 search_cAddr
    # get_queryset 是繼承models.Manager內的指令，不能亂改
    # super()呼叫父類別search_cAddr
    # 後面再銜接get_queryset.filter(條件)
    class search_cAddr(models.Manager):
        def get_queryset(self):
            return super(search_cAddr,self).get_queryset().filter(cAddr__contains = '台北')


<br>


原始查詢集是我們利用全查詢得到的查詢集 “objects.all()”

不過只要透過get_queryset方法就能改變原始查詢集，使用多個不同管理器時，這樣才不會跟原始查詢集的指令衝突


#


第41~43行

    # Create your models here.
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
        last_modified = models.DateTimeField('最后修改日期', auto_now = True)
        created = models.DateTimeField('保存日期',default = timezone.now)
        objects = models.Manager()
        obj_cSex = search_cSex()
        obj_cAddr = search_cAddr()

<br>

注意：

如果有用到自定義管理器，原始的objects一定要賦值，不然會導致該模型不存在objects管理器 (objects = models.Manager())


#


進入 Python 的互動模式進行測試

(django) C:\Users\ *****\django_test\myweb>py manage.py shell


    (django) C:\Users\ *****\django_test\myweb>py manage.py shell
    Python 3.7.0 (default, Jun 28 2018, 08:04:48) [MSC v.1912 64 bit (AMD64)] on win32
    Type "help", "copyright", "credits" or "license" for more information.
    (InteractiveConsole)
    
    >>> from myapp.models import student
    >>> from django.utils import timezone
    >>> student.objects.all()
    <QuerySet [<student: Kevin>, <student: evan>, <student: lu>, <student: linc>, <student: ee>]>
    >>>


<br>

先看看有哪些資料

![image](https://github.com/YueYue32/Django_Learning/blob/main/16.%20API%20%E6%B8%AC%E8%A9%A6%20%E6%96%B0%E5%A2%9E%E8%87%AA%E5%AE%9A%E7%BE%A9%E6%9F%A5%E8%A9%A2%E9%9B%86/1.png)


#


發現有一筆資料有錯，改

    # 先找出內部資料有問題的那筆資料
    >>> s6 = student.objects.get(cName="hata")
    
    # 確認有誤的資料
    >>> s6.cSex  
    'M'
    
    # 改成正確的
    >>> s6.cSex = "F"
    
    # 記得存檔 
    >>> s6.save()
    
    # 確認改變                        
    >>> s6.cSex   
    'F'


#


輸入 

    student.obj_cSex.all()

![image](https://github.com/YueYue32/Django_Learning/blob/main/16.%20API%20%E6%B8%AC%E8%A9%A6%20%E6%96%B0%E5%A2%9E%E8%87%AA%E5%AE%9A%E7%BE%A9%E6%9F%A5%E8%A9%A2%E9%9B%86/2.png)

顯示的資料，內部cSex資料都是”F”(男性)


#


輸入 

    student.obj_cAddr.all()

![image](https://github.com/YueYue32/Django_Learning/blob/main/16.%20API%20%E6%B8%AC%E8%A9%A6%20%E6%96%B0%E5%A2%9E%E8%87%AA%E5%AE%9A%E7%BE%A9%E6%9F%A5%E8%A9%A2%E9%9B%86/3.png)


顯示的資料，內部cAddr資料都是”台北”

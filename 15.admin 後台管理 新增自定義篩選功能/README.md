# admin 後台管理 新增自定義篩選功能


C:\Users\ *****\django_test\myweb\myapp/admin.py

第6行 新增

    from django.utils.translation import gettext_lazy as _


#

第12~27行 新增

    # 定義一個class 後面參數很重要 ，admin.SimpleListFilter = 自定義查詢的過濾器
    # 內部title、parameter_name都是繼承自admin.SimpleListFilter，不能隨意亂換變數名稱
    class Morethan4(admin.SimpleListFilter):
        title = _('id')    # 顯示在頁面上，該過濾器的標題 (以id，"以"是系統預設字)
        parameter_name = 'compareid'  # parameter_name為載入頁面時url中攜帶的引數名稱，方便觀看/辨識你的選項功能
    
    
    		# 繼承自admin裡面的元組功能名稱lookups，不能隨意更換變數名稱
    		# 回傳值格式：
    		# return (
        #       ('上方網址字串1', _('右側篩選器字串1')),  
        #       ('上方網址字串2', _('右側篩選器字串2')),
        #    )
    		# 篩選器字串會顯示在頁面右側
    
        def lookups(self, request, model_admin):
            return (
                ('>4', _('id > 4')),  
                ('<4', _('id < 4')),
            )
    
        # 定義查詢時的過濾條件，名稱同"lookups"
    		# if self.value() == '網址字串1':
    		# 回傳符合條件的資料
    		# return queryset.filter(看你想要找什麼樣的條件)
    		# filter條件可以觀看前面學習檔案，在"API 測試"裡面
        def queryset(self, request, queryset):
            if self.value() == '>4':
                return queryset.filter(id__gt=3)
            if self.value() == '<4':
                return queryset.filter(id__lt=4)


#


執行後，畫面右側出現過濾器

![image](https://github.com/YueYue32/Django_Learning/blob/main/15.admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86%20%E6%96%B0%E5%A2%9E%E8%87%AA%E5%AE%9A%E7%BE%A9%E7%AF%A9%E9%81%B8%E5%8A%9F%E8%83%BD/1.png)


#


第35行

新增篩選器list_filter

    class studentAdmin(admin.ModelAdmin):
        list_display=('id','cName','cSex','cBirthday','cEmail','cPhone',)
        # list_filter=('cSex',)
        search_fields=('cName','cEmail','cPhone',)
        ordering=('id','cName',)
        list_filter = (Morethan4,)


#

測試結果

一開始的頁面，資料是我隨便輸入的，不重要，只要id都不同就好

可以看到網址是 http://127.0.0.1:8000/admin/myapp/student/

並且畫面右側有顯示篩選器

![image](https://github.com/YueYue32/Django_Learning/blob/main/15.admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86%20%E6%96%B0%E5%A2%9E%E8%87%AA%E5%AE%9A%E7%BE%A9%E7%AF%A9%E9%81%B8%E5%8A%9F%E8%83%BD/2.png)


#


點擊 “>4”

可以看到網址發生改變

變成[http://127.0.0.1:8000/admin/myapp/student/?compareid=>4](http://127.0.0.1:8000/admin/myapp/student/?compareid=%3E4)

類似之前使用postman查詢資料的用法


![image](https://github.com/YueYue32/Django_Learning/blob/main/15.admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86%20%E6%96%B0%E5%A2%9E%E8%87%AA%E5%AE%9A%E7%BE%A9%E7%AF%A9%E9%81%B8%E5%8A%9F%E8%83%BD/3.png)


#


點擊 “<4”
可以看到網址發生改變

變成[http://127.0.0.1:8000/admin/myapp/student/?compareid=<4](http://127.0.0.1:8000/admin/myapp/student/?compareid=%3E4)

類似之前使用postman查詢資料的用法


![image](https://github.com/YueYue32/Django_Learning/blob/main/15.admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86%20%E6%96%B0%E5%A2%9E%E8%87%AA%E5%AE%9A%E7%BE%A9%E7%AF%A9%E9%81%B8%E5%8A%9F%E8%83%BD/4.png)

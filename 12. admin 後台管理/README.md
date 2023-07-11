# admin 後台管理


Django 會自動建立管理的後台

具體來說就是透過 admin 應用程式管理 db.sqlite3 內的使用者、群組與對應模型的資料表。


#

建立管理員帳號：

請輸入以下指令進行管理員帳號的建立


    (django) C:\Users\*****\django_test\myweb>py manage.py createsuperuser


#

並依序輸入：

使用者名稱：預設會帶出目前登入的使用者名稱。

電子信箱。

密碼：輸入至少8碼包含文數字的密碼2次，若不符合系統會問你是否略過此項驗證。


<br>

密碼不會顯示出來，要記得自己輸入了什麼，我密碼跟使用者名稱一樣，所以跳出訊息，不過只是測試，所以不管他

不管他，按y

![image](https://github.com/YueYue32/Django_Learning/blob/main/12.%20admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86/1.png)


#

啟動伺服器並打開 admin 頁面：

輸入以下指令啟動開發伺服器：

    (django) C:\Users\******\django_test\myweb>py manage.py runserver


<br>

打開瀏覽器，輸入網址：http://127.0.0.1:8000/admin/，再輸入上一步驟建立的管理員帳密

![image](https://github.com/YueYue32/Django_Learning/blob/main/12.%20admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86/2.png)


#


向 admin 頁面註冊自訂的應用程式模型

開啟 myapp\admin.py，填入以下第 3 行之後的程式碼
    
    # Register your models here.
    from myapp.models import student
    
    admin.site.register(student)


<br>

回到剛剛開啟的 admin 頁面，按下 F5 重新載入頁面，會看到增加了的應用程式模型


#


新增與變更資料

按下 Students 的 “+新增”

![image](https://github.com/YueYue32/Django_Learning/blob/main/12.%20admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86/3.png)


#


嘗試儲存一筆資料

![image](https://github.com/YueYue32/Django_Learning/blob/main/12.%20admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86/4.png)


#

儲存後，會跳到可異動資料的畫面

![image](https://github.com/YueYue32/Django_Learning/blob/main/12.%20admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86/5.png)


#


admin 頁面顯示多個欄位

如果要在 admin 的後台，一次看到多個欄位並設定欄位的過濾、搜尋與排序

則必須在 myapp\admin.py 中定義 ModelAdmin 類別，再以 list_display 變數定義想要顯示的欄位，然後透過 register 方法註冊。

開啟 myapp\admin.py，填入以下第 3 行之後的程式碼

    # Register your models here.
    from myapp.models import student
    
    # admin.site.register(student) # 最簡易的顯示
    
    class studentAdmin(admin.ModelAdmin):
        list_display=('id','cName','cSex','cBirthday','cEmail','cPhone',)
        list_filter=('cSex',)
        search_fields=('cName','cEmail','cPhone',)
        ordering=('id','cName',)
    
    admin.site.register(student, studentAdmin)


<br>


回到剛剛開啟的 admin 頁面，按下 F5 重新載入頁面，會看到 admin 頁面顯示了多個欄位、搜尋框以及過濾器

![image](https://github.com/YueYue32/Django_Learning/blob/main/12.%20admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86/6.png)


#


補充：

說明上面class studentAdmin(admin.ModelAdmin): 內各項變數、指令、功能


<br>


admin.ModelAdmin

admin管理功能與自定義ModelAdmin類別

admin管理平台的功能或是頁面呈現的樣子都是預設的，但我們其實可以針對我們理想中的介面進行客製化。

這有賴於註冊模型於admin上時，要採用繼承於ModelAdmin的自定義類別。


<br>


繼承自admin.ModelAdmin的studentAdmin類別，有限制”元組變數”的名稱，以下皆為ModelAdmin內預設的名稱，不能隨意亂命名


<br>


list_display

此元組裡面的每個元素都是一個字串而且要是模型欄位的名字。只要有指定在此元組的欄位，都會被顯示在admin中的全檢視頁面中，更方便的是，點擊列表的欄位名，會自動進行排序


<br>


list_filter

過濾器，出現在網頁畫面的最右側

點選選項，可篩選出符合的資料


<br>

search_fields
搜尋功能

![image](https://github.com/YueYue32/Django_Learning/blob/main/12.%20admin%20%E5%BE%8C%E5%8F%B0%E7%AE%A1%E7%90%86/7.png)


在這個框框裡面輸入搜尋文字

效果等同於在資料庫中輸入

”select * from <table_name> WHERE ( cName ILIKE ‘你輸入的文字' OR cEmail ILIKE '你輸入的文字' OR cPhone ILIKE ‘你輸入的文字')”

也就搜尋符合指定條件的欄位值

ILIKE  為輸入文字不分大小寫，皆會搜尋到


#


ordering

設定ordering元組，指定欄位名稱，資料便會依照指定欄位進行排序，加入一個減號可以實現降序排序


#


admin.site.register(student, studentAdmin)

透過admin.site.register方法，便可以在admin介面中新增、檢視、編輯、刪除我們模型中的資料。當然我們要記得匯入admin本身(預設)還有各項想註冊的模型。

括號內參數是 (資料,模型)

都要放入才會都顯示


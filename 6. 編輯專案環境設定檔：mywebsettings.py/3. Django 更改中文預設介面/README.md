# Django 更改中文預設介面


C:\Users\226083\django_test\myweb\myweb\setting.py 

第106行：語言設定

第108行：時區設定

![image](https://github.com/YueYue32/Django_Learning/blob/main/6.%20%E7%B7%A8%E8%BC%AF%E5%B0%88%E6%A1%88%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%E6%AA%94%EF%BC%9Amywebsettings.py/3.%20Django%20%E6%9B%B4%E6%94%B9%E4%B8%AD%E6%96%87%E9%A0%90%E8%A8%AD%E4%BB%8B%E9%9D%A2/4.png)


<br>
改成

    #修改預設語言為<繁體中文>
    LANGUAGE_CODE = 'zh-hant'
    #修改時區為<亞洲/台北>
    TIME_ZONE = 'Asia/Taipei'

![image](https://github.com/YueYue32/Django_Learning/blob/main/6.%20%E7%B7%A8%E8%BC%AF%E5%B0%88%E6%A1%88%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%E6%AA%94%EF%BC%9Amywebsettings.py/3.%20Django%20%E6%9B%B4%E6%94%B9%E4%B8%AD%E6%96%87%E9%A0%90%E8%A8%AD%E4%BB%8B%E9%9D%A2/5.png)


#


再次 “啟動網頁伺服器進行測試”

進入專案目錄 myweb

        cd myweb

啟動 web server

        py manage.py runserver 


<br>
以瀏覽器開啟 http://127.0.0.1:8000/

將出現以下畫面，可按 Ctrl + C 終止執行(在Anaconda prompt裡面按下終止指令)

![image](https://github.com/YueYue32/Django_Learning/blob/main/6.%20%E7%B7%A8%E8%BC%AF%E5%B0%88%E6%A1%88%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%E6%AA%94%EF%BC%9Amywebsettings.py/3.%20Django%20%E6%9B%B4%E6%94%B9%E4%B8%AD%E6%96%87%E9%A0%90%E8%A8%AD%E4%BB%8B%E9%9D%A2/6.png)

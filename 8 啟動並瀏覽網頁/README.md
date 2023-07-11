# 啟動並瀏覽網頁

    py manage.py runserver

![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/1.png)


#


先來查看之前寫了什麼

urls.py 檔案，寫入哪些網址對應哪些功能

![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/2.png)


#


path('', views.home)

<br>

雙引號內是空字串，表示就是直接貼上預設網址 http://127.0.0.1:8000/

網址後面什麼都不加 ，對應到views.py裡面的 “home”功能

<br>

“home”功能(在myapp\views.py)：

![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/3.png)


#


path('hi/<username>/', views.hiname), # 傳遞字串參數 username

傳遞字串參數 username 是什麼?

<br>


來看看views.py中，”hiname”功能的內容
![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/5.png)


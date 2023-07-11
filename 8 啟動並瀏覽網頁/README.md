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


![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/4.png)



#


path('hi/<username>/', views.hiname), # 傳遞字串參數 username

傳遞字串參數 username 是什麼?

<br>


來看看views.py中，”hiname”功能的內容

![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/5.png)

功能 “hiname”，有個外部參數，在網址後面加入的 <username>，就是這邊的參數username


#


'hi/<username>/ ‘

引號內的 hi/<username>/ ，表示在預設網址後面加入這個字串

後面的<username>/，用<>括起來的部分，表示是user要自己手動輸入(輸入的是名稱)

例如輸入evan，完整網址為http://127.0.0.1:8000/hi/evan


![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/6.png)


#


ath('age/int:year/', views.age), # 傳遞數值參數 year

‘age/int:year’

同理，不過參數year多了轉換成數值的部分(int)，後續再轉換成字串


![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/7.png)


![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/8.png)



#







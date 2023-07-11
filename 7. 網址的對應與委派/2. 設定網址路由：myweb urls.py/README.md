# 設定網址路由：myweb/urls.py
<br>

    from django.contrib import admin
    from django.urls import path,include
    from myapp import views
    
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', views.home),
        path('hi/<username>/', views.hiname),      # 傳遞字串參數 username
        path('age/<int:year>/', views.age),        # 傳遞數值參數 year
        path('hello/', views.hello_view),
        # path(r'^admin/', admin.site.urls),
        # path(r'^$', sayhello),
    ]


#

http://127.0.0.1:8000/

![image](https://github.com/YueYue32/Django_Learning/blob/main/7.%20%E7%B6%B2%E5%9D%80%E7%9A%84%E5%B0%8D%E6%87%89%E8%88%87%E5%A7%94%E6%B4%BE/2.%20%E8%A8%AD%E5%AE%9A%E7%B6%B2%E5%9D%80%E8%B7%AF%E7%94%B1%EF%BC%9Amyweb%20urls.py/1.png)









![image](https://github.com/YueYue32/Django_Learning/blob/main/7.%20%E7%B6%B2%E5%9D%80%E7%9A%84%E5%B0%8D%E6%87%89%E8%88%87%E5%A7%94%E6%B4%BE/2.%20%E8%A8%AD%E5%AE%9A%E7%B6%B2%E5%9D%80%E8%B7%AF%E7%94%B1%EF%BC%9Amyweb%20urls.py/2.png)







![image](https://github.com/YueYue32/Django_Learning/blob/main/7.%20%E7%B6%B2%E5%9D%80%E7%9A%84%E5%B0%8D%E6%87%89%E8%88%87%E5%A7%94%E6%B4%BE/2.%20%E8%A8%AD%E5%AE%9A%E7%B6%B2%E5%9D%80%E8%B7%AF%E7%94%B1%EF%BC%9Amyweb%20urls.py/3.png)




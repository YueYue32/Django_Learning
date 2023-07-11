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

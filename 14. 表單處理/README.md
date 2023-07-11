# 表單處理

單純傳送欄位變數的表單

新增一個內含表單的子網頁 login.html ，留意表單的傳送處為/login/


C:\Users\ *****\django_test\myweb\templates\login.html


    {% extends 'base.html'%}
    
    {% block title %}使用者登入{% endblock %}
    
    {% block main %}
        <h1>使用者登入</h1>
        <form action="/login/" method="post">
            {% csrf_token %}
            <label for="uName">名稱：</label>
            <input id="uName" type="text" name="uName">
            <label for="uPass">密碼：</label>
            <input id="uPass" type="text" name="uPass">
            <input type="submit" value="送出">
        </form>
    {% endblock %}


#


C:\Users\ *****\django_test\myweb\myweb\urls.py

    
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', views.main),
        path('hi/<username>/', views.hiname),      # 傳遞字串參數 username
        path('age/<int:year>/', views.age),        # 傳遞數值參數 year
        path('hello/', views.hello_view),
        path('getName/<username>/', views.getOneByName), # 傳遞字串參數 username
        path('getAll/', views.getAll),
        path('login/', views.login),
        # path(r'^admin/', admin.site.urls),
        # path(r'^$', sayhello),
    ]


#


C:\Users\226083\django_test\myweb\myapp\views.py

修改第 1 行敘述，多了 redirect
增加第 6 行敘述

    
    from django.shortcuts import render, redirect
    from django.http import HttpResponse
    from datetime import datetime
    from myapp.models import student
    from django.http import Http404
    from django.contrib import auth

# 模板繼承


通常一個網站都會規劃相同的顏色、主頁標題、主頁結尾作為母版(或稱骨架)，然後讓所有的頁面繼承這個母版，就會有同樣的風格，未來只要修改母版就能快速更換網站風格


#

母版設計：

C:\Users\*****\django_test\myweb\static\css\style.css

覆蓋掉之前的內容


    header {
      padding: 60px;
      text-align: center;
      background: #1abc9c;
      color: white;
      font-size: 30px;
      display: flex;
      justify-content: space-between;
    }
    
    footer {
      padding: 20px;
      text-align: center;
      color: white;
      background-color: indigo;
    }
    
    main {
      margin: 0 auto;
      padding: 18px;
    }
    
    .info {color:red;}


#


C:\Users\*****\django_test\myweb\templates\base.html

title、main作為子網頁繼承之用


    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      {% load static %}
      <link href="{% static 'css/style.css'%}" rel="stylesheet">
      <title>{% block title %}{% endblock %}</title>
    </head>
    <body>
      <header>
        <h1>主頁標題</h1>
        <p>副標題</p>
      </header>
      <main>
        {% block main %}{% endblock %}
      </main>
      <footer>
        <h2>主頁結尾</h2>
      </footer>
    </body>
    </html>


#


C:\Users\*****\django_test\myweb\templates\index.html


    {% extends 'base.html'%}
    
    {% block title %}{{pageTitle}}{% endblock %}
    
    {% block main %}
        <h1>{{mainTitle}}</h1>
        <p>{{mainContent}}</p>
        {% if artitles %}
            {% for i in artitles %}
            <article>
                <h2>{{i.aTitle}}</h2>
                <p>{{i.aContent}}</p>
            </article>
            {% endfor %}
        {% else %}
            <p>沒有資料</p>
        {% endif %}
    {% endblock %}


#


日後子網頁只要描述以下三大區塊即可

使用 extends 繼承母版 base.html

使用 block title 填寫子網頁標題

使用 block main 填寫子網頁內容


#

調整路由(urls.py)與視圖(views.py)

調整 myweb/urls.py

第 22 行 的 views.home 更改為 views.main


    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', views.main),
        path('hi/<username>/', views.hiname),      # 傳遞字串參數 username
        path('age/<int:year>/', views.age),        # 傳遞數值參數 year
        path('hello/', views.hello_view),
        path('getName/<username>/', views.getOneByName), # 傳遞字串參數 username
        path('getAll/', views.getAll),
        # path(r'^admin/', admin.site.urls),
        # path(r'^$', sayhello),
    ]


#


調整 myapp/views.py

增加第 53 行的 main 函數

render()的第3個參數 locals()，可將所有區域變數轉為字典


    def main(request):
        pageTitle="子網頁繼承"
        mainTitle="段落標題"
        mainContent="段落內文"
        artitle1={"aTitle":"文章標題","aContent":"文章1內文"}
        artitle2={"aTitle":"文章標題","aContent":"文章2內文"}
        artitles=[artitle1, artitle2]
        return render(request, 'index.html', locals())


#


瀏覽測試

啟動 web server

    (django) C:\Users\*****\django_test\myweb>py manage.py runserver


#


http://127.0.0.1:8000/

變成設計出來的版型


![image](https://github.com/YueYue32/Django_Learning/blob/main/13.%E6%A8%A1%E6%9D%BF%E7%B9%BC%E6%89%BF/1.png)


#


補充：

<footer> 頁尾

Footer 常駐於每個網頁底部，在主體內容下方，他就像是一個導航系統，他能夠短促的告訴使用者網站提供的服務

類似這個，很多網頁底下會有的功能、服務、選項


![image](https://github.com/YueYue32/Django_Learning/blob/main/13.%E6%A8%A1%E6%9D%BF%E7%B9%BC%E6%89%BF/2.png)


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


path('hello/', views.hello_view)


![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/9.png)


<br>


hello_view功能內容較多，來一個個分析


        def hello_view(request):
        
        		# fourSeason 為數值1~4
            fourSeason = range(1, 5)
        
        		# p1、p2、p3 分別是3個dictionary資料
            p1 = {"name": "Amy", "phone": "0912-345678", "age": 20}
            p2 = {"name": "Jack", "phone": "0937-123456", "age": 25}
            p3 = {"name": "Nacy", "phone": "0958-654321", "age": 17}
        
        		# 用個變數"persons"，儲存上面3筆資料，整體變成list型態
            persons = [p1, p2, p3]
        
        
        		# 補充 render()函式：用於封裝整體網頁內會需要的參數，其中的"request"是必加的
        		# request, 'hello_django.html'，表示取得來源名稱是'hello_django.html'的檔案
        		# 上述檔案放置路徑為 "C:\Users\226083\django_test\myweb\templates"
        
        		# 回傳
            return render(request, 'hello_django.html', {
                'title': "樣板使用",
                'data': "Hello Django!",
                'seasons': fourSeason,
                'persons': persons,
                'now': datetime.now()
            })


<br>


        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta http-equiv="X-UA-Compatible" content="IE=edge">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>{{title}}</title>
            {% load static %}
            <link href="{% static 'css/style.css'%}" rel="stylesheet">
        </head>
        <body>
            <h1>{{data}}</h1>
            <h2>季統計</h2>
            {% if seasons %}
                <ul>
                {% for i in seasons %}
                    <li>{{i}}</li>
                {% endfor %}
                </ul>
            {% else %}
                <p>沒有資料</p>
            {% endif %}
            <h2>人員清單</h2>
            {% if persons %}
            <table border="1">
        				<tr>
        				<!--這層td可以換成tr-->
                    <td>name</td>
                    <td>phone</td>
                    <td>age</td>
                </tr>
            {% for person in persons %}
                <tr>
                    <td>{{person.name}}</td>
                    <td>{{person.phone}}</td>
                    <td>{{person.age}}</td>
                </tr>
            {% endfor %}
            </table>
            {% else %}
                <p>沒有資料</p>
            {% endif %}
            <img src="{% static 'images/py-django.png' %}" alt="python/django">
            <p>現在時刻：<span class="info">{{now}}</span></p>
        </body>
        </html>


<br>

![image](https://github.com/YueYue32/Django_Learning/blob/main/8%20%E5%95%9F%E5%8B%95%E4%B8%A6%E7%80%8F%E8%A6%BD%E7%B6%B2%E9%A0%81/10.png)

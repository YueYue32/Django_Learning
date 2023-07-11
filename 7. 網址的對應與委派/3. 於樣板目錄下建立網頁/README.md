# 於樣板目錄下建立網頁

下載靜態圖片，並放進 “static\images” 目錄下

靜態圖片：

![image](https://github.com/YueYue32/Django_Learning/blob/main/7.%20%E7%B6%B2%E5%9D%80%E7%9A%84%E5%B0%8D%E6%87%89%E8%88%87%E5%A7%94%E6%B4%BE/3.%20%E6%96%BC%E6%A8%A3%E6%9D%BF%E7%9B%AE%E9%8C%84%E4%B8%8B%E5%BB%BA%E7%AB%8B%E7%B6%B2%E9%A0%81/py-django.png)

<br>

![image](https://github.com/YueYue32/Django_Learning/blob/main/7.%20%E7%B6%B2%E5%9D%80%E7%9A%84%E5%B0%8D%E6%87%89%E8%88%87%E5%A7%94%E6%B4%BE/3.%20%E6%96%BC%E6%A8%A3%E6%9D%BF%E7%9B%AE%E9%8C%84%E4%B8%8B%E5%BB%BA%E7%AB%8B%E7%B6%B2%E9%A0%81/1.png)


#

插播：

如何建立css、html檔案?

A：https://progressbar.tw/posts/104


記得先下載”Brackets”

檔案副檔名記得要加上.html、或是.css

例如：hello_django.html、style.css

#

在 static\css 目錄下，建立 style.css 樣式檔，內容如下：


    .info {color:red;}

<br>

![image](https://github.com/YueYue32/Django_Learning/blob/main/7.%20%E7%B6%B2%E5%9D%80%E7%9A%84%E5%B0%8D%E6%87%89%E8%88%87%E5%A7%94%E6%B4%BE/3.%20%E6%96%BC%E6%A8%A3%E6%9D%BF%E7%9B%AE%E9%8C%84%E4%B8%8B%E5%BB%BA%E7%AB%8B%E7%B6%B2%E9%A0%81/2.png)


# 

<br>
在 templates 樣板目錄下新增一個 hello_django.html

Template 內的 {{變數}} 會透過 views.py 將變數傳送過來

![image](https://github.com/YueYue32/Django_Learning/blob/main/7.%20%E7%B6%B2%E5%9D%80%E7%9A%84%E5%B0%8D%E6%87%89%E8%88%87%E5%A7%94%E6%B4%BE/3.%20%E6%96%BC%E6%A8%A3%E6%9D%BF%E7%9B%AE%E9%8C%84%E4%B8%8B%E5%BB%BA%E7%AB%8B%E7%B6%B2%E9%A0%81/3.png)

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

    

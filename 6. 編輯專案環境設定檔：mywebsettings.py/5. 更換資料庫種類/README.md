# 更換資料庫種類

setting.py 文件中，預設的資料庫種類是”sqlite”

![image](https://github.com/YueYue32/Django_Learning/blob/main/6.%20%E7%B7%A8%E8%BC%AF%E5%B0%88%E6%A1%88%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%E6%AA%94%EF%BC%9Amywebsettings.py/5.%20%E6%9B%B4%E6%8F%9B%E8%B3%87%E6%96%99%E5%BA%AB%E7%A8%AE%E9%A1%9E/7.png)


<br>
<br>

改成"MYSQL"
![image](https://github.com/YueYue32/Django_Learning/blob/main/6.%20%E7%B7%A8%E8%BC%AF%E5%B0%88%E6%A1%88%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%E6%AA%94%EF%BC%9Amywebsettings.py/5.%20%E6%9B%B4%E6%8F%9B%E8%B3%87%E6%96%99%E5%BA%AB%E7%A8%AE%E9%A1%9E/8.png)


    DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',  # 指定使用mysql資料庫
        'NAME': 'django_test',  # 資料庫名字 不要用"new_1"，裡面有其他之前的測試資料，會搞亂
        'USER': "root",  # mysql user名稱
        'PASSWORD': 'allen33323',  # 資料庫的密碼
        'HOST': "localhost",  # 資料庫服務地址，填本地地址
        'PORT': 3306,   # mysql 對應的埠號，MYSQL的登入區塊中看的到這數值
        'default-character-set': "UTF8",  # 設定編碼規則 utf8
    }
}


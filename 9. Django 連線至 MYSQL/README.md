# Django 連線至 MYSQL


預設情況下，Django 使用 SQLite 資料庫，如下


    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': BASE_DIR / 'db.sqlite3',
        }
    }

#


<br>

要將設定改成MYSQL資料庫


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


#


Anaconda：

pip install PyMySQL


#


在”setting.py” 同級的 __init__.py檔案中 加入一段code：


    import pymysql
    pymysql.install_as_MySQLdb()


#


在”setting.py”中的”INSTALLED_APPS”加入一段code：


    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'myapp.apps.MyappConfig'
    ]

myapp指”myapp”資料夾、apps指該資料夾中的apps.py檔案，MyappConfig指該檔案中的class

這段很重要，如果沒加，後續執行 “py [manage.py](http://manage.py/) makemigrations myapp”後會顯示錯誤

“No installed app with label ‘myapp'.”


#



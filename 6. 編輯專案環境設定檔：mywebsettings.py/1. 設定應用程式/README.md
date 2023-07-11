# 設定應用程式

Django 已預設將常用的 app 設定為 INSTALLED_APPS 


myweb/settings.py
第 40 行，將應用程式” myapp” 設定進去

    INSTALLED_APPS = [
    'django.contrib.admin',        # 管理者後台
    'django.contrib.auth',         # 認證授權管理
    'django.contrib.contenttypes', # 內容類型管理
    'django.contrib.sessions',     # session 管理
    'django.contrib.messages',     # 訊息管理
    'django.contrib.staticfiles',  # 靜態檔案管理
    'myapp',
]


可依需求自行增減設定專案會用到的應用程式。


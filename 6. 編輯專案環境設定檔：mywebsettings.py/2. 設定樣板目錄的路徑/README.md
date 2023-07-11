# 設定樣板目錄的路徑


在settings.py中，對於該專案的基本路徑已經有預設值

    BASE_DIR = os.path.dirname(os.path.dirname(__file__))

<br>



BASE_DIR 指的是 最上層的專案目錄 (”myweb”資料夾)

  os.path.dirname(__file__) 

  執行後會取得 “settings.py”這個檔案 所在子目錄的路徑 (\myweb)

  連續使用兩次得到的路徑，即是 子目錄的目錄 自然就是最上層myweb (\myweb\myweb)  

#

'DIRS': [BASE_DIR / "templates"],

在最上層”myweb”中建立一個目錄”templates”就可以放置所需的樣板了(樣板之後會提到)

![image](https://github.com/YueYue32/Django_Learning/blob/main/6.%20%E7%B7%A8%E8%BC%AF%E5%B0%88%E6%A1%88%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%E6%AA%94%EF%BC%9Amywebsettings.py/2.%20%E8%A8%AD%E5%AE%9A%E6%A8%A3%E6%9D%BF%E7%9B%AE%E9%8C%84%E7%9A%84%E8%B7%AF%E5%BE%91/1.png)


        TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / "templates"],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

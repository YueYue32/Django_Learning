# 設定靜態檔案的路徑

在settings.py中，對於該專案的基本路徑已經有預設值

    BASE_DIR = os.path.dirname(os.path.dirname(__file__))

BASE_DIR 指的是 最上層的專案目錄 (”myweb”資料夾)

<br>

#

新增這兩行

![image](https://github.com/YueYue32/Django_Learning/blob/main/6.%20%E7%B7%A8%E8%BC%AF%E5%B0%88%E6%A1%88%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%E6%AA%94%EF%BC%9Amywebsettings.py/4.%20%E8%A8%AD%E5%AE%9A%E9%9D%9C%E6%85%8B%E6%AA%94%E6%A1%88%E7%9A%84%E8%B7%AF%E5%BE%91/1.png)

<br>


        STATIC_URL = '/static/'

        STATICFILES_DIRS = [
            BASE_DIR / "static",
        ]

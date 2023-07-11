# 建立專案

語法： django-admin startproject <專案名稱>

建立第一個 Django 專案 : myweb

![image](https://github.com/YueYue32/Django_Learning/blob/main/%E5%BB%BA%E7%AB%8B%E5%B0%88%E6%A1%88/1.png)


#

執行後，在”django_test”資料夾中會產生一個”myweb”資料夾(專案目錄)

![image](https://github.com/YueYue32/Django_Learning/blob/main/%E5%BB%BA%E7%AB%8B%E5%B0%88%E6%A1%88/2.png)



內含一個同名的 myweb( 套件目錄)、manage.py檔案

![image](https://github.com/YueYue32/Django_Learning/blob/main/%E5%BB%BA%E7%AB%8B%E5%B0%88%E6%A1%88/3.png)
![image](https://github.com/YueYue32/Django_Learning/blob/main/%E5%BB%BA%E7%AB%8B%E5%B0%88%E6%A1%88/4.png)


# 

__init__ .py：Python 文件，可以將所在目錄內導入Python文件，告訴Python這資料夾是個套件

asgi.py：包含 Django 專案的 *ASGI 配置屬性

settings.py：包含 Django 專案的配置與設定檔

urls.py：包含 Django 專案的各個應用程式(APP)的網址

wsgi.py：含 Django 專案的 *WSGI 配置屬性

manage.py：用來管理整個Django專案，像是啟動本地端伺服器、連接資料庫及建立應用程式(APP)

# 建立應用程式 application (app)

application 可視作為本專案建立的套件，通常會有多個 app 進行搭配，負責不同的功能。

語法：

進入專案目錄 myweb

    cd myweb

建立第一個 Django app : myapp

    py manage.py startapp <app名稱>


![image](https://github.com/YueYue32/Django_Learning/blob/main/4.%20%E5%BB%BA%E7%AB%8B%E6%87%89%E7%94%A8%E7%A8%8B%E5%BC%8F%20application%20(app)/1.png)


#

執行後，打開”myapp”資料夾

”myapp”資料夾為”應用程式套件目錄”

![image](https://github.com/YueYue32/Django_Learning/blob/main/4.%20%E5%BB%BA%E7%AB%8B%E6%87%89%E7%94%A8%E7%A8%8B%E5%BC%8F%20application%20(app)/2.png)


#


__init__ .py ：空文件，代表這個目錄是一個套件

admin.py :設定資料庫呈現的模式，之後會跟models溝通

apps.py：區別app的一個檔案

models.py : 建構你的資料庫型態

tests.py :檢查商業邏輯的地方，用來測試你的邏輯是否有遺漏

views.py :寫商業邏輯的地方

migrations : 資料夾裡面存放的內容，記錄著models裡面所創建的資料庫型態


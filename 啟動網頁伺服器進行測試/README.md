# 啟動網頁伺服器進行測試

進入專案目錄 myweb

    cd myweb

  
啟動 web server

    py manage.py runserver 

  

![image](https://github.com/YueYue32/Django_Learning/blob/main/%E5%95%9F%E5%8B%95%E7%B6%B2%E9%A0%81%E4%BC%BA%E6%9C%8D%E5%99%A8%E9%80%B2%E8%A1%8C%E6%B8%AC%E8%A9%A6/1.png)


#

執行後會產生以下內容
![image](https://github.com/YueYue32/Django_Learning/blob/main/%E5%95%9F%E5%8B%95%E7%B6%B2%E9%A0%81%E4%BC%BA%E6%9C%8D%E5%99%A8%E9%80%B2%E8%A1%8C%E6%B8%AC%E8%A9%A6/2.png)


#

以瀏覽器開啟 http://127.0.0.1:8000/

將出現以下畫面，可按 Ctrl + C 終止執行(在Terminal那邊按)

![image](https://github.com/YueYue32/Django_Learning/blob/main/%E5%95%9F%E5%8B%95%E7%B6%B2%E9%A0%81%E4%BC%BA%E6%9C%8D%E5%99%A8%E9%80%B2%E8%A1%8C%E6%B8%AC%E8%A9%A6/3.png)


#

前述

manage.py：用來管理整個Django專案，像是啟動本地端伺服器、連接資料庫及建立應用程式(APP)

可下達 -h 參數可得知更多的使用方式

例如：

    py manage.py -h
    py manage.py runserver -h

注意：

    py manage.py runserver 

    
  為啟動Web 服務的方式，僅用於開發專案，千萬不要在正式上線的場合中使用。

  預設使用的 port 為 8000，若要改變 port 號可參考範例：py manage.py runserver XXXX (XXXX為port 號)

  此測試執行後，會在專案根目錄下產生一個 db.sqlite3 的資料庫檔案，但因為尚未產生其中的資料表，因此訊息中會出現 18 個未處理資料庫遷移警告(You have 18 unapplied migration(s))
  在此請忽略，後續說明資料庫時會加以解釋。


因為環境設定檔中預設的資料庫是 sqlite3，所以會在專案根目錄下產生 db.sqlite3。
![image](https://github.com/YueYue32/Django_Learning/blob/main/%E5%95%9F%E5%8B%95%E7%B6%B2%E9%A0%81%E4%BC%BA%E6%9C%8D%E5%99%A8%E9%80%B2%E8%A1%8C%E6%B8%AC%E8%A9%A6/4.png)


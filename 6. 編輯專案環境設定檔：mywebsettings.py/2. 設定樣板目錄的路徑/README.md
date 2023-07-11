# 設定樣板目錄的路徑


在settings.py中，對於該專案的基本路徑已經有預設值

    BASE_DIR = os.path.dirname(os.path.dirname(__file__))

#
BASE_DIR 指的是 最上層的專案目錄 (”myweb”資料夾)

  os.path.dirname(__file__) 

  執行後會取得 “settings.py”這個檔案 所在子目錄的路徑 (\myweb)

  連續使用兩次得到的路徑，即是 子目錄的目錄 自然就是最上層myweb (\myweb\myweb)

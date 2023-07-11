# 設定應用程式中函數的對應 myapp\views.py

views.py

用於寫入”功能”

![image](https://github.com/YueYue32/Django_Learning/blob/main/7.%20%E7%B6%B2%E5%9D%80%E7%9A%84%E5%B0%8D%E6%87%89%E8%88%87%E5%A7%94%E6%B4%BE/1.%20%E8%A8%AD%E5%AE%9A%E6%87%89%E7%94%A8%E7%A8%8B%E5%BC%8F%E4%B8%AD%E5%87%BD%E6%95%B8%E7%9A%84%E5%B0%8D%E6%87%89%20myapp%20views.py/1.png)


# 


      from django.shortcuts import render
      from django.http import HttpResponse
      from datetime import datetime
         
      def home(request):
          return HttpResponse("Home page")
          
      def hiname(request, username):
          return HttpResponse("Hi " + username)
          
      def age(request, year):
          return HttpResponse("Age: " + str(year))
          
      def hello_view(request):
          fourSeason = range(1, 5)
          p1={"name":"Amy","phone":"0912-345678","age":20}
          p2={"name":"Jack","phone":"0937-123456","age":25}
          p3={"name":"Nacy","phone":"0958-654321","age":17}
          persons=[p1,p2,p3]
          return render(request, 'hello_django.html', {
              'title':"樣板使用",
              'data':"Hello Django!",
              'seasons':fourSeason,
              'persons':persons,
              'now':datetime.now()
          } )

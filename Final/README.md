# 期末報告
透過github，找到簡易的Web Server，參考專案:[Linux-C-Web-Server](https://github.com/Skycrab/Linux-C-Web-Server)
並非原創程式，有盡量了解完整執行，但有部分還需再思考與分析。
# 執行
在執行時，遇到我沒有安裝SLL的開發工具，導致無法make，故參考了[OpenSLL](https://blog.csdn.net/guo_qiangqiang/article/details/103613410)，解決無法執行的問題。  
make後會產生webd的檔案。 
./webd 去執行後，再輸入ps，結果如下

    ps -ef | grep webd
    root      3277     1  0 05:11 ?        00:00:00 ./webd
    root      3279  3277  0 05:11 ?        00:00:00 ./webd
    root      3310  2781  0 05:12 pts/0    00:00:00 grep --color=auto webd
在背景進行執行，並透過ifconfig確認自己的ip為只為192.168.56.115，加上預設阜號為8000，透過網頁搜尋192.168.56.115:8000，就能顯示伺服器預設的網頁了。
## 結果
![picture](01.JPG)
![picture](02.JPG)
![picture](03.JPG)

# 第一週

# 課程使用程式與環境設定 
* [參考gcc安裝](https://ithelp.ithome.com.tw/articles/10190235)
* [參考環境變數](https://hjwang520.pixnet.net/blog/post/404935456-win-10%E8%A8%AD%E5%AE%9A%E7%92%B0%E5%A2%83%E8%AE%8A%E6%95%B8)
* gcc 課程範例程式運行
#  Github與README
## git指令 ##  
    git add -A  
    git commit -m "fix document"    
    git add -A  
    git commit -m "fix document"    
    git push origin master  
    git add -A  
    git commit -m "add note week1"  
    git push origin main    
    git branch  
    git checkout -b master  
    git branch  
    git push origin master  
    git branch  
    git branch main 
    git checkout main   
    git branch  
## gcc ##
    gcc sum.c   //編譯a.out
    ./a or ./a.out   //執行a.out
    gcc sum.c -o sum  //編譯成sum.exe
    ./sum          //執行sum
    gcc -S sum.c -o sum.s //產生組合語言sum.s
    gcc -c sum.s -o sum.o //組合語言轉換為目的碼(Object Code)
    gcc sum.o -o sum //目的碼與函式庫連結後產生執行檔sum.exe
    ./sum //執行sum
    objdump -d sum.o //反組譯目的碼
    gcc main.c sum.c -o run.o //直接編譯連結
    ./run.o //執行run.o
    gcc -S main.c -o main.s
    gcc -S sum.c -o sum.s //產生組合語言
    gcc main.c sum.s -o run.o  //組譯後連結
    gcc -c sum.c -o sum.o
    gcc -c main.c -o main.o //產生目的檔，只編譯不連結
    gcc main.o sum.o -o run.o //連結目的檔
    objdump -d sum.o //反組譯
## makefile ##
    make //執行makefile檔
    make clean //清除執行結果
* [Markdown](http://programmermedia.org/root/%E9%99%B3%E9%8D%BE%E8%AA%A0/%E6%8A%80%E8%83%BD/markdown.md)

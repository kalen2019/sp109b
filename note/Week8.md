## 執行erf ##
    gcc erf.c -o erf -lm
    ./erf
    normal(0,1) distribution between(-1.96, 1.96) is 0.950004
## 執行glib2 ##
    make
    gcc glist.c -o glist `pkg-config --cflags glib-2.0` -g -Wall -std=gnu11 -O3 `pkg-config --libs glib-2.0` 
    gcc gslist.c -o gslist `pkg-config --cflags glib-2.0` -g -Wall -std=gnu11 -O3 `pkg-config --libs glib-2.0` 
    gcc htable.c -o htable `pkg-config --cflags glib-2.0` -g -Wall -std=gnu11 -O3 `pkg-config --libs glib-2.0`
    ./glist
    a
    b
    c
    The list is now 0 items long
    ./gslist
    The list is now 0 items long
    The list is now 2 items long
    ./htable
    There are 2 keys in the hash table
    Jazzy likes Cheese
## 執行sqlite ##
    make
    gcc sqlite_read.c -o sqlite_read `pkg-config --cflags sqlite3` -g -Wall -std=gnu11 -O3 `pkg-config --libs sqlite3`
    gcc sqlite_write.c -o sqlite_write `pkg-config --cflags sqlite3` -g -Wall -std=gnu11 -O3 `pkg-config --libs sqlite3`
    ./sqlite_write
    ./sqlite_read
    Id = 1
    Name = Audi
    Price = 52642

    Id = 2
    Name = Mercedes
    Price = 57127

    Id = 3
    Name = Skoda
    Price = 9000

    Id = 4
    Name = Volvo
    Price = 29000

    Id = 5
    Name = Bentley
    Price = 350000

    Id = 6
    Name = Citroen
    Price = 21000

    Id = 7
    Name = Hummer
    Price = 41400

    Id = 8
    Name = Volkswagen
    Price = 21600
## 01-basic/hello ##
    gcc hello.c -o hello
    ./hello
    hello!
    gcc forever.c -o forever
    ./forever
    ^C
    ps
        PID TTY           TIME CMD
        583 pts/0     00:00:00 ps
      31479 pts/0     00:00:00 su
      31480 pts/0     00:00:00 bash
    ./forever &[1] 586
    ps
        PID TTY           TIME CMD
        586 pts/0     00:00:00 forever
        589 pts/0     00:00:00 ps
      31479 pts/0     00:00:00 su
      31480 pts/0     00:00:00 bash
    kill 586
    ps
        593 pts/0     00:00:00 ps
      31479 pts/0     00:00:00 su
      31480 pts/0     00:00:00 bash
      [1]+  Terminated               ./forever
## file.c ##
    gcc file.c -o file
    ./file
    cat hello.txt
    hello world!



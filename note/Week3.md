## lexer ##
    ./lexer sum.c
    #include "sum.h"
    int main() {
    int t = sum(10);
    printf("sum(10)=%d\n", t);
    }
    token=#
    token=include
    token="sum.h"
    token=int
    token=main
    token=(
    token=)
    token={
    token=int
    token=t
    token==
    token=sum
    token=(
    token=10
    token=)
    token=;
    token=printf
    token=(
    token="sum(10)=%d\n"
    token=,
    token=t
    token=)
    token=;
    token=}
    0:#
    1:include
    2:"sum.h"
    3:int
    4:main
    5:(
    6:)
    7:{
    8:int
    9:t
    10:=
    11:sum
    12:(
    13:10
    14:)
    15:;
    16:printf
    17:(
    18:"sum(10)=%d\n"
    19:,
    20:t
    21:)
    22:;
    23:}
## pointer ##
    ** pointer1:
    #include <stdio.h>

    int main(){
        char x = 'a';
        char *p = &x;
        *p='b';
        printf("*p=%c x=%c\n", *p, x);
    }

    ** pointer1bug:
    #include <stdio.h>

    int main(){
        char x = 'a';
        char *p; // = &x;
        *p='b';
        printf("*p=%c x=%c\n", *p, x);
    }
    //這樣指標沒有指向x，變成指向未知
    ** scanf.c:
    #include <stdio.h>

    int main(){
        char x;
        scanf("%c", x);
    }
    //沒加上&，無法指向X的位置
## compiler ##
    make
    gcc -std=c99 -O0 lexer.c compiler.c main.c -o compiler
    //輸出執行檔
    ./compiler test/while.c   //編譯while.c
        i = 1;
        while (i<10) i = i + 1;
        ========== lex ==============
        token=i
        token==
        token=1
        token=;
        token=while
        token=(
        token=i
        token=<
        token=10
        token=)
        token=i
        token==
        token=i
        token=+
        token=1
        token=;
        ========== dump ==============
        0:i
        1:=
        2:1
        3:;
        4:while
        5:(
        6:i
        7:<
        8:10
        9:)
        10:i
        11:=
        12:i
        13:+
        14:1
        15:;
        ============ parse =============
        t0 = 1
        i = t0
        (L0)
        t1 = i
        t2 = 10
        t3 = t1 < t2
        if not T3 goto L1
        t4 = i
        t5 = 1
        t6 = t4 + t5
        i = t6
        goto L0
        (L1)
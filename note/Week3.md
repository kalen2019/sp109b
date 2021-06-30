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
    **pointer1:
    #include <stdio.h>

    int main(){
        char x = 'a';
        char *p = &x;
        *p='b';
        printf("*p=%c x=%c\n", *p, x);
    }

    **pointer1bug:
    #include <stdio.h>

    int main(){
        char x = 'a';
        char *p; // = &x;
        *p='b';
        printf("*p=%c x=%c\n", *p, x);
    }
    //這樣指標沒有指向x，變成指向未知
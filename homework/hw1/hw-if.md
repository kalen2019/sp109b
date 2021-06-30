## 程式 ##
(compiler(參考老師的while程式碼去修改測試出來的))[]
## compiler if部分 ##
    void IF() {
        int ifBegin = nextLabel();
        int ifNext = nextLabel();
        int ifEnd = nextLabel();
        emit("(L%d)\n", ifBegin);  //開始標記
        skip("if");               //略過
        skip("(");
        int e = E();              //處理括號內部
        emit("if not T%d goto L%d\n", e, ifNext);
        skip(")");
        STMT();
        emit("goto L%d\n", ifEnd);
        emit("(L%d)\n", ifNext);
        if (isNext("else")){
            skip("else");
            STMT();
            emit("(L%d)\n",ifEnd);
        }   //如果遇到要進入else的情況才執行
    
    }
## if.c沒進入else ##
    x = 3;
    if (x>2) {
        x = x + 1;
    }
    else {
        x = x - 1;
    }
## 結果 ##
    ./compiler test/if.c
    x = 3;
    if (x>2) {
        x = x + 1;
    }
    else {
        x = x - 1;
    }
    ========== lex ==============
    token=x
    token==
    token=3
    token=;
    token=if
    token=(
    token=x
    token=>
    token=2
    token=)
    token={
    token=x
    token==
    token=x
    token=+
    token=1
    token=;
    token=}
    token=else
    token={
    token=x
    token==
    token=x
    token=-
    token=1
    token=;
    token=}
    ========== dump ==============
    0:x
    1:=
    2:3
    3:;
    4:if
    5:(
    6:x
    7:>
    8:2
    9:)
    10:{
    11:x
    12:=
    13:x
    14:+
    15:1
    16:;
    17:}
    18:else
    19:{
    20:x
    21:=
    22:x
    23:-
    24:1
    25:;
    26:}
    ============ parse =============
    t0 = 3
    x = t0
    (L0)
    t1 = x
    t2 = 2
    t3 = t1 > t2
    if not T3 goto L1
    t4 = x
    t5 = 1
    t6 = t4 + t5
    x = t6
    goto L2
    (L1)
    t7 = x
    t8 = 1
    t9 = t7 - t8
    x = t9
    (L2)
## if.c有進入else ##
    x = 2;
    if (x>2) {
        x = x + 1;
    }
    else {
        x = x - 1;
    }
## 結果 ##
    ./compiler test/if.c
    x = 2;
    if (x>2) {
        x = x + 1;
    }
    else {
        x = x - 1;
    }
    ========== lex ==============
    token=x
    token==
    token=2
    token=;
    token=if
    token=(
    token=x
    token=>
    token=2
    token=)
    token={
    token=x
    token==
    token=x
    token=+
    token=1
    token=;
    token=}
    token=else
    token={
    token=x
    token==
    token=x
    token=-
    token=1
    token=;
    token=}
    ========== dump ==============
    0:x
    1:=
    2:2
    3:;
    4:if
    5:(
    6:x
    7:>
    8:2
    9:)
    10:{
    11:x
    12:=
    13:x
    14:+
    15:1
    16:;
    17:}
    18:else
    19:{
    20:x
    21:=
    22:x
    23:-
    24:1
    25:;
    26:}
    ============ parse =============
    t0 = 2
    x = t0
    (L0)
    t1 = x
    t2 = 2
    t3 = t1 > t2
    if not T3 goto L1
    t4 = x
    t5 = 1
    t6 = t4 + t5
    x = t6
    goto L2
    (L1)
    t7 = x
    t8 = 1
    t9 = t7 - t8
    x = t9
    (L2)
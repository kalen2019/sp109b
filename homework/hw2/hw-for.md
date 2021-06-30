## 程式 ##
* [compiler(使用老師程式碼去修改測試出來的)]()
* 
* [for.c]()
## compiler for部分 ##
    
## for.c ##
    for ( i = 0; i < 9; i++){
    x= x + 1;
    }
## 結果 ##
    ./compiler test/for.c
    for ( i = 0; i < 9; i++){
        x= x + 1;
    }
    ========== lex ==============
    token=for
    token=(
    token=i
    token==
    token=0
    token=;
    token=i
    token=<
    token=9
    token=;
    token=i
    token=++
    token=)
    token={
    token=x
    token==
    token=x
    token=+
    token=1
    token=;
    token=}
    ========== dump ==============
    0:for
    1:(
    2:i
    3:=
    4:0
    5:;
    6:i
    7:<
    8:9
    9:;
    10:i
    11:++
    12:)
    13:{
    14:x
    15:=
    16:x
    17:+
    18:1
    19:;
    20:}
    ============ parse =============
    t0 = 0
    i = t0
    (L0)
    t1 = i
    t2 = 9
    t3 = t1 < t2
    if not T3 goto L1
    i = i + 1
    t5 = x
    t6 = 1
    t7 = t5 + t6
    x = t7
    goto L0
    (L1)

    
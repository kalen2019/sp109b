# 第二週

## 系統程式 ##
1. Compiler
2. Assembler
3. Virtual Machine
4. OS - Operating system
#
## Compiler ##
* Syntax(語法)
    * [Lexer(詞彙解析)](http://programmermedia.org/root/%E9%99%B3%E9%8D%BE%E8%AA%A0/%E8%AA%B2%E7%A8%8B/%E7%B3%BB%E7%B5%B1%E7%A8%8B%E5%BC%8F/03-compiler/02-lexer/)
    * Parser
* Semantic(語義)
* Code Generation(Code編譯)
* [Compiler簡介參考](http://programmermedia.org/root/%E9%99%B3%E9%8D%BE%E8%AA%A0/%E8%AA%B2%E7%A8%8B/%E7%B3%BB%E7%B5%B1%E7%A8%8B%E5%BC%8F/03-compiler/%E7%B7%A8%E8%AD%AF%E5%99%A8%E7%B0%A1%E4%BB%8B.md)  
     * [EBNF](http://programmermedia.org/root/%E9%99%B3%E9%8D%BE%E8%AA%A0/%E8%AA%B2%E7%A8%8B/%E7%B3%BB%E7%B5%B1%E7%A8%8B%E5%BC%8F/03-compiler/%E7%B7%A8%E8%AD%AF%E5%99%A8%E7%B0%A1%E4%BB%8B.md)
* [High Level Language](http://programmermedia.org/root/%E9%99%B3%E9%8D%BE%E8%AA%A0/%E8%AA%B2%E7%A8%8B/%E7%B3%BB%E7%B5%B1%E7%A8%8B%E5%BC%8F/03-compiler/%E9%AB%98%E9%9A%8E%E8%AA%9E%E8%A8%80%E7%9A%84%E8%AA%9E%E6%B3%95.md)
## gen (use EBNF) ##
    gcc genExp.c rlib.c -o genExp.o  //產生運算式
    ./genExp.o  //執行
    gcc genEnglish.c rlib.c -o genEnglish.o //產生語句
    ./genEnglish.o //執行
## exp ##
    ** exp0範例1:
    ./exp0 '3+5'
    argv[0]=D:\kalen VS\sp\code\c\02-compiler\00-exp0\exp0.exe argv[1]=3+5
    === EBNF Grammar ===== 
    E=F ([+-] F)*
    F=Number | '(' E ')'   
    ==== parse:3+5 ========
    t0=3
    t1=5
    t2=t0+t1
    ** exp0範例2:
    ./exp0 '3+(5-4)'
    argv[0]=D:\kalen VS\sp\code\c\02-compiler\00-exp0\exp0.exe argv[1]=3+(5-4)
    === EBNF Grammar =====
    E=F ([+-] F)*
    F=Number | '(' E ')'
    ==== parse:3+(5-4) ========
    t0=3
    t1=5
    t2=4
    t3=t1-t2
    t4=t0+t3
    ** exp0hack範例:
    ./exp0hack '3+5'
    === EBNF Grammar =====
    E=F ([+-] F)*
    F=Number | '(' E ')'
    ==== parse:3+5 ========
    # t0=3
    @3
    D=A
    @t0
    M=D
    # t1=5
    @5
    D=A
    @t1
    M=D
    # t2=t0+t1
    @t0
    D=M
    @t1
    D=D+M
    @t2
    M=D
    ** exp0var範例:
    ./exp0var 'x+3-y'
    === EBNF Grammar =====
    E=F ([+-] F)*
    F=Number | '(' E ')'
    ==== parse:x+3-y ========
    # t0=x
    @x
    D=M
    @t0
    M=D
    # t1=3
    @3
    D=A
    @t1
    M=D
    # t2=t0+t1
    @t0
    D=M
    @t1
    D=D+M
    @t2
    M=D
    # t3=y
    @y
    D=M
    @t3
    M=D
    # t4=t2-t3
    @t2
    D=M
    @t3
    D=D-M
    @t4
    M=D





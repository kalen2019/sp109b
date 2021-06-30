## vm.c執行 ##
    make
    gcc -std=c99 -O0 asm.c c6.c -o asm
    gcc -std=c99 -O0 vm.c -o vm

    ./asm ../test/Add
# 虛擬機介紹
    * 狹義: 1.虛擬機  2.模擬器
    * 廣義: VMWare、Virtual PC、Virtual Box等軟體
  ## ============================================================
* 原生式虛擬機
* 寄生式虛擬機
* 程序虛擬機
  ## ============================================================
* 中間碼  //具有跨平台的能力
  ## ============================================================
* 記憶體機
* 暫存器機
* 堆疊機
# ============================================================
* 建置java執行環境與開發工具
## 執行HelloWorld.java ##
    javac HelloWorld.java
    java HelloWorld
    Hello World!

    javap -c HelloWorld.class  //反組譯
    class HelloWorld {
     HelloWorld();   
        Code:
            0: aload_0
            1: invokespecial #1                  // Method java/lang/Object."<init>":()V
            4: return

     public static void main(java.lang.String[]);
        Code:
            0: getstatic     #7                  // Field java/lang/System.out:Ljava/io/PrintStream;
            3: ldc           #13                 // String Hello World!
            5: invokevirtual #15                 // Method java/io/PrintStream.println:(Ljava/lang/String;)V
            8: return
    }
## 執行PitifulVM ##
    make
    CC+LD         jvm
    javac tests/Factorial.java
    cd tests
    java Factorial
    43954714
    ./jvm tests/Factorial.class
    43954714






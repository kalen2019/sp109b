* 安裝linux
* git clone https://gitlab.com/ccc109/sp.git
## asm ##
    gcc -c hello.s  //編譯，產生hello.o
    ld hello.o -o hello //產生hello
    ./hello     //執行hello
    Hello, world

    myMacro:
    # write(1, message, 13)
    .macro WRITES fd, msg, len  //.macro為開頭,fd檔案描述值
        mov     $1, %rax            # system call 1 is write
        mov     \fd, %rdi           # file handle 1 is stdout
        mov     \msg, %rsi          # address of string to output
        mov     \len, %rdx          # number of bytes
        syscall
    .endm //.endm為結尾

    .macro EXIT  //讓程式停止
        mov 	$60, %rax  //60即EXIT的代號 0為正常結束
        xor	%rdi, %rdi
        syscall
    .endm

    .macro PUTS msg
        mov   \msg, %rdi
        call  puts
    .endm


    .macro PRINTF fmt, p1
        # We need to call printf, but we are using eax, ebx, and ecx.  printf
        # may destroy eax and ecx so we will save these before the call and
        # restore them afterwards.

        push    %rax                    # caller-save register
        push    %rcx                    # caller-save register

        mov     \fmt, %rdi              # set 1st parameter (format)
        mov     \p1, %rsi               # set 2nd parameter (current_number)
        xor     %rax, %rax              # because printf is varargs

        # Stack is already aligned because we pushed three 8 byte registers
        call    printf                  # printf(format, current_number)

        pop     %rcx                    # restore caller-save register
        pop     %rax                    # restore caller-save register
    .endm
    //有巨集執行hello
    gcc -c helloMacro.s
    ld helloMacro.o -o helloMacro
    ./helloMacro
    Hello, world

    hola.s
    # ----------------------------------------------------------------------------------------
    # Writes "Hola, mundo" to the console using a C library. Runs on Linux or any other system
    # that does not use underscores for symbols in its C library. To assemble and run:
    #
    #     gcc hola.s && ./a.out
    # ----------------------------------------------------------------------------------------

        .global main

        .text
    main:                                   # This is called by C library's startup code
        mov     $message, %rdi          # First integer (or pointer) parameter in %rdi
        call    puts                    # puts(message)//呼叫C函式庫
        ret                             # Return to C library code
    message:
        .asciz "Hola, mundo"            # asciz puts a 0 byte at the end

    執行:
    gcc -no-pie hola.s -o hola
    ./hola
    Hola, mundo
 


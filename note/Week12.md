## fork1.c ##
    gcc fork1.c -o fork1
    ./fork1
    12568 : Hello world!
    13665 : Hello world!
    14336 : Hello world!
    14325 : Hello world!
## fork2.c ##
    gcc fork2.c -o fork2
    ./fork2
    11232 : enter
    11232 : after 1st fork
    11232 : Hello world!
    11233 :after 1st fork
    11233 : Hello world!
    11234 : Hello world!
    11234 : Hello world!    
## echo1.c ##
    gcc echo1.c -o echo1
    ./echo
    hello world
    hello world
    hello world
## fecho1.c ##
    gcc fecho1.c -o fecho
    ./fecho
    產生a.txt&b.txt

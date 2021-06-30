## task.c ##
    gcc task.c -o task
    ./task
    0:(null)
    1:(null)
    2:(null)
    3:(null)
    4:(null)
    ^c
    ./task abc
    0:abc
    1:abc
    2:abc
    3:abc
    4:abc
## vmem.c ##
    gcc vmem.c -o vmem
    ./vmem
    location of code : 00401460
    location of heap : 00BA4020
    location of stack: 0061FF1C
## mem.c ##
    gcc mem.c -o mem
    ./mem
    (9304) addr of counter: 00407020
    0:(9304) value of counter: 1
    1:(9304) value of counter: 2
    2:(9304) value of counter: 3
    3:(9304) value of counter: 4
    4:(9304) value of counter: 5
## mem0.c ##
    gcc mem0.c -o mem0
    ./mem0
    (3944) addr pointed to by p: 006A1910
    0:(3944) value of p: 1
    1:(3944) value of p: 2
    2:(3944) value of p: 3
    3:(3944) value of p: 4
    4:(3944) value of p: 5
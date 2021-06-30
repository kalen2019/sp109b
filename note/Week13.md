## stderr1.c ##
    gcc stderr1.c -o stderr1
    ./stderr1
    Some message!
    Warning: xxx 
    Error: yyy
    ./stderr1 2>error.txt
    Some message!
    ./stderr1 1>output.txt
    Warning: xxx
    Error: yyy
    ./stderr1 1>output.txt 2>error.txt
    cat error.txt
    Warning: xxx
    Error: yyy
    cat output.txt
    Some message!
## stderr2.c ##
    gcc stderr2.c -o stderr2
    ./stderr2
    cat log.txt
    Warning: xxx
    Error: yyy
## time.c ##
     gcc time.c -o time
     ./time
    Thu Jul 01 02:32:59 2021
    Thu Jul 01 02:33:00 2021
    Thu Jul 01 02:33:01 2021

## client.c

### 建立連接

```
if (connect(sk, (struct sockaddr*) &addr, sizeof(addr)) == -1) {
    printf("connect error :%s\n", strerror(errno));
    return EXIT_FAILURE;
}
pthread_t th1, th2; // 開啟兩個線程，一個發送訊息，一個監聽消息
pthread_create(&th1, NULL, recvsocket, &sk);
pthread_create(&th2, NULL, sendsocket, &sk);
pthread_join(th1, NULL);
```

### sendsocket

```
memset(&str, 0, BUFSIZE);  // 初始化記憶體
memset(&deststr, 0, BUFSIZE);
read(STDIN_FILENO, &str, sizeof(str)); // 接收訊息
int sendlen = strlen(str); // 獲取字串長度
if(sendlen==1) // 只輸入enter
{
    printf("send can not be null\n");
    break; // 離開聊天
}
str[sendlen]='\0'; // 取出最後的enter
```
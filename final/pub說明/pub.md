## pub.c

### 最多允許100個client

```
#define MAXCHAT_P 100
int sts[MAXCHAT_P]={0};
```

### 添加client

```
int addchatpeople(int st)
{
	int i;
	for(i=0;i<MAXCHAT_P;i++) // 檢查sts[MAXCHAT_P]
	{
		
		if(sts[i]==0) // 查找空位
		{
			sts[i]=st; // client綁定
			chatsum++;
			return 1; // 退出
		}
	}
	return 0; // 滿了
	
}
```

### 減少client

```
void deletechatpeople(int st)
{
	int i;
	for(i=0;i<MAXCHAT_P;i++) // 檢查sts[MAXCHAT_P]
	{
		if(sts[i]==st)
		{
			sts[i]=0;  // 清除client
			chatsum--;
		}
	}
}
```

### 發送聊天紀錄

```
void sendtocharroom(char * buf,int currst) // 獲取輸入訊息與輸入訊息的client
{
	int i;
	for(i=0;i<MAXCHAT_P;i++)
	{
		if(sts[i]!=0&&sts[i]!=currst)  // 訊息不發送到空房間與輸入訊息的client
		{
			send(sts[i], buf, strlen(buf), 0);
		}
	}
	
}
```

### 創建參數port指定端口號的server端socket

```
//AF_INET是ipv4, SOCK_STREAM為訊息完整傳輸, 0默認是創建TCP socket 
int st = socket(AF_INET, SOCK_STREAM, 0);
return st
```

### 接收来自client socket发送来的消息

```
ssize_t rc = recv(st, recvbuf, sizeof(recvbuf), 0);
```

### 接受到來自client的socket連接

```
int client_st = accept(listen_st,  (struct sockaddr *)&client_addr, &len);
```

### epoll

```
void run(int port)
{
	int listen_st = socket_create(port); // 創建參數port指定端口号的server端socket
	setnonblocking(listen_st); // 把socket設置为非阻塞方式
	struct epoll_event ev, events[MAX_EVENT]; // 聲明epoll_event結構體的變量,ev用於註冊事件,數組用於回傳要處理的事件
	int epfd = epoll_create(MAX_EVENT); // 生成用於處理accept的epoll專用的文件描述符

	ev.data.fd = listen_st; // 設置與要處理的事件相關的文件描述符
	ev.events = EPOLLIN | EPOLLERR | EPOLLHUP; // 設置要處理的事件類型

	epoll_ctl(epfd, EPOLL_CTL_ADD, listen_st, &ev); // 注册epoll事件

	int st = 0;
	while (1)
	{
		int nfds = epoll_wait(epfd, events, MAX_EVENT, -1); // 等待epoll事件的发生
		if (nfds == -1)
		{
			printf("epoll_wait failed %s\n", strerror(errno));
			break;
		}
		
		int i = 0;
		for (; i < nfds; i++)
		{
			if (events[i].data.fd < 0)
				continue;
			if (events[i].data.fd == listen_st) // 監測到一个socket用户連接到了绑定的socket端口，建立新										   的連結
			{
				st = socket_accept(listen_st);
				if (st >= 0)
				{
					
					setnonblocking(st); // 將來自client端的socket描述符設置為非阻塞
					ev.data.fd = st;
					ev.events = EPOLLIN | EPOLLERR | EPOLLHUP; // 設置主要處理的事件類型
					epoll_ctl(epfd, EPOLL_CTL_ADD, st, &ev); // 將來自client端的socket描述符加入epoll	
				}
				continue;
			}
			if (events[i].events & EPOLLIN) // socket收到數據
			{
				st = events[i].data.fd;
				if (socket_recv(st) <= 0)
				{
					deletechatpeople(st); // 踢出聊天
					close(st);
					events[i].data.fd = -1;
				}
			}
			if (events[i].events & EPOLLERR) // socket錯誤。
			{
				st = events[i].data.fd;
				close(st);
				events[i].data.fd = -1;
			}

			if (events[i].events & EPOLLHUP) // socket被掛斷。
			{
				st = events[i].data.fd;
				close(st);
				events[i].data.fd = -1;
			}
		}
	}
	close(epfd);
}
```
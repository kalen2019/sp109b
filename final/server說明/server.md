## server.c

### 判斷參數

```
int main(int arg, char *args[])
{
	if (arg < 2)
	{
		printf("usage:server port\n");
		return EXIT_SUCCESS;    //return -1
	}
```

### 將第一個參數設為端口號

```
int iport = atoi(args[1]);
	if (iport == 0)
	{
		printf("port %d is invalid\n", iport);
		return EXIT_SUCCESS;
	}
	run(iport);
	return EXIT_SUCCESS;
```
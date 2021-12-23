# Thread_test
### 简单的线程打印  

```c
#include <stdio.h>
#include <pthread.h>
 
void *mythread1(void)
{
	int i;
	for(i = 0; i < 10; i++)
	{
		printf("This is the 1st pthread,created by xiaoqiang!\n");
		sleep(1);
	}
}
 
void *mythread2(void)
{
	int i;
	for(i = 0; i < 10; i++)
	{
		printf("This is the 2st pthread,created by xiaoqiang!\n");
		sleep(1);
	}
}
 void *mythread3(void)
{
	int i;
	for(i = 0; i < 10; i++)
	{
		printf("This is the 3st pthread,created by xiaoqiang!\n");
		sleep(1);
	}
}
int main(int argc, const char *argv[])
{
	
	int ret = 0;
	pthread_t id1,id2,id3;
 
	ret = pthread_create(&id1, NULL, (void *)mythread1,NULL);
	if(ret)
	{
		printf("Create pthread error!\n");
		return 1;
	}
 
	ret = pthread_create(&id2, NULL, (void *)mythread2,NULL);
	if(ret)
	{
		printf("Create pthread error!\n");
		return 1;
	}
	ret = pthread_create(&id3, NULL, (void *)mythread3,NULL);
	if(ret)
	{
		printf("Create pthread error!\n");
		return 1;
	}
	
	pthread_join(id1,NULL);
	pthread_join(id2,NULL);
    	pthread_join(id3,NULL);
    
	return 0;
}
```

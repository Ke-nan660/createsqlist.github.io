# createsqlist.github.io
C语言实现顺序表的创建
#include<stdio.h>
#include<stdlib.h>
#define max 100
typedef struct
{
	int data[max];
	int last;
 }sqlist;
 void initlist(sqlist l)	//初始化 
 {
 	l.last=0;
 	printf("初始化已完成，该表已为空表\n");
 }
 void createlist(sqlist *l,int n)  //建表 
 {
 	int i=0;
 	int j;
 	for(i;i<n;i++)
 	{
 		scanf("%d",&j);
 		l->data[i]=j;
	 }
	 l->last=n;
 }
 //增  插入
 void insertelem(sqlist *l,int i,int e)
 {
 	int k;
 	if(i<0||i>l->last)
 	{
 		printf("插入的位置不合法\n");
	 }
	 if(l->last>max)
	 {
	 	printf("表满，无法插入\n");
	 }
	 for(k=l->last;k>=i;--k);
	 {
	 	l->data[k+1]=l->data[k];
	  }
	  l->last++; 
  } 
  // 删 
 int  deletelem1(sqlist *l,int i)
 {
 	int k;
 	if(i<0||i>l->last)
 	{
 		printf("删除的位置不合法\n");
 		return 0;
	 }
	printf("删除的元素为%d\n",l->data[i]);
	for(k=i;k<=l->last;++k)
	{
		l->data[k]=l->data[k+1];
	}	
	l->last--;
	return 1;
  } 
  //按元素值查找
  int  findelem(sqlist *l,int e)
  {
  	int k;
  	for(k=0;k<l->last;k++)
  	{
  		if(l->data[k]==e)
  		{
  			printf("查找成功！该元素在顺序表中的位置为%d\n",k);
  			return 1;
		  }
	 }	
	printf("查找失败\n");
	return 0;
   } 
   //按元素位置查找
   int  getelem(sqlist *l,int i)
   {
   	if(i<0||i>l->last)
   	{
   		printf("查找位置不合法\n");
   		return 0;
	   }
	printf("第%d的元素为%d\n",i,l->data[i]); 
	return 1;
	} 
	void printlist(sqlist l)
	{
		int i=0;
		while(i<l.last )
		{
			printf("%d\t",l.data[i]);
			++i;
		}
	}
	int main()
	{
		sqlist l;
		initlist(l);
		int n;
		printf("请输入数据元素的个数：\n");
		scanf("%d",&n);
		printf("请向顺序表中输入元素：\n");
		createlist(&l,n);
		printlist(l);
		int i,e;
		printf("请输入要删除的元素的位置:\n");
		scanf("%d",&i);
		deletelem1(&l,i);
		printlist(l);
		printf("请输入你要查找的元素值：\n");
		int a;
		scanf("%d",&a);
		findelem(&l,a);
		printf("请输入你要查找的元素的位置：\n");
		int p;
		scanf("%d",&p);
		getelem(&l,p);
		return 0;
	 } 

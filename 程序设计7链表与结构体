#define _CRT_SECURE_NO_WARNINGS 1
//	创建一个 单向链表 来记录学生信息，人数3--5人；链表结点为结构变量，结构的要求如下：
//	struct stu_info
//	{
// 
//	    char stu_num[10];  //学号
//	    char stu_name[8];  //姓名
//	    char stu_sex[2];    //性别
//	    int stu_score    //成绩
//	    struct stu_info* next;
//	};
//	程序设计要求：
//	（1）插入新的学生信息(插入节点的位置可任意指定）
//	（2）删除指定的学生信息
//	（3）根据学号查询并显示查询到的学生信息
//	（4）以上三项任务分别自定义函数实现，执行后显示执行结果
//	（5）程序运行后要求可以循环执行前三项操作，直到选择退出时结束程序
#include<stdio.h>
#include <stdlib.h>
#include <string.h>

struct stu_info//结构体声明
{
	char stu_num[10];  //学号
	char stu_name[8];  //姓名
	char stu_sex[2];   //性别
	int stu_score;     //成绩
	struct stu_info* next;
};

struct stu_info* head;//全局变量：头指针与总人数
int NOP;

int Count()//计算总人数的函数
{
	int a = 1;
	struct stu_info* p1;
	p1 = head;
	while (1 == 1)
	{
		if ((*p1).next != NULL)
		{
			p1 = (*p1).next;
			a++;
		}
		else
		{
			break;
		}
	}
	return a;
}

void Insert(int n)//插入新的学生信息
{
	struct stu_info* p1, * p2 = head, * p3 = head;
	p1 = (struct stu_info*)malloc(sizeof(struct stu_info));
	printf("输入学号(最多9数字):");
	scanf("%9s", &(*p1).stu_num);
	printf("输入姓名(最多7字符):");
	scanf("%7s", &(*p1).stu_name);
	printf("输入性别(最多1字符，M男，F女):");
	scanf("%1s", &(*p1).stu_sex);
	printf("输入成绩:");
	scanf("%d", &(*p1).stu_score);
	if (n == 0)
	{
		(*p1).next = head;
		head = p1;
	}
	if (n != 0 && n != NOP)
	{
		for (int i = 0; i < n - 1; i++)
		{
			p2 = (*p2).next;
		}
		p3 = (*p2).next;
		(*p2).next = p1;
		(*p1).next = p3;
	}
	if (n == NOP)
	{
		for (int i = 0; i < n - 1; i++)
		{
			p2 = (*p2).next;
		}
		(*p2).next = p1;
		(*p1).next = NULL;
	}
}

void Delete(int n)//删除指定学生信息
{
	struct stu_info* p1 = head, * p2 = head, * p3 = head;
	if (n == 1)
	{
		head = (*head).next;
		free(p1);
	}
	if (n != 1 && n != NOP)
	{
		for (int i = 1; i < n - 1; i++)
		{
			p1 = (*p1).next;
		}
		p2 = (*p1).next;
		p3 = (*p2).next;
		(*p1).next = p3;
		free(p2);
	}
	if (n == NOP)
	{
		for (int i = 1; i < n - 1; i++)
		{
			p1 = (*p1).next;
		}
		p2 = (*p1).next;
		(*p1).next = NULL;
		free(p2);
	}
}

void Search(char arr[10])//查询指定学生信息
{
	struct stu_info* p1 = head;
	for (int i = 0; i < NOP; i++)
	{
		if (strcmp((*p1).stu_num, arr) == 0)
		{
			printf("--查找到目标，以下是其信息--\n");
			printf("学号%s\n", (*p1).stu_num);
			printf("姓名%s\n", (*p1).stu_name);
			printf("性别%s\n", (*p1).stu_sex);
			printf("成绩%d\n", (*p1).stu_score);
			break;
		}
		else
		{
			if ((*p1).next == NULL)
			{
				printf("未查找到目标！\n");
				break;
			}
			else
			{
				p1 = (*p1).next;
			}
		}
	}
}

void ShowAll()//显示全部
{
	struct stu_info* p;
	p = head;
	do
	{
		printf("学号%s\n", (*p).stu_num);
		printf("姓名%s\n", (*p).stu_name);
		printf("性别%s\n", (*p).stu_sex);
		printf("成绩%d\n\n", (*p).stu_score);
		p = (*p).next;
	} while (p != NULL);
}

int main()
{
	printf("兰州大学某学术巨巨制作的简陋资料管理系统(菜只是一时的！)--作者李浩--学号320240941381\n");
	struct stu_info* p;
	p = (struct stu_info*)malloc(sizeof(struct stu_info));
	strcpy((*p).stu_num, "000000001");
	strcpy((*p).stu_name, "Xiaohua");
	strcpy((*p).stu_sex, "F");
	(*p).stu_score = 100;
	(*p).next = NULL;
	head = p;
	int input, z;
	while (1 == 1)
	{
		printf("\n输入操作数字\n1：插入新的学生信息\n2：删除指定学生信息\n3：根据学号查询并显示查询到的学生信息\n4：显示全部\n5：退出\n请输入：");
		scanf("%d", &input);
		if (input == 1)//插入新的学生信息
		{
			NOP = Count();
			printf("\n要插入在第几号后面(0<=n<=%d,输入0以插入在最首端):", NOP);
			scanf("%d", &z);
			if (z < 0 || z>NOP)
			{
				printf("无效！\n");
				continue;
			}
			Insert(z);
			printf("\n完成！\n");
		}
		else if (input == 2)//删除指定学生信息
		{
			NOP = Count();
			if (NOP == 1)
			{
				printf("\n请至少保留一条信息！\n");
				continue;
			}
			printf("\n要删除第几号的信息(1<=n<=%d):", NOP);
			scanf("%d", &z);
			if (z <= 0 || z > NOP)
			{
				printf("无效！\n");
				continue;
			}
			Delete(z);
			printf("\n完成！\n");
		}
		else if (input == 3)//根据学号查询并显示查询到的学生信息
		{
			NOP = Count();
			char arr[10];
			printf("\n请输入学号:");
			scanf("%s", arr);
			Search(arr);
		}
		else if (input == 4)//显示全部
		{
			NOP = Count();
			printf("\n");
			ShowAll();
			printf("\n共有%d人\n", NOP);
		}
		else if (input == 5)//退出
		{
			break;
		}
		else
		{
			printf("无效！\n");
			continue;
		}
	}
	printf("\n\n感谢您的使用，我们下次再见！\n");
	return 0;
}

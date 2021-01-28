---
title: 数据结构
date: 2021-1-26 18:03:45
categories: 
    - 算法
tags: 
    - 笔记
    - 王道考研
mp3: 
cover: img/vue_js_shizhan.jpg
---

CH1 顺序表基本操作及实现（C）

```c
#include<stdio.h>
#include<stdlib.h>

#define MAXSIZE 50
#define Elemtype int 

typedef struct{
    Elemtype data[MAXSIZE];
    int length;
}Sqlist;

void InitSqlist(Sqlist *L)
{
    L->length=0;
    printf("Init the list successfully!\n");
    return;
}

void CreateSqlist(Sqlist *L,int temp_data[],int temp_length)
{
    if(temp_length>MAXSIZE)
    {
        printf("Overflow!\n");
        return;
    }

    for(int index=0;index<temp_length;index++)
    {
        L->data[index]=temp_data[index];
    }
    L->length=temp_length;
    printf("Create the table successfully!\n");
    return;
}

void InsertList(Sqlist *L,Elemtype newData,int temp_position)
{
    if(temp_position<0||temp_position>L->length+1)
    {
        printf("Wrong position!\n");
        return;
    }
    else
    {
        for(int index=L->length;index>temp_position;index--)
        {
            L->data[index]=L->data[index-1];
        }
        L->data[temp_position]=newData;
        printf("Add new data successfully!\n");
        return;
    }
}

void DeleteDataByElement(Sqlist *L,Elemtype deletedData)
{
    int counter=0;
    for(int index=0;index<L->length-1;index++)
    {
        if(L->data[index]==deletedData)
        {
            counter+=1;
            for(int index1=index;index1<L->length-1;index1++)
            {
                L->data[index1]=L->data[index1+1];
            }
        }
    }
    L->length-=counter;
    printf("The counter is %d\n",counter);
    printf("Delete the data successfully!\n");
    return;
}

void DeleteDataByPosition(Sqlist *L,int tempDeletePosition)
{
    Elemtype deleted_data;
    if(tempDeletePosition<0||tempDeletePosition>L->length)
    {
        printf("Wrong position!\n");
    }
    else{
        deleted_data=L->data[tempDeletePosition];
        for(int index=tempDeletePosition;index<L->length;index++)
        {

            L->data[index]=L->data[index+1];
        }
        L->length--;
    }
    printf("Delete the data successfully!\n");
    printf("The deleted data is %d\n",deleted_data);
    return;
}

void PrintList(Sqlist *L)
{
    printf("The list is below:\n");
    for(int index=0;index<L->length;index++)
    {
        printf("%d ",L->data[index]);
    }
    printf("\nThe length is %d\n",L->length);
    return;
}

//不确定是否正确
// void EmptyList(Sqlist *L)
// {
//     free(L->data);
//     L->length=0;
//     return;
// }



int main(){
    int my_data[MAXSIZE]={1,2,3,4,5,6,4,3,22,1};
    int my_length=10;
    Sqlist my_list;
    Elemtype insertData=10;
    int my_new_position=3;
    int my_abandoned_data=3;
    int my_deleted_position=2;

    InitSqlist(&my_list);
    CreateSqlist(&my_list,my_data,my_length);
    InsertList(&my_list,insertData,my_new_position);
    PrintList(&my_list);
    DeleteDataByElement(&my_list,my_abandoned_data);
    DeleteDataByPosition(&my_list,my_deleted_position);
    // EmptyList(&my_list);
    PrintList(&my_list);
    return 0;
}
```


## Resource
https://pintia.cn/problem-sets/434/problems/5653

## Code
```c
#include <stdio.h>

void printList(int[],int);
void doubleCircle(int,int,int[]);
void reverse(int[],int,int);
int main(){
    int n,m;
    scanf("%d %d",&n,&m);
    
    int numbers[n];
    for(int i = 0;i < n;i++){
        scanf("%d",&numbers[i]);
    }

    //判断是否需要移动
        //若不需要直接打印当前数组
        //所需要，则计算a0的存放位置
    int newA0 = (n - m % n) % n; 
    if(newA0 == 0){
       printList(numbers,n);
       return 0;
    }
    //暴力求解法：依次把头部的数据存放起来，然后后续数组整体前移一位
    //doubleCircle(n,newA0,numbers);
    //交换法：三步转置法，按照示例，先转置123，然后转置45678 最后在整体转置即可得到结果
    changePosition(newA0,n,m,numbers);
    
    //打印数组
    printList(numbers,n);
    
    return 0;
}

void doubleCircle(int n,int newA0,int numbers[]){
    for(int i = 0;i < n-newA0;i++){
        int tmp = numbers[0];
        for(int j = 1;j<n;j++){
            numbers[j-1] = numbers[j];
        }
        numbers[n-1] = tmp;
    }
}

void changePosition(int newA0,int n,int m,int numbers[]){
    reverse(numbers,0,n-newA0-1);
    reverse(numbers,n-newA0,n-1);
    reverse(numbers,0,n-1);
}

void printList(int list[],int count){
    for(int i =0;i<count;i++){
       if(i != count-1){
           printf("%d ",list[i]);
       }else{
           printf("%d",list[i]);
       }
    }
}

void reverse(int list[],int start,int end){
    if(start == end){
        return;
    }
    int left = start;
    int right = end;
    while(left < right){
        int tmp = list[left];
        list[left] = list[right];
        list[right] = tmp;
        left++;
        right--;
    }
}
```


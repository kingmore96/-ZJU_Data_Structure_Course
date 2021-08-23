## Resource
https://pintia.cn/problem-sets/434/problems/5405
## Code
```c
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>

int calculate(int[],int *);

int main(){
    //操作数
        //没有操作符，等待计算
        //有操作符，取出操作符和前一个操作数，判断操作符，进行计算后存入
    //操作符，等待计算；若为等号，则输出操作数，计算结束
    //异常情况:除法的第二个操作数不能为0，为0则终止计算；若遇到非法操作符，则终止计算
    int tmp[2] = {-1,-1};
    while(1){
        //一直读到操作符停止
        char string[100] = "";
        int i = 0;
        char c;
        while(isdigit(c = getchar())){
            string[i++] = c;
        }
        //转化为数字
        int number = atoi(string);
        //printf("number is %d\n",number);
        if(tmp[1] == -1){
            tmp[0] = number;
        }else{
            if(!calculate(tmp,&number)){
                printf("%s","ERROR");
                return 0;
            }
        }
        //读到操作符
        switch(c){
            case '=':
                printf("%d",tmp[0]);
                return 0;
            case '+':
            case '-':
            case '*':
            case '/':tmp[1] = (int)c;break;
            default:
                printf("%s","ERROR");
                return 0;
        }
     }
}

int calculate(int p[],int* c){
    int operator = p[1];
    int number = *c;
    //printf("calculate: number is %d\n",number);
    int newResult;
    switch(operator){
        case '+':
            //printf("calculate, operator is +\n");
            newResult = p[0] + number;
            //printf("newResult is %d\n",newResult);
            break;
        case '-':
            //printf("calculate, operator is -\n");
            newResult = p[0] - number;
            //printf("newResult is %d\n",newResult);
            break;
        case '*':
            //printf("calculate, operator is *\n");
            newResult = p[0] * number;
            //printf("newResult is %d\n",newResult);
            break;
        case '/':
            //printf("calculate, operator is /\n");
            if(number == 0){
               //printf("calculate, operator is /\n");
               return 0;
            }
            newResult = p[0] / number;
            //printf("newResult is %d\n",newResult);
            break;
    }
    p[0] = newResult;
    return 1;
}
```

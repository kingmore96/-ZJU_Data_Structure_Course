## Resourse
https://pintia.cn/problem-sets/434/problems/965573204499779584

## Code
```c
bool Insert( List L, ElementType X ){
    //判断数组是否已满
    if(L->Last == MAXSIZE - 1){
        return false;
    }
    
    //若最小，直接插入即可
    if(L->Data[L->Last] > X){
        L->Data[++L->Last] = X;
        return true;
    }
    
    //判断在数组中是否存在
    Position left = 0;
    Position right = L->Last;
    while(left <= right){
        Position mid = left + (right -left)/2;
        if(L->Data[mid] == X){
            return false;
        }else if(L->Data[mid] > X){
            left = mid + 1;
        }else{
            right = mid - 1;
        }
    }
    
    //找到插入位置
    int rightPosition = -1;
    for(int i =0;i<=L->Last;i++){
        if(L->Data[i] < X){
            rightPosition = i;
            break;
        }
    }
    
    //插入
    for(int i = L->Last;i>=rightPosition;i--){
        L->Data[i+1] = L->Data[i];
    }
    L->Data[rightPosition] = X;
    L->Last++;
    return true;
}
```

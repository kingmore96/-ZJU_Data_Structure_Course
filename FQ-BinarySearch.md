## Resource
https://pintia.cn/problem-sets/434/problems/965458856133562368

## code
```c
Position BinarySearch( List L, ElementType X ){
    Position left = 1;
    Position right = L->Last;
    while(left <= right){
        Position mid = left + (right - left)/2;
        //printf("mid:%d\n", mid);
        if(L->Data[mid] == X){
            return mid;
        }else if(L->Data[mid] < X){
            left = mid + 1;
        }else{
            right = mid - 1;
        }
    }
    return NotFound;
}
```

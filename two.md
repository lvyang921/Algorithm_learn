## 问题引入 
---
Que1(荷兰国旗问题)：给定一个数组arr,和一个数num，请把小于等于num的数放在数组的左边，等于num的数放在数组中间，大于num的数放在数组的右边 *要求额外空间复杂度为O(1),时间复杂度为O(N)*
 ```
def helan(arr,num):
    less=-1
    more=len(arr)
    curr=0
    while curr!=more:
        if arr[curr]<num:
            arr[less+1],arr[curr]=arr[curr],arr[less+1]
            less+=1
            curr+=1
        elif arr[curr]>num:
            arr[more-1],arr[curr]=arr[curr],arr[more-1]
            more=more-1
        else:
            curr+=1
```
# 随机快速排序
--- 
- 时间复杂度O(N*logN)
- 额外空间复杂度 O(logN)
### 经典快排
```
def quick_sort(arr):
    less=-1
    more=len(arr)
    curr=0
    num=arr[-1]
    while curr!=more:
        if arr[curr]<num:
            arr[less+1],arr[curr]=arr[curr],arr[less+1]
            less+=1
            curr+=1
        elif arr[curr]>num:
            arr[more-1],arr[curr]=arr[curr],arr[more-1]
            more=more-1
        else:
            curr+=1
    if curr==more:
        return
    quick_sort(arr[:less+1])
    quick_sort(arr[more:])
```
### 随机快排
```
import random
def quick_sort(arr):
    less=-1
    more=len(arr)
    curr=0
    num=
    while curr!=more:
        if arr[curr]<num:
            arr[less+1],arr[curr]=arr[curr],arr[less+1]
            less+=1
            curr+=1
        elif arr[curr]>num:
            arr[more-1],arr[curr]=arr[curr],arr[more-1]
            more=more-1
        else:
            curr+=1
    if curr==more:
        return
    quick_sort(arr[:less+1])
    quick_sort(arr[more:])
```


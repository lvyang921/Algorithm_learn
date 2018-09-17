# 冒泡排序
---
冒泡法排序   一次判断两个数大小 交换交换排序  
- 复杂度 O(N^2)
```
def maopao(vt):
    long = len(vt)
    while long >1:
        for i in range(0,long-1):
            if vt[i]>vt[i+1]:
                vt[i+1],vt[i]=vt[i],vt[i+1]
        long=long-1
    return vt
```
# 选择排序
---
选择排序 从序列里依次找到最小的放到开始 
- 复杂度 O(N^2)
```
def xuanze(vt):
    list=[]
    long = len(vt)
    while long >=1:
        list.append(min(vt))
        vt.remove(min(vt))
        long=long-1
    return list
```
# 插入排序
---
插入排序  从第i个位置依次向前直到停下 
- 复杂度 O(N^2)
- 与数据状况有关 最好为O(N)
- 复杂度一律按照最差估计
```
def charu(vt):
    long=len(vt)
    for i in range(1,long):
        j=i-1
        while vt[j]>vt[j+1] and j>=0:
            vt[j+1],vt[j]=vt[j],vt[j+1]
            j=j-1

    return vt
```

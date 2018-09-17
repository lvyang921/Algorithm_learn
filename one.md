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
# 归并排序
---
- 复杂度 O(N*logN)
## 小和问题 
在一个数组中，每一个数左边比当前数小的数累加起来，叫做这个数组的小和。求一个数组的小和 

```
def merge_sort(arr,l,r):
    if l==r:
        return 0
    else:
        mid=l+((r-l)>>1)
        return merge_sort(arr,l,mid)+merge_sort(arr,mid+1,r)+merge(arr,l,mid,r)

def merge(arr,l,m,r):
    help=[]
    p1=l
    p2=m+1
    res=0
    while p1<=m and p2<=r:
        if arr[p1] < arr[p2]:
            res += (r - p2 + 1)*arr[p1]
            help.append(arr[p1])
            p1+=1
        else:
            help.append(arr[p2])
            p2 += 1
    while p1 <= m :
        help.append(arr[p1])
        p1 += 1
    while p2 <= r :
        help.append(arr[p2])
        p2 += 1
    for i in range(len(help)):
        arr[l+i]=help[i]
    return res
def small_sum(arr):
    if len(arr)<1:
        return 0
    else:
        return merge_sort(arr,0,len(arr)-1)
```


## 逆序对问题
在一个数组中，左边的数如果比右边的数大，则两个数构成一个逆序对，，请打印所有的逆序对
- 与小和问题类似
```
def merge_sort(arr,l,r):
    if l==r:
        return 0
    else:
        mid=l+((r-l)>>1)
        return merge_sort(arr,l,mid)+merge_sort(arr,mid+1,r)+merge(arr,l,mid,r)

def merge(arr,l,m,r):
    help=[]
    p1=l
    p2=m+1
    while p1<=m and p2<=r:
        if arr[p1] > arr[p2]:
            print arr[p1],arr[p2]
            help.append(arr[p2])
            p2+=1
        else:
            help.append(arr[p1])
            p1+= 1
    while p1 <= m :
        help.append(arr[p1])
        p1 += 1
    while p2 <= r :
        help.append(arr[p2])
        p2 += 1
    for i in range(len(help)):
        arr[l+i]=help[i]
    return 0
def small_sum(arr):
    if len(arr)<1:
        return 0
    else:
        return merge_sort(arr,0,len(arr)-1)
```
  
---

# 细节问题
- ``$\frac{L+R}{2}$`` 可能会导致溢出，应改为``$L+\frac{R-L}{2}$``


- ``$\frac{a}{2}$``相当于 ``a>>2`` , 2a 相当于``a<<2``
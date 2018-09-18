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
- 任何递归函数在工程上为非递归
- 工程上不允许出现递归，因为代价大，手动压栈
### 经典快排
```
def sort(arr,l,r): 
    if l<r:
        less=l-1
        curr=l
        num=arr[-1]
        while curr<=r:
            if arr[curr] < num:
                arr[less + 1], arr[curr] = arr[curr], arr[less + 1]
                less += 1
                curr += 1
            else:
                curr += 1
        return less
def quick_sort(arr,l,r):
    if l<r:
        p=sort(arr,l,r)
        quick_sort(arr,l,p)
        quick_sort(arr,p+1,r)
```
### 随机快排
```
import random
def sort(arr,l,r):
    if l<r:
        less=l-1
        curr=l
        num=random.sample(arr,1)[0]
        while curr<=r:
            if arr[curr] < num:
                arr[less + 1], arr[curr] = arr[curr], arr[less + 1]
                less += 1
                curr += 1
            else:
                curr += 1
        return less
def quick_random(arr,l,r):
    if l<r:
        p=sort(arr,l,r)
        quick_random(arr,l,p)        quick_random(arr,p+1,r)
```

# 堆排列（重要）
---
## 背景
#### 补充二叉树可以用list表示
- 堆为完全二叉树（从左到右依次填满）
    1. 父节点记为i，其左子节点为2*i+1，右子节点2*i+2i+2
    2. 父节点为 i-1/2

#### 堆 
- 大根堆 ：任何子树的最大值为子树的头部 
- 小根堆 ：任何子树的最小值为子树的头部 
形成大根堆（向上）：
```
def heapinsert(arr,i):
    def chu(i):
        if i==0:
            return 0
        if i>0:
            return (i-1)>>1
    while arr[i]>arr[chu(i)]:
        arr[i],arr[chu(i)]=arr[chu(i)],arr[i]
        i=chu(i)
def heapsort(arr):
    for i in range(len(arr)):
        heapinsert(arr,i)
```
当大根堆中某元素变小时形成大根队（向下）：
```
def heapify(arr,index,heapsize):
    left=index*2+1
    while left<heapsize:
        if arr[left]<arr[left+1] and arr[left+1]<heapsize:
            largest=left+1
        else:
            largest=left
        if arr[largest]<arr[index]:
            largest=index
        if largest==index:
            break
        arr[index],arr[largest]=arr[largest],arr[index]
        index=largest
        left=index*2+1
```
其中``index``为变小元素下标，``heapsize``这一子堆数列长度
- 弹出大根堆顶：相当于数列尾与数列头部交换 删除当前数列尾部且``heapsize``减1 最后对当前堆顶``heapify（）``
- **应用：**对于流式数据处理，可各建立一大根堆与小根堆，添加入大根堆，当大根堆与小根堆数量差大于1，则弹出大根堆堆顶加入小根堆。此时大根堆堆顶为数据为最小的N/2的最大值，小根堆堆顶为最大的N/2的最小值。故两堆顶通过计算可以得到时时的中位数。
## 堆排序
- 时间复杂度O（N*logN）,空间复杂度O（1）
```
def heapinsert(arr,i):
    def chu(k):
        if k==0:
            return 0
        if k>0:
            return (k-1)/2
    while arr[i]>arr[chu(i)]:
        arr[i],arr[chu(i)]=arr[chu(i)],arr[i]
        i=chu(i)
def heapsort(arr):
    for i in range(len(arr)):
        heapinsert(arr,i)

def heapify(arr,index,heapsize):
    left=index*2+1
    while left<heapsize:
        if arr[left]<arr[left+1] and arr[left+1]<heapsize:
            largest=left+1
        else:
            largest=left
        if arr[largest]<arr[index]:
            largest=index
        if largest==index:
            break
        arr[index],arr[largest]=arr[largest],arr[index]
        index=largest
        left=index*2+1
def heap_sort(arr):
    heapsort(arr)
    heapsize=len(arr)
    arr[0],arr[heapsize-1]=arr[heapsize-1],arr[0]
    heapsize-=1
    while heapsize>0:
        heapify(arr,0,heapsize)
        arr[0], arr[heapsize - 1] = arr[heapsize - 1], arr[0]
        heapsize -= 1
```

# 其他
---
## 排序的稳定性
- 排序的稳定性指相同的指在排序后的原始次序不变 
  1.稳定：冒泡排序、插入排序、归并排序、桶排序、计数排序、基数排序
  2.不稳定：选择排序、快速排序、堆排序
- 稳定性的意思：现实业务需要稳定性

## 比较器
- 对于自定义类的实例或自定义数据进行比较可以自定义比较器对其中自定义内容进行比较
- python中可通过sorted（）函数插入比较器
- 堆结构也可以用比较器

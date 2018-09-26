## Que1
---
对于矩阵
[[1,2,3],
[4,5,6],
[7,8,9]]
进行转圈打印

```
a=[[1,2,3],[4,5,6],[7,8,9]
def print_wai(lis,a,b,c,d):
    for j in range(b-1,d-1):
        print lis[a-1][j]
    for i in range(a-1,c-1):
        print lis[i][d-1]
    for j in range(d-1,a-1,-1):
        print lis[c-1][j]
    for i in range(c-1,a-1,-1):
        print lis[i][a-1]
def print_mat(lis,a,b,c,d):
    while not (a>c or b>d):
        print_wai(lis,a,b,c,d)
        a+=1
        b+=1
        c-=1
        d-=1
```

## Que2
---
对于矩阵
[[1,2,3,4],
[5,6,7,8],
[9,10,11,12]
[13,14,15,16]]
进行之字打印
```
a=[[1,2,3,4],[5,6,7,8],[9,10,11,12],[13,14,15,16]]
def print_jiao(lis,a,b,c,d,bool):
    if bool==1:       #from down to up
        while d<=b:
            print lis[c][d]
            c-=1
            d+=1
    else:
        while a<=c:
            print lis[a][b]
            a+=1
            b-=1
def print_zhi(lis):
    row=len(lis)
    column=len(lis[0])
    arr=1
    a=0
    b=0
    c=0
    d=0
    while a<=row and d<=column:
        print_jiao(lis,a,b,c,d,arr)
        if b+1>column-1:
            a+=1
        else:
            b+=1
        if c+1>row-1:
            d+=1
        else:
            c+=1
        if arr==1:
            arr=0
        else:
            arr=1
```
## Note
---
- 对于判断链表是否为回文结构 可设计快指针走两步 慢指针走一步 当快指针走到底 慢指针指向中点
- 对于有向有环链表 可设计快指针走两步 慢指针走一步 当快慢指针相遇 下一节点为该有向有环图的 第一个相遇节点 
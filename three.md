## Que1
转圈打印问题：对于矩阵

[[1,2,3],
[4,5,6],
[7,8,9]]
进行转圈打印

```
a=[[1,2,3,4],[5,6,7,8],[9,10,11,12],[13,14,15,16]]
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
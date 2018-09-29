# 二叉树实现
---
```
class Node:
    def __init__(self,item):
        self.item = item
        self.child1 = None
        self.child2 = None


class Tree:
    def __init__(self):
        self.root = None

    def add(self, item):
        node = Node(item)
        if self.root is None:
            self.root = node
        else:
            q = [self.root]

            while True:
                pop_node = q.pop(0)
                if pop_node.child1 is None:
                    pop_node.child1 = node
                    return
                elif pop_node.child2 is None:
                    pop_node.child2 = node
                    return
                else:
                    q.append(pop_node.child1)
                    q.append(pop_node.child2)
```

# 二叉树遍历
---
## 递归遍历
- 二叉树的遍历：先遍历head 再遍历左子树 后遍历右子树
- 先序 为返回第一次遍历的值(先当前节点->左子树->右子树)；
- 中序 为返回第二次遍历的值(先左子树->当前节点->右子树)； 
- 后序 为返回第三次遍历的值(先左子树->右子树->当前节点)

## 非递归遍历
- 用栈的方式实现先序：
   1. 压入当前节点
   2. 弹出栈当前值输出 且压入：
       a. 有左child压入
       b. 有右child压入
   3. 重复步骤2
- 用栈的方式实现中序：
   1. 压入头节点 头节点指向左child
   2. 当节点为空 且栈不为空 弹出栈 节点指向该弹出点右child
   3. 重复步骤1、2
- 用栈的方式实现中序：
   1. 实现先序类似 先实现先中再右再左的方法
   2. 因为栈是输入的逆序 所以把1中的栈弹出的值压入一个新的栈 那么就变成了先左再右再中

# 二叉树的前驱后继
--- 
## 二叉树后继节点
二叉树后继节点为在中序遍历中遍历该节点的下一个值，方法为：
1. 如果有右子树，则为右子树的最左节点
2. 如果没有右子树，判断是否为其父节点的右节点，是则继续判断，知道为左节点。那么后继节点为该左节点的父节点。如为空则无后继节点
## 二叉树前驱节点
二叉树前驱节点为在中序遍历中遍历该节点的上一个值，方法与后继节点相反

# 各类二叉树
---
- 平衡二叉树：对于二叉树的任何一个节点 其左子树和右子树高度差不超过1
- 搜索二叉树：对于二叉树的任何一个节点 其左子树都比它小 右子树都比它大 （中序遍历依次升序）
- 完全二叉树（见堆）判断原则：
    1. 如果只有右child 则不是
    2. 如果只有左child or 没有child则其后的所有节点必须为叶节点

# Note
- 如果一个二叉树是一个满二叉树高度为l,其节点个数为2^l-1个
- 二叉树适合用递归函数的思想
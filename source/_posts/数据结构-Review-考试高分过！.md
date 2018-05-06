---
title: 数据结构-Review-考试高分过！
date: 2018-04-29 10:42:36
tags:
---

### 前言

复习一下课没好好上过的数据结构，唉！要期末考试噜！得刷一波绩点啦！！！认真复习嗯嗯嗯！一边复习一边总结，边看书边看别人写的`blog`，做了一些小总结。不过嘛，数据结构和算法要是想成为`Master`，还得加把劲努力啦！

> Q：如何高效率使用这篇总结？
> A：查看写的所有数据结构的定义，然后戳所有带`-> recommend！`这个标识的链接，嗯！速度就是这样~认真的话，建议复写所有数据结构的实现代码啦！

---

### 目录

1. **线性表**
    1.1 顺序表示和实现
    1.2 链式表示和实现
    1.2.1 `线性链表`
    1.2.2 `循环链表`
    1.2.3 `双向链表`

2. **栈和队列**
    2.1 栈
    2.2 队列

3. **数组**
    3.1 数组的顺序表示和实现
    3.2 矩阵的压缩存储
    3.2.1 `稀疏矩阵`

4. **树**
    4.1 二叉树
    4.2 遍历二叉树
    4.2.1 `三大遍历的递归实现`
    4.2.2 `三大遍历的非递归实现`
    4.2.3 `层次遍历`
    4.3 树和森林
    4.3.1 `数和森林的存储结构`
    4.3.2 `数和森林的遍历`
    4.4 赫夫曼树

5. **图**
    5.1 图的定义
    5.2 图的存储结构
    5.2.1 `邻接表`
    5.2.2 `十字链表`
    5.3 图的遍历
    5.3.1 `深度优先搜索`
    5.3.2 `广度优先搜索`
    5.4 图的连通性
    5.4.1 `最小生成树`
    5.5 拓扑排序
    5.6 最短路径

6. **查找**
    6.1 静态查找
    6.2 动态查找
    6.2.1 `二叉排序树`
    6.3 哈希表

7. **内部排序**
    7.1 插入排序
    7.1.1 `直接插入排序`
    7.1.2 `希尔排序`
    7.2 快速排序
    7.3 选择排序
    7.4 归并排序

---

### 1. 线性表

> 线性表`Linear_list`是最常用且最简单的一种数据结构。简言之，一个线性表是n个数据元素的有限序列。

#### 1.1 顺序表示和实现

> 线性表的顺序表示`Sequential List`指的是用一组地址连续的储存单元依次储存线性表的数据元素。`顺序储存结构`是一种随机存取的储存结构。通常用`数组`来描述顺序储存结构。

C语言用动态分配的一维数组，来描述线性表：

~~~C
 #define LIST_INIT_SIZE 100 //线性表储存空间的初始分配量
 #define LISTINCREMENT 10 //线性表的分配量
typedef int ElemType;
typedef struct {
    ElemType *elem;  // 储存空间的基地址
    int length;  //当前线性表的长度
    int listsize; //当前分配的储存容量
}SqList;
~~~

> 更多有关线性表的知识，请戳：
* [线性表与13个基本操作的实现](https://blog.csdn.net/bruthyu/article/details/52645510)

#### 1.2 链式表示和实现

> 链式储存结构`Linked List`与顺序储存结构`Sequential List`的不同：顺序储存结构的特点是逻辑关系上两个相邻元素在物理位置上也相同，这样随机存取任意元素很快很直观，缺点是需要移动大量其他元素。而链式结构，它不要求逻辑上相邻的元素在物理位置上相邻，因此它存取元素不需要移动其他元素，但是对于查找元素有心无力。

##### 1.2.1 `线性链表`

> 可以理解为单向链表`Singly Linked List`，单向链表是非随机存取结构。

一些常用的方法：

* 添加元素（s是指向待添加节点的指针）

    ~~~C
    s->next = p->next;
    p->next = s;
    ~~~

* 删除元素（a,b,c是链表中相连的3个结点，b是待删除的结点，现在p是指向a结点的指针）

    ~~~C
    p->next = p->next->next;
    ~~~

用结构体实现链表结点：

~~~C
//线性表的单链表储存结构
struct Node {
    int data; //数据域
    struct Node *next; //指针域
};
~~~

> 更多链表知识，请戳：

* [C语言单向链表的实现](https://blog.csdn.net/21aspnet/article/details/160019)
* [链表的基本使用一（构建链表）](https://blog.csdn.net/lan74__/article/details/53819849)
* [数据结构：链表(linked-list)](https://blog.csdn.net/juanqinyang/article/details/51351619)

##### 1.2.2 `循环链表`

1. 循环单链表特点：

    链表中最后一个结点的指针域不再是结束标志，而是指向整个链表的第一个结点，从而使链表形成一个环。和单链表相同，循环单链表也有带头结点和不带头结点两种。带头结点的循环单链表实现插入和删除操作较为方便，且更加适用。

2. 单链表与循环单链表比较：

    循环单链表可以从尾到头，而单链表不能从尾到头。因此处理的数据序列具有环形结构特点时，适合采用循环单链表。

3. 带头结点的循环单链表和带头结点的单链表比较：

    ① 在初始化函数中，把语句`head->next=NULL`改为`head->next = head`，即形成一个环 
    ② 在其他函数中，循环判断条件`p->next!=NULL`和`p->next->next!=NULL`中的NULL改成头指针`head`。

##### 1.2.3 `双向链表`

1. 双向链表特点：
    每个节点除了有后继指针域还有一个前驱指针域。

2. 双向链表的分类：
    双向链表有：带头结点和不带头结点的双向链表（但是带头结点的双向链表更为常用）。也有循环和非循环之分，循环结构的双向链表更为常用。因此下面讨论的是带头结点的循环双链表。

3. 双向循环链表结点的结构体定义
    ~~~C
    //线性表的双向链表储存结构
    struct DuLNode {
        Elemtype data; //数据域
        struct DuLNode *prior; //前驱结点
        struct DuLNode *next;  //后继结点
    }DuLNode， *DuLinklist;
    ~~~
    **备注**：data域、next域、prior域。其中data域是数据域，next域为指向后继结点的指针域，prior域为指向前驱结点的指针域。

4. 双向链表的优点：
    在单链中查找当前结点的后继结点并不困难，可以通过当前结点的next指针进行，但要查找当前结点的前驱结点，就要从头指针head开始重新进行。对于一个要频繁进行当前结点的后继结点和前驱结点的应用来说，使用双向链表很有效。

5. 双向循环链表的实现
    在双向链表中，有如下指针关系：设指针p指向双向循环链表中的第i个位置，则`p->next`指向i+1个结点。`p->next->prior`仍指向第i个结点，即`p->next->prior==p`;同样`p->prior`指向第i-1个结点，`p->prior->next`仍指向第i个结点，即`p->prior->next==p`;双向循环链表关系算法可以方便算法设计。

> 更多循环链表和双向链表的知识，请戳：
* [数据结构——循环单链表和双向链表](https://blog.csdn.net/xiaofei__/article/details/50984255)

* [数据结构 | 双向链表简单实现及图示](http://www.cnblogs.com/hughdong/p/6785391.html) -> *recommend*！

### 2. 栈和队列

从数据结构上看，栈和队列也是线性表。不过他们是操作受限的线性表，因此，称它们为限定性的数据结构。

#### 2.1 栈

栈`stack`是限定仅在表尾进行插入和删除的线性表。对于栈，表尾称为`栈顶`，相应地，表头称为`栈底`。不含元素的空表称为`空栈`。栈是一种后进先出（last in first out, LIFO）结构。

栈有两种储存方式，顺序栈和链式栈。

顺序栈的定义：

~~~C
struct stack {
    SElemType *base;
    SElemType *top;
    int stacksize;
}SqStack;
~~~

**备注**：`stacksize`指当前可使用的最大容量，`base`表示栈底指针，`base`为NULL时，表明栈结构不存在，其初值指向栈底，即`top = base`可作为栈空的标记。插入元素，top+1；删除元素，top-1。

> 更多栈的知识，请戳：
* [[数据结构]C语言栈的实现](https://www.cnblogs.com/racaljk/p/7822309.html)
* [数据结构图文解析之：栈的简介及C++模板实现](https://www.cnblogs.com/QG-whz/p/5170418.html) -> *recommend*！

#### 2.2 队列

和栈相反，队列`quene`是一种先进先出（first in first out, FIFO）的线性表，它只允许在表的一端插入，另一端删除。在队列中，允许插入的一端叫做队尾`rear`，允许删除的一端叫做队头`front`。

队列也有两种储存方式，顺序队列和链队列。

链队列的实现：

~~~C
struct QNode {
    QElemType data;
    struct QNode *next;
}QNode, *QuenePtr;
struct LinkQuene {
    QuenePtr front; //队头指针
    QuenePtr rear; //队尾指针
}LinkQuene;
~~~

> 更多队列知识，请戳：
* [数据结构-队列(queue)](https://blog.csdn.net/juanqinyang/article/details/51354293) -> *recommend*！

### 3. 数组

数组和广义表可以看作是线性表的扩展，也算是一种数据结构。

#### 3.1 数组的顺序表示和实现

由于数组一般不做插入或删除操作，因此采用顺序储存结构表示数组是最吼滴！

> 假设每个数据元素占$L$个存储单元，则二维数组$A$中任一元素$aij$的存储位置可由下式确定：$LOC(i, j) = LOC(0, 0) + (b_2*i + j)L$

数组的顺序存储的表示：

~~~C
 #define MAX_ARRAY_DIM 8
struct array {
    ElemType *base;
    int dim;
    int *bounds;
    int *constants;
}Array;
~~~

#### 3.2 矩阵的压缩存储

> 压缩存储指的是为多个值相同的元只分配一个存储单元；对零元不分配空间。

##### 3.2.1 `稀疏矩阵`

> 对于那些零元素数目远远多于非零元素数目，并且非零元素的分布没有规律的矩阵称为稀疏矩阵（sparse）。

* 由于非零元素分布没有任何规律，所以在进行压缩存储的时侯需要存储非零元素值的同时还要存储非零元素在矩阵中的位置，即非零元素所在的行号和列号，也就是在存储某个元素比如$aij$的值的同时，还需要存储该元素所在的行号$i$和它的列号$j$，这样就构成了一个三元组$(i,j,aij)$的线性表。

```C
 #define MAXSIZE 12500
struct triple {
    int i, j; // 该非零元的行下标和列下标
    ElemType e;
}Triple;
struct tsmatrix {
    Triple data[MAXSIZE + 1]; //非零元三元组
    int mu, nu, tu; //行数，列数，非零元个数
}TSMatrix;
```

> 更多稀疏矩阵的知识，请戳：

* [稀疏矩阵](https://blog.csdn.net/sunhuaqiang1/article/details/51296803)

### 4. 树

> 树状图是一种数据结构，它是由$n$（$n>=1$）个有限节点组成一个具有层次关系的集合。把它叫做“树”是因为它看起来像一棵倒挂的树，也就是说它是根朝上，而叶朝下的。它具有以下的特点：
> * 每个节点有零个或多个子节点
> * 没有父节点的节点称为根节点
> * 每一个非根节点有且只有一个父节点（除了根节点外，每个子节点可以分为多个不相交的子树）

#### 4.1 二叉树

> 二叉树`Binary Tree`是另一种树型结构，它的特点是每个结点至多有$2$棵子树（即二叉树中不存在度大于$2$的结点），并且，二叉树的子树有左右之分，其次序不能任意颠倒。

二叉树的性质：

* 在二叉树的第$i$层上至多有$2^(i-1)$个结点（$i>=1$）。
* 深度为$k$的二叉树至多有$2^k - 1$个结点（$K>=1$）。
* 对任何一棵二叉树$T$，如果其终端结点数为$n_0$，度为$2$的结点树为$n_2$，则$n_0=n_2+1$。
* 具有$n$个结点的完全二叉树的深度为|$\log_2 n$| + 1。（|$\log_2 n$|表示不大于$\log_2 n$的最大整数）
* 如果对一棵有$n$个结点的完全二叉树（其深度为|$\log_2 n$| + 1）的结点按层序编号（从第$1$层到第|$\log_2 n$| + $1$层，每层从左到右），则对任一结点$i$（$1 <= i <= n$），有：
    1. 如果$i = 1$，则结点$i$是二叉树的根，无双亲；如果$i > 1$，则其双亲`PARENT(i)`是结点|$i/2$|。
    2. 如果$2i > n$，则结点$i$无左孩子（即结点i为叶子结点）；否则其左孩子`LCHILD(i)`是结点$2$。
    3. 如果$2i + 1 > n$，则结点$i$无右孩子；否则其右孩子`RCHILD(i)`是结点$2i+1$。

二叉树的顺序储存结构（仅适用于完全二叉树）：

```C
# define MAX_TREE_SIZE 100 // 二叉树的最大结点树
typedef TElemType SqBiTree[MAX_TREE_SIZE]; // 0号单元存储根节点
SqBiTree bt;
```

二叉树的链式存储结构：

```C++
struct BiTree {
    TElemType data; // 数据域
    struct BiTree *lchild, *rchild; // 左右孩子指针
}BiTree, *BiTree;
```

> 更多二叉树知识，请戳：

* [二叉树总结(一)概念和性质](https://www.cnblogs.com/yeqluofwupheng/p/7428935.html)

* [markdown中的数学公式简要](https://blog.csdn.net/wireless_com/article/details/70596155)

#### 4.2 遍历二叉树

> 二叉树是一种非线性结构，是由3个基本单元组成：根节点，左子树和右子树。规定先左后右，有3种基本情况，先序遍历，中序遍历和后序遍历。

##### 4.2.1 `三大遍历的递归实现`

* 先序遍历（根-左-右）

    ~~~C
    void preOrder1(BinaryTreeNode* pRoot)  
    {  
        if(pRoot==NULL)  
            return;  
    
        cout<<pRoot->value;  
        if(pRoot->left!=NULL)  
            preOrder1(pRoot->left);  
        if(pRoot->right!=NULL)  
            preOrder1(pRoot->right);  
    } 
    ~~~

* 中序遍历（左-根-右）

    ~~~C
    void inOrder1(BinaryTreeNode* pRoot)  
    {  
        if(pRoot==NULL)  
            return;  
        
        if(pRoot->left!=NULL)  
            inOrder1(pRoot->left);  
        cout<<pRoot->value;  
        if(pRoot->right!=NULL)  
            inOrder1(pRoot->right);  
    }
    ~~~

* 后序遍历（左-右-根）

    ~~~C
    void postOrder1(BinaryTreeNode* pRoot)  
    {  
        if(pRoot==NULL)  
            return;  
        postOrder1(pRoot->left);  
        postOrder1(pRoot->right);  
        cout<<pRoot->value<<" ";  
    }  
    ~~~

##### 4.2.2 `三大遍历的非遍历实现`

* 先序遍历（根-左-右）

    ~~~C
    void preOrder2(BinaryTreeNode* pRoot)  
    {  
        stack<BinaryTreeNode*> s;  
        BinaryTreeNode *p=pRoot;  
    
        if(pRoot==NULL)  
            return;  
        while(p!=NULL||!s.empty())  
        {  
            while(p!=NULL)  
            {  
                cout<<p->value<<" ";  
                s.push(p);  
                p=p->left;  
            }  
            if(!s.empty())  
            {  
                p=s.top();  
                s.pop();  
                p=p->right;  
            }  
        }  
    }  
    ~~~

* 中序遍历（左-根-右）

    ~~~C
    void inOrder(BinaryTreeNode* pRoot)  
    {  
        stack<BinaryTreeNode*> s;  
        BinaryTreeNode *p=pRoot;  
        while(p!=NULL||!s.empty())  
        {  
            while(p!=NULL)  
            {  
                s.push(p);  
                p=p->left;  
            }  
            if(!s.empty())  
            {  
                p=s.top();  
                cout<<p->value;  
                s.pop();  
                p=p->right;  
            }  
        }  
    }  
    ~~~

* 后序遍历（左-右-根）

    ~~~C
    void postOrder(BinaryTreeNode* pRoot)  
    {  
        stack<BinaryTreeNode*> s;  
        BinaryTreeNode *cur;  
        BinaryTreeNode *pre=NULL;  
        s.push(pRoot);//根结点入栈  
        while(!s.empty())  
        {  
            cur=s.top();  
            if((cur->left==NULL&&cur->right==NULL)||(pre!=NULL&&(pre==cur->left||pre==cur->right)))  
            {  
                //左孩子和右孩子同时为空，或者当前结点的左孩子或右孩子已经遍历过了  
                cout<<cur->value<<" ";  
                s.pop();  
                pre=cur;  
            }  
            else  
            {  
                if(cur->right!=NULL)  
                    s.push(cur->right);  
                if(cur->left!=NULL)  
                    s.push(cur->left);  
            }  
        }  
    } 
    ~~~

##### 4.2.3 `层次遍历`

~~~C
void PrintFromTopToBottom(BinaryTreeNode* pRoot)  
{  
    if(pRoot == NULL)  
        return;  
  
    std::deque<BinaryTreeNode *> dequeTreeNode;  
  
    dequeTreeNode.push_back(pRoot);  
  
    while(dequeTreeNode.size())  
    {  
        BinaryTreeNode *pNode = dequeTreeNode.front();  
        dequeTreeNode.pop_front();  
  
        printf("%d ", pNode->m_nValue);  
  
        if(pNode->m_pLeft)  
            dequeTreeNode.push_back(pNode->m_pLeft);  
  
        if(pNode->m_pRight)  
            dequeTreeNode.push_back(pNode->m_pRight);  
    }  
}  
~~~

> 更多二叉树的知识，请戳：
* [二叉树的四种遍历的递归和非递归的实现](https://blog.csdn.net/xiaominkong123/article/details/51567437) -> *recommend*！
* [二叉树三种遍历方式的递归和循环实现](https://blog.csdn.net/lieacui/article/details/52453292)

#### 4.3 树和森林

##### 4.3.1 `树的存储结构`

> 双亲表示法

~~~C
 #define MAX_TREE_SIZE 100
typedef struct PTNode { // 结点结构
    TElemType data; // 数据域
    int parent; // 双亲位置域
}PTNode;
typedef struct { // 树结构
    PTNode nodes[MAX_TREE_SIZE]; 
    int r, n; // 根的位置和结点数
}
~~~

缺点：求结点的孩子时需要遍历整个结构。

>  孩子表示法

~~~C
typedef struct CTNode { // 孩子结点
    int child; 
    sturct CTNode *next;
}*ChildPtr;
typedef struct {
    TElemType data;
    ChildPtr firstchild; // 孩子链表头结点
}CTBox;
typedef struct {
    CTBox nodes[MAX_TREE_SIZE];
    int n, r; // 结点数的根的位置
}
~~~

> 孩子兄弟表示法（可以把复杂的树变成二叉树）

~~~C
typedef struct CSNode {
    ElemType data;
    struct CSNode *firstchild, *nextsibling; // 第一个孩子结点和下一个兄弟结点
}
~~~

##### 4.3.2 `树和森林的遍历`

当二叉链表作为树的储存结构时，树的**先根遍历**和**后根遍历**类似于二叉树的**先序遍历**和**中序遍历**实现。

森林一般只说**先序遍历**和**中序遍历**，和二叉树的**先序遍历**和**中序遍历**相同。

> 更多树和森林的知识，请戳：
* [树的存储结构和代码实现](https://blog.csdn.net/qq_36016407/article/details/55272598)
* [树和森林的遍历](https://blog.csdn.net/wangzi11322/article/details/45391157)

#### 4.4 赫夫曼树

> 赫夫曼树`Huffman`，又称最优二叉树，是一类带权路径长度最短的树。树的路径长度为树中所有叶子结点的带权路径长度之和。通常记作$WPL=\sum_{k=0}^{n}\omega_k\iota_k$ 。

假设有n个权值，构造一棵有n个叶子结点的二叉树，每个叶子结点带权为$\omega_i$，则其中带权路径长度$WPL$最小的二叉树称为**赫夫曼树**。

~~~C
typedef struct {
    unsigned int weight; // 权重
    unsigned int parent, lchild, rchild; 
}HTNode, *HuffmanTree; // 动态分配数组存储赫夫曼树
~~~

> 更多赫夫曼树的知识，请戳：
* [哈夫曼树](https://blog.csdn.net/wo16fafafa/article/details/52420007)
* [基础数据结构-二叉树-赫夫曼树的解码](https://www.cnblogs.com/nathaneko/p/6497982.html)

### 5. 图

> **图**`Graph`是一种较线性表和树更为复杂的数据结构。在**线性表**中，数据元素之间仅有线性关系，每个数据元素只有一个直接前驱和一个直接后继；在**树**形结构中，数据元素之间有着明显的层次关系，并且每一层上的数据元素可能和下一层的多个元素（即孩子结点）相关，但只和上一层的一个元素（即双亲结点）相关。而在**图**形结构中，结点之间的关系是任意的。

#### 5.1 图的定义

在图中，数据元素称为**顶点**，$V$是顶点的有穷非空集合；$VR$是两个顶点之间的关系集合。

* 若$<v,w>\epsilon VR$,则$<v,w>$表示从$v$到$w$的一条**弧**`Arc`，且称$v$为**弧尾**`Tail`or**初始点**，$w$为**弧头**`Head`or**终端点**。此时的图称为**有向图**`Digraph`。

$$G_1 = (V_1,{A_1})$$

* 若$<v,w>\epsilon VR$，必有$<w,v>\epsilon VR$，即$VR$是对称的，则以无序对$(v,w)$代替这两个有序对，表示$v$和$w$之间的一条**边**`Edge`，此时的图称为**无向图**`Undigraph`。

$$G_2 = (V_2,{E_2})$$

#### 5.2 图的存储结构

> 图的结构较为复杂，常用的存储结构有**邻接表**，**十字链表**。

##### 5.2.1 `邻接表`

> **邻接表**`Adjacency List`是图的一种链式存储结构。

~~~C
 #define MAX_VERTEX_NUM 20
typedef struct ArcNode {
    int adjvex; // 该弧所指向的顶点的位置
    struct ArcNode *nextarc; // 指向下一条弧的指针
    InfoType *info; // 该弧相关信息的指针
}ArcNode;
typedef struct VNode {
    VertexType data; // 顶点信息
    ArcNode *firstarc; //指向第一条依附该顶点的弧的指针
}VNode, AdjList[MAX_VERTEX_NUM];
typedef struct {
    AdjList vertices;
    int vexnum, arcnum; //图的当前顶点数和弧数
    int kind; // 图的种类标志
}ALGraph;
~~~

##### 5.2.2 `十字链表`

> **十字链表**`Orthogonal List`是有向图的另一种链式存储结构。可以看作是将有向图的邻接表和逆邻接表结合起来的一种链表。

~~~C
 #define MAX_VERTEX_NUM 20
typedef struct ArcBox {
    int tailvex, headvex; // 该弧的尾和头顶点的位置
    struct ArcBox *hlink, *tlink; // 分别为弧头相同和弧尾相同的弧的链域
    InfoType *info; // 该弧相关的信息的指针
}ArcBox;
typedef struct VexNode {
    VertexType data;
    ArcBox *firstin, *firstout; // 分别指向该顶点的第一条入弧和出弧
}VexNode;
typedef struct {
    VexNode xlist[MAX_VERTEX_NUM]; // 表头向量
    int vexnum, arcnum; // 有向图的当前顶点数和弧数
}OLGraph;
~~~

> 更多关于图的存储的知识，请戳：
* [数据结构(16)--图的存储及实现](https://blog.csdn.net/u010366748/article/details/50790324)
* [图的存储结构之邻接表(详解)](https://www.cnblogs.com/ECJTUACM-873284962/p/6905416.html)
* [图的存储 ( 十字链表 )](https://blog.csdn.net/wr_technology/article/details/51909432) -> *recommend*！
* [十字链表的画法](https://www.cnblogs.com/zyl905487045/p/7815429.html) -> *recommend*！

#### 5.3 图的遍历

> **图的遍历**`Traversing Graph`指从图中某一顶点出发访遍图中其余顶点，且使每一个顶点仅被访问一次。

##### 5.3.1 深度优先搜索

> **深度优先搜索**`Depth_First Search`遍历类似于树的**先根遍历**。

~~~C
void DFS(Graph G, int v) {
    //从第v个顶点出发递归地深度优先遍历图G
    visited[v] = TRUE;
    visitFunc(v); // 访问第v个顶点
    for(w = FirstAdjVex(G,v); w >= 0; w = NextAdjVex(G,v,w))
        if(!visited[w])
            DFS(G,w); // 对v的尚未访问的邻接顶点w递归调用DFS
}
~~~

##### 5.3.2 广度优先搜索

> **广度优先搜索**`Breadth_First Search`遍历类似于树的**层次遍历**。

~~~C
void BFSTraverse(Graph G, Status(*visit)(int v)) {
    // 按广度优先非递归遍历图G，使用辅助队列Q和访问标志数组visited
    for(v = 0; v < G.vexnum; ++v)
        visited[v] = FALSE;
    InitQuene(Q); // 置空的辅助队列Q
    for(v = 0; v < G.vexnum; ++v)
        if(!visited[v]) { // v尚未访问
            visited[v] = TRUE;
            Visit(v);
            Enquene(Q, v); // v入队列
            while(!QueneEmpty(Q)) {
                DeQuene(Q, u); // 队头元素出列并置为0
                for(w = FirstAdjVex(G, u); w >= 0; w = NextAdjVex(G, u, w))
                    if(!Visited[w]) { // w为u的尚未访问的邻接顶点
                        Visited[w] = TRUE;
                        Visit(w);
                        EnQuene(Q, W);
                    } // if
            } //while
        } // if
} // BFSTraverse
~~~

遍历图的过程实质上是通过边或弧找邻接点的过程，因此广度优先搜索和深度优先搜索地**时间复杂度**相同。

> 更多关于图的遍历的知识，请戳：
* [图的深度优先遍历和广度优先遍历理解](https://www.cnblogs.com/George1994/p/6399889.html)
* [数据结构和算法总结（一）：广度优先搜索BFS和深度优先搜索DFS](https://www.cnblogs.com/0kk470/p/7555033.html) -> *recommend*！

#### 5.4 图的连通性问题

> 对于连通图来说，从任一顶点出发，便可访问图中所有顶点。而对于非连通地图，则需从多个顶点出发进行搜索。

##### 5.4.1 `最小生成树`

关于图的几个概念定义：

* 连通图：在无向图中，若任意两个顶点vi与vj都有路径相通，则称该无向图为连通图。
* 强连通图：在有向图中，若任意两个顶点vi与vj都有路径相通，则称该有向图为强连通图。
* 连通网：在连通图中，若图的边具有一定的意义，每一条边都对应着一个数，称为权；权代表着连接连个顶点的代价，称这种连通图叫做连通网。
* 生成树：一个连通图的生成树是指一个连通子图，它含有图中全部n个顶点，但只有足以构成一棵树的n-1条边。一颗有n个顶点的生成树有且仅有n-1条边，如果生成树中再添加一条边，则必定成环。
* 最小生成树：在连通网的所有生成树中，所有边的代价和最小的生成树，称为最小生成树。

> **最小生成树**`Minimum Cost Spanning Tree`指构造连通网的最小代价生成树。

* **Kruskal算法**

> 此算法可以称为“加边法”，初始最小生成树边数为0，每迭代一次就选择一条满足条件的最小代价边，加入到最小生成树的边集合里。 

1. 把图中的所有边按代价从小到大排序； 
2. 把图中的n个顶点看成独立的n棵树组成的森林； 
3. 按权值从小到大选择边，所选的边连接的两个顶点ui,vi,应属于两颗不同的树，则成为最小生成树的一条边，并将这两颗树合并作为一颗树。 
4. 重复(3),直到所有顶点都在一颗树内或者有n-1条边为止。


* **Prim算法**

> 此算法可以称为“加点法”，每次迭代选择代价最小的边对应的点，加入到最小生成树中。算法从某一个顶点s开始，逐渐长大覆盖整个连通网的所有顶点。

1. 图的所有顶点集合为V；初始令集合u={s},v=V−u;
2. 在两个集合u,v能够组成的边中，选择一条代价最小的边(u0,v0)，加入到最小生成树中，并把v0并入到集合u中。
3. 重复上述步骤，直到最小生成树有n-1条边或者n个顶点为止。

由于不断向集合u中加点，所以最小代价边必须同步更新；需要建立一个辅助数组closedge,用来维护集合v中每个顶点与集合u中最小代价边信息：

~~~C
struct
{
    char vertexData   //表示u中顶点信息
    UINT lowestcost   //最小代价
}closedge[vexCounts]
~~~

> 更多关于最小生成树的知识，请戳：
* [算法导论--最小生成树（Kruskal和Prim算法）](https://blog.csdn.net/luoshixian099/article/details/51908175) -> *recommend*！

#### 5.5 拓扑排序

> **拓扑排序**`Topological Sort`指由某个集合上的一个偏序得到该集合上的一个全序。

拓扑排序的实现步骤:

1. 在有向图中选一个没有前驱的顶点并且输出。
2. 从图中删除该顶点和所有以它为尾的弧（白话就是：删除所有和它有关的边）。
3. 重复上述两步，直至所有顶点输出，或者当前图中不存在无前驱的顶点为止，后者代表我们的有向图是有环的。

因此，也可以通过拓扑排序来判断一个图是否有环。

> 更多关于拓扑排序的知识，请戳：
* [数据结构---拓扑排序详解](https://blog.csdn.net/qq_35644234/article/details/60578189)

#### 5.6 最短路径

> **最短路径**指从图中的某个顶点出发到达另外一个顶点的所经过的边的权重和最小的一条路径.

> 更多关于最短路径的知识，请戳：
* [最短路径问题---Dijkstra算法详解](https://blog.csdn.net/qq_35644234/article/details/60870719)
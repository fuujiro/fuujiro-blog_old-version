---
title: ���ݽṹ-Review-���Ը߷ֹ���
date: 2018-04-29 10:42:36
tags:
---

### ǰ��

��ϰһ�¿�Ҫ��û�ú��Ϲ������ݽṹ������Ҫ�����࣡��ˢһ�����������������渴ϰ�����ţ���������`���ݽṹ��˫�`��ѧ��Ȳ����أ���û�н���ɶ���㷨���������໪��ʦ���Ǻܰ��ģ����ĺ�������~�������ֳ���`������Ϣ`��`�����`���ֲ�ͬ��Ҫ�󣬵紴���Ȼ�ǵ���Ҫ�󣬲���ɭ���������ݽṹ���㷨Ҫ�����Ϊ`Master`����Ҫ���ǿ���ѧ������

---

### Ŀ¼

1. **���Ա�**
    1.1 ˳���ʾ��ʵ��
    1.2 ��ʽ��ʾ��ʵ��
    1.2.1 `��������`
    1.2.2 `ѭ������`
    1.2.3 `˫������`

2. **ջ�Ͷ���**
    2.1 ջ
    2.2 ����

3. **����**
    3.1 �����˳���ʾ��ʵ��
    3.2 �����ѹ���洢
    3.2.1 `ϡ�����`

4. **��**
    4.1 ������
    4.2 ����������
    4.2.1 `��������ĵݹ�ʵ��`
    4.2.2 `��������ķǵݹ�ʵ��`
    4.2.3 `��α���`
    4.3 ����ɭ��
    4.3.1 `����ɭ�ֵĴ洢�ṹ`
    4.3.2 `����ɭ�ֵı���`
    4.4 �շ�����

5. **ͼ**
    5.1 ͼ�Ķ���
    5.2 ͼ�Ĵ洢�ṹ
    5.2.1 `�ڽӱ�`
    5.2.2 `ʮ������`
    5.3 ͼ�ı���
    5.3.1 `�����������`
    5.3.2 `�����������`
    5.4 ͼ����ͨ��
    5.4.1 `������`
    5.4.2 `��С������`
    5.5 ��������
    5.6 ���·��

6. **����**
    6.1 ��̬����
    6.2 ��̬����
    6.2.1 `����������`
    6.3 ��ϣ��

7. **�ڲ�����**
    7.1 ��������
    7.1.1 `ֱ�Ӳ�������`
    7.1.2 `ϣ������`
    7.2 ��������
    7.3 ѡ������
    7.4 �鲢����

---

### 1. ���Ա�

> ���Ա�`Linear_list`���������򵥵�һ�����ݽṹ������֮��һ�����Ա���n������Ԫ�ص��������С�

#### 1.1 ˳���ʾ��ʵ��

> ���Ա��˳���ʾ`Sequential List`ָ������һ���ַ�����Ĵ��浥Ԫ���δ������Ա������Ԫ�ء�`˳�򴢴�ṹ`��һ�������ȡ�Ĵ���ṹ��ͨ����`����`������˳�򴢴�ṹ��

C�����ö�̬�����һά���飬���������Ա�

~~~C
 #define LIST_INIT_SIZE 100 //���Ա���ռ�ĳ�ʼ������
 #define LISTINCREMENT 10 //���Ա�ķ�����
typedef int ElemType;
typedef struct {
    ElemType *elem;  // ����ռ�Ļ���ַ
    int length;  //��ǰ���Ա�ĳ���
    int listsize; //��ǰ����Ĵ�������
}SqList;
~~~

> �����й����Ա��֪ʶ�������
* [���Ա���13������������ʵ��](https://blog.csdn.net/bruthyu/article/details/52645510)

#### 1.2 ��ʽ��ʾ��ʵ��

> ��ʽ����ṹ`Linked List`��˳�򴢴�ṹ`Sequential List`�Ĳ�ͬ��˳�򴢴�ṹ���ص����߼���ϵ����������Ԫ��������λ����Ҳ��ͬ�����������ȡ����Ԫ�غܿ��ֱ�ۣ�ȱ������Ҫ�ƶ���������Ԫ�ء�����ʽ�ṹ������Ҫ���߼������ڵ�Ԫ��������λ�������ڣ��������ȡԪ�ز���Ҫ�ƶ�����Ԫ�أ����Ƕ��ڲ���Ԫ������������

##### 1.2.1 `��������`

> �������Ϊ��������`Singly Linked List`�����������Ƿ������ȡ�ṹ

һЩ���õķ�����

* ���Ԫ�أ�s��ָ�����ӽڵ��ָ�룩

    ~~~C
    s->next = p->next;
    p->next = s;
    ~~~

* ɾ��Ԫ�أ�a,b,c��������������3����㣬b�Ǵ�ɾ���Ľ�㣬����p��ָ��a����ָ�룩

    ~~~C
    p->next = p->next->next;
    ~~~

�ýṹ��ʵ�������㣺

~~~C
//���Ա�ĵ�������ṹ
struct Node {
    int data; //������
    struct Node *next; //ָ����
};
~~~

> ��������֪ʶ�������

* [C���Ե��������ʵ��](https://blog.csdn.net/21aspnet/article/details/160019)
* [����Ļ���ʹ��һ����������](https://blog.csdn.net/lan74__/article/details/53819849)
* [���ݽṹ������(linked-list)](https://blog.csdn.net/juanqinyang/article/details/51351619)

##### 1.2.2 `ѭ������`

1. ѭ���������ص㣺

    ���������һ������ָ�������ǽ�����־������ָ����������ĵ�һ����㣬�Ӷ�ʹ�����γ�һ�������͵�������ͬ��ѭ��������Ҳ�д�ͷ���Ͳ���ͷ������֡���ͷ����ѭ��������ʵ�ֲ����ɾ��������Ϊ���㣬�Ҹ������á�

2. ��������ѭ��������Ƚϣ�

    ѭ����������Դ�β��ͷ�����������ܴ�β��ͷ����˴�����������о��л��νṹ�ص�ʱ���ʺϲ���ѭ��������

3. ��ͷ����ѭ��������ʹ�ͷ���ĵ�����Ƚϣ�

    �� �ڳ�ʼ�������У������`head->next=NULL`��Ϊ`head->next = head`�����γ�һ���� 
    �� �����������У�ѭ���ж�����`p->next!=NULL`��`p->next->next!=NULL`�е�NULL�ĳ�ͷָ��`head`��

##### 1.2.3 `˫������`

1. ˫�������ص㣺
    ÿ���ڵ�����к��ָ������һ��ǰ��ָ����

2. ˫������ķ��ࣺ
    ˫�������У���ͷ���Ͳ���ͷ����˫���������Ǵ�ͷ����˫�������Ϊ���ã���Ҳ��ѭ���ͷ�ѭ��֮�֣�ѭ���ṹ��˫�������Ϊ���á�����������۵��Ǵ�ͷ����ѭ��˫����

3. ˫��ѭ��������Ľṹ�嶨��
    ~~~C
    //���Ա��˫��������ṹ
    struct DuLNode {
        Elemtype data; //������
        struct DuLNode *prior; //ǰ�����
        struct DuLNode *next;  //��̽��
    }DuLNode�� *DuLinklist;
    ~~~
    **��ע**��data��next��prior������data����������next��Ϊָ���̽���ָ����prior��Ϊָ��ǰ������ָ����

4. ˫��������ŵ㣺
    �ڵ����в��ҵ�ǰ���ĺ�̽�㲢�����ѣ�����ͨ����ǰ����nextָ����У���Ҫ���ҵ�ǰ����ǰ����㣬��Ҫ��ͷָ��head��ʼ���½��С�����һ��ҪƵ�����е�ǰ���ĺ�̽���ǰ������Ӧ����˵��ʹ��˫���������Ч��

5. ˫��ѭ�������ʵ��
    ��˫�������У�������ָ���ϵ����ָ��pָ��˫��ѭ�������еĵ�i��λ�ã���`p->next`ָ��i+1����㡣`p->next->prior`��ָ���i����㣬��`p->next->prior==p`;ͬ��`p->prior`ָ���i-1����㣬`p->prior->next`��ָ���i����㣬��`p->prior->next==p`;˫��ѭ�������ϵ�㷨���Է����㷨��ơ�

> ����ѭ�������˫�������֪ʶ�������
* [���ݽṹ����ѭ���������˫������](https://blog.csdn.net/xiaofei__/article/details/50984255)

* [���ݽṹ | ˫�������ʵ�ּ�ͼʾ](http://www.cnblogs.com/hughdong/p/6785391.html) -> *recommend*��

### 2. ջ�Ͷ���

�����ݽṹ�Ͽ���ջ�Ͷ���Ҳ�����Ա����������ǲ������޵����Ա���ˣ�������Ϊ�޶��Ե����ݽṹ��

#### 2.1 ջ

ջ`stack`���޶����ڱ�β���в����ɾ�������Ա�����ջ����β��Ϊ`ջ��`����Ӧ�أ���ͷ��Ϊ`ջ��`������Ԫ�صĿձ��Ϊ`��ջ`��ջ��һ�ֺ���ȳ���last in first out, LIFO���ṹ��

ջ�����ִ��淽ʽ��˳��ջ����ʽջ��

˳��ջ�Ķ��壺

~~~C
struct stack {
    SElemType *base;
    SElemType *top;
    int stacksize;
}SqStack;
~~~

**��ע**��`stacksize`ָ��ǰ��ʹ�õ����������`base`��ʾջ��ָ�룬`base`ΪNULLʱ������ջ�ṹ�����ڣ����ֵָ��ջ�ף���`top = base`����Ϊջ�յı�ǡ�����Ԫ�أ�top+1��ɾ��Ԫ�أ�top-1��

> ����ջ��֪ʶ�������
* [[���ݽṹ]C����ջ��ʵ��](https://www.cnblogs.com/racaljk/p/7822309.html)
* [���ݽṹͼ�Ľ���֮��ջ�ļ�鼰C++ģ��ʵ��](https://www.cnblogs.com/QG-whz/p/5170418.html) -> *recommend*��

#### 2.2 ����

��ջ�෴������`quene`��һ���Ƚ��ȳ���first in first out, FIFO�������Ա���ֻ�����ڱ��һ�˲��룬��һ��ɾ�����ڶ����У���������һ�˽�����β`rear`������ɾ����һ�˽�����ͷ`front`��

����Ҳ�����ִ��淽ʽ��˳����к������С�

�����е�ʵ�֣�

~~~C
struct QNode {
    QElemType data;
    struct QNode *next;
}QNode, *QuenePtr;
struct LinkQuene {
    QuenePtr front; //��ͷָ��
    QuenePtr rear; //��βָ��
}LinkQuene;
~~~

> �������֪ʶ�������
* [���ݽṹ-����(queue)](https://blog.csdn.net/juanqinyang/article/details/51354293) -> *recommend*��

### 3. ����

����͹������Կ��������Ա����չ��Ҳ����һ�����ݽṹ��

#### 3.1 �����˳���ʾ��ʵ��

��������һ�㲻�������ɾ����������˲���˳�򴢴�ṹ��ʾ���������Σ�

> ����ÿ������Ԫ��ռ$L$���洢��Ԫ�����ά����$A$����һԪ��$aij$�Ĵ洢λ�ÿ�����ʽȷ����$LOC(i, j) = LOC(0, 0) + (b_2*i + j)L$

�����˳��洢�ı�ʾ��

~~~C
 #define MAX_ARRAY_DIM 8
struct array {
    ElemType *base;
    int dim;
    int *bounds;
    int *constants;
}Array;
~~~

#### 3.2 �����ѹ���洢

> ѹ���洢ָ����Ϊ���ֵ��ͬ��Ԫֻ����һ���洢��Ԫ������Ԫ������ռ䡣

##### 3.2.1 ϡ�����

> ������Щ��Ԫ����ĿԶԶ���ڷ���Ԫ����Ŀ�����ҷ���Ԫ�صķֲ�û�й��ɵľ����Ϊϡ�����sparse����

* ���ڷ���Ԫ�طֲ�û���κι��ɣ������ڽ���ѹ���洢��ʱ����Ҫ�洢����Ԫ��ֵ��ͬʱ��Ҫ�洢����Ԫ���ھ����е�λ�ã�������Ԫ�����ڵ��кź��кţ�Ҳ�����ڴ洢ĳ��Ԫ�ر���$aij$��ֵ��ͬʱ������Ҫ�洢��Ԫ�����ڵ��к�$i$�������к�$j$�������͹�����һ����Ԫ��$(i,j,aij)$�����Ա�

```C
 #define MAXSIZE 12500
struct triple {
    int i, j; // �÷���Ԫ�����±�����±�
    ElemType e;
}Triple;
struct tsmatrix {
    Triple data[MAXSIZE + 1]; //����Ԫ��Ԫ��
    int mu, nu, tu; //����������������Ԫ����
}TSMatrix;
```

> ����ϡ������֪ʶ�������

* [ϡ�����](https://blog.csdn.net/sunhuaqiang1/article/details/51296803)

### 4. ��

> ��״ͼ��һ�����ݽṹ��������$n$��$n>=1$�������޽ڵ����һ�����в�ι�ϵ�ļ��ϡ�������������������Ϊ����������һ�õ��ҵ�����Ҳ����˵���Ǹ����ϣ���Ҷ���µġ����������µ��ص㣺
> * ÿ���ڵ�����������ӽڵ�
> * û�и��ڵ�Ľڵ��Ϊ���ڵ�
> * ÿһ���Ǹ��ڵ�����ֻ��һ�����ڵ㣨���˸��ڵ��⣬ÿ���ӽڵ���Է�Ϊ������ཻ��������

#### 4.1 ������

> ������`Binary Tree`����һ�����ͽṹ�������ص���ÿ�����������$2$�����������������в����ڶȴ���$2$�Ľ�㣩�����ң�������������������֮�֣������������ߵ���

�����������ʣ�

* �ڶ������ĵ�$i$����������$2^(i-1)$����㣨$i>=1$����
* ���Ϊ$k$�Ķ�����������$2^k - 1$����㣨$K>=1$����
* ���κ�һ�ö�����$T$��������ն˽����Ϊ$n_0$����Ϊ$2$�Ľ����Ϊ$n_2$����$n_0=n_2+1$��
* ����$n$��������ȫ�����������Ϊ|$\log_2 n$| + 1����|$\log_2 n$|��ʾ������$\log_2 n$�����������
* �����һ����$n$��������ȫ�������������Ϊ|$\log_2 n$| + 1���Ľ�㰴�����ţ��ӵ�$1$�㵽��|$\log_2 n$| + $1$�㣬ÿ������ң��������һ���$i$��$1 <= i <= n$�����У�
    1. ���$i = 1$������$i$�Ƕ������ĸ�����˫�ף����$i > 1$������˫��`PARENT(i)`�ǽ��|$i/2$|��
    2. ���$2i > n$������$i$�����ӣ������iΪҶ�ӽ�㣩������������`LCHILD(i)`�ǽ��$2$��
    3. ���$2i + 1 > n$������$i$���Һ��ӣ��������Һ���`RCHILD(i)`�ǽ��$2i+1$��

��������˳�򴢴�ṹ������������ȫ����������

```C
# define MAX_TREE_SIZE 100 // ���������������
typedef TElemType SqBiTree[MAX_TREE_SIZE]; // 0�ŵ�Ԫ�洢���ڵ�
SqBiTree bt;
```

����������ʽ�洢�ṹ��

```C++
struct BiTree {
    TElemType data; // ������
    struct BiTree *lchild, *rchild; // ���Һ���ָ��
}BiTree, *BiTree;
```

> ���������֪ʶ�������

* [�������ܽ�(һ)���������](https://www.cnblogs.com/yeqluofwupheng/p/7428935.html)

* [markdown�е���ѧ��ʽ��Ҫ](https://blog.csdn.net/wireless_com/article/details/70596155)

#### 4.2 ����������

> ��������һ�ַ����Խṹ������3��������Ԫ��ɣ����ڵ㣬�����������������涨������ң���3�ֻ�������������������������ͺ��������

##### 4.2.1 ��������ĵݹ�ʵ��

* �����������-��-�ң�

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

* �����������-��-�ң�

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

* �����������-��-����

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

##### 4.2.2 ��������ķǱ���ʵ��

* �����������-��-�ң�

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

* �����������-��-�ң�

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

* �����������-��-����

    ~~~C
    void postOrder(BinaryTreeNode* pRoot)  
    {  
        stack<BinaryTreeNode*> s;  
        BinaryTreeNode *cur;  
        BinaryTreeNode *pre=NULL;  
        s.push(pRoot);//�������ջ  
        while(!s.empty())  
        {  
            cur=s.top();  
            if((cur->left==NULL&&cur->right==NULL)||(pre!=NULL&&(pre==cur->left||pre==cur->right)))  
            {  
                //���Ӻ��Һ���ͬʱΪ�գ����ߵ�ǰ�������ӻ��Һ����Ѿ���������  
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

##### 4.2.3 ��α���

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

> �����������֪ʶ�������
* [�����������ֱ����ĵݹ�ͷǵݹ��ʵ��](https://blog.csdn.net/xiaominkong123/article/details/51567437) -> *recommend*��
* [���������ֱ�����ʽ�ĵݹ��ѭ��ʵ��](https://blog.csdn.net/lieacui/article/details/52453292)

#### 4.3 ����ɭ��

##### 4.3.1 ���Ĵ洢�ṹ

> ˫�ױ�ʾ��

~~~C
 #define MAX_TREE_SIZE 100
typedef struct PTNode { // ���ṹ
    TElemType data; // ������
    int parent; // ˫��λ����
}PTNode;
typedef struct { // ���ṹ
    PTNode nodes[MAX_TREE_SIZE]; 
    int r, n; // ����λ�úͽ����
}
~~~

ȱ�㣺����ĺ���ʱ��Ҫ���������ṹ��

>  ���ӱ�ʾ��

~~~C
typedef struct CTNode { // ���ӽ��
    int child; 
    sturct CTNode *next;
}*ChildPtr;
typedef struct {
    TElemType data;
    ChildPtr firstchild; // ��������ͷ���
}CTBox;
typedef struct {
    CTBox nodes[MAX_TREE_SIZE];
    int n, r; // ������ĸ���λ��
}
~~~

> �����ֵܱ�ʾ�������԰Ѹ��ӵ�����ɶ�������

~~~C
typedef struct CSNode {
    ElemType data;
    struct CSNode *firstchild, *nextsibling; // ��һ�����ӽ�����һ���ֵܽ��
}
~~~

##### 4.3.2 ����ɭ�ֵı���

������������Ϊ���Ĵ���ṹʱ�������ȸ������ͺ�������ɽ��ö�������������������ʵ�֡�

ɭ��һ��ֻ˵���������������Ͷ���������������������ͬ��

> ��������ɭ�ֵ�֪ʶ�������
* [���Ĵ洢�ṹ�ʹ���ʵ��](https://blog.csdn.net/qq_36016407/article/details/55272598)
* [����ɭ�ֵı���](https://blog.csdn.net/wangzi11322/article/details/45391157)

#### 4.4 �շ�����

> �շ�����`Huffman`���ֳ����Ŷ���������һ���Ȩ·��������̵���������·������Ϊ��������Ҷ�ӽ��Ĵ�Ȩ·������֮�͡�ͨ������$WPL=\sum_{k=0}^{n}\omega_k\iota_k$ ��

������n��Ȩֵ������һ����n��Ҷ�ӽ��Ķ�������ÿ��Ҷ�ӽ���ȨΪ$\omega_i$�������д�Ȩ·������$WPL$��С�Ķ�������Ϊ**�շ�����**��

~~~C
typedef struct {
    unsigned int weight; // Ȩ��
    unsigned int parent, lchild, rchild; 
}HTNode, *HuffmanTree; // ��̬��������洢�շ�����
~~~

> ����շ�������֪ʶ�������
* [��������](https://blog.csdn.net/wo16fafafa/article/details/52420007)
* [�������ݽṹ-������-�շ������Ľ���](https://www.cnblogs.com/nathaneko/p/6497982.html)

### 5. ͼ

> **ͼ**`Graph`��һ�ֽ����Ա������Ϊ���ӵ����ݽṹ����**���Ա�**�У�����Ԫ��֮��������Թ�ϵ��ÿ������Ԫ��ֻ��һ��ֱ��ǰ����һ��ֱ�Ӻ�̣���**��**�νṹ�У�����Ԫ��֮���������ԵĲ�ι�ϵ������ÿһ���ϵ�����Ԫ�ؿ��ܺ���һ��Ķ��Ԫ�أ������ӽ�㣩��أ���ֻ����һ���һ��Ԫ�أ���˫�׽�㣩��ء�����**ͼ**�νṹ�У����֮��Ĺ�ϵ������ġ�

#### 5.1 ͼ�Ķ���

��ͼ�У�����Ԫ�س�Ϊ**����**��$V$�Ƕ��������ǿռ��ϣ�$VR$����������֮��Ĺ�ϵ���ϡ�

* ��$<v,w>\epsilon VR$,��$<v,w>$��ʾ��$v$��$w$��һ��**��**`Arc`���ҳ�$v$Ϊ**��β**`Tail`or**��ʼ��**��$w$Ϊ**��ͷ**`Head`or**�ն˵�**����ʱ��ͼ��Ϊ**����ͼ**`Digraph`��

$$G_1 = (V_1,{A_1})$$

* ��$<v,w>\epsilon VR$������$<w,v>\epsilon VR$����$VR$�ǶԳƵģ����������$(v,w)$��������������ԣ���ʾ$v$��$w$֮���һ��**��**`Edge`����ʱ��ͼ��Ϊ**����ͼ**`Undigraph`��

$$G_2 = (V_2,{E_2})$$

#### 5.2 ͼ�Ĵ洢�ṹ

> ͼ�Ľṹ��Ϊ���ӣ����õĴ洢�ṹ��**�ڽӱ�**��**ʮ������**��

##### 5.2.1 �ڽӱ�

> **�ڽӱ�**��ͼ��һ����ʽ�洢�ṹ��

~~~C
 #define MAX_VERTEX_NUM 20
typedef struct ArcNode {
    int adjvex; // �û���ָ��Ķ����λ��
    struct ArcNode *nextarc; // ָ����һ������ָ��
    InfoType *info; // �û������Ϣ��ָ��
}ArcNode;
typedef struct VNode {
    VertexType data; // ������Ϣ
    ArcNode *firstarc; //ָ���һ�������ö���Ļ���ָ��
}VNode, AdjList[MAX_VERTEX_NUM];
typedef struct {
    AdjList vertices;
    int vexnum, arcnum; //ͼ�ĵ�ǰ�������ͻ���
    int kind; // ͼ�������־
}ALGraph;
~~~

> ����ͼ��֪ʶ�������
* [���ݽṹ(16)--ͼ�Ĵ洢��ʵ��](https://blog.csdn.net/u010366748/article/details/50790324)
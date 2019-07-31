---
title: "二叉查找树（Binary Search Tree）"
# permalink: /tips/data-structure/binary-search-tree
last_modified_at: 2019-07-27
toc: true
toc_label: 目录
category: 
  - tips
tag:
  - data-structure
excerpt_separator: <!--more-->
---

二叉查找树是指具有如下性质的二叉树：

- 左子树上的所有节点的值都小于根节点；
- 右子树上的所有节点的值都大于根节点；
- 左右子树均为二叉搜索树。

<!--more-->

{% include image.html url="/assets/images/binary-search-tree.png" description="Binary Search Tree (Source: https://visualgo.net)" %}

## C#代码

{% highlight csharp %}
//树节点的定义
public class TreeNode {
  public int val;
  public TreeNode left;
  public TreeNode right;
  public TreeNode(int x) { val = x; }
}

//查找算法
bool SearchBST(TreeNode node, int target) {
    if (node == null) { // 查找不成功
        return false;
    } else if (target == node.val) { // 查找成功
        return true;
    } else if (target < node.val) { // 在左子樹中繼續查找
        return SearchBST(node.left, target);
    } else { // 在右子樹中繼續查找
        return SearchBST(node.right, target);
    }
}

//插入算法
TreeNode InsertBST(TreeNode node, int target) {
    if (node == null) {
        return new TreeNode(target);
    } 
    if (node.val > target){
        node = InsertBST(node.left, target);  // 將 e 插入左子樹
    } else {
        node = InsertBST(node.right, target);  // 將 e 插入右子樹
    }
    return node;
}


Status DeleteBST(BiTree *T, KeyType key) {
    // 若二叉查找树T中存在关键字等于key的数据元素时，则删除该数据元素，并返回
    // TRUE；否则返回FALSE
    if (!T)
        return false; //不存在关键字等于key的数据元素
    else {
        if (key == T->data.key)   //   找到关键字等于key的数据元素
            return Delete(T);
        else if (key < T->data.key)
            return DeleteBST(T->lchild, key);
        else
            return DeleteBST(T->rchild, key);
    }
}

Status Delete(BiTree *&p) {
    // 该节点为叶子节点，直接删除
    BiTree *q, *s;
    if (!p->rchild && !p->lchild) {
        delete p;
        p = NULL;  // Status Delete(BiTree *&p) 要加&才能使P指向NULL
    } else if (!p->rchild) { // 右子树空则只需重接它的左子树
        q = p->lchild;
        /*
        p->data = p->lchild->data;
        p->lchild=p->lchild->lchild;
        p->rchild=p->lchild->rchild;
        */
        p->data = q->data;
        p->lchild = q->lchild;
        p->rchild = q->rchild;
        delete q;
    } else if (!p->lchild) { // 左子树空只需重接它的右子树
        q = p->rchild;
        /*
        p->data = p->rchild->data;
        p->lchild=p->rchild->lchild;
        p->rchild=p->rchild->rchild;
        */
        p->data = q->data;
        p->lchild = q->lchild;
        p->rchild = q->rchild;
        delete q;
    } else { // 左右子树均不空
        q = p;
        s = p->lchild;
        while (s->rchild) {
            q = s;
            s = s->rchild;
        } // 转左，然后向右到尽头
        p->data = s->data;  // s指向被删结点的“前驱”
        if (q != p)
            q->rchild = s->lchild;  // 重接*q的右子树
        else
            q->lchild = s->lchild;  // 重接*q的左子树
        delete s;
    }
    return true;
}
//

{% endhighlight %}

## 时间与空间复杂度

二叉查找树相比于其他数据结构的优势在于查找、插入的时间复杂度较低，均为O(logN)。

## 其它特性

{% include related-problems.md %}

{% include data-structure-footer.md %}
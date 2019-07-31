---
title: "插入排序（Insertion Sort）"
# permalink: /tips/algorithms/sorting/insertion-sort
last_modified_at: 2019-07-25
toc: true
toc_label: 目录
category: 
  - tips
tag:
  - algorithm
  - algorithm-sorting
---

插入排序是我们在整理扑克牌手牌的时候不自觉会用到的一种排序方法。基本原理是构造一个一开始为空的有序序列，然后不停地在未排序的序列中抓取一个元素放入有序序列中，直至未排序序列为空。在将新元素放入有序序列的时候，对已经在序列里的元素由后向前依次进行扫描，找出适合当前元素插入的位置，以使每次插入后序列依然保持有序。

{% include image.html url="/assets/images/insertion-sort.gif" description="Insertion Sort (Source: https://visualgo.net)" %}

## C#代码

{% highlight csharp %}
void InsertSort<T>(T[] arr) where T : IComparable<T>{
    int len = array.length;
    for(int i = 1; i < len; i++) {
        int temp = arr[i];
        for(int j = i - 1; j >= 0; j--) {
            if(arr[j].CompareTo(temp) > 0) {
                arr[j + 1] = arr[j];
                arr[j] = temp;
            }
            else {
                break;
            }
        }
    }
}
{% endhighlight %}

## 时间与空间复杂度

对插入排序而言最差的情况是一开始的数据出现反向排序，从而使每次插入新元素时都要扫描所有的已排序元素，出现扫描元素数量最大化。在这种情况下我们需要比较

1 + 2 + ... + N-1

~N^2/2次来完成整个排序，因此时间复杂度为O(N^2).

## 其它特性

一般在使用数组实现插入排序的时候，为了节省空间，通常会采用in-place排序（即不使用额外的数组存储排好后的序列），因而在从后向前扫描过程中，需要反复把已排序元素逐步向后挪位，为最新元素提供插入空间。因此会出现大量的数据交换的操作。

相对而言，如果使用链表(linked list)作为数据存储的结构，由于链表在数据插入的时候不需要额外的数据换位，因此效率而言会更加地高。

相较于选择排序，插入排序的效率会受到输入的序列起始状态的影响。如果输入的序列是一条已经差不多是正序(partially sorted)的数列，插入排序会有很高的效率，因为插入的时候不需要扫描太多的元素，很可能只需要插入的已排序序列的尾端。

插入排序是一种稳定的排序。

{% include related-problems.md %}

{% include algorithm-footer.md %}
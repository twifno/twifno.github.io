---
title: "冒泡排序（Bubble Sort）"
# permalink: /tips/algorithms/sorting/bubble-sort
toc: true
toc_label: 目录
category: 
  - tips
tag:
  - algorithm
  - algorithm-sorting
---

冒泡排序是一种简单的排序算法。他的名字来源于在运算过程中，未完成排序的较小（较大）元素会随着它运行慢慢往排序好的序列浮，就像水中的气泡一样。冒泡排序的基本原理是重复地走访尚未完成排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来。每一轮走访，未排序中的最小（最大）元素就会被交换到最末端。重复走访数列的工作直到没有再需要交换，测试整个序列就已经完成排序。

冒泡排序算法的运作如下：

1. 比较相邻的元素。如果第一个比第二个大，就交换他们两个。
2. 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。这步做完后，最后的元素会是最大的数，这个元素就已经完成排序。
3. 针对所有未完成排序的元素重复以上的步骤。
4. 持续每次对越来越少的未排序元素重复上面的步骤，直到没有任何一对数字需要交换。

{% include image.html url="/assets/images/bubble-sort.gif" description="Bubble Sort (Source: https://visualgo.net)" %}

## C#代码

{% highlight csharp %}
void BubbleSort<T>(T[] arr) where T : IComparable<T>{
    int len = arr.Length;
    bool swapped;
    for (int i = 0; i < len; i++){
        swapped = false;
        for (int j = 0; j < len - 1 - i; j++){
            if (arr[j].CompareTo(arr[j + 1]) > 0){
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                if (!swapped){
                    swapped = true;
                }
            }
        }
        if (!swapped) return;
    }
}
{% endhighlight %}

## 正确性分析

冒泡排序的终止条件是整个序列不再需要任何交换，这说明所有元素之间没有inversion，这符合序列已经被排序的定义。

## 时间与空间复杂度

在最坏的情况下，冒泡排序的每一轮都要对未排序的相邻的每对元素进行比较和交换，因此比较和交换的次数为

(N-1) + (N-2) + ... 1

~N^2/2，因此冒泡排序算法的时间复杂度为O(N^2).

## 其它特性

- 在没有进行额外优化的情况下，冒泡排序的复杂度对输入数据的情况不敏感，即不管什么情况，算法都需要N^2/2的比较来完成排序（交换的数量会有变化）。
- 冒泡排序是一种稳定的排序算法。
- 相关优化可参见鸡尾酒排序。

{% include related-problems.md %}

{% include algorithm-footer.md %}
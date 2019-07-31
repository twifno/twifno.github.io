---
title: "选择排序（Selection Sort）"
# permalink: /tips/algorithms/sorting/selection-sort
last_modified_at: 2019-07-25
toc: true
toc_label: 目录
category: 
  - tips
tag:
  - algorithm
  - algorithm-sorting
---

选择排序是一种最简单直观的排序算法。中心思想是在未排序的序列中，找出最小（最大）的元素，将其放在序列的最前端，并归为已经排序的序列，然后再在剩下的未排序序列中继续寻在最小（最大）的元素，放到最前端。以此类推，直到处理完所有的未排序元素。

{% include image.html url="/assets/images/selection-sort.gif" description="Selection Sort (Source: https://visualgo.net)" %}

## C#代码

{% highlight csharp %}
void SelectionSort<T>(T[] arr) where T : IComparable<T>{
  int min, len = arr.Length;
  T temp;
  for (int i = 0; i < len - 1; i++) {
    min = i;
    for (int j = i + 1; j < len; j++) {
      if (arr[min].CompareTo(arr[j]) > 0) min = j;
    }
    temp = arr[min];
    arr[min] = arr[i];
    arr[i] = temp;
  }
}
{% endhighlight %}

## 时间与空间复杂度

假设未排序序列有N个元素，因为我们每次都从未排序的序列里拿出一个最小（最大）的元素，直到所以元素都被拿光，所以我们一个要进行N轮的拿取。每一轮的拿取，我们需要比较所有未排序的元素以找到其中的最小（最大），所以每轮比较次数为剩下的为排序序列的总数减一。因此总共的比较次数为

(N-1) + (N-2) ... + 1

~N^2/2，相对而言，每轮拿取最多进行一次元素的交换（将最小(最大）的元素移到最前端)，最多只会产生N次交换，因此相对与元素比较的次数，元素交换并不会影响复杂度。

所以，选择排序的时间复杂度为O(N^2)。

## 其它特性

- 选择排序的时间复杂度不会受到数据本身的影响，不管什么样的数据，只要数据的大小的N，就大概需要N^2/2次元素比较，即使是元素一开始已经排好序。
- 选择排序是一种不稳定算法。稳定性指的是当两个元素大小一致是排序后的相对位置与排序前相同。选择排序每论的元素交换都有可能破坏相同大小的元素间的前后顺序。
- 选择排序只需要理论上最少的次数来进行数据交换。

{% include related-problems.md %}

{% include algorithm-footer.md %}
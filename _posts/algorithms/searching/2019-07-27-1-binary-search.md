---
title: "二分查找（Binary Search）"
# permalink: /tips/algorithms/searching/binary-search
last_modified_at: 2019-07-27
toc: true
toc_label: 目录
category: 
  - tips
tag:
  - algorithm
  - algorithm-searching
---

二分搜索是一种在有序数组中查找某一特定元素的搜索算法。搜索过程从数组的中间元素开始，如果中间元素正好是要查找的元素，则搜索过程结束；如果某一特定元素大于或者小于中间元素，则在数组大于或小于中间元素的那一半中查找，而且跟开始一样从中间元素开始比较。如果在某一步骤数组为空，则代表找不到。这种搜索算法每一次比较都使搜索范围缩小一半。

## C#代码

{% highlight csharp %}
int BinarySearch(int[] arr, int x) { 
    int l = 0, r = arr.Length - 1;
    while (l <= r) { 
        int m = l + (r - l) / 2;
  
        // Check if x is present at mid 
        if (arr[m] == x) return m;

        // If x greater, ignore left half 
        if (arr[m] < x) l = m + 1;
        // If x is smaller, ignore right half 
        else r = m - 1; 
    }

    // if we reach here, then element was
    // not present
    return -1; 
}
{% endhighlight %}

## 时间与空间复杂度

二分搜索的时间复杂度为O(logN)，因为每一轮的搜索都可以将搜索范围减少为当前的一半。

## 其它特性

二分搜索算法亦可以用来计算一个赋值的排名、前趋（下一个最小元素）、后继（下一个最大元素）以及最近邻。搜索两个值之间的元素数目的范围查询可以借由两个排名查询来运行。

{% include related-problems.md %}

{% include algorithm-footer.md %}

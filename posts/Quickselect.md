---
title: Quickselect
date: 2024-05-25 16:00:35
categories: code💻
hide: false
index_img: https://nuyoahwjl.github.io/img/Quickselect.png
excerpt: 快速选择算法
---

为了求整型数组的中位数，并且效率要优于O(n^2)，同时不对全部数据进行排序，可以使用一种称为 **选择算法**（Selection Algorithm）的方法。最著名的选择算法是 **快速选择算法**（Quickselect），它的平均时间复杂度是O(n)。

快速选择算法基于快速排序的分治思想。快速选择每次可以选定一个枢轴（pivot），然后通过一次划分（partition）将数组分成两部分，其中一部分所有元素都小于等于枢轴，另一部分所有元素都大于等于枢轴。根据枢轴的位置，可以确定中位数所在的部分，并递归进行选择。

下面是实现快速选择算法来求中位数的C语言代码：

```c
#include <stdio.h>
#include <stdlib.h>

// 辅助函数：交换两个元素
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// 分区函数：选择最后一个元素作为枢轴，返回枢轴的最终位置
int partition(int a[], int low, int high) {
    int pivot = a[high];
    int i = low - 1;
    for (int j = low; j < high; j++) {
        if (a[j] <= pivot) {
            i++;
            swap(&a[i], &a[j]);
        }
    }
    swap(&a[i + 1], &a[high]);
    return i + 1;
}

// 快速选择函数：在a[low...high]范围内寻找第k小的元素
int quickSelect(int a[], int low, int high, int k) {
    if (low == high) {
        return a[low];
    }

    int pivotIndex = partition(a, low, high);

    // 计算当前枢轴是第几个元素
    int numElementsInLowPartition = pivotIndex - low + 1;

    if (numElementsInLowPartition == k) {
        return a[pivotIndex];
    } else if (k < numElementsInLowPartition) {
        return quickSelect(a, low, pivotIndex - 1, k);
    } else {
        return quickSelect(a, pivotIndex + 1, high, k - numElementsInLowPartition);
    }
}

// 主函数：求数组的中位数
int MidValue(int a[], int n) {
    if (n % 2 == 1) {
        // 数组长度为奇数，中位数为第(n/2 + 1)小的元素
        return quickSelect(a, 0, n - 1, n / 2 + 1);
    } else {
        // 数组长度为偶数，中位数为第(n/2)和第(n/2 + 1)小的元素的平均值
        int mid1 = quickSelect(a, 0, n - 1, n / 2);
        int mid2 = quickSelect(a, 0, n - 1, n / 2 + 1);
        return (mid1 + mid2) / 2;
    }
}

int main() {
    int a[] = {7, 10, 4, 3, 20, 15};
    int n = sizeof(a) / sizeof(a[0]);

    int median = MidValue(a, n);
    printf("数组的中位数是: %d\n", median);

    return 0;
}
```

### 代码解释

1. **辅助函数** `swap`：交换两个整数的值。
2. **分区函数** `partition`：实现快速排序中的分区步骤，选择最后一个元素作为枢轴。
3. **快速选择函数** `quickSelect`：在数组的指定范围内寻找第k小的元素。根据分区结果递归查找目标元素。
4. **主函数** `MidValue`：根据数组长度的奇偶性，调用`quickSelect`寻找中位数。如果长度为奇数，直接返回第`n/2 + 1`小的元素；如果为偶数，返回第`n/2`和第`n/2 + 1`小的元素的平均值。

### 注意事项

- 快速选择算法在最坏情况下时间复杂度是O(n^2)，但其平均时间复杂度为O(n)，在绝大多数情况下效率较高。
- 该实现通过数组中的元素范围来递归查找目标中位数，而不需要对整个数组进行排序，从而满足题目的效率要求。

此实现有效利用了快速排序的思想，确保了在大多数情况下的高效性，同时避免了全面排序带来的额外开销。

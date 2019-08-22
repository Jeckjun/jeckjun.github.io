---
title: 2019.8.22-python3-基本算法
tags: Python
categories: Python
---

* TOC
{:toc}

2019.8.22的python3基础算法学习

# 笔记内容
~~~Python
# python基本算法
# 二分法查找，先折半，在值得折半范围内再折半查找，一直循环，直到查找完成
# 递归二分法查找,匹配列表中有没匹配元素，递归层数不适合超过1000层，效率低
import random
# max_num = 10 ** 3
# l = []
# for i in range(max_num):
#     l.append(i)
# def two_find(num, num_list):      # 二分法查找，成功返回True，否则返回Flase
#     if len(num_list) == 0:
#         return False
#     if num == num_list[len(num_list) // 2]:
#         return True
#     if num > num_list[len(num_list) // 2]:
#         num_list = num_list[len(num_list) // 2+1:]
#         return two_find(num, num_list)
#     else:
#         num_list = num_list[:len(num_list) // 2]
#         return two_find(num, num_list)

# def bin_search(num, l):   # 优化二分法查找，成功返回True，否则返回Flase
#     if len(l) == 0:
#         return False
#     mid = len(l) // 2
#     if l[mid] == num:
#         return True
#     elif l[mid] < num:
#         # bin_search(101,l[1:])
#         return bin_search(num, l[mid + 1:])
#     else:
#         return bin_search(num, l[:mid])

# def binary_search(num, l, start, end):  # 二分法查找，成功返回索引值，否则返回-1
#     if start <= end:
#         mid = (start + end) // 2        # 算出中间值
#         if l[mid] == num:
#             return mid
#         elif l[mid] < num:
#             # bin_search(101,l[1:])
#             start = mid + 1
#             return binary_search(num, l, start, end)
#         else:
#             end = mid - 1
#             return binary_search(num, l, start, end)
#     else:
#         return -1
#
# print(two_find(5, l))
# # print(bin_search(9,l))
# print(binary_search(2,l,0,len(l)-1))

# 普通二分法查找

# def binarySearch(arr, key):
#     low = 0
#     high = len(arr) - 1
#     while low <= high:
#         mid = (low + high) // 2
#         if key == arr[mid]:
#             return mid
#         elif key > arr[mid]:
#             low = mid + 1
#         else:
#             high = mid - 1
#     return -1

# 普通查找
# def generalSearch(arr, key):
#     for i in arr:
#         if i == key:
#             return i
#     return -1
#
# print(generalSearch(l, 500))
# print(binarySearch(l, 550))

# 计时函数
# import time
# def timeCount1(arr, key):
#     start = time.perf_counter()
#     generalSearch(arr, key)
#     end = time.perf_counter()
#     result = end - start
#     print("普通时间：{0:f}".format(result))
#
# def timeCount2(arr, key):
#     start = time.perf_counter()
#     binarySearch(arr, key)
#     end = time.perf_counter()
#     result = end - start
#     print("二分时间：{0:f}".format(result))
#
# timeCount1(l, max_num)
# timeCount2(l, max_num)

# 冒泡排序算法，大的元素向后面移，一直移到最后乱序的最后一个位置
l = [5, 4, 3, 8, 6, 8, 7, 10, 9]
def bubble_sort(l):
    for i in range(len(l)):     # 排序一趟
        is_sort = False     # 判断是否排好序的标识
        j = 0
        while j < len(l) - 1 - i:     # 每次从第一个开始，到排好序的前一个结束
            if l[j] > l[j+1]:     # 把最大的往后移
                temp = l[j]
                l[j] = l[j+1]
                l[j+1] = temp
                is_sort = True       # 没有交换说明是有顺序的，停止排序
            j += 1
        if not is_sort:
            break
    return l

# 改进的定向冒泡算法
def bubble_sort_V2(l):
    left = 0        # 最左边开始
    right = len(l) - 1      # 最右边开始
    while left < right:     # 左边小于右边结束循环
        for i in range(right):  # 从左向右冒泡，大的移至最后
            if l[i] > l[i+1]:
                temp = l[i]
                l[i] = l[i+1]
                l[i+1] = temp
            right -= 1      # 每排一次，右边范围减一
        j = right
        while j > left:     # 从右向左冒泡，小的移至最左
            if l[j] < l[j-1]:
                temp = l[j]
                l[j] = l[j-1]
                l[j-1] = temp
            left += 1       # 每排一次，范围减一
            j -= 1
    return l
# print(bubble_sort(l))
# print(bubble_sort_V2(l))

# 选择排序，从第一个元素开始，和后面每个元素比较，最小的和前面索引互换，从排好序的后面一直循环，至到全部换完，排序完成。
def select_sort(l):
    for i in range(len(l)):
        min_index = i       # 记录最小索引的变量
        j = i               # 从排好序的后一个元素开始
        while j < len(l):
            if l[min_index] > l[j]:     # 找最小的数
                min_index = j       # 把最小元素的索引保存
            j += 1
        # l[min_index], l[i] = l[i], l[min_index]   # python特有的换值语法
        temp = l[i]
        l[i] = l[min_index]
        l[min_index] = temp
    return l

# print(select_sort(l))

# 插入排序，第一个元素可以理解为排好序的，从第二个元素开始和前面的排好序的元素比较，插入比它小的元素后面，一直循环，至到排序完成
def insertion_sort(l):
    current = 0     # 定义中间变量
    for i in range(len(l)):
        pre_index = i - 1
        current = l[i]  # 存储当前插入元素
        while pre_index >= 0 and current < l[pre_index]:    # 向前比较元素，一直比较到合适位置
            l[pre_index+1] = l[pre_index]   # 比较元素后移一位
            pre_index -= 1
        l[pre_index+1] = current    # 插入元素到合适位置
    return l

# print(insertion_sort(l))

# for range倒序
# for i in range(9,-1,-1):
#     print(i)
# for i in range(10)[::-1]:
#     print(i)

# 归并排序
# 1）把长度为 n 的输入序列分成两个长度为 n / 2 的子序列
# # 2）对这两个子序列分别采用归并排序
# # 3）将两个排序好的子序列合并成一个最终的排序序列
def merge_sort(l):
    if len(l) < 2:
        return l    # 递归退出条件
    else:
        mid = len(l) // 2   # 切割成两部分
        left = merge_sort(l[:mid])      # 左边部分
        right = merge_sort(l[mid:])     # 右边部分
        i, j = 0, 0
        temp = []   # 接收新的list
        while i < len(left) or j < len(right):  # 两边循环
            if(i < len(left)) and (j < len(right)): # 正常情况，小的放前面
                if left[i] < right[j]:
                    temp.append(left[i])
                    i += 1
                else:
                    temp.append(right[j])
                    j += 1
            elif i >= len(left):    # 右边长一个，加在后面
                temp.append(right[j])
                j += 1
            else:
                temp.append(left[i])
                i += 1
        return temp

print(merge_sort(l))
~~~

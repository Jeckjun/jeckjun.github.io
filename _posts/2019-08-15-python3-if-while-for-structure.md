---
title: 2019.8.15-python3-if-while-for-算法笔记
tags: Python
categories: Python
---

* TOC
{:toc}

2019.8.15的python3笔记，if、while、for和算法练习

# 笔记内容
~~~Python

# print(1<<2)
# print(2<<2)
# print(3<<2)
# print(4<<4)
# print(8>>2)
# print(64>>4)
'''
1 0 1 0
1 0 1 1
--------
1 0 1 1
'''
# print(10 | 11)
'''
1 0 1 0
1 0 1 1
--------
0 0 0 1
'''
# print(10 ^ 11)
"""
1 0 1 0
1 0 1 1
--------
1 0 1 0
"""
# print(10 & 11)

# if选择结构
# is_not = True
# price = float(input('goods price：'))
# if is_not == True:        # 在内部完成想要的结果
#     print("member打8折：{0:0.2f}".format(price*0.8))
# if is_not == False:
#     print('nonmember不打折：{0:0.2f}'.format(price))
# else:
#     print('nonmember不打折：{0:0.2f}'.format(price))
# if is_not:      # 在内部只改变需要变量的值
#     price = price * 0.8
# print('price：{0:0.2f}'.format(price))

# 练习
# price = float(input('花费金额：'))
# if price > 400:
#     price = price * 0.85
#     print("折后金额：{0:0.2f}".format(price))
# elif 0 <= price <= 400:
#     price = price * 0.95
#     print("折后金额：{0:0.2f}".format(price))
# else:
#     print("输入金额非法")

# 课堂练习
# while True:
#     score = int(input("输入分数："))
#     if score < 0 or score >100:
#         break
#     elif score >= 90:
#         print("A")
#     elif 80 <= score <=89:
#         print("B")
#     elif 70 <= score <= 79:
#         print("C")
#     elif 60 <= score <=69:
#         print("D")
#     else:
#         print("F")

# other method
# flog = True
# while flog:
#     score = int(input("输入分数："))
#     if score < 0 or score >100:
#         flog = False
#     elif score >= 90:
#         print("A")
#     elif 80 <= score <=89:
#         print("B")
#     elif 70 <= score <= 79:
#         print("C")
#     elif 60 <= score <=69:
#         print("D")
#     else:
#         print("F")

# practice
# count = 0
# sumGrade = 0
# while count < 5:
#     grade = int(input("请输入第{0:d}课成绩：".format(count+1)))
#     if grade < 0 or grade > 100:
#         print("成绩输入无效，请重新输入")
#         continue
#     sumGrade += grade
#     count += 1
# print("总成绩为：{0:d}\n平均成绩为：{1:0.2f}".format(sumGrade,sumGrade / count))

# 或者

# if price < 0:
#     print("输入金额非法")
# else:
#     if price > 400:
#         price = price * 0.85
#     else:
#         price = price * 0.95
#     print("折后金额：{0:0.2f}".format(price))


# while循环
# i = 0
# sum1 = 0
# while i < 10:
#     sum1 += i
#     i += 1
# print(sum1)

# for循环
# sum2 = 0
# for i in range(1,10,2):
#     sum2 += i
#     print(i)
# print(sum2)

# 随机排序
# import random
# lists = ["张三", "李四", "王二", "麻子", "皮特", "鲍勃", "苏珊", "阿三"]
# newList = []
# for i in range(1, len(lists)+1):
#     name = random.choice(lists)
#     newList.append(name)
#     lists.remove(name)
# print(newList)


# 九九乘法表
# for i in range(1, 10):
#     for j in range(1, i+1):
#         print("{0:d}x{1:d}={2:d}".format(j, i, i*j), end="\t")
#     print()

# 使用while
# i = 1
# while i < 10:
#     j = 1
#     while j < i+1:
#         print("{0:d}x{1:d}={2:d}".format(j, i, i * j), end="\t")
#         j += 1
#     i += 1
#     print()

# 反的九九乘法表
# for i in range(1, 10):
#     for j in range(1, 11-i):
#         print("{0:d}x{1:d}={2:d}".format(i, 10-j, i*j), end="\t")
#     print

# 使用while
# i = 1
# while i < 10:
#     j = 1
#     while j < 11-i:
#         print("{0:d}x{1:d}={2:d}".format(i, 10-j, i * j), end="\t")
#         j += 1
#     i += 1
#     print()

# n = 1
# while n <= 9:
#     j = 1
#     content = ""
#     while j <= 10-n:
#         content += ("{0:2d} x{1:2d}={2:2d} |".format(n, 10-j, n * j))
#         j += 1
#     print(content)
#     n += 1

# 或者用-=
# n = 1
# while n <= 9:
#     j = 9
#     content = ""
#     while j >= n:
#         content += ("{0:2d} x{1:2d}={2:2d} |".format(n, j, n * j))
#         j -= 1
#     print(content)
#     n += 1

"""
   1
  2 3
 4 5 6
7 8 9 0
"""
# n = 4
# i = 1
# space_num = n - 1
# while space_num >= 0:
#     string = (" "*space_num)  # 打印前面的空格
#     j = 0
#     while n - space_num > j:    # 循环行数
#         string += str(i % 10) + " "     # 拼接
#         i += 1
#         j += 1
#     print(string)
#     space_num -= 1

# n = 5
# i = 1
# while n >= i:
#     print("*"*n)
#     n -= 1

"""
     *
    **
   ***
  ****
 *****
******
"""
# n = 6
# start_num = 1
# j = 0
# while j < n:
#     space_num = n - start_num
#     print(" "*space_num+"*"*start_num)
#     start_num += 1
#     j += 1

"""
******
 *****
  ****
   ***
    **
     *
"""
# n = 6       # 行数
# start_num = 6       # 开始*的个数
# j = 0
# while j < n:
#     space_num = n - start_num   # 计算每行的空格数
#     print(" "*space_num+"*"*start_num)  # 打印每行的内容
#     start_num -= 1
#     j += 1

# 简化版
# line = 6
# j = 0
# while j < line:        # 循环行数，每行的空格数等于j
#     print(" "*j + "*"*(line-j))     # 行数空格*的规律：j = 空格数，line - j = *数
#     j += 1

"""
   *
  ***
 *****
*******
 *****
  ***
   *
"""
# 必须是基数
# def starArrange(line):
#     if line % 2 == 0:
#         raise Exception('必须是奇数')
#     else:
#         star_num = 1
#         j = 0
#         space_num = line // 2   # 第一排空格的规律
#         while j < line:
#             print(" "*space_num + "*"*star_num)     # 打印结果
#             if j < line // 2:       # 程序运行前半部分
#                 star_num += 2       # 星星数等差2增加
#                 space_num -= 1      # 空格等差1减少
#             else:                   # 程序运行后半部分
#                 star_num -= 2       # 星星等差2减少
#                 space_num += 1      # 星星等差1增加
#             j += 1
# starArrange(4)
# 老师的方法
# n = 7
# if n % 2 == 0:
#     raise Exception('必须是奇数')
# mid = n // 2 + 1    # 找到中间排
# i = 1
# while n > 0:        # 循环n次:1,2,3
#     space_num = abs(mid - i)        # 算出每次循环的空格数:3,2,1
#     base_num = mid - space_num      # 每列中间一半的**数:1,2,3
#     star_num = base_num * 2 - 1     # 计算**数:1,3,5
#     print(" " * space_num + "*" * star_num)     # 打印结果
#     i += 1
#     n -= 1

# 绝对值函数
# print(abs(-8))
"""
   *
  * *
 *   *
*     *
 *   *
  * *
   *
"""
n = 7
if n % 2 == 0:
    raise Exception('必须是奇数')
mid = n // 2 + 1    # 找到中间排
i = 1
while n > 0:        # 循环n次:1,2,3
    space_num = abs(mid - i)        # 算出每次循环的空格数:3,2,1
    base_num = mid - space_num      # 每列中间一半的**数:1,2,3
    star_num = base_num * 2 - 1     # 计算**数:1,3,5
    if base_num == 1:
        print(" " * space_num + "A" * star_num)  # 打印首尾
    else:
        print(" " * space_num + "A" + " " * (star_num-2)+"A")     # 打印有空格部分
    i += 1
    n -= 1

~~~

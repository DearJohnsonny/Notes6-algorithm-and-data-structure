# 杂谈
## Introduction to data structure
### 线性结构
线性结构是最简单的数据结构，包括数组、链表，以及由它们衍生出来的栈、队列、哈希表。

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196073863-67dd00c2-67b7-4b81-be08-b85c10ef0bae.png" width="600">
</div>

### 树
树是相对复杂的数据结构，其中比较有代表性的是二叉树，由它又衍生出了二叉堆之类的数据结构。

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196073872-e4931893-ec3c-4e95-9768-82c006165ee1.png" width="300">
</div>

### 图
图是更为复杂的数据结构，因为在图中会呈现出多对多的关联关系

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196073895-96964919-f6cf-455b-bb97-639f70d19967.png" width="300">
</div>

### 其他数据结构
除上述所列的几种基本数据结构以外，还有一些其他的千奇百怪的数据结构。它们由基本数据结构变形而来，用于解决某些特定问题，如跳表、哈希链表、位图等。

## 关于算法的好坏

设T(n)为程序基本操作执行次数的函数（也可以认为是程序的相对执行时间函数），n为输入规模，程序中最常见的4种执行方式分别是：
* T(n) = 3n，执行次数是线性的
* T(n) = 5logn，执行次数是用对数计算的
* T(n) = 2，执行次数是常量
* T(n) = 0.5n^2 + 0.5n，执行次数是用多项式计算的

### 渐进时间复杂度（asymptotic time complexity）
若存在函数f(n)，使得当n趋近于无穷大时，T(n)/f(n)的**极限值**为不等于零的常数，则称f(n)是T(n)的同数量级函数。记作T(n)=O(f(n))，称为O(f(n))，O为算法的渐进时间复杂度，简称为时间复杂度。

因为渐进时间复杂度用大写O来表示，所以也被称为大O表示法。如：
* T(n)=O(n)
* T(n) = 5logn
* T(n) = 2
* T(n) = 0.5n^2+ 0.5n
不难得出以下结论：

$$
\mathrm{O}(1)<\mathrm{O}(\log n)<\mathrm{O}(\mathrm{n})<\mathrm{O}\left(\mathrm{n}^2\right)
$$

还有很多其他的时间复杂度： $\mathrm{O}(\mathrm{nlogn}) 、 \mathrm{O}\left(\mathrm{n}^3\right) 、 \mathrm{O}(\mathrm{mn}) 、 \mathrm{O}\left(2^{\mathrm{n}}\right) 、 \mathrm{O}(\mathrm{n} !)$

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
### 渐进时间复杂度（asymptotic time complexity）
设T(n)为程序基本操作执行次数的函数（也可以认为是程序的相对执行时间函数），n为输入规模，程序中最常见的4种执行方式分别是：
* T(n) = 3n，执行次数是线性的
* T(n) = 5logn，执行次数是用对数计算的
* T(n) = 2，执行次数是常量
* T(n) = 0.5n^2 + 0.5n，执行次数是用多项式计算的

若存在函数f(n)，使得当n趋近于无穷大时，T(n)/f(n)的**极限值**为不等于零的常数，则称f(n)是T(n)的同数量级函数。记作T(n)=O(f(n))，称为O(f(n))，O为算法的渐进时间复杂度，简称为时间复杂度。

因为渐进时间复杂度用大写O来表示，所以也被称为大O表示法。如：
* T(n) = O(n)
* T(n) = O(logn)
* T(n) = O(1)
* T(n) = =O(n^2)
不难得出以下结论：

$$
\mathrm{O}(1)<\mathrm{O}(\log n)<\mathrm{O}(\mathrm{n})<\mathrm{O}\left(\mathrm{n}^2\right)
$$

还有很多其他的时间复杂度： $\mathrm{O}(\mathrm{nlogn}) 、 \mathrm{O}\left(\mathrm{n}^3\right) 、 \mathrm{O}(\mathrm{mn}) 、 \mathrm{O}\left(2^{\mathrm{n}}\right) 、 \mathrm{O}(\mathrm{n} !)$

### 空间复杂度
和时间复杂度类似，空间复杂度是对一个算法在运行过程中临时占用存储空间大小的量度，它同样使用了大O表示法。

程序占用空间大小的计算公式记作S(n)=O(f(n))，其中n为问题的规模，f(n)为算法所占存储空间的函数

#### 常量空间
当算法的存储空间大小固定，和输入规模没有直接的关系时，空间复杂度记作O(1)。

#### 线性空间
当算法分配的空间是一个线性的集合（如数组），并且集合大小和输入规模n成正比时，空间复杂度记作O(n)。

#### 二维空间
当算法分配的空间是一个二维数组集合，并且集合的长度和宽度都与输入规模n成正比时，空间复杂度记作O(n2)。

#### 递归空间
递归是一个比较特殊的场景。虽然递归代码中并没有显式地声明变量或集合，但是计算机在执行程序时，会专门分配一块内存，用来存储“方法调用栈”。

“方法调用栈”包括进栈和出栈两个行为。当进入一个新方法时，执行入栈操作，把调用的方法和参数信息压入栈中。当方法返回时，执行出栈操作，把调用的方法和参数信息从栈中弹出。

由上面“方法调用栈”的出入栈过程可以看出，**执行递归操作所需要的内存空间和递归的深度成正比**。纯粹的递归操作的空间复杂度也是线性的，如果递归的深度是n，那么空间复杂度就是O(n)。

# 数据结构基础
## 数组
数组对应的英文是array，是有限个相同类型的变量所组成的有序集合，数组中的每一个变量被称为元素。数组是最为简单、最为常用的数据结构。

数组的另一个特点，是在内存中顺序存储，因此可以很好地实现逻辑上的顺序表。

* 数组读取元素和更新元素的时间复杂度都是O(1)
* 数组扩容的时间复杂度是O(n)，插入并移动元素的时间复杂度也是O(n)，综合起来插入操作的时间复杂度是O(n)。
* 删除操作，只涉及元素的移动，时间复杂度也是O(n)。

### 数组的优劣势
优势：数组拥有非常高效的随机访问能力，只要给出下标，就可以用常量时间找到对应元素。有一种高效查找元素的算法叫作二分查找，就是利用了数组的这个优势。

劣势：数组的劣势，体现在插入和删除元素方面。由于数组元素连续紧密地存储在内存中，插入、删除元素都会导致大量元素被迫移动，影响效率。

总的来说，数组所适合的是读操作多、写操作少的场景，而链表则恰恰相反

## 链表
链表（linked list）是一种在物理上非连续、非顺序的数据结构，由若干节点（node）所组成。

单向链表的每一个节点又包含两部分，一部分是存放数据的变量data，另一部分是指向下一个节点的指针next。

双向链表比单向链表稍微复杂一些，它的每一个节点除了拥有data和next指针，还拥有指向前置节点的prev指针。

这正如地下党的联络方式，一级一级，单线传递。
### 内存储存方式
如果说数组在内存中的存储方式是顺序存储，那么链表在内存中的存储方式则是随机存储。

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196078719-87590c47-d65b-4fb3-99c2-6490fb700c31.png" width="600">
</div>

### 基本操作
**查找节点**：在查找元素时，链表不像数组那样可以通过下标快速进行定位，只能从头节点开始向后一个一个节点逐一查找。链表中的数据只能按顺序进行访问，最坏的时间复杂度是O(n)。
**更新节点**：如果不考虑查找节点的过程，链表的更新过程会像数组那样简单，直接把旧数据替换成新数据即可

## 数组 VS 链表

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196079089-7e25e149-698b-4a7f-938f-6dbc4c025d7a.png" width="600">
</div>

从表格可以看出，数组的优势在于能够快速定位元素，对于读操作多、写操作少的场景来说，用数组更合适一些。

相反地，链表的优势在于能够灵活地进行插入和删除操作，如果需要在尾部频繁插入、删除元素，用链表更合适一些。

## 栈和队列
逻辑结构是抽象的概念，它依赖于物理结构而存在。

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196079429-9715da93-7ebc-4f8b-85a7-beaf93279bec.png" width="500">
</div>

两个常用数据结构：栈和队列。这两者都属于逻辑结构，它们的物理实现既可以利用数组，也可以利用链表来完成。

### 栈 stack
栈（stack）是一种线性数据结构，栈中的元素只能先入后出（First In Last Out，简称FILO）。最早进入的元素存放的位置叫作栈底（bottom），最后进入的元素存放的位置叫作栈顶（top）。栈这种数据结构既可以用数组来实现，也可以用链表来实现。
#### 栈的基本操作
入栈 push：把新元素放入栈中，只允许从栈顶一侧放入元素，新元素的位置将会成为新的栈顶。以数组为例：
![image](https://user-images.githubusercontent.com/111955215/196079971-818060ec-a5e6-4fae-859b-25df593d7c1c.png)

出栈 pop：把元素从栈中弹出，只有栈顶元素才允许出栈，出栈元素的前一个元素将会成为新的栈顶。
![image](https://user-images.githubusercontent.com/111955215/196079983-0b401802-39b2-4bb6-9469-1c12730746d1.png)

入栈和出栈只会影响到最后一个元素，不涉及其他元素的整体移动，所以无论是以数组还是以链表实现，入栈、出栈的时间复杂度都是O(1)。

### 队列
队列（queue）是一种线性数据结构，它的特征和行驶车辆的单行隧道很相似。不同于栈的先入后出，队列中的元素只能先入先出（First In First Out，简称FIFO）。队列的出口端叫作队头（front），队列的入口端叫作队尾（rear）

与栈类似，队列这种数据结构既可以用数组来实现，也可以用链表来实现。
#### 队列的基本操作
入队（enqueue）：把新元素放入队列中，只允许在队尾的位置放入元素，新元素的下一个位置将会成为新的队尾。
出队操作（dequeue）：把元素移出队列，只允许在队头一侧移出元素，出队元素的后一个元素将会成为新的队头。

如果像这样不断出队，队头左边的空间失去作用，那队列的容量岂不是越来越小了？

用数组实现的队列可以采用**循环队列**的方式来维持队列容量的恒定

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196080588-67375ce5-c024-458a-8638-80c2db0d4cad.png" width="600">
</div>

### 栈与队列的应用
栈的输出顺序和输入顺序相反，所以栈通常用于对“历史”的回溯，也就是逆流而上追溯“历史”。
* 例如实现递归的逻辑，就可以用栈来代替，因为栈可以回溯方法的调用链。
* 栈还有一个著名的应用场景是面包屑导航，使用户在浏览页面时可以轻松地回溯到上一级或更上一级页面。

队列的输出顺序和输入顺序相同，所以队列通常用于对“历史”的回放，也就是按照“历史”顺序，把“历史”重演一遍。
* 例如在多线程中，争夺公平锁的等待队列，就是按照访问顺序来决定线程在队列中的次序的。
* 再如网络爬虫实现网站抓取时，也是把待抓取的网站URL存入队列中，再按照存入队列的顺序来依次抓取和解析的。

## 散列表
散列表也叫作哈希表（hash table），这种数据结构提供了键（Key）和值（Value）的映射关系。只要给出一个Key，就可以高效查找到它所匹配的Value，时间复杂度接近于O(1)。
![image](https://user-images.githubusercontent.com/111955215/196081186-8b7bf856-26ca-4254-95c2-eb68985258a5.png)

散列表在本质上也是一个数组；可以说是数组和链表的结合

数组只能根据下标，像a[0]、a[1]、a[2]、a[3]、a[4]这样来访问，而散列表的Key则是以字符串类型为主的。

而哈希函数可以通过某种方式，把Key和数组下标进行转换
### 哈希函数
在Java及大多数面向对象的语言中，每一个对象都有属于自己的hashcode，这个hashcode是区分不同对象的重要标识。无论对象自身的类型是什么，它们的hashcode都是一个整型变量。

通过哈希函数，我们可以把字符串或其他类型的Key，转化成数组的下标index。

#### 写操作（put）
如调用hashMap.put("002931", "王五")，意思是插入一组Key为002931、Value为王五的键值对。

但是，由于数组的长度是有限的，当插入的Entry越来越多时，不同的Key通过哈希函数获得的下标有可能是相同的。例如002936这个Key对应的数组下标是2；002947这个Key对应的数组下标也是2。这种情况，就叫作哈希冲突。如何解决？

##### 开放寻址法

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196088166-768dab94-8a6f-4fcf-ad20-42e2a0068ebd.png" width="600">
</div>

##### 链表法
HashMap数组的每一个元素不仅是一个Entry对象，还是一个链表的头节点（数组的每一个元素都与一个链表对应）。每一个Entry对象通过next指针指向它的下一个Entry节点。当新来的Entry映射到与之冲突的数组位置时，只需要插入到对应的链表中即可。

HashMap数组的每一个元素不仅是一个Entry对象，还是一个链表的头节点。每一个Entry对象通过next指针指向它的下一个Entry节点。当新来的Entry映射到与之冲突的数组位置时，只需要插入到对应的链表中即可。
![image](https://user-images.githubusercontent.com/111955215/196088516-3f9c86e0-4f9d-4668-84f7-35b9a7cfbc3c.png)

#### 读操作（get）
调用 hashMap.get("002936")，意思是查找Key为002936的Entry在散列表中所对应的值。

具体该怎么做呢？下面以链表法为例来讲一下。

第1步，通过哈希函数，把Key转化成数组下标2。

第2步，找到数组下标2所对应的元素，如果这个元素的Key是002936，那么就找到了；如果这个Key不是002936也没关系，由于数组的每个元素都与一个链表对应，我们可以顺着链表慢慢往下找，看看能否找到与Key相匹配的节点。

#### 扩容（resize）
当经过多次元素插入，散列表达到一定饱和度时，Key映射位置发生冲突的概率会逐渐提高。这样一来，大量元素拥挤在相同的数组下标位置，形成很长的链表，对后续插入操作和查询操作的性能都有很大影响。这时，散列表就需要扩展它的长度，也就是进行扩容。
![image](https://user-images.githubusercontent.com/111955215/196088661-a6a3f897-ce2f-41b0-919f-a6e63c1f41df.png)
步骤：
1．扩容，创建一个新的Entry空数组，长度是原数组的2倍。

2．重新Hash，遍历原Entry数组，把所有的Entry重新Hash到新数组中。为什么要重新Hash呢？因为长度扩大以后，Hash的规则也随之改变。
经过扩容，原本拥挤的散列表重新变得稀疏，原有的Entry也重新得到了尽可能均匀的分配。
![image](https://user-images.githubusercontent.com/111955215/196088811-361d50a2-c780-4ee7-abab-a7c594242b1b.png)

# 树
## 树的简介
有许多逻辑关系并不是简单的线性关系，在实际场景中，常常存在着一对多，甚至是多对多的情况。其中树和图就是典型的非线性数据结构

在数据结构中，树的定义如下。
树（tree）是n（n≥0）个节点的有限集。当n=0时，称为空树。在任意一个非空树中，有如下特点。
* 有且仅有一个特定的称为根的节点。
* 当n>1时，其余节点可分为m（m>0）个互不相交的有限集，每一个集合本身又是一个树，并称为根的子树。
![image](https://user-images.githubusercontent.com/111955215/196089307-c524df74-2e57-4124-91a2-0780313e4171.png)

在上图中，节点1是根节点（root）；节点5、6、7、8是树的末端，没有“孩子”，被称为叶子节点（leaf）。图中的虚线部分，是根节点1的其中一个子树。
![image](https://user-images.githubusercontent.com/111955215/196089394-497d7df7-91d6-44dc-96bb-700f289bbcb3.png)

在上图中，节点4的上一级节点，是节点4的父节点（parent）；从节点4衍生出来的节点，是节点4的孩子节点（child）；和节点4同级，由同一个父节点衍生出来的节点，是节点4的兄弟节点（sibling）。
树的最大层级数，被称为树的高度或深度。显然，上图这个树的高度是4。

## 二叉树
二叉树节点的两个孩子节点，一个被称为左孩子（left child），一个被称为右孩子（right child）。这两个孩子节点的顺序是固定的，就像人的左手就是左手，右手就是右手，不能够颠倒或混淆。
![image](https://user-images.githubusercontent.com/111955215/196089522-0b6720bc-0748-4cd6-8384-cdd43b31f8d4.png)

### 满二叉树
一个二叉树的所有非叶子节点都存在左右孩子，并且所有叶子节点都在同一层级上，那么这个树就是满二叉树。
![image](https://user-images.githubusercontent.com/111955215/196089604-3a004814-d742-4073-9be1-10379e33d31d.png)

### 完全二叉树
对一个有n个节点的二叉树，按层级顺序编号，则所有节点的编号为从1到n。如果这个树所有节点和同样深度的满二叉树的编号为从1到n的节点位置相同，则这个二叉树为完全二叉树。

![image](https://user-images.githubusercontent.com/111955215/196089778-09009af0-5ccb-47c1-8efa-f5501b2d3a3a.png)

完全二叉树的条件没有满二叉树那么苛刻：满二叉树要求所有分支都是满的；而完全二叉树只需保证最后一个节点之前的节点都齐全即可

### 二叉树的物理存储结构
#### 链式存储结构。
相较于链表，二叉树稍微复杂一些，一个节点最多可以指向左右两个孩子节点，所以二叉树的每一个节点包含3部分
* 存储数据的data变量
* 指向左孩子的left指针
* 指向右孩子的right指针
![image](https://user-images.githubusercontent.com/111955215/196089950-fe4777f0-beab-4081-b500-297abbf9ad47.png)

#### 数组。
使用数组存储时，会按照层级顺序把二叉树的节点放到数组中对应的位置上。如果某一个节点的左孩子或右孩子空缺，则数组的相应位置也空出来。这样可以更方便地**在数组中定位二叉树的孩子节点和父节点**。

**假设一个父节点的下标是parent，那么它的左孩子节点下标就是2×parent + 1；右孩子节点下标就是2×parent + 2。**

![image](https://user-images.githubusercontent.com/111955215/196089993-a8b1e5eb-b5bf-45eb-a634-459acbc5c56b.png)

### 二叉树的应用
#### 查找
二叉查找树（binary searchtree）在二叉树的基础上增加了以下几个条件。
* 如果左子树不为空，则左子树上所有节点的值均小于根节点的值
* 如果右子树不为空，则右子树上所有节点的值均大于根节点的值
* 左、右子树也都是二叉查找树

![image](https://user-images.githubusercontent.com/111955215/196090419-e0290aa5-5577-4ac9-9326-0396560536d4.png)

对于一个节点分布相对均衡的二叉查找树来说，如果节点总数是n，那么搜索节点的**时间复杂度就是O(logn)**，**和树的深度**是一样的。这种依靠比较大小来逐步查找的方式，和二分查找算法非常相似。
#### 维持相对顺序
二叉查找树还有另一个名字——二叉排序树（binary sort tree）。

新插入的节点，同样要遵循二叉排序树的原则。例如插入新元素5，由于5<6，5>3，5>4，所以5最终会插入到节点4的右孩子位置。

![image](https://user-images.githubusercontent.com/111955215/196090649-96b4059d-644c-428e-93dc-24833e3dc93f.png)

这一切看起来很顺利，然而却隐藏着一个致命的问题。什么问题呢？下面请试着在二叉查找树中依次插入9、8、7、6、5、4，看看会出现什么结果。

![image](https://user-images.githubusercontent.com/111955215/196090711-918b7472-fe0f-4d3e-9813-ba63ec9570fb.png)

不只是外观看起来变得怪异了，查询节点的时间复杂度也退化成了O(n)，如何解决？————二叉树的自平衡（红黑树、AVL树、树堆）

### 二叉树的遍历
在计算机程序中，遍历本身是一个线性操作。所以遍历同样具有线性结构的数组或链表，是一件轻而易举的事情。

反观二叉树，是典型的非线性数据结构，遍历时需要把非线性关联的节点转化成一个线性的序列，以不同的方式来遍历，遍历出的序列顺序也不同。

从节点之间位置关系的角度来看，二叉树的遍历分为4种。
1. 前序遍历。
2. 中序遍历。
3. 后序遍历。
4. 层序遍历。

从更宏观的角度来看，二叉树的遍历归结为两大类。
1. 深度优先遍历（前序遍历、中序遍历、后序遍历）。
2. 广度优先遍历（层序遍历）。

#### 深度优先遍历
所谓深度优先，顾名思义，就是偏向于纵深，“一头扎到底”的访问方式。

二叉树用递归方式来实现前序、中序、后序遍历，是最为自然的方式。这3种遍历方式的区别，仅仅是输出的执行位置不同：前序遍历的
输出在前，中序遍历的输出在中间，后序遍历的输出在最后。

代码中值得注意的一点是二叉树的构建。二叉树的构建方法有很多，这里把一个线性的链表转化成非线性的二叉树，链表节点的顺序恰恰是二叉树前序遍历的顺序。链表中的空值，代表二叉树节点的左孩子或右孩子为空的情况。

##### 前序遍历
二叉树的前序遍历，输出顺序是根节点、左子树、右子树。

![image](https://user-images.githubusercontent.com/111955215/196096266-0f1c5c45-b772-437c-b75d-2b606cfd58f5.png)

##### 中序遍历
二叉树的中序遍历，输出顺序是左子树、根节点、右子树

找完子树的左中右，则将其视为左，再往上找
##### 后序遍历

#### 广度优先遍历

## 二叉堆
二叉堆本质上是一种完全二叉树，它分为两个类型。
1. 最大堆：最大堆的任何一个父节点的值，都大于或等于它左、右孩子节点的值。![image](https://user-images.githubusercontent.com/111955215/196097546-19f00f46-7d5e-4e81-96d1-d245cf31e6d8.png)

2. 最小堆：最小堆的任何一个父节点的值，都小于或等于它左、右孩子节点的值。![image](https://user-images.githubusercontent.com/111955215/196097561-b17bb439-1f50-4790-b32c-e25d0d096175.png)

二叉堆的根节点叫作堆顶。

最大堆和最小堆的特点决定了：最大堆的堆顶是整个堆中的最大元素；最小堆的堆顶是整个堆中的最小元素。

### 二叉堆的自我调整
对于二叉堆，有如下几种操作。
1. 插入节点。
2. 删除节点。
3. 构建二叉堆。

#### 插入节点

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196098021-f742b0a7-4e9d-4185-9f36-e0ce254e409c.png" width="1500">
</div>

#### 删除节点
二叉堆删除节点的过程和插入节点的过程正好相反，所删除的是处于堆顶的节点。例如删除最小堆的堆顶节点1。

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/196098307-1649dba8-a3dd-404b-bf05-dcd27b08775d.png" width="1500">
</div>

其实插入和删除都是通过逐个比较来实现的

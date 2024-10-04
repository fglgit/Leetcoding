[toc]

# 面试经典150题

## 数组/字符串

### [88. 合并两个有序数组](https://leetcode.cn/problems/merge-sorted-array/)

#### 题目

给你两个按 **非递减顺序** 排列的整数数组 `nums1` 和 `nums2`，另有两个整数 `m` 和 `n` ，分别表示 `nums1` 和 `nums2` 中的元素数目。

请你 **合并** `nums2` 到 `nums1` 中，使合并后的数组同样按 **非递减顺序** 排列。

**注意：**最终，合并后数组不应由函数返回，而是存储在数组 `nums1` 中。为了应对这种情况，`nums1` 的初始长度为 `m + n`，其中前 `m` 个元素表示应合并的元素，后 `n` 个元素为 `0` ，应忽略。`nums2` 的长度为 `n` 。

**示例 1：**

```
输入：nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
输出：[1,2,2,3,5,6]
解释：需要合并 [1,2,3] 和 [2,5,6] 。
合并结果是 [1,2,2,3,5,6] ，其中斜体加粗标注的为 nums1 中的元素。
```

#### 题解--同向双指针

两个有序数组的合并。使用两个指针分别指向两个数组，接着哪个更小则加入新数组中，直到一个数组中元素处理完了，接着分别处理两个剩下的数组。

* 时间复杂度：O(m+n)。
  指针移动单调递增，最多移动 m+n 次，因此时间复杂度为 O(m+n)。

* 空间复杂度：O(m)。
  需要建立长度为 m 的临时数组 temp。

优化：逆向双指针，即指针从后往前，每次确定最大的元素，可以将时间复杂度降低为O(1)

#### 代码

```
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int[] temp=new int[m];
        for(int i=0;i<m;i++){
            temp[i]=nums1[i];
        }
        int p=0;
        int q=0;
        int i=0;
        while(p<m&&q<n){
            if(temp[p]>=nums2[q]){
                nums1[i]=nums2[q];
                q++;
            }else{
                nums1[i]=temp[p];
                p++;                
            }
            i++;
        }
        if(p==m){
            while(i<n+m){
                nums1[i]=nums2[q];
                i++;
                q++;
            }
        }
        if(q==n){
            while(i<n+m){
                nums1[i]=temp[p];
                i++;
                p++;
            }
        }
    }
}
```

### [27. 移除元素](https://leetcode.cn/problems/remove-element/)

### 题目

给你一个数组 `nums` 和一个值 `val`，你需要 **[原地](https://baike.baidu.com/item/原地算法)** 移除所有数值等于 `val` 的元素。元素的顺序可能发生改变。然后返回 `nums` 中与 `val` 不同的元素的数量。

假设 `nums` 中不等于 `val` 的元素数量为 `k`，要通过此题，您需要执行以下操作：

- 更改 `nums` 数组，使 `nums` 的前 `k` 个元素包含不等于 `val` 的元素。`nums` 的其余元素和 `nums` 的大小并不重要。
- 返回 `k`。

### 题解--双指针

一前一后双指针，如果遇到对应的元素，则前后交换，把其放到末尾。注意交换后前面的指针不能往后移动，因为其交换后可能换回来的就是该元素。

### 代码

```
class Solution {
    public int removeElement(int[] nums, int val) {
        int k=0;
        int j=nums.length-1;
        for(int i=0;i<nums.length&&i<=j;i++){
            if(nums[i]==val){
                nums[i]=nums[j];
                nums[j]=val;
                i--;
                j--;
                k++;
            }
        }
        return nums.length-k;

    }
}
```



## 双指针

## 滑动窗口

## 矩阵

## 哈希表

## 区间

## 栈

## 链表

## 二叉树

## 二叉树遍历

## 二叉树搜索

## 图

## 图的广度优先搜索

## 字典树

## 回溯

## 分治

## Kadane算法

## 二分查找

## 堆

## 位运算

## 数字

## 一维动态规划

## 多维动态规划


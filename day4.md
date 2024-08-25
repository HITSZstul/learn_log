1. leetcode hard[4](https://leetcode.cn/problems/median-of-two-sorted-arrays/)寻找两个数组的中位数：主要思路
   1. 找第k个元素
   2. 使用二分排除的方式，对两个数组比较k/2的大小
   3. 排除掉较小的数组中k/2的元素（原因在于必然小于第k个元素的大小）
   4. 更新k和被排除的数组
   5. 重复步骤3和4，直到排除掉所有元素
   6. 代码中需要注意：
      1. 可能会出现数组的的大小小于k/2的情况，需要特殊处理，这里可以使用min（k/2，len）选择对应比较的值。
      2. 由于在递归的末尾，必然会有一个数组为空，因此可以对剩下的数组直接取出第k个元素。这是输出。而为了代码的简洁，可以加入长度的判断条件，让数组2的长度大于数组1的长度。这时候只需要判断数组1是否为空即可。 
      3. 注意数组的奇偶情况，使用
        ```java
            int left = (n + m + 1)/2;
            int right = (n + m + 2)/2;
        //将偶数和奇数的情况合并，如果是奇数，会求两次同样的 k
            return (getKth(nums1,0,n-1,nums2,0,m-1,left)+getKth(nums1,0,n-1,nums2,0,m-1,right))*0.5;
        ```
2. 以下是代码：
   ```java
    class Solution {
        public double findMedianSortedArrays(int[] nums1, int[] nums2) {
            int n = nums1.length;
            int m = nums2.length;
            int left = (n + m + 1)/2;
            int right = (n + m + 2)/2;
            //将偶数和奇数的情况合并，如果是奇数，会求两次同样的 k
            return (getKth(nums1,0,n-1,nums2,0,m-1,left)+getKth(nums1,0,n-1,nums2,0,m-1,right))*0.5;
        }
        private int getKth(int[] nums1,int start1,int end1,int[] nums2,int start2,int end2,int k){
            int len1 = end1 - start1 + 1;
            int len2 = end2 - start2 + 1;
            //让 len1 的长度小于 len2，这样就能保证如果有数组空了，一定是 len1
            if(len1>len2)return getKth(nums2, start2,end2,nums1,start1,end1,k);
            if(len1 == 0)return nums2[start2 + k -1];
            if(k == 1)return Math.min(nums1[start1], nums2[start2]);
    
            int i = start1 + Math.min(len1, k/2) - 1;
            int j = start2 + Math.min(len2, k/2) - 1;
    
            if(nums1[i] > nums2[j]){
                return getKth(nums1, start1, end1, nums2, j+1, end2, k - (j - start2 + 1));
            }
            else{
                return getKth(nums1, i+1, end1, nums2, start2, end2, k - (i - start1 + 1));
            }
        }
    }
    ```

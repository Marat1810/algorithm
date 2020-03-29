## 判断丑数

### leetcode 263

编写一个程序判断给定的数是否为丑数。丑数就是只包含质因数 2, 3, 5 的正整数。

```
输入: 6
输出: true
解释: 6 = 2 × 3
示例 2:

输入: 8
输出: true
解释: 8 = 2 × 2 × 2
示例 3:

输入: 14
输出: false 
解释: 14 不是丑数，因为它包含了另外一个质因数 7。
```

解题思路：将这个数的2、3、5因子都约掉，看最后剩的数是否等于1

```java
class Solution {
    public boolean isUgly(int num) {
        if(num<=0) return false;
        if(num==1) return true;
        while(num%2==0){
            num=num/2;
        }
        while(num%3==0){
            num=num/3;
        }
        while(num%5==0){
            num=num/5;
        }
        return num==1;
    }
}
```


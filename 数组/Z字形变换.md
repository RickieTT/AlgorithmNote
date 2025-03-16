Z字形变换

https://leetcode.cn/problems/zigzag-conversion/?envType=study-plan-v2&envId=top-interview-150

```java
class Solution {
    public String convert(String s, int numRows) {
        int n = s.length();
        if (n == 1 || numRows == 1) {
            return s;
        }
        StringBuilder strb = new StringBuilder();
        for(int i = 0; i < numRows; i++) {
            int offset = 2 * (numRows - 1);
            if (i == 0 || i == numRows-1) {
                int pos = i;
            
                while(pos < n){
                    strb.append(s.charAt(pos));
                    pos += offset;    
                }
            } else {
                int posFirst = i;
                int posSecond = 2 * numRows - i -2;
                while (posFirst < n || posSecond < n) {
                    if (posFirst < n) {
                        strb.append(s.charAt(posFirst));
                        posFirst += offset;
                    }
                    if (posSecond < n) {
                        strb.append(s.charAt(posSecond));
                        posSecond += offset;
                    }
                }
            }
        }
        return strb.toString();
    }
}

// 其实就是一道找规律题
// 主要就是注意按照公差 一次性放入某一行的字符 就可以
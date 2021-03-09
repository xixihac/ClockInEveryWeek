### Leetcode地址

https://leetcode-cn.com/problems/string-to-url-lcci/

代码如下：

```java
class Solution {
    public String replaceSpaces(String S, int length) {
        char[] chars = S.toCharArray();
        int count = 0;
        for (int i=0;i<length;i++){
            if (chars[i]==' '){
                count++;
            }
        }
        int newLen = count*2 + length;
        char[] res = new char[newLen];
        for (int i=0,j=0;i<length;i++,j++){
            if (chars[i]==' '){
                res[j] = '%';
                res[++j] = '2';
                res[++j] = '0';
            }else {
                res[j] = chars[i];
            }
        }

        return new String(res);
    }
}
```


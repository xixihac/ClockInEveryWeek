### Leetcode地址

https://leetcode-cn.com/problems/implement-trie-prefix-tree/

代码如下：

```java
class Trie {

    TrieNode head;

    /** Initialize your data structure here. */
    public Trie() {
        head = new TrieNode('/');
    }
    
    /** Inserts a word into the trie. */
    public void insert(String word) {
        TrieNode head = this.head;
        char[] chars = word.toCharArray();
        for(int i=0;i<chars.length;i++){
            int index = chars[i]-'a';
            if(head.child[index]==null){
                head.child[index] = new TrieNode(chars[i]);
            }
            head = head.child[index];
        }
        head.isEnd = true;
    }
    
    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        TrieNode head = this.head;
        char[] chars = word.toCharArray();
        for(int i=0;i<chars.length;i++){
            int index = chars[i] - 'a';
            if(head.child[index]==null){
                return false;
            }
            head = head.child[index];
        }
        if(!head.isEnd){
            return false;
        }
        return true;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
        TrieNode head = this.head;
        char[] chars = prefix.toCharArray();
        for(int i=0;i<chars.length;i++){
            int index = chars[i] - 'a';
            if(head.child[index]==null){
                return false;
            }
            head = head.child[index];
        }
        
        return true;
    }
}

class TrieNode{
    char data;
    TrieNode[] child = new TrieNode[26];
    boolean isEnd = false;
    public TrieNode(char data){
        this.data = data;
    }
}

/**
 * Your Trie object will be instantiated and called as such:
 * Trie obj = new Trie();
 * obj.insert(word);
 * boolean param_2 = obj.search(word);
 * boolean param_3 = obj.startsWith(prefix);
 */
```


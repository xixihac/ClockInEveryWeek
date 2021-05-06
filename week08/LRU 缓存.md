### Leetcode地址

https://leetcode-cn.com/problems/lru-cache-lcci/

代码如下：

```java
class LRUCache {

    LinkedList<Node> cache;
    int capacity;

    public LRUCache(int capacity) {
        this.cache = new LinkedList<>();
        this.capacity = capacity;
    }
    
    public int get(int key) {
        Iterator<Node> it = cache.iterator();
            int res = -1;
            while (it.hasNext()){
                Node next = it.next();
                if (next.key == key){
                    it.remove();
                    res = next.val;
                    break;
                }
            }
            if (res!=-1){
                cache.offerLast(new Node(key,res));
            }
            return res;
    }
    
    public void put(int key, int value) {
        Iterator<Node> iterator = cache.iterator();
        while (iterator.hasNext()){
            Node next = iterator.next();
            if (next.key==key){
                iterator.remove();
                break;
            }
        }
        cache.offerLast(new Node(key,value));
        if (cache.size()>capacity){
            cache.removeFirst();
        }
    }
}
class Node {
    int key;
    int val;

    public Node(int key, int val) {
        this.key = key;
        this.val = val;
    }
}
/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```


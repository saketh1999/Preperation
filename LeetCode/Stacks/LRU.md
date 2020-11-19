LRU Cache
.........

https://leetcode.com/problems/lru-cache/

```
class LRUCache {
public:
    list <pair<int,int>> dll;
    map<int , list <pair<int,int>>::iterator > mp;
    
    int cap;
    LRUCache(int capacity) {
      cap=capacity;
        
    }
    
    int get(int key) {
        if(mp.find(key)==mp.end())
            return -1;
        auto it=mp[key];
        int ans=(*it).second;
        dll.erase(it);
        dll.push_front({key,ans});                       
        mp[key] = dll.begin();                           
        return ans;
    }
    
    void put(int key, int value) {
        if(mp.find(key)!=mp.end())
        {
            auto it= mp[key];
            dll.erase(it);
        }
        dll.push_front(make_pair(key,value));
        
        mp[key]=dll.begin();
        
        if(dll.size()>cap)
        {
            auto x=dll.back();
            mp.erase(x.first);
            dll.pop_back();
        }
    }
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache* obj = new LRUCache(capacity);
 * int param_1 = obj->get(key);
 * obj->put(key,value);
 */

```
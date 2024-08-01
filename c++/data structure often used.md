（智谱清言，2024.8.1）





C++提供了丰富的数据结构，用于存储和管理数据。以下是一些常用的数据结构和它们的例子：



1. **数组（Array）**：
   
   * 例子：`int arr[10];` 这里定义了一个包含10个整数的数组。
     

2. **向量（Vector）**：
   
   * 例子：`std::vector<int> vec;` vec是一个动态数组，可以自动调整大小。
   * 使用：`vec.push_back(1);` 向向量中添加元素。
     

3. **列表（List）**：
   
   * 例子：`std::list<int> lst;` lst是一个双向链表。
   * 使用：`lst.push_back(1);` 向列表中添加元素。
     

4. **队列（Queue）**：
   
   * 例子：`std::queue<int> que;` que是一个先进先出（FIFO）的数据结构。
   * 使用：`que.push(1);` 向队列中添加元素，`que.front();` 获取队列前端的元素。
     

5. **栈（Stack）**：
   
   * 例子：`std::stack<int> stk;` stk是一个后进先出（LIFO）的数据结构。
   * 使用：`stk.push(1);` 向栈中添加元素，`stk.top();` 获取栈顶元素。
     

6. **优先队列（Priority Queue）**：
   
   * 例子：`std::priority_queue<int> pq;` pq是一个按照元素优先级排序的队列。
   * 使用：`pq.push(1);` 向优先队列中添加元素，`pq.top();` 获取最高优先级元素。
     

7. **映射（Map）**：
   
   * 例子：`std::map<int, string> map;` map是一个键值对集合，键是唯一的。
   * 使用：`map[1] = "one";` 在映射中添加键值对。
     

8. **集合（Set）**：
   
   * 例子：`std::set<int> set;` set是一个有序的元素集合，元素是唯一的。
   * 使用：`set.insert(1);` 向集合中添加元素。
     

9. **多重映射（Multimap）**：
   
   * 例子：`std::multimap<int, string> mmap;` mmap允许键有多个值。
   * 使用：`mmap.insert(std::make_pair(1, "one"));` 向多重映射中添加键值对。
     

10. **多重集合（Multiset）**：
    
    * 例子：`std::multiset<int> mset;` mset允许有重复的元素。
    * 使用：`mset.insert(1);` 向多重集合中添加元素。
      

11. **无序映射（Unordered Map）**：
    
    * 例子：`std::unordered_map<int, string> umap;` umap是一个基于哈希表的映射，键是唯一的。
    * 使用：`umap[1] = "one";` 在无序映射中添加键值对。
      

12. **无序集合（Unordered Set）**：
    
    * 例子：`std::unordered_set<int> uset;` uset是一个基于哈希表的集合，元素是唯一的。
    * 使用：`uset.insert(1);` 向无序集合中添加元素。
      



这些数据结构在C++的STL（Standard Template Library）中定义，提供了丰富的操作接口，可以满足不同的编程需求。

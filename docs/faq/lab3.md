
# Lab3常见问题

本节总结了一些目前遇到的问题供大家参考：

## 1. 问题：panic init exiting
    
内存分配出问题，导致第一个用户进程崩溃

(1)可能是kinit修改错误，导致同一个空闲物理页重复出现在freelist；

(2)也可能是没能理解kalloc的含义，返回值错误或者链表操作错误。

    

## 2. 问题：panic freeing free block"

很可能是bget函数锁的使用不正确，一定需要保证bget函数的原子性(指导书有提及)，否则同一磁盘块可能在缓存重复出现，造成二次释放。
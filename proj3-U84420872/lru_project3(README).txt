
                                                                           PROJECT 3 : README FILE
NAME : Monika Phani Swaraj Padavala
UID : U84420872


The Zip folder consists of the source files of Buffermanager in "PostgreSQL 15.4" These are modified to implement the LEAST RECENTLY USED(LRU) algorithm instead of clock algorithm in Postgres.

The List of source files changed to implement the LRU are as follows
1)freelist.c
2)buf_internals.h
3)bufmgr.c
4)buf_init.c


LEAST RECENTLY USED IMPLEMENTATION

-> Created a struct LRUControl (single linkedlist).
-> " Get buf from freelist " : When a buffer is accessed, we have to move the buffer out of the freelist. This increases the refcount of the buffer.
-> " Add buf in tail in LRU " : If refcount of the buffer is zero, unpin the buffer adding it to the tail of LRUControl list (using function AddToLruList). 
-> " Add buf in head and tail if LRU " : If LRU list is empty adding the buffer to head and tail of LRU list.
-> "Get buf from LRU List" : In LRU Algorthim ,the head buffer in LRUControl list, having refcount as zero will be considered as the least recently used buffer and use it for replacement.
-> " Remove buffer from lru " : If the refcount value is greater than zero for a buffer (that is, when we are using a buffer that is already in LRU list), then that buffer should be removed from LRUControl(using function RemoveFromLruList) list and the next buffer should be linked to the previous buffer (that is removing the buffer from the LRU list).
-> " Remove head and tail from lru " : for above condition if LRU list has only one element remove the buffer from head and tail of LRU Control.






the applcation is tested using the input.sql 

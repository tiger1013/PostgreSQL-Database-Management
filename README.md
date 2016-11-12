# PostgreSQL-Database-Management
Team Members:
Yuxiang Wang (wang5350)
Mashfique Anwar (anwar016)

Files modified: freelist.c

We used a doubly-linked list to link up all of buffer pages- the tail corresponds to the least recently used page, whereas the head points to the most recently used one. When a buffer page is referenced and it is already in the buffer pool, it is moved to the head of the list. If an accessed page is not available in the buffer pool and a free buffer is available, then the selected buffer from the free list is inserted onto the head of the list. Whenever a replacement page is sought for eviction from the list, the unpinned buffer page that is closest to the tail is selected .

We made a custom struct “ListNode” to hold the linked list information with corresponding attributes, i.e., next, prev and buf_id. We modified existing “BufferStrategyControl” struct to hold information on the linked list’s head and tail buffer ids. Also, the functions “HandleAddOrReplacement” takes care of buffer page additions and replacements (evictions), whereas, “HandleDelete” takes care of freeing the list, i.e., when a buffer is put on the freelist.

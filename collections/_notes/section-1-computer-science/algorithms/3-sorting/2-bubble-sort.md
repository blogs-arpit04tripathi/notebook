---
layout: post
title: Bubble Sort
permalink: /:collection/cs/algorithms/sorting/bubble-sort
---

![bubble-sort.png]({{site.cdn}}/cse/algo/sort/bubble-sort.png)

**Algorithm**
```
begin BubbleSort(list)
   for all elements of list
      if list[i] > list[i+1]
         swap(list[i], list[i+1])
      end if
   end for   
   return list   
end BubbleSort
```

**Pseudo Code**
```java
procedure bubbleSort( list : array of items )
   loop = list.count;   
   for i = 0 to loop-1 do:
      swapped = false        
      for j = 0 to loop-1 do:
         /* compare the adjacent elements */   
         if list[j] > list[j+1] then
            /* swap them */
            swap( list[j], list[j+1] )         
            swapped = true
         end if         
      end for      
      /*if no number was swapped that means array is sorted now, break the loop.*/      
      if(not swapped) then
         break
      end if      
   end for   
end procedure return list
```

##**Question**

Hey mentor,

I hope you're doing well. I'm really enjoying learning algorithms, but I'm pretty confused by this Big O Notation thing. Can you explain how I'm supposed to figure out which notation my algorithm uses?

-Student

##**Response**

Student,

Big O Notation is basically just a way to measure how long an algorithm takes to run as the data it processes increases in size. We're not trying to compute the exact time it takes, but we're interested in seeing what the worst-case scenario is.

To get started let's take a look at some of the most common orders of growth along with descriptions and examples:

##### O(1)
O(1) references an algorithm that will always have the same run time regardless of the size of the input data. Think of looking up a value in a Ruby Hash or getting an attribute from a JavaScript object.

```
// Find the first item
function FindFirstItem(items) {
     return items[0];
}
```

##### O(N)
O(N) references an algorithm whose execution time will grow linearly with the size of the input data. This is a good example of how Big O Notation favors the showing of the worst case scenario. Imagine iterating over a list of items to find the last item in the array. As the size of the array increases the required time to find the item also increases.If it takes 10 seconds to look through an array of length 10, it will take 20 seconds to look through an array of length 20.

```
function FindItem(items, match) {
     for (var i=0; i < items.length; i++) {
          if (items[i] == match) {
               return true;
          }
     }
     return false;
}
```

##### O(N^2)
O(N^2) represents an algorithm whose execution time is directly proportional to the square of the size of the input size. You will see this time complexity most often in algorithms that have nested iterations over the data set. The deeper you nest iterations, the higher the Big O Notation: O(N^3), O(N^4), etc.

```
function printSums(items) {
     for (var i=0; i < items.length; i++) {
       for (var j = 0; j < items.length; j++) {
         let sum = items[i] + items[j];
         console.log(sum);
       }
     }
}
```

##### O(logN)
O(logN) representes an algorithm that follow a procedure similar to finding a name in an alphabetically list of names by starting at the middle of the list. If the name is not on the middle of the list, you move to the upper or lower half based on the alphabet, pick the middle element in that half and repeat the procedure until you find the name. This type of search algorithm is known as binary search.

```
function FindItemBinarySearch(items, match) {

      var low = 0,
          high = items.length -1;

      while (low <= high) {
          mid = parseInt((low + high) / 2);

           current = items[mid];

          if (current > match) {
             high = mid - 1;
           } else if (current < match) {
              low = mid + 1;
            } else {
              return mid;
           }   
      }       

      return -1;
    }
```

##### Recap
1. Check out this graph of Big O Notation To get a better of understanding of how time complexity increases with data input (space). <img src="https://apelbaum.files.wordpress.com/2011/10/yaacovapelbaumbigoplot.jpg" width="800px"/>
2. Try finding the Big O Notation for algorithms you have previously written.
3. If you have any further questions let me know and i will walk you through finding the Big O Notation for a particular algorithm.

Best regards,

Stefan

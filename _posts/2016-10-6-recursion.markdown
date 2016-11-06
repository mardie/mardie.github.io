---
layout: post

title:  "Generative and structure recursion"
date:   2016-10-6 00:00:00 +0100
categories: computer-science code
---

## Recursion
According to Oxford dictionaries:
> the repeated application of a recursive procedure or definition.
https://en.oxforddictionaries.com/definition/recursion

In the programming field this happens when a function(or method, procedure, ...) call itself. Usually it has this shape:

```javascript

function a(param){
  //The function checks whether there is a inmediate solution or it needs deeper information
  if(needsRecursion){
    //If the function needs recursion it applies itself over a subset of the original params.
    return a(newParams);
  }else{
    return solution;
  }
}

```

There are two kinds of recursion depending on what they recur on.

## Structure recursion
If the recursion takes place over elements contained in the input of the function it is call Structure recursion. You can see this recursion as a way of iteration (usually over nested structures).
One example of this recursion is in a recursive version of the binary search algorithm.
This algorithm works on a sorted array. Every step we take the element in the middle of the array and we compare it with the one we are searching.If the number is smaller that the one in the array we take the first half of the array. If it is bigger we take the second half.
The half has to be passed again to the function till we found the element or the array gets empty.

These are the steps for searching 4 in this array:

![https://en.wikipedia.org/wiki/Binary_search_algorithm](https://upload.wikimedia.org/wikipedia/commons/f/f7/Binary_search_into_array.png "https://en.wikipedia.org/wiki/Binary_search_algorithm")

(https://en.wikipedia.org/wiki/Binary_search_algorithm)

Step 1: Compare 4 and 7 (from __[1, 3, 4, 6, 7, 8, 10, 13, 14]__ )

Step 2: Compare 4 and 3 (from __[1, 3, 4, 6]__ )

Step 3: Compare 4 and 6 (from __[4, 6]__ )

Step 4: Compare 4 and 4 (from __[4]__ )

The array presented in each step is a part of the original array. This kind of recursion helps to traverse nested structures or algorithms.

Other examples could be the recursive function length wich stops recuring when the array is empty or any branch-leaf traversing function.

## Generative Recursion

Generative recursion is when the data recurred on is not contained in the array. Although this data usually depends on the original but it is not a requisite.

You can see this pattern in the recursive fibonacci call tree:

![https://commons.wikimedia.org/wiki/File:Fibonacci_call_tree_5.gif](https://upload.wikimedia.org/wikipedia/commons/1/1a/Fibonacci_call_tree_5.gif "https://commons.wikimedia.org/wiki/File:Fibonacci_call_tree_5.gif")


Step 1: f(5)

Step2: f(4)

.....

As you can see the the recured data is not part of the original input. 4 is not part of 5. It's new data.

This kind of recursion opens a door for more expressive programming. Letting us define abstract processes easily.

The nature of generative recursion let us ignore some part of the structure or the original data for improving performance.

Other software using generative recursion are AST generators and the quick-sort algorithm among others.







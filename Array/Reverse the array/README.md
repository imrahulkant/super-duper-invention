# Array Reverse

Reversing an array means rearranging the elements such that the first element becomes the last, the second element becomes second last and so on.

## Approach 1 :- Using a temporary array [Naive approach]

* Create a temporary array of same size as the original array. 
* Now, copy all elements from original array to the temporary array in reverse order.
* Finally, copy all the elements from temporary array back to the original array.

``` python
def reverseArray(arr):
    n = len(arr)
    temp = [0] * n
    for i in range(n):
        temp[i] = arr[n - i - 1]
    for i in range(n):
        arr[i] = temp[i]
```

```JavaScript
function reverseArray(arr) {
    let n = arr.length;
    let temp = new Array(n);
    for (let i = 0; i < n; i++)
        temp[i] = arr[n - i - 1];
    for (let i = 0; i < n; i++)
        arr[i] = temp[i];
}
```

Time Complexity: ***O(n)***,

Auxiliary Space: ***O(n)***

## Approach 2 :- Using Two Pointers

Two pointers: left and right, such that left points at the beginning of the array and right points to the end of the array. 

While left pointer is less than the right pointer, swap the elements at these two positions. After each swap, increment the left pointer and decrement the right pointer to move towards the center of array. This will swap all the elements in the first half with their corresponding element in the second half.
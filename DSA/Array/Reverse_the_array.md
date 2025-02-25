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

Time Complexity: ***O(n)***,
Auxiliary Space: ***O(n)***

## Approach 2 :- Using Two Pointers

Two pointers: left and right, such that left points at the beginning of the array and right points to the end of the array.

While left pointer is less than the right pointer, swap the elements at these two positions. After each swap, increment the left pointer and decrement the right pointer to move towards the center of array. This will swap all the elements in the first half with their corresponding element in the second half.

``` python
def reverseArray(arr):
    left = 0
    right = len(arr) - 1
    while left < right:
        arr[left], arr[right] = arr[right], arr[left]
        left += 1
        right -= 1
```

Time Complexity: ***O(n)***,
Auxiliary Space: ***O(1)***

## Approach 3 :- By Swapping Elements

The idea is to iterate over the first half of the array and swap each element with its corresponding element from the end. So, while iterating over the first half, any element at index i is swapped with the element at index (n – i – 1).

``` python
def reverseArray(arr):
    n = len(arr)
    for i in range(n // 2):
        temp = arr[i]
        arr[i] = arr[n - i - 1]
        arr[n - i - 1] = temp
```

Time Complexity: ***O(n)***,
Auxiliary Space: ***O(1)*** (in-place)

## Approach 4 :- Using Recursion

Recursive function that takes a range of array elements as input and reverses it. Inside the recursive function,

* Swap the first and last element.
* Recursively call the function with the remaining subarray.

``` python
def reverseArrayRec(arr, l, r):
    if l >= r:
        return
    arr[l], arr[r] = arr[r], arr[l]
    reverseArrayRec(arr, l + 1, r - 1)

def reverseArray(arr):
    n = len(arr)
    reverseArrayRec(arr, 0, n - 1)
```

Time Complexity: ***O(n)***,
Auxiliary Space: ***O(n)***

## Approach 4 :- Using Inbuilt Methods

Use inbuilt reverse methods available across different languages.

``` python
def reverse_array(arr):
    arr.reverse()
```

Or

``` python
def reverse_array(arr):
    return arr[::-1]
```

Time Complexity: ***O(n)***,
Auxiliary Space: ***O(1)***

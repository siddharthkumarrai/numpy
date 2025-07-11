# numpy
```mermaid 
graph TD
    A[NumPy] --> B[Vector]
    A --> C[Matrix]
    
    B --> D["[1, 2, 3, 4, 5, 6]"]
    D --> E["1D Array<br/>6 elements"]
    
    C --> F["[[1, 2, 3],<br/> [4, 5, 6]]"]
    F --> G["2D Array<br/>2 rows × 3 columns"]
    
    style A fill:#ff6b35,stroke:#333,stroke-width:3px,color:#000
    style B fill:#4ecdc4,stroke:#333,stroke-width:2px,color:#000
    style C fill:#4ecdc4,stroke:#333,stroke-width:2px,color:#000
    style D fill:#f7f7f7,stroke:#666,stroke-width:1px,color:#000
    style F fill:#f7f7f7,stroke:#666,stroke-width:1px,color:#000
    style E fill:#ffe66d,stroke:#333,stroke-width:1px,color:#000
    style G fill:#ffe66d,stroke:#333,stroke-width:1px,color:#000
```
```mermaid
graph TD
    A[User] --> B[Python NumPy Interface]
    B --> A
    
    B --> C[NumPy Core]
    C --> D[C++ Implementation]
    
    subgraph "NumPy Stack"
        D
        C
        B
    end
    
    style A fill:#ff6b35,stroke:#333,stroke-width:3px,color:#000
    style B fill:#4ecdc4,stroke:#333,stroke-width:2px,color:#000
    style C fill:#45b7d1,stroke:#333,stroke-width:2px,color:#000
    style D fill:#96ceb4,stroke:#333,stroke-width:2px,color:#000
```
## Creating Array from list
```python
import numpy as np

arr_1D = np.array([1,2,3]) 
print(arr_1D)                                output: [1 2 3]

arr_2D = np.array([[1,2,3],[4,5,6]])
print(arr_2D)                                output: [[1 2 3]
                                                      [4 5 6]]
```
## Numpy Array vs Python List
```python
py_list = [1,2,3]
print("python list multiplication : ", py_list * 2)             output: python list multiplication :  [1, 2, 3, 1, 2, 3]

np_array = np.array([[1,2,3]])
print("python numpy array multiplication : ", np_array * 2)     output: python numpy array multiplication :  [[2 4 6]]

import time 

start = time.time()
py_list = [ element * 2 for element in range(100000000)]
print("\n list operation time : ", time.time() - start)           output: list operation time :  12.6350736618042

start = time.time()
np_array = np.arange(100000000)
np_array*2
print("\n list operation Numpy array : ", time.time() - start)    output: list operation Numpy array :  0.7995524406433105
```
## creating Numpy Array form scaratch
```python
zeros_arr = np.zeros((3,3))
print("matrix of ones : \n",zeros_arr)            
output:- 
matrix of ones : 
 [[0. 0. 0.]
 [0. 0. 0.]
 [0. 0. 0.]]

ones_arr = np.ones((3,3))
print("ones matrix(array) : \n", ones_arr)
output:- 
ones matrix(array) : 
 [[1. 1. 1.]
 [1. 1. 1.]
 [1. 1. 1.]]

full_constant_arr = np.full((3,3),7)
print("matrix of constant number : \n", full_constant_arr)
output:- 
matrix of constant number : 
 [[7 7 7]
 [7 7 7]
 [7 7 7]]

random_num_arr = np.random.random((3,3))
print("matrix of random number : \n", random_num_arr)
output:-
matrix of random number : 
 [[0.67331133 0.78696991 0.3835139 ]
 [0.56709472 0.39115883 0.40419826]
 [0.03819528 0.24757474 0.91139398]]

sequence_arr = np.arange(0,10,2)
print("vector of random number : \n", sequence_arr)
output:-
vector of random number : 
 [0 2 4 6 8]
```
## vector , matrix and Tensor
```python
vector = np.array([1,2,3,4])
print("vector : ", vector)
output:- 
vector :  [1 2 3 4]

matrix = np.array([[1,2,3],
                   [4,5,6],
                   [7,8,9]])
print("matrix : \n",matrix)
output:- 
matrix : 
 [[1 2 3]
 [4 5 6]
 [7 8 9]]

tensor = np.array([[[1,2,3], [4,5,6], [7,8,9]],
                   [[10,11,12], [13,14,15], [16,17,18]],
                   [[19,20,21], [22,23,24], [25,26,27]]])
print("tensor : \n",tensor, "\n", tensor.shape)
output:- 
tensor : 
 [[[ 1  2  3]
  [ 4  5  6]
  [ 7  8  9]]

 [[10 11 12]
  [13 14 15]
  [16 17 18]]

 [[19 20 21]
  [22 23 24]
  [25 26 27]]] 
 (3, 3, 3)
```
## Array properties
```python
numpy_array1 = np.array([[1,2,3],
                         [4,5,6],
                         [7,8,9]])

print("shape : ", numpy_array1.shape)            output:- shape :  (3, 3)
print("dimension : ", numpy_array1.ndim)         output:- dimension :  2
print("size : ", numpy_array1.size)              output:- size :  9
print("dataType : ", numpy_array1.dtype)         output:- dataType :  int64
```
## Array Reshaping
```python
arr = np.arange(12)
print("Orignal array : ",arr)
output :-
Orignal array :  [ 0  1  2  3  4  5  6  7  8  9 10 11]

reshaped_arr = arr.reshape((4,3))
print("Reshaped array : \n",reshaped_arr)
output :-
Reshaped array : 
 [[ 0  1  2]
 [ 3  4  5]
 [ 6  7  8]
 [ 9 10 11]]

flatten_arr = reshaped_arr.flatten()
print("Flattern array : ", flatten_arr)
output :-
Flattern array :  [ 0  1  2  3  4  5  6  7  8  9 10 11]

reveled_arr = reshaped_arr.ravel()          # return view insted of copy
print("Reveled array : ", reveled_arr)
output :-
Reveled array :  [ 0  1  2  3  4  5  6  7  8  9 10 11]

transpose_arr = reshaped_arr.T
print("Transpose array : \n", transpose_arr)
output :-
Transpose array : 
 [[ 0  3  6  9]
 [ 1  4  7 10]
 [ 2  5  8 11]]
```
## Numpy Array operations
```python
arr = np.array([1,2,3,4,5,6,7,8,9,10,11,12])
print("Baic Slicing : ", arr[3:8])                output:-  Baic Slicing :  [4 5 6 7 8]
print("Slice with step : ",arr[2:9:3])            output:- Slice with step :  [3 6 9]
print("Negative indexing :",arr[-2])              output:- Negative indexing : 11
```

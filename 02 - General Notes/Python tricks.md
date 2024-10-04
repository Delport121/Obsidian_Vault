### 1. **Negative Indexing:**
- `s[-1]`: Refers to the **last element** in the sequence.
- `s[-2]`: Refers to the **second-to-last element**, and so on.
- Negative indexing counts from the end of the list, with `-1` being the last element.
```python
s = [10, 20, 30, 40]
print(s[-1])  # Output: 40 (last element)
print(s[-2])  # Output: 30 (second-to-last element)
```
### 2. **Slicing:**
- You can extract a portion of the sequence using the slicing syntax: `start:stop:step`.
- `s[start:stop]`: Returns elements from index `start` to `stop-1`.
    - Omitting `start` means starting from the beginning.
    - Omitting `stop` means going to the end.
- `s[start:stop:step]`: Allows you to control the step size between elements.
    - The default `step` is `1`, but it can be negative to reverse the sequence.
```python
s = [10, 20, 30, 40, 50]
print(s[1:4])  # Output: [20, 30, 40] (from index 1 to 3)
print(s[:3])   # Output: [10, 20, 30] (from start to index 2)
print(s[2:])   # Output: [30, 40, 50] (from index 2 to the end)
print(s[::2])  # Output: [10, 30, 50] (every second element)
print(s[::-1]) # Output: [50, 40, 30, 20, 10] (reversed list)
```
### 3. **Step Slicing (with Negative Steps):**
- If you include a negative `step` in slicing, it will reverse the sequence.
- `s[::-1]`: Reverses the entire list.
- `s[start:stop:-1]`: Moves backward from `start` to `stop+1`.
```python
s = [10, 20, 30, 40, 50]
print(s[::-1])  # Output: [50, 40, 30, 20, 10] (reversed list)
print(s[3:1:-1])  # Output: [40, 30] (reversed from index 3 to 2)
```
### 4. **Ellipsis (`...`)**:
- The `Ellipsis` object (`...`) can be used in slicing, primarily in multi-dimensional arrays (especially in libraries like NumPy).
- It represents selecting all dimensions up to a certain point.
```python
import numpy as np
arr = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
print(arr[..., 1])  # Output: [[2, 4], [6, 8]] (takes the 1st element from the last dimension)
```
### 5. **Indexing with a List or Boolean Array:**
- You can also use a list or boolean array to index sequences (this is common in NumPy).
```python
import numpy as np
arr = np.array([10, 20, 30, 40, 50])
idx = [0, 2, 4]  # Use list of indices
print(arr[idx])  # Output: [10, 30, 50]

mask = np.array([True, False, True, False, True])
print(arr[mask])  # Output: [10, 30, 50]
```
### 6. **Multi-Dimensional Indexing:**
- For multi-dimensional arrays, you can access elements using tuples or comma-separated indices.
```python
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(arr[1, 2])  # Output: 6 (element at row 1, column 2)
print(arr[:, 1])  # Output: [2, 5, 8] (all rows, column 1)
```
### 7. **Unpacking (Extended Unpacking):**
- You can use unpacking to assign multiple values from a sequence to variables.
- The extended unpacking feature (`*`) allows capturing the remaining elements in a list.
```python
a, *b, c = [1, 2, 3, 4, 5]
print(a)  # Output: 1
print(b)  # Output: [2, 3, 4] (captures middle elements)
print(c)  # Output: 5
```
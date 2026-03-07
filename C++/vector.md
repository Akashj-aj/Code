# C++ - Vector

`vector` is a dynamic array container in C++ that can automatically resize when elements are inserted or removed.

Unlike normal arrays:

- Size can change dynamically
- Memory is managed automatically
- Provides many built-in functions

`vector` stores elements in contiguous memory locations, just like arrays.

---

## Header File

```cpp
#include <vector>
```

Usually used with:

```cpp
#include <iostream>
using namespace std;
```

---

## Syntax

```cpp
vector<data_type> vector_name;
```

Example:

```cpp
vector<int> v;
```

---

## Initialization of Vector

### Empty vector

```cpp
vector<int> v;
```

### Vector with values

```cpp
vector<int> v = {1, 2, 3, 4};
```

### Vector with fixed size

```cpp
vector<int> v(5);
```

Result:

```text
0 0 0 0 0
```

### Vector with size and default value

```cpp
vector<int> v(5, 10);
```

Result:

```text
10 10 10 10 10
```

---

## Vector Functions

| Function      | What it does                      | Example                  |
|---------------|-----------------------------------|--------------------------|
| `push_back()` | Adds element at end               | `v.push_back(10);`       |
| `pop_back()`  | Removes last element              | `v.pop_back();`          |
| `size()`      | Returns number of elements        | `v.size();`              |
| `max_size()`  | Maximum elements vector can store | `v.max_size();`          |
| `capacity()`  | Current allocated storage         | `v.capacity();`          |
| `resize(n)`   | Change size of vector             | `v.resize(10);`          |
| `empty()`     | Checks if vector is empty         | `v.empty();`             |
| `front()`     | Returns first element             | `v.front();`             |
| `back()`      | Returns last element              | `v.back();`              |
| `at(i)`       | Access element safely             | `v.at(2);`               |
| `assign()`    | Assign new values                 | `v.assign(5, 10);`       |
| `insert()`    | Insert element at position        | `v.insert(v.begin(), 5);`|
| `erase()`     | Remove element at position        | `v.erase(v.begin());`    |
| `clear()`     | Remove all elements               | `v.clear();`             |
| `swap()`      | Swap two vectors                  | `v1.swap(v2);`           |

---

## Example of Vector Functions

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    vector<int> v;

    v.push_back(10);
    v.push_back(20);
    v.push_back(30);

    cout << "First element: " << v.front() << endl;
    cout << "Last element: " << v.back() << endl;

    cout << "Size: " << v.size() << endl;

    v.pop_back();

    cout << "After pop_back size: " << v.size() << endl;

    return 0;
}
```

Output:

```text
First element: 10
Last element: 30
Size: 3
After pop_back size: 2
```

---

## Accessing Elements

### Using index

```cpp
cout << v[0];
```

### Using `at()`

```cpp
cout << v.at(1);
```

---

## Iterating Over Vector

### Using for loop

```cpp
for (int i = 0; i < v.size(); i++)
{
    cout << v[i] << " ";
}
```

### Using range-based loop

```cpp
for (int x : v)
{
    cout << x << " ";
}
```

### Using iterator

```cpp
for (auto it = v.begin(); it != v.end(); it++)
{
    cout << *it << " ";
}
```

---

## Example Program

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    vector<int> v = {1, 2, 3, 4};

    for (int x : v)
    {
        cout << x << " ";
    }

    return 0;
}
```

Output:

```text
1 2 3 4
```

---

## Time Complexity

| Operation        | Complexity     |
|------------------|----------------|
| Access element   | O(1)           |
| Insert at end    | O(1) amortized |
| Insert in middle | O(n)           |
| Delete element   | O(n)           |
| Traversal        | O(n)           |

---

## Advantages of Vector

- Dynamic resizing
- Fast random access
- Easy to use
- Many built-in functions
- Efficient memory management

## Disadvantages of Vector

- Inserting in middle is slow
- Deleting from middle is slow
- Extra memory overhead due to capacity

## When to Use Vector

Use vector when:

- Size of data is not fixed
- Need fast index access
- Need dynamic arrays

Common uses in DSA:

- Storing input
- Adjacency lists
- Dynamic arrays
- Sliding window problems

---

## Quick Revision

### What is `vector`?

- Dynamic array in C++ STL
- Resizes automatically
- Stores elements in contiguous memory
- Fast random access like arrays

### Basic Syntax

```cpp
vector<int> v;
```

### Common Initialization

```cpp
vector<int> a;                // empty
vector<int> b = {1, 2, 3};    // with values
vector<int> c(5);             // size 5, all 0
vector<int> d(5, 10);         // size 5, all 10
```

### Most Used Functions

```cpp
v.push_back(x);   // add at end
v.pop_back();     // remove last
v.size();         // number of elements
v.empty();        // true if empty
v.front();        // first element
v.back();         // last element
v.at(i);          // bounds-checked access
v.clear();        // remove all elements
```

### Complexity Cheat Sheet

- Access by index: `O(1)`
- Push at end: `O(1)` amortized
- Insert/Delete in middle: `O(n)`
- Traversal: `O(n)`

Note: Vector looks simple until capacity decides to do surprise cardio.

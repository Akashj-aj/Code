# C++ - unordered_map

`unordered_map` is a container in C++  that stores key-value pairs.

Example:

```text
Key -> Value
word -> frequency
id -> name
number -> count
```

It is implemented using a hash table, which makes most operations very fast (average `O(1)`).

Unlike `map`, elements in `unordered_map` are not stored in sorted order.

---

## Header File

```cpp
#include <unordered_map>
```

Usually used with:

```cpp
#include <iostream>
using namespace std;
```

---

## Syntax

```cpp
unordered_map<key_type, value_type> map_name;
```

Example:

```cpp
unordered_map<int, int> mp;
```

Meaning:

```text
Key -> int
Value -> int
```

---

## Creating an unordered_map

### Empty unordered_map

```cpp
unordered_map<int, int> mp;
```

### Initialize with values

```cpp
unordered_map<int, int> mp = {
    {1, 10},
    {2, 20},
    {3, 30}
};
```

---

## unordered_map Functions

| Function     | What it does                | Example              |
|--------------|-----------------------------|----------------------|
| `insert()`   | Inserts key-value pair      | `mp.insert({1, 10});`|
| `operator[]` | Insert or access element    | `mp[1] = 10;`        |
| `at()`       | Access element safely       | `mp.at(1);`          |
| `find()`     | Returns iterator to element | `mp.find(1);`        |
| `count()`    | Checks if key exists        | `mp.count(1);`       |
| `erase()`    | Removes element by key      | `mp.erase(1);`       |
| `size()`     | Returns number of elements  | `mp.size();`         |
| `empty()`    | Checks if map is empty      | `mp.empty();`        |
| `clear()`    | Removes all elements        | `mp.clear();`        |
| `begin()`    | Iterator to first element   | `mp.begin();`        |
| `end()`      | Iterator to end element     | `mp.end();`          |

---

## Example of unordered_map Functions

```cpp
#include <iostream>
#include <unordered_map>

using namespace std;

int main()
{
    unordered_map<int, int> mp;

    mp[1] = 10;
    mp[2] = 20;
    mp[3] = 30;

    cout << "Value of key 2: " << mp[2] << endl;

    cout << "Size: " << mp.size() << endl;

    mp.erase(2);

    cout << "After erase size: " << mp.size() << endl;

    return 0;
}
```

Output:

```text
Value of key 2: 20
Size: 3
After erase size: 2
```

---

## Accessing Elements

### Using `[]`

```cpp
cout << mp[1];
```

### Using `at()`

```cpp
cout << mp.at(1);
```

---

## Checking if Key Exists

Using `count()`:

```cpp
if (mp.count(5))
{
    cout << "Key exists";
}
```

---

## Searching Element

Using `find()`:

```cpp
auto it = mp.find(1);

if (it != mp.end())
{
    cout << "Found";
}
```

---

## Traversing unordered_map

### Using range loop

```cpp
for (auto x : mp)
{
    cout << x.first << " " << x.second << endl;
}
```

Meaning:

```text
x.first  -> key
x.second -> value
```

### Using iterator

```cpp
for (auto it = mp.begin(); it != mp.end(); it++)
{
    cout << it->first << " " << it->second << endl;
}
```

---

## Example Program

```cpp
#include <iostream>
#include <unordered_map>

using namespace std;

int main()
{
    unordered_map<string, int> freq;

    freq["apple"]++;
    freq["banana"]++;
    freq["apple"]++;

    for (auto x : freq)
    {
        cout << x.first << " -> " << x.second << endl;
    }

    return 0;
}
```

Output:

```text
apple -> 2
banana -> 1
```

---

## Frequency Counting Example

One of the most common interview uses.

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

using namespace std;

int main()
{
    vector<int> arr = {1, 2, 2, 3, 1};

    unordered_map<int, int> freq;

    for (int x : arr)
    {
        freq[x]++;
    }

    for (auto x : freq)
    {
        cout << x.first << " -> " << x.second << endl;
    }
}
```

Output:

```text
1 -> 2
2 -> 2
3 -> 1
```

---

## Time Complexity

| Operation | Complexity   |
|-----------|--------------|
| Insert    | O(1) average |
| Delete    | O(1) average |
| Search    | O(1) average |
| Traversal | O(n)         |

Worst case:

```text
O(n)
```

(because of hash collisions)

---

## Advantages of unordered_map

- Very fast lookup
- Average `O(1)` operations
- Good for frequency counting
- Efficient hashing

## Disadvantages of unordered_map

- Elements are not sorted
- Worst-case performance can degrade
- Uses more memory

## When to Use unordered_map

Use it when you need:

- Fast lookups
- Frequency counting
- Key-value storage
- Hashing problems

Common interview problems:

```text
Two Sum
Top K Frequent Elements
Subarray Sum
Longest Substring
Duplicate detection
```

---

## Quick Revision

### What is `unordered_map`?

- Hash-table based key-value container
- Average insert/search/delete: `O(1)`
- Not sorted by key

### Basic Syntax

```cpp
unordered_map<int, int> mp;
```

### Most Used Operations

```cpp
mp[key] = value;   // insert/update
mp.at(key);        // safe access
mp.find(key);      // iterator lookup
mp.count(key);     // key exists or not
mp.erase(key);     // delete by key
mp.clear();        // remove all
```

### Complexity Cheat Sheet

- Insert: `O(1)` average
- Search: `O(1)` average
- Delete: `O(1)` average
- Traversal: `O(n)`
- Worst case operations: `O(n)`

Note: unordered_map is fast on average and dramatic on bad days.

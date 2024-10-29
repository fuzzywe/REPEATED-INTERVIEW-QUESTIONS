how and why hashing is done ( a small discussion on it ) then he asked me about Map and some STL function on about how they are implemented in c++  i.e internal working and a little code explanation of them


https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/

look the above link for the implementation part very important


**What is Hashing in C++?**


**Hashing in C++ STL is a technique that maps a key with the associated hash valu**e. The elements in an array can be referred to as the keys, which will have a hash value that helps in finding these keys in the hash table easily. This helps in faster access to the required element, and the efficiency might vary based on the selection of the hash function.

Why is Hashing so Important? Although the most popular data structures, such as arrays and linked lists, can still be utilized to search for the necessary key, they could be more efficient.

Arrays can be helpful when we need to randomly access any element from a particular index, but for this purpose, we need to know the index of the specific element.

This is where hashing comes into the picture. The hash function finds the hash value where a key should be stored. When we need to fetch this key, it can be easily done with the help of its hash value.

As an example, the hashing technique makes finding a person's contact information easier with the help of their names.

How to Work with Hash Function in C++?
The hash function yields an integer value from the given key, be it a character, string, integer, etc., and associates this index with the actual key.

### Hashing: How and Why

#### What is Hashing?

Hashing is a technique used to uniquely identify a specific object from a group of similar objects. It involves using a hash function to convert data into a fixed-size numerical value, which is then used as an index in a hash table.

#### Why Use Hashing?

1. **Efficient Lookup**: Hashing allows for constant-time complexity (O(1)) for search, insert, and delete operations, making it highly efficient for large datasets.
2. **Data Integrity**: Hash functions are used in cryptography to ensure data integrity and security.
3. **Load Balancing**: Hashing is used in distributed systems to evenly distribute data across multiple servers.

#### How Hashing Works

1. **Hash Function**: A hash function takes input data (or a key) and returns a fixed-size string of bytes. Common hash functions include MD5, SHA-1, and SHA-256.
2. **Hash Table**: The output of the hash function is used as an index in a hash table, which is an array of buckets. Each bucket contains a list of elements that hash to the same index.
3. **Collision Handling**: Since multiple keys can hash to the same index (a collision), techniques like chaining (linked lists) or open addressing (probing) are used to handle collisions.

#### Example in C++

```cpp
#include <iostream>
#include <unordered_map>

int main() {
    std::unordered_map<std::string, int> hashMap;

    // Insert key-value pairs
    hashMap["apple"] = 1;
    hashMap["banana"] = 2;
    hashMap["cherry"] = 3;

    // Access values
    std::cout << "Value of 'apple': " << hashMap["apple"] << std::endl;

    // Check if key exists
    if (hashMap.find("banana") != hashMap.end()) {
        std::cout << "Value of 'banana': " << hashMap["banana"] << std::endl;
    }

    return 0;
}
```

### Map and STL Functions in C++

#### std::map

`std::map` is a part of the C++ Standard Template Library (STL) that implements a balanced binary search tree (usually a Red-Black Tree). It stores key-value pairs and maintains the keys in a sorted order.

##### Internal Working

- **Balanced Tree**: `std::map` uses a balanced tree to ensure that the tree remains balanced after insertions and deletions, providing O(log n) time complexity for search, insert, and delete operations.
- **Ordered Keys**: The keys are stored in a sorted order, which allows for efficient range queries and traversal.

##### Example

```cpp
#include <iostream>
#include <map>

int main() {
    std::map<std::string, int> myMap;

    // Insert key-value pairs
    myMap["apple"] = 1;
    myMap["banana"] = 2;
    myMap["cherry"] = 3;

    // Access values
    std::cout << "Value of 'apple': " << myMap["apple"] << std::endl;

    // Iterate through the map
    for (const auto& pair : myMap) {
        std::cout << pair.first << ": " << pair.second << std::endl;
    }

    return 0;
}
```

#### std::unordered_map

`std::unordered_map` is another associative container in the STL that implements a hash table. It stores key-value pairs but does not maintain any order among the keys.

##### Internal Working

- **Hash Table**: `std::unordered_map` uses a hash table to achieve average-case constant-time complexity (O(1)) for search, insert, and delete operations.
- **Collision Handling**: Collisions are handled using chaining (linked lists) or open addressing (probing).

##### Example

```cpp
#include <iostream>
#include <unordered_map>

int main() {
    std::unordered_map<std::string, int> myHashMap;

    // Insert key-value pairs
    myHashMap["apple"] = 1;
    myHashMap["banana"] = 2;
    myHashMap["cherry"] = 3;

    // Access values
    std::cout << "Value of 'apple': " << myHashMap["apple"] << std::endl;

    // Iterate through the unordered_map
    for (const auto& pair : myHashMap) {
        std::cout << pair.first << ": " << pair.second << std::endl;
    }

    return 0;
}
```

### Summary

- **Hashing**: A technique for efficient data lookup and integrity verification using hash functions and hash tables.
- **std::map**: An ordered associative container that uses a balanced binary search tree to store key-value pairs.
- **std::unordered_map**: An unordered associative container that uses a hash table to store key-value pairs.

Both `std::map` and `std::unordered_map` are powerful tools in the C++ STL for managing key-value pairs, each with its own strengths and use cases.

### Hashing

**Hashing** is a technique used in programming to map data of arbitrary size to fixed-size values (hash codes). This mapping helps quickly locate and retrieve data, making it a cornerstone in data structures like hash tables, maps, and sets. Here’s a small breakdown of why and how hashing works:

1. **Purpose**:
   - Hashing provides efficient data storage and retrieval.
   - It is typically used in data structures like hash maps (or hash tables), where each value is assigned a unique "key."
   - Hash tables support fast insertions, deletions, and lookups, making them ideal for scenarios requiring quick data access.

2. **How Hashing Works**:
   - **Hash Function**: A hash function takes an input (or "key") and produces a fixed-size integer, the "hash code."
   - **Mapping**: The hash code is used as an index to store the key-value pair in an array or table.
   - **Collisions**: If two keys produce the same hash code, this is called a "collision." Collision resolution strategies like chaining (storing collided items in a list) or open addressing (finding a new empty slot) are used to handle these situations.

### Maps and Their Internal Working in C++

In C++, a `std::map` and `std::unordered_map` are popular choices for associative data structures, but they work differently internally.

1. **std::map**:
   - `std::map` in C++ is implemented as a self-balancing binary search tree, usually a Red-Black Tree.
   - **Ordered**: Elements are stored in a sorted order based on the key.
   - **Complexity**: `O(log n)` for insertions, deletions, and lookups, due to the tree structure.
   - **Internal Working**: Each insertion maintains the balance property of the Red-Black Tree to ensure that the tree remains balanced, which keeps the operations efficient.

2. **std::unordered_map**:
   - `std::unordered_map` uses a hash table internally.
   - **Unordered**: Elements are not stored in any specific order.
   - **Complexity**: Average `O(1)` for insertions, deletions, and lookups, thanks to the hash table.
   - **Internal Working**: When a key-value pair is added, the hash function is called on the key, determining the bucket where the pair will be stored. The hash table dynamically resizes when it becomes too full to maintain efficiency.
   
### STL Functions and Code Explanation

Here are a few common STL functions with a brief explanation of how they work internally:

1. **`insert` in std::map**:
   - Internally, `insert` finds the correct position based on the key (using the Red-Black Tree structure) and inserts the element, rebalancing the tree as needed.

2. **`find` in std::unordered_map**:
   - `find` computes the hash for the key and looks up the bucket where the key might be stored. It iterates through any elements in that bucket to find the matching key, returning the iterator if found or `end()` if not.

3. **Example Code**:

   ```cpp
   #include <iostream>
   #include <map>
   #include <unordered_map>
   using namespace std;

   int main() {
       // Ordered map example
       map<int, string> ordered_map;
       ordered_map.insert({1, "apple"});
       ordered_map[2] = "banana"; // Insert using operator
       cout << "Ordered Map:\n";
       for (auto &entry : ordered_map) {
           cout << entry.first << ": " << entry.second << endl;
       }

       // Unordered map example
       unordered_map<int, string> unordered_map;
       unordered_map.insert({1, "cherry"});
       unordered_map[2] = "date";
       cout << "\nUnordered Map:\n";
       for (auto &entry : unordered_map) {
           cout << entry.first << ": " << entry.second << endl;
       }

       return 0;
   }
   ```

   - **Explanation**:
     - In `ordered_map`, elements are stored in a sorted order, while in `unordered_map`, the order is arbitrary and depends on the hash values.
     - Access to elements in `unordered_map` is faster in most cases (`O(1)`), while `ordered_map` operations have a `O(log n)` complexity due to the underlying tree structure. 

This overview should help clarify hashing, `std::map`, `std::unordered_map`, and their internal workings.

The syntax to create a template for hash class:

template <class key> struct hash;

Now, to create objects with the hash class, we can use the following syntax:

hash<class template> object-name

The hash class also has a single member function, operator(), that returns the object's hash value.

Example:

// Initializing character.
char ch = 'n';

// Creating object of the hash class.
hash<char> ch_hash;

// Using operator() to find hash value.
cout << ch_hash(ch); 

But How Does Hashing Work? There are two heuristic techniques (an approach that finds shortcuts to a solution that might not be optimal but can be reached within the required deadline) to create a hash function, hashing by division and hashing by multiplication. 

A good hash function has the following properties:

It should be efficient for computation.
All the keys should be uniformly distributed in the hash table.
How to work with hash function in C++

Suppose we have 7 elements in an array. We must create a hash table where these elements will be stored for efficient access. When we come across the first element, 52, we'll perform the following operation to get its index.

hash_index(key) = key % size of the hash table

hash_index(key) = 52 % 7 = 3

What if we have more than one element with the same index? As in our case, 52 and 66 will get the same index, 3. This leads to a collision. There's always a need for a good hash function to avoid collision in frequent cases, but it is likely to happen.

There are two ways to deal with collision:

Separate chaining
Open Addressing
deal with collision

Hashing in C++ STL can be done with the help of the hash class, which we are yet to see in the examples given below. When we pass an argument to the hash class, it obtains the hash value of the passed argument. The hashed value makes searching for objects easier. The keys passed as the argument will be mapped to their obtained hash values.

Given below are some programs to find the hash value of different arguments.

Character Hashing

// Program to demonstrate the character hashing.
#include <iostream>

// To avoid using std:: before each statement.
using namespace std; 

// Function for character hashing.
void hashingChar() {
    
    char ch = 'n';
    
    // Instantiation of a hash object.
    hash<char> char_hash; 
    
    // Using operator() to return hashed value.
    cout << "The hashed value of character 'n' is: " << char_hash(ch) << endl; 
}

// Main function.
int main() { 
    // Calling function for character hashing.
    hashingChar(); 
}  

Output:

The hashed value is: 110

String Hashing

// Program to demonstrate the string hashing.
#include <iostream>

// To avoid using std:: before each statement.
using namespace std; 

// Function for string hashing.
void hashingString() {
    
    string str = "hashing";
    
    // Instantiation of a hash object.
    hash<string> string_hash; 
    
    // Using operator() to return hashed value.
    cout << "The hashed value of string is: " << string_hash(str) << endl; 
}

// Main function.
int main() { 
    // Calling function for string hashing.
    hashingString(); 
} 

Output:

The hashed value of the string is: 11997348938128597782

Integer Hashing

// Program to demonstrate the integer hashing.
#include <iostream>

// To avoid using std:: before each statement.
using namespace std; 

// Function for integer hashing.
void hashingInteger() {
    
    int num = 17;
    
    // Instantiation of a hash object.
    hash<int> int_hash; 
    
    // Using operator() to return hashed value.
    cout << "The hashed value of integer is: " << int_hash(num) << endl; 
}

// Main function.
int main() { 
    // Calling function for string hashing.
    hashingInteger(); 
} 

Output:

The hashed value of the integer is: 17

Vector Hashing

// Program to demonstrate the vector hashing
#include <iostream>
#include <vector>

// To avoid using std:: before each statement.
using namespace std; 

// Function for vector hashing.
void hashingVector() {
    
    vector<bool> vec { true, true, false, false };
    
    // Instantiation of a hash object.
    hash<vector<bool>> vector_hash; 
    
    // Using operator() to return hashed value.
    cout << "The hashed value of vector_hash is: " << vector_hash(vec) << endl; 
}

// Main function.
int main() { 
    // Calling function for vector hashing.
    hashingVector(); 
} 

Output:

The hashed value of vector_hash is: 17166569625921664880

Examples to Understand the Working of Hashing Function in C++
Let us look at a C++ program to see how the hash function works for a hash table. We also need to deal with collision, so each index comprises a list sequence of keys because two or more keys can have the same table position.

And to get the index, we'll use the following hash function, get_hash(), which returns the index by division.

int get_hash(int key) {
    return key % ht_size;
}

Here, ht_size is the size of the hash table.

// Program to demonstrate the working of the hash function in the table.
#include <iostream>
#include <list>

using namespace std;

// Creating class hash table.
class hash_table {
        // Initializing a list for every index.
        list<int> *tbl;
        int ht_size;
        
        // Hash function to get the index of the keys.
        int get_hash(int key) {
            return key % ht_size;
        }
    
    public:
        // Constructor for the class hash_table.
        hash_table(int n) { 
            ht_size = n;
            tbl = new list<int>[ht_size];
        }
    
    // Function to insert keys in the hash table.
    void insert_key(int key) {
        tbl[get_hash(key)].push_back(key);
    }
    
    // Function to display all the keys at their indexes.
    void show() {
        for(int i = 0; i < ht_size; i++) {
            cout << "Values at index " << i << ": ";
            for(int num : tbl[i])
                cout << num << " ";
            cout << endl;
        }
    }
};

// Main function.
int main() {
    // Creating an array of keys.
    int arr[] = {52, 42, 44, 66, 25, 29, 32};
    
    // Find the size of the array.
    int sz_arr = sizeof(arr)/sizeof(int);
    
    // Initializing the hash table.
    hash_table ht(sz_arr);
    
    // Inserting the elements into the hash table.
    for(int i = 0; i < sz_arr; i++) {
        ht.insert_key(arr[i]);
    }
    cout << "The hash table after insertion of elements: " << endl;
    // Calling function to display the hash table.
    ht.show();
    
    return 0;
}

Output:

The hash table after the insertion of elements: 
Values at index 0: 42 
Values at index 1: 29 
Values at index 2: 44 
Values at index 3: 52 66 
Values at index 4: 25 32
Values at index 5:  
Values at index 6: 

As evident in the above program, we can have several keys having the same index after division, so both keys have to be associated with the same index. Therefore, a list has to be used at every index to store more keys in the same position.

Learn More
To learn more about the other concepts in C++, you can find all the C++ topics here.

Conclusion
Hashing in C++ STL is a technique that maps a key to its corresponding hash value. The components of an array can be thought of as its keys because they each get a hash value from the hash function that makes it simple to locate them in the hash table.
The hash function yields an integer value from the given key, be it a character, string, integer, etc., and associates this index with the actual key.
A hash class is a template class, which can be used to create the objects without passing any arguments.
To create objects with the hash class, we can use the following syntax:
hash<class template> objectName

A hash class comprises a member function, operator(), that returns the hash value for the passed argument.
// Initializing character.
char ch = 'n';

// Creating object of the hash class.
hash<char> ch_hash;

// Using operator() to find hash value.
cout << ch_hash(ch); 


Good job on finishing the article! Its time to level up with a Challenge

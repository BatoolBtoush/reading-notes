# **Hashtables**

## **What are Hashtables?**

A hashtable is a data structure that stores key-value pairs. The key is used to retrieve the value. The value is the data that is stored. The key is a unique identifier for the value. The key is a string, integer, or other data type. The value can be any data type. 

<br>

## **Terminology**


1. **Hash:** A hash is the result of an algorithm that converts an entering string into a value that may be used for security or any other purpose. It is used to find the index of the array in the case of a hashtable. 


2. **Buckets:** A bucket is the content of each index in the hashtable's array. Each index corresponds to a bucket. If a collision happens, an index could include multiple key/value pairs. 

3. **Collisions:** A collision occurs When more than one key is hashed to the same place in the hashtable. For example, if the key "hello" is hashed to the index 3, and the key "world" is hashed to the index 3, then there is a collision.

<br>


## **What Do Hashtables Do?**


The basic idea of a hashtable is the ability to store the key into this data structure, and quickly retrieve the value. This is done through what we call a *hash*. A hash is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value.

Since we are able to hash our key and determine the exact location where our value is stored, we can do a lookup in an O(1) time complexity. This is ideal when quick lookups are required.

<br>

### **Hash Function**

Hash maps take advantage of an array’s O(1) read access. Instead of adding elements to an array from beginning to end, a hash map uses a “hash function” to place each item at a precise index location, based off it’s key.

Basically, the hash function takes a key and returns an integer. We use the integer to determine where the key/value pair should be placed in the array. The hash code is calculated in constant time and writing to an array at one index is O(1) so the hash map has O(1) access.

<br>


## **Structure**

### **Hashing**

A hash code turns a key into an integer. And their output is determined only by their input. 

Hash codes should never have randomness to them. The same key should always produce the same hash code.


### **Creating a Hash**

A hashtable traditionally is created from an array. After you have created your array of the appropriate size, do some sort of logic to turn that “key” into a numeric number value. Here is a possible suggestion:

1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.


**Example:**

```
Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16
```

Key gets placed in index of 16. 
We now know that our key “*Cat*” maps to index 16 of the array. We can view into this index and find “*Josie*”, our value quickly.

<br>

### **How the key/values Are Stored in The Array?**

Each index of the array can hold many types of values. 

Each Index of the array contain “buckets”.
Each of these “buckets” holds one key/value pair combination. 

When there is no entry in a specific bucket, the buckets (each index of the array) all start null.

The hash table starts each bucket empty and overwrites their value once a key generates a hashCode that corresponds with an index.

<br>

### **Collisions**

A collision occurs when more than one key hashes to the same index in an array. A “perfect hash” will never have any collisions.

If two keys ever ultimately resolved to the same index, then two calls to ```.Add(key, val)``` with different keys would overwrite each other.


Since different keys can lead to the same bucket it’s important to store the entire key/value pair in the bucket, not just the value. The key must be stored with the value! If only values were stored in buckets then it would be impossible to determine which value to return when a key led you to a bucket.

<br>

### **Hash maps do this to store values:**

1. accept a key
2. calculate the hash of the key
3. use modulus to convert the hash into an array index
4. store the key with the value by appending both to the end of a linked list

<br>

### **Hash maps do this to read value:**

1. accept a key
2. calculate the hash of the key
3. use modulus to convert the hash into an array index
4. use the array index to access the short LinkedList representing a bucket
5. search through the bucket looking for a node with a key/value pair that matches the key you were given

<br>

## **Internal Methods**

**Add()**

    
    ```
    public void Add(string key, string value)
    {
        int hash = GetHash(key);
        int index = hash % _buckets.Length;
        _buckets[index].AddLast(new KeyValuePair<string, string>(key, value));
    }
    ```


**GetHash()**

    
    ```
    public int GetHash(string key)
    {
        int hash = 0;
        for (int i = 0; i < key.Length; i++)
        {
            hash += key[i];
        }
        return hash;
    }
    ```


**Find()**

    
    ```
    public string Find(string key)
    {
        int hash = GetHash(key);
        int index = hash % _buckets.Length;
        foreach (var item in _buckets[index])
        {
            if (item.Key == key)
            {
                return item.Value;
            }
        }
        return null;
    }
    ```

**Contains()**

    
    ```
    public bool Contains(string key)
    {
        int hash = GetHash(key);
        int index = hash % _buckets.Length;
        foreach (var item in _buckets[index])
        {
            if (item.Key == key)
            {
                return true;
            }
        }
        return false;
    }
    ```

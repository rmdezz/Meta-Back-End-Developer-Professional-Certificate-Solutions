# Hash tables

# Introduction

Have you ever wondered how search engines quickly find information for you? Or how online shopping sites can recommend products based on your search history? **One of the data structures behind this efficiency is a hash table.**

In this section, we will learn about hash tables, their structure, and inherent features, and how they work. You will also explore some of the advantages of using hash tables and understand what collisions are in hashing.

# ****What is a Hash Table?****

A hash table is a data structure that contains multiple slots or "buckets" to hold key-value pairs. It requires a hashing function to determine the correct bucket to place the data into. The hashing function is any algorithm or formula that is applied to a key to generate a unique number.

Here's an example of a hash table containing three key-value pairs:

```python
index:  0   1    2   3   4  
keys:   23  17   5   3   7
values: "A" "B" "C" "D" "E"
```

# ****How Does a Hash Table Work?****

To use a hash table, each data item to be stored must have a key and a value. The key is taken, and the hashing function is applied to it, reducing it to a fixed-size value. This value acts as the index indicator, determining where in the table the value will be stored.

Here's an example of how the hash function works:

```python
hashing function: key % 5
key: 17
index = 17 % 5 = 2
```

In this example, the key **`17`** is reduced to the index **`2`** using the hashing function **`key % 5`**.

# ****Advantages of Hash Tables****

Hash tables prioritize speed over space, and can retrieve an item in O(1) time. This is in contrast to arrays, where a search through each element takes O(n) time in the worst-case scenario.

# ****Collisions in Hash Tables****

What happens when two keys result in the same index after being processed by the hashing function? This is called a collision, and it is a common problem in hash tables.

**There are several solutions to handle collisions, such as growing the table, increasing the complexity of the hashing function, or creating a linked list at the point of collision.**

# Conclusion

In this section, you learned about hash tables, their structure and features, and how they work. You also discovered the advantages of hash tables, such as their fast retrieval times, and the concept of collisions in hash tables and how they can be resolved.
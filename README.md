# Assignment 1: Circular Buffer Implementation

## Overview

This project implements a **Circular Buffer** (also known as a ring buffer) in the C programming language. A circular buffer is a fixed-size data structure that efficiently handles reading and writing operations in a wrap-around manner using head and tail pointers.

## Features

- Fixed-size buffer (`SIZE = 10`)
- Write operation with **overflow** detection
- Read operation with **underflow** detection
- Wraparound using modulo arithmetic
- Tracks the number of elements using a counter

## Functions

| Function          | Description                                                             |
| ----------------- | ----------------------------------------------------------------------- |
| `init(cb)`        | Initializes the buffer (head = 0, tail = 0, count = 0)                  |
| `isFull(cb)`      | Returns 1 if the buffer is full, otherwise 0                            |
| `isEmpty(cb)`     | Returns 1 if the buffer is empty, otherwise 0                           |
| `write(cb, data)` | Writes one character to the buffer. Prints "Buffer Overflow" if full    |
| `read(cb)`        | Reads one character from the buffer. Prints "Buffer Underflow" if empty |

## Main Function

1. Prompts the user to enter a name
2. Appends the suffix **"CE-ESY"** to the entered name
3. Writes each character of the resulting string into the circular buffer
4. Reads all characters back from the buffer and prints them in order
5. No newline is printed between characters during the read-back

## Buffer Cases

- **Buffer Overflow**: If the buffer becomes full while writing, an error message is printed and the write operation is ignored.
- **Buffer Underflow**: If a read operation is attempted on an empty buffer, an error message is printed and `'\0'` is returned.

## How the Wraparound Works

When `tail` or `head` reaches the end of the buffer (`SIZE - 1`), the next operation moves them back to index 0 using modulo arithmetic:

```c
tail = (tail + 1) % SIZE;
head = (head + 1) % SIZE;
````

This allows the buffer to reuse space that has already been read.

## Prerequisites

- `Assignment1.c` - Source code containing the circular buffer implementation
- `README.md` - This explanation file

## Compilation and Execution

```bash
gcc Assignment1.c -o Assignment1
./Assignment1
```

## Example 1

**Input:**
```
Enter name: abd
```
**Output:**
```
abdCE-ESY
Buffer is now empty
```

## Example 2

**Input:**
```
Enter name: abdullah
```
**Output:**
```
Buffer Overflow
Buffer Overflow
Buffer Overflow
Buffer Overflow
abdullahCE
Buffer is now empty
```
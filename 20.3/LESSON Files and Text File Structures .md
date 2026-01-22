# 20.3 LESSON Files and Text File Structures  
**Outcomes 1.3-1.5:**  
- Understand the logical structure of text files  
- Learn the main operations with text files  
- Explore advantages and disadvantages of different file types  

---

## 1. Logical Structure of Text Files

Text files store information as a **sequence of characters**.  
In p5.js, you usually work with text files using:  
- `loadStrings()`  
- `saveStrings()`  
- `loadTable()` (for structured data)
  
>[!TIP]
> Choosing the right structure makes your program faster and easier to manage.

---

### 1.1 Sequential Text Files

- **Definition:** Data is stored **one line after another**, in order.  
- **Access:** To get a specific line, you must read all previous lines first.  

```javascript
let lines;

function preload() {
  lines = loadStrings("data.txt"); // Loads all lines sequentially
}
````
> [!NOTE]
> **Analogy:** A book: you read pages from start to finish to reach page 50.


* Simple to implement
* Best for logs or datasets processed from start to finish
* Limitation: Accessing a line far down the file can be slow

---

### 1.2 Random-Access Text Files

* **Definition:** Data can be read or written at **any position** without reading everything first.
* **Access:** You can "jump" directly to a line or byte.

```javascript
let lines = loadStrings("data.txt");
console.log(lines[5]); // Access line 6 directly
```
> [!NOTE]
> **Analogy:** A filing cabinet, you open any drawer to reach a specific file.

**Notes:**

* Faster for retrieving specific entries
* Slightly more complicated to implement
* True byte-level random access is harder with plain text

---

### 1.3 Indexed Sequential Access Method (ISAM)

* **Definition:** Combines sequential and random access using an **index**.
* **Access:** Jump to a section quickly using the index, then read sequentially from there.

```javascript
let scores = loadStrings("scores.txt");
let index = { "Alice": 0, "Bob": 5 }; // Index points to line numbers
console.log(scores[index["Bob"]]); // Access Bob’s score directly
```
> [!NOTE]
> **Analogy:** A phone book with alphabetical tabs, you jump to a section, then read sequentially to find the exact entry.

**Notes:**

* Great for large files needing sequential and fast access
* Requires index maintenance
* Common in databases and applications with lots of records

---

## 2. Main Operations with Text Files

| Operation            | Description               | p5.js Example                                                      | Notes                                       |
| -------------------- | ------------------------- | ------------------------------------------------------------------ | ------------------------------------------- |
| Create a file buffer | Allocate temporary memory | `let buffer = [];`                                                 | Speeds up processing before writing to disk |
| Open a file          | Load file for reading     | `lines = loadStrings("data.txt");`                                 | Access data without modifying original file |
| Create new file      | Store new data            | `let newFile = [];`                                                | Save data later with `saveStrings()`        |
| Export data          | Save to disk              | `saveStrings(lines, "output.txt");`                                | Writes contents of buffer/array             |
| Import data          | Read from disk            | `lines = loadStrings("input.txt");`                                | Loads file into memory                      |
| Append data          | Add at end                | `lines.push("New data"); saveStrings(lines, "data.txt");`          | Useful for logs                             |
| Close a file         | Finish reading/writing    |                                                                   | p5.js handles automatically                 |
| Compare files        | Check if contents match   | `arraysEqual(file1, file2)`                                        | Verify updates or integrity                 |
| Copy a file          | Duplicate                 | `saveStrings(loadStrings("file1.txt"), "file2.txt");`              | Backup or duplicate                         |
| Merge files          | Combine contents          | `merged = file1.concat(file2); saveStrings(merged, "merged.txt");` | Useful for datasets                         |

**Helper Function for comparing arrays:**

```javascript
function arraysEqual(a, b) {
  return a.length === b.length && a.every((v, i) => v === b[i]);
}
```

---

## 3. Advantages & Disadvantages of File Types

| File Type     | Access Speed              | Storage     | Difficulty | Maintainability           | Notes                                    |
| ------------- | ------------------------- | ----------- | ---------- | ------------------------- | ---------------------------------------- |
| Sequential    | Slow for specific records | Low         | Easy       | Easy                      | Great for logs and small datasets        |
| Random-Access | Fast for specific records | Medium      | Medium     | Moderate                  | Good for frequently accessed lines       |
| ISAM          | Fast and organized        | Medium-High | Hard       | Easier for large datasets | Needs an index, ideal for large datasets |

> [!NOTE]
> **Key Points:**
>
> * Sequential: Simple, but slow for specific records
> * Random-Access: Faster access, slightly more complex
> * ISAM: Best for large, structured datasets; combines sequential and fast lookups

---

## 4. Quick Examples

**Sequential Read:**

```javascript
let lines;
function preload() {
  lines = loadStrings("data.txt");
}
function setup() {
  for (let line of lines) {
    print(line);
  }
}
```

**Appending a New Line:**

```javascript
lines.push("New high score: 100");
saveStrings(lines, "data.txt");
```

**Merging Two Files:**

```javascript
let file1 = loadStrings("file1.txt");
let file2 = loadStrings("file2.txt");
let merged = file1.concat(file2);
saveStrings(merged, "merged.txt");
```

---

## 5. Quick Review Questions

1. **What is the difference between sequential and random-access text files?**  
    <details>
    <summary>Answer</summary>
    
      
    - **Sequential:** You must read data in order, one line after another. Slow for accessing specific records far down the file.  
    - **Random-access:** You can jump directly to a specific line or byte without reading everything before it. Faster for retrieving specific entries.
    </details>

2. **How does ISAM combine sequential and random access?**  
    <details>
    <summary>Answer</summary>

    - ISAM uses an **index** to jump quickly to a section of the file, then reads sequentially from there.  
    - This combines fast access for specific entries (random-access) with the ability to read sequentially when needed.
    </details>

2. **How do you **append** a new line to a file in p5.js?**  
    <details>
    <summary>Answer</summary>
  
      
    ```javascript
    lines.push("New data");       // Add new line to array
    saveStrings(lines, "data.txt"); // Save back to the file
    ````
    
    </details>

4. **Why might ISAM be better for large datasets than sequential files?**

    <details>
    <summary>Answer</summary>
      
    - Sequential files are slow for finding specific entries because you must read from the start.  
    - ISAM lets you jump to the correct section using an index, making lookups faster while still allowing sequential reads.
    </details>

5. **Which type of file is easiest to implement and maintain for small datasets?**
  
    <details>
    <summary>Answer</summary>
    
      
    - **Sequential files** are the simplest to implement and maintain, especially for small datasets or logs.
    </details>

6. **What is the purpose of a file buffer in p5.js?**

    <details>
    <summary>Answer</summary>
      
    - A **file buffer** is temporary memory (usually an array) where data is stored before writing to or after reading from a file.  
    - It speeds up reading/writing by avoiding slow, repeated access to disk.
    </details>



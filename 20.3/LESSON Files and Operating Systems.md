# 20.3 LESSON Files and Operating Systems

**Things to focus on:**  
- Understand the client/server relationship between a program (like a p5.js sketch) and the operating system when handling files.

---

## 1. Client/Server Relationship

Think of this like a restaurant:  

- **Client:** The program you’re using (e.g., a p5.js sketch, Python program, or game)  
- **Server:** The operating system (OS), which manages your computer’s resources  

**Example:**  
You want to save a file from a p5.js sketch:  

1. The sketch (program) asks the OS (restaurant) for a “table” (space in memory).  
2. The OS manages the table and gives the sketch what it needs.  

> [!NOTE]
> **Important:** Programs, including p5.js sketches, don’t talk directly to hardware (like the hard drive or SSD). They ask the OS to handle it. This keeps things safe and organized.

---

## 2. How Programming Environments Access Secondary Storage

**Secondary storage:** Hard drives, SSDs, USB drives (where files are stored permanently).  

- Programming environments like p5.js cannot directly manipulate the hard drive.  
- They request services from the OS.
- 
> [!NOTE]
>**Analogy:** You can’t cook in someone else’s kitchen without asking them first. The OS gives the sketch access to the “kitchen” (storage).  

**Example:**
```javascript
let scores;

function preload() {
  scores = loadStrings("scores.txt");  // Request OS to load file
}
````

Here, `loadStrings()` asks the OS to access `scores.txt` and load its contents into memory.

---

## 3. How the OS Handles Data in Secondary Memory

The OS does all the “heavy lifting”:

* Locates the file on the disk
* Reads or writes the data
* Ensures multiple programs don’t corrupt each other’s files

**Steps for reading a file:**

1. OS finds the file on the hard drive
2. Copies data from the drive into memory (RAM)
3. Provides that data to the program
   
> [!NOTE]
>**Analogy:** You ask a librarian (OS) for a book (file). They find it on the shelf (secondary storage) and hand it to you to read.

---

## 4. How Programming Environments Request File Services

* Programs use file handling commands to request services from the OS.
* In p5.js: `loadStrings()`, `saveStrings()`, `loadJSON()`, etc.
* The sketch doesn’t move the file itself; it sends a request to the OS.
* The OS executes the request safely and returns the results.

```
p5.js Sketch (Client) ---> "Please load scores.txt" ---> OS (Server) ---> File on Disk
```

---

## 5. File Buffers, Data Streams, and File Descriptor Tables

**a) File Buffer**

* Temporary memory (RAM) that stores data before it’s written to disk or after it’s read.
* Speeds up reading/writing because the sketch doesn’t have to wait for the slow hard drive.
* **Analogy:** A tray in a restaurant—you carry multiple plates at once instead of one at a time.

**b) Data Stream**

* A pipeline for data going in or out of the sketch:

  * Input stream → reading from file
  * Output stream → writing to file

> [!NOTE]
> * **Analogy:** Water flowing through a pipe from a reservoir (disk) to your glass (program).

**c) File Descriptor Table**

* A special list the OS keeps to track open files for each sketch.
* Each open file gets a unique number (file descriptor) so the OS knows which file the program wants to use.

> [!NOTE]
> * **Analogy:** A waiter keeping a ticket for each order. When you want your meal, the waiter looks at the ticket to see which table gets what.

---

## 6. Summary Table

| Concept                     | p5.js Example / Analogy                         |
| --------------------------- | ----------------------------------------------- |
| Client                      | p5.js sketch requesting file access             |
| Server                      | OS handling requests (Windows, macOS, Linux)    |
| Accessing secondary storage | Sketch calls `loadStrings()` or `saveStrings()` |
| OS handling data            | OS finds file, moves data to/from RAM           |
| File buffer                 | Tray holding multiple plates (temporary RAM)    |
| Data stream                 | Pipe moving data in/out of the sketch           |
| File descriptor table       | Waiter’s ticket tracking each open file         |


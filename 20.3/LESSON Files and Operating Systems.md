# 20.3 LESSON Files and Operating Systems

**Outcomes 1.1-1.2:**
**Things to focus on:**

* Understand the client/server relationship between a program (like a p5.js sketch) and the operating system when handling files.

---

## 1. Client/Server Relationship

Think of this like a **restaurant**:

* **Client:** The *program* you’re running (like a p5.js sketch, Python app, or game).
* **Server:** The *operating system (OS)*, which manages the computer’s hardware (storage, memory, etc.).

### How it works

When a program wants to open or save a file, it **does not** touch the hard drive directly.
Instead, it **asks the OS** to handle it.

> [!NOTE]
> **Analogy:**
> The program is a customer who tells the waiter (the OS) what it wants. The waiter then goes to the kitchen (hardware) and brings back the result.

**Example:**
You want to load a text file in a p5.js sketch:

```javascript
let scores;

async function loadStuff() {
  scores = await loadStrings("scores.txt");
}
```

Here’s what happens:

1. The sketch **requests** the OS (through the browser) to fetch `"scores.txt"`.
2. The OS loads the file **in the background** (asynchronously).
3. Once the OS finishes, the data is **returned and stored in memory** inside `scores`.

Because of the **`await`**, the sketch pauses and waits until the OS finishes loading before continuing. This ensures that the program doesn’t try to use the file before it’s ready.

> [!NOTE]
> The sketch (client) never touches the hard drive directly, it always goes through the OS (server). This protects the computer and ensures that multiple programs can safely share storage resources.

---

## 2. How Programming Environments Access Secondary Storage

**Secondary storage** means devices that keep data permanently, like hard drives, SSDs, and USB drives.

* p5.js and other programming environments **cannot** directly read or write to disk.
* Instead, they make **requests** to the operating system to perform file operations.

> [!NOTE]
> **Analogy:**
> You can’t just open the fridge in a restaurant kitchen, you must ask the chef (OS) to bring what you need.

**Example:**

```javascript
async function loadStuff(){
  scores = await loadStrings("scores.txt");  // Ask OS to get this file
}
```

The OS:

1. Finds the file on the storage device.
2. Loads its data into **temporary memory (RAM)**.
3. Sends the data back to the p5.js sketch.
4. The sketch can then use the data, for example displaying the scores on screen.

> [!TIP]
> Secondary storage is **non-volatile**, meaning data stays there even after the computer is turned off, unlike RAM which is temporary.

---

## 3. How the OS Handles Data in Secondary Memory

The OS does the “heavy lifting” behind every file request.

### When reading a file:

1. The OS locates the file on disk.
2. It copies the data into a **buffer** (a temporary memory area).
3. Then it provides that data to the program.

### When writing a file:

1. The program sends data to the OS.
2. The OS may place it into a **buffer** first.
3. Then it writes it out to the actual disk.
4. Once finished, the OS confirms that the file has been written successfully.

> [!NOTE]
> **Analogy:**
> You ask a librarian (the OS) for a book (file). The librarian goes to the shelves (storage), finds the book, and hands it to you to read (RAM). When you return it, the librarian puts it back on the shelf safely.

---

## 4. How Programming Environments Request File Services

Programs request file services through **function calls** (like `loadStrings()` or `saveStrings()`).

```
p5.js Sketch (Client)
   ↓
"Please load scores.txt"
   ↓
Operating System (Server)
   ↓
File on Disk
```

* The sketch sends the request.
* The OS opens the file (creating an entry in its file descriptor table).
* Data is moved using a **data stream** and may pass through a **buffer**.
* The OS then returns the results to the program.
* When finished, the OS closes the file and removes it from the descriptor table.

**Example of saving:**

```javascript
saveStrings(scores, "scores.txt");
```

Here, the sketch tells the OS:

> “Please write this data to a file called scores.txt.”

The OS places the data into a **buffer** before it’s written to disk, so it can manage multiple requests efficiently.
This prevents the hard drive from being overwhelmed by small, constant write operations.

> [!TIP]
> The OS controls *when* data is written to disk, not the program. This makes file writing safer and more efficient.

---

## 5. File Buffers, Data Streams, and File Descriptor Tables

### a) File Buffer

* A **temporary memory area** that holds data while it moves between the disk and the program.
* Prevents the program from waiting while the disk reads or writes.
* The OS automatically manages buffers.
* Buffers are cleared or “flushed” once the data has been safely written to disk.

> **Analogy:**
> A tray used to carry several plates from the kitchen to a table. You can serve more efficiently when you don’t run back and forth for each item.

---

### b) Data Stream

* A **pipeline** for moving data **in or out** of a program.

  * **Input stream:** reads data *from* a file.
  * **Output stream:** sends data *to* a file.
* Streams make it possible to process data gradually instead of all at once.
* Every file operation happens through these streams, which are managed by the OS.

> [!NOTE]
> **Analogy:**
> Water flowing through a pipe: the reservoir is the disk, and the faucet is your program. Turning on the faucet (requesting the stream) lets data flow in or out.

---

### c) File Descriptor Table

* Every time a program opens a file, the OS gives it an **ID number** (file descriptor).
* The OS keeps a **table** to track:

  * Which files are open
  * Where each file’s read/write position is
  * What permissions the program has
  * Which program the file belongs to

If a file isn’t properly closed, the OS still keeps it in the table temporarily until it’s released, this prevents file corruption.

> [!NOTE]
> **Analogy:**
> A waiter keeps an order ticket for each table, so the kitchen knows which food belongs to which customer. When the meal is done (file closed), the ticket is removed.

---

## 6. Example of the Entire File Flow

### Reading (loadStrings):

1. Sketch requests the file → `loadStrings("scores.txt")`
2. OS finds file on disk
3. OS opens the file and assigns a file descriptor
4. Data moves: **Disk → OS → Buffer → Sketch**
5. Sketch processes the data, then the OS closes the file

### Writing (saveStrings):

1. Sketch sends data → `saveStrings(scores, "scores.txt")`
2. OS receives data and may buffer it
3. OS writes the buffered data to the file
4. Data moves: **Sketch → Buffer → OS → Disk**
5. The OS updates the file descriptor table to mark the file as closed

> [!TIP]
> These steps happen quickly, but they always follow this logical order. Even in p5.js, the browser communicates through the OS using this process.

---

## 7. Summary Table

| Concept                                | Description                                        | Example / Analogy                     |
| -------------------------------------- | -------------------------------------------------- | ------------------------------------- |
| **Client**                             | Program requesting file access                     | p5.js sketch                          |
| **Server**                             | Operating system managing access                   | Windows, macOS, Linux                 |
| **Access to storage**                  | Program requests OS to read/write                  | `loadStrings()` / `saveStrings()`     |
| **File buffer**                        | Temporary RAM space for file data                  | A tray holding multiple plates        |
| **Data stream**                        | Pipeline for data in/out of program                | Water pipe carrying data              |
| **File descriptor table**              | OS list tracking open files                        | Waiter’s ticket system                |
| **Async load (`await loadStrings()`)** | OS loads file in background, sketch waits for data | Like waiting for your order to arrive |

# Operating System Process & Thread-Based File Analyzer

This project was developed using the C programming language and the POSIX `pthreads` library as a midterm assignment for the Operating Systems course at university.

It demonstrates the use of **process creation, multithreading, synchronization, and shared memory** to efficiently analyze a directory structure.

---

## Project Overview

The program takes a directory path as input and recursively analyzes its structure using a hybrid concurrency model:

- **Processes** are created for first-level subdirectories
- **Threads** are created for nested subdirectories
- Each thread/process performs file system analysis in parallel

This design improves performance by distributing workload across multiple execution units.

---

## Key Features

### File System Analysis
The program performs the following operations:

- Counts total number of files
- Identifies the largest file (name and path)
- Identifies the smallest file (name and path)
- Categorizes files by type (e.g., PDF, TXT, PPTX, etc.)
- Counts number of files per file type

---

## Concurrency Model

### Process-Level Parallelism
- Each first-level subdirectory is handled by a separate process
- Enables isolation and parallel execution at the directory level

### Thread-Level Parallelism
- Subdirectories inside each process are handled using threads
- Improves performance for deeper directory traversal

---

## Synchronization & Shared Memory

To ensure correct results across concurrent execution units, the project uses:

- Synchronization mechanisms to prevent race conditions
- Shared memory for aggregating results from processes and threads
- Safe updates to global statistics (file counts, size comparisons, etc.)

---

## Technologies Used

- C Language
- POSIX Threads (`pthreads`)
- Process management (fork)
- Shared memory mechanisms
- Linux file system APIs

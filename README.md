# Inverted Search in C

## Overview

Inverted Search is a C-based application that implements an inverted indexing system to efficiently search for words across multiple text files.

Instead of scanning every file whenever a search is performed, the program creates an inverted index that maps each word to the files in which it appears, along with its occurrence count.

The project uses **Hash Tables and Linked Lists** to organize and retrieve data efficiently, demonstrating how basic search engine indexing works.

## Features

- **File Validation:** Validates input files based on file extension, existence, duplicate entries, and empty files.
- **Create Database:** Builds an inverted index by reading words from multiple text files.
- **Display Database:** Displays indexed words along with their hash index, file count, filenames, and word frequencies.
- **Search Database:** Searches for a specific word and displays the files containing it along with its occurrence count.
- **Save Database:** Saves the generated database into a `.txt` file for future use.
- **Update Database:** Loads an existing database from a backup file and incorporates additional input files.
- **Dynamic Memory Allocation:** Creates main nodes and sub nodes dynamically as the database grows.

## Data Structures Used

| Data Structure | Purpose |
|---|---|
| Hash Table | Stores words based on the index calculated from their first character. |
| Main Linked List | Stores words belonging to the same hash index. |
| Sub Linked List | Stores filenames and the occurrence count of each word in those files. |
| File Linked List | Maintains the list of validated input files. |
| Structures | Organize word information, file information, and their relationships. |

### How the Inverted Index Works

The database uses a hash table of 27 indexes:

- Index `0–25` represents the letters `a–z`.
- Index `26` is reserved for characters that do not fall within these ranges.

Each hash index points to a linked list of main nodes. Every main node stores a word and points to a sub linked list containing filenames and word counts.

For example, if the word `hello` occurs in three files, the database stores:

| Word | File Count | Filename | Word Count |
|---|---:|---|---:|
| hello | 3 | file1.txt | 2 |
| hello | 3 | file2.txt | 1 |
| hello | 3 | file3.txt | 4 |

This allows the program to retrieve the files containing a particular word without scanning all the original files again.

## Project Structure

| File | Description |
|---|---|
| `main.c` | Entry point of the application and initializes the hash table and file linked list. |
| `inv_search.c` | Handles initial file validation, program initialization, and menu operations. |
| `inv_search.h` | Contains function declarations used throughout the project. |
| `main_functions.c` | Implements database creation, searching, displaying, saving, and updating operations. |
| `types.h` | Defines structures, constants, and status enumerations. |
| `file1.txt` | Sample input text file. |
| `file2.txt` | Sample input text file. |
| `file3.txt` | Sample input text file. |
| `database.txt` | Sample database file used for storing indexed information. |

## Compilation and Execution

### 1. Clone the Repository

```bash
git clone https://github.com/Aditya-73619/Inverted-Search.git
```

### 2. Navigate to the Project Directory

```bash
cd Inverted-Search
```

### 3. Compile the Project

```bash
gcc main.c inv_search.c main_functions.c -o inverted_search
```

### 4. Run the Application

```bash
./inverted_search file1.txt file2.txt file3.txt
```

You can also provide your own `.txt` files as command-line arguments.

## Menu Options

After successful file validation, the program displays the following menu:

| Option | Operation | Description |
|---|---|---|
| 1 | Create Database | Creates the inverted index from the validated input files. |
| 2 | Display Database | Displays all indexed words and their corresponding file information. |
| 3 | Search Database | Searches for a word and displays its file occurrences. |
| 4 | Update Database | Loads an existing database and incorporates remaining input files. |
| 5 | Save Database | Saves the current database into a `.txt` file. |
| 6 | Exit | Terminates the application. |

## Sample Search Output

For example, if the word `hello` occurs in multiple input files, searching for it displays the number of files containing the word and its occurrence count in each file.

```text
Enter the word to search: hello

Word hello is present in 3 files

In file1.txt -> 2 times
In file2.txt -> 1 times
In file3.txt -> 4 times
```

*The above is an illustrative example of the search output.*

## Database Storage Format

The application saves the database in a structured text format.

Each database entry contains:

- Hash table index
- Word
- Number of files containing the word
- Filename
- Word occurrence count in that file

Example:

```text
#7;hello;2;file1.txt;2;file2.txt;1;#
```

This format allows the program to reconstruct the indexed database during the update operation.

## Key Learning Outcomes

Through this project, I gained practical experience with:

- Implementation of Hash Tables.
- Singly Linked Lists and Nested Linked Lists.
- Dynamic Memory Allocation using `malloc()` and `free()`.
- File Handling in C.
- Command-Line Argument Validation.
- String Manipulation and Comparison.
- Efficient Searching and Data Organization.
- Database Creation, Storage, and Updating.
- Modular Programming in C.

---

## 👨‍💻 Author

**Aditya Gupta**

This project helped me strengthen my understanding of C programming, hash tables, linked lists, dynamic memory allocation, and file handling by implementing an inverted indexing system from scratch.

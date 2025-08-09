# 📜 minigrep

A simple command-line search tool written in Rust — inspired by the classic `grep` utility. It searches for a given word in a text file, prints all matching lines, and provides detailed statistics about the matches.

## 🚀 Features

* Search for a specific word in a file
* Prints all lines where the word is found
* Displays the **number of lines** containing the word
* Displays the **total number of occurrences** of the word
* Case-sensitive and case-insensitive search options
* Simple, fast, and built with Rust!

## 📦 Installation

### Prerequisites

Make sure you have Rust installed. If not, install it from [rustup.rs](https://rustup.rs/).

### Clone and Build

```bash
# Clone the repository
git clone https://github.com/yourusername/rust-minigrep.git
cd rust-minigrep

# Build the project
cargo build --release
```

## 🖥️ Usage

### Basic Usage

```bash
cargo run <query> <filename>
```

### Environment Variables

For case-insensitive search, set the `CASE_INSENSITIVE` environment variable:

```bash
# Case-insensitive search (Unix/Linux/macOS)
CASE_INSENSITIVE=1 cargo run <query> <filename>

# Case-insensitive search (Windows)
set CASE_INSENSITIVE=1 && cargo run <query> <filename>
```

### Examples

#### Example 1: Basic Search

Suppose `poem.txt` contains:
```
The sun shines bright.
The moon glows softly.
The stars twinkle in the night.
```

Run:
```bash
cargo run the poem.txt
```

**Output:**
```
Searching for the
In file poem.txt
The stars twinkle in the night.
Query the appeared 1 times in above 1 lines
```

#### Example 2: Case-Insensitive Search

```bash
CASE_INSENSITIVE=1 cargo run THE poem.txt
```

**Output:**
```
Searching for THE
In file poem.txt
The sun shines bright.
The moon glows softly.
The stars twinkle in the night.
Query THE appeared 3 times in above 3 lines
```

#### Example 3: No Matches Found

```bash
cargo run rainbow poem.txt
```

**Output:**
```
Searching for rainbow
In file poem.txt
Query rainbow appeared 0 times in above 0 lines
```

## ⚙️ Options & Behavior

* **Case-sensitive** by default (searches for exact case matches)
* **Case-insensitive** when `CASE_INSENSITIVE` environment variable is set
* Displays search parameters at the start (query and filename)
* Shows each matching line found in the file
* Reports total occurrences of the query and number of lines containing matches
* Supports any text file format
* Handles UTF-8 encoded files
* Graceful error handling for missing files or invalid arguments

## 📂 Project Structure

```
rust-minigrep/
├── src/
│   ├── main.rs          # CLI argument parsing, config setup & entry point
│   └── lib.rs           # Search logic, Config struct & core functionality
├── Cargo.toml           # Rust package configuration
├── Cargo.lock           # Dependency lock file
├── README.md            # Project documentation

```
## 📝 Error Handling

The application handles various error scenarios:

* **Missing arguments**: Shows "Problem passing arguments: not enought arguments!" and exits
* **File not found**: Shows "Application error: No such file or directory" and exits
* **Permission denied**: Shows "Application error: Permission denied" and exits
* **Invalid UTF-8**: Handles non-UTF-8 text files with appropriate error messages

## 👤 Author

**Lingaraj Patil** - [@Lingaraj-Patil](https://github.com/Lingaraj-Patil)

# 🏗️ ByteHawk: A Lightweight Linux Process Monitor
![Language](https://img.shields.io/badge/Language-C%2B%2B-blue?logo=c%2B%2B) ![Standard](https://img.shields.io/badge/C%2B%2B-11%2B-blueviolet?logo=c%2B%2B) ![OS](https://img.shields.io/badge/OS-Linux-black?logo=linux) ![Data Source](https://img.shields.io/badge/Data-%2Fproc-critical?logo=linux) ![Build](https://img.shields.io/badge/build-g%2B%2B-success?logo=gnu) ![Interface](https://img.shields.io/badge/Interface-Terminal-darkgreen?logo=gnubash) ![Kernel](https://img.shields.io/badge/Kernel-Linux%20Userspace-yellow?logo=linux) ![Monitoring](https://img.shields.io/badge/Type-System%20Monitor-red?logo=htop)

**ByteHawk** is a lightweight, terminal-based Linux system monitor written in **C++**, inspired by `top` and `htop` but intentionally kept simple for learning. It reads live system and process data from the **`/proc` filesystem** and displays it in the terminal, focusing on core C++ fundamentals rather than full feature parity.

## 🎯 Project Goals

- Learn core **C++ basics** through a real Linux system project
- Understand how Linux exposes system data via `/proc`
- Practice file I/O, strings, loops, structs/classes, and STL
- Build a live-updating terminal application

## 🛠 Tech Stack

- **Language:** C++
- **Platform:** Linux
- **Data Source:** `/proc` filesystem
- **Build Tool:** g++ / make (simple compilation)
- **Optional:** Python (only for offline log analysis)

## 📦 Requirements

- Linux system (any distro)
- g++ compiler (C++11 or later)
- Basic terminal knowledge
- No root access required ❌

## ✨ Features (Planned & Implemented)

| System Info                     | Process Info                     | UI                          |
|---------------------------------|----------------------------------|-----------------------------|
| Total & available memory        | List running processes           | Live terminal refresh       |
| CPU usage                       | PID & process name               | Simple text-based layout    |
| System uptime                   | Memory usage per process         | No ncurses (initially)      |
|                                 | Basic CPU usage per process      |                             |

## 🚫 Out of Scope (Intentionally)

To keep the project beginner-friendly, the following are **not included**:
- Killing processes
- Process tree view
- Kernel modules or hooks
- Root-only features
- Advanced TUI libraries (ncurses)

## 📂 Project Structure

```text
ByteHawk/
├── src/
│   ├── main.cpp
│   ├── proc_reader.cpp
│   ├── proc_reader.h
│   └── ui.cpp
├── include/
├── logs/
├── README.md
└── Makefile
```

## 📁 Project Structure Explanation

- **`src/`**  
  Contains all the C++ source code for ByteHawk.

  - **`main.cpp`**  
    Entry point of the program.  
    Handles program flow, refresh loop, and calls other modules.

  - **`proc_reader.cpp`**  
    Implements logic to read and parse system and process data from `/proc`.

  - **`proc_reader.h`**  
    Declares structs/classes and function prototypes used to read `/proc`.

  - **`ui.cpp`**  
    Handles terminal output and formatting of displayed data.

- **`include/`**  
  Reserved for future header files if the project grows.

- **`logs/`**  
    Stores optional logs or snapshots of system data for analysis or debugging.

- **`README.md`**  
  Project documentation, goals, and usage instructions.

- **`Makefile`**  
  Simplifies building the project using `make`.

## 🚀 How It Works (High Level)

- Reads system and process data from `/proc`
- Parses text files using standard C++ I/O
- Stores data using structs/classes
- Refreshes output in a loop to simulate live monitoring

## 🧠 Inspiration

- `top`
- `htop`
- Linux `/proc` documentation

## 📄 License

This project is licensed under **Apache License** for educational purposes. Free to use, modify, and learn from.

## 🧩 ASCII art
```
 /$$              /$$$$$$$              /$$               /$$   /$$                         /$$      
|  $$            | $$__  $$            | $$              | $$  | $$                        | $$      
 \  $$           | $$  \ $$ /$$   /$$ /$$$$$$    /$$$$$$ | $$  | $$  /$$$$$$  /$$  /$$  /$$| $$   /$$
  \  $$          | $$$$$$$ | $$  | $$|_  $$_/   /$$__  $$| $$$$$$$$ |____  $$| $$ | $$ | $$| $$  /$$/
   /$$/          | $$__  $$| $$  | $$  | $$    | $$$$$$$$| $$__  $$  /$$$$$$$| $$ | $$ | $$| $$$$$$/ 
  /$$/           | $$  \ $$| $$  | $$  | $$ /$$| $$_____/| $$  | $$ /$$__  $$| $$ | $$ | $$| $$_  $$ 
 /$$/            | $$$$$$$/|  $$$$$$$  |  $$$$/|  $$$$$$$| $$  | $$|  $$$$$$$|  $$$$$/$$$$/| $$ \  $$
|__//$$$$$$      |_______/  \____  $$   \___/   \_______/|__/  |__/ \_______/ \_____/\___/ |__/  \__/
   |______/                 /$$  | $$                                                                
                           |  $$$$$$/                                                                
                            \______/                                                                 

```


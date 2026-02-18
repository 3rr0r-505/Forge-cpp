# 🏗️ HawkPro: A Lightweight Linux Process Monitor
![Language](https://img.shields.io/badge/Language-C%2B%2B-blue?logo=c%2B%2B) ![Standard](https://img.shields.io/badge/C%2B%2B-11%2B-blueviolet?logo=c%2B%2B) ![OS](https://img.shields.io/badge/OS-Linux-black?logo=linux) ![Data Source](https://img.shields.io/badge/Data-%2Fproc-critical?logo=linux) ![Build](https://img.shields.io/badge/build-g%2B%2B-success?logo=gnu) ![Interface](https://img.shields.io/badge/Interface-Terminal-darkgreen?logo=gnubash) ![Kernel](https://img.shields.io/badge/Kernel-Linux%20Userspace-yellow?logo=linux) ![Monitoring](https://img.shields.io/badge/Type-System%20Monitor-red?logo=htop)

**HawkPro** is a lightweight, terminal-based Linux system monitor written in **C++**, inspired by `top` and `htop` but intentionally kept simple for learning. It reads live system and process data from the **`/proc` filesystem** and displays it in the terminal, focusing on core C++ fundamentals rather than full feature parity. [Link to 0xProject.md](https://github.com/3rr0r-505/Forge-CPP/blob/main/0xchk/0xProject.md)

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

## 📂 Project Structure

```text
hawkpro/
├── CMakeLists.txt
├── README.md
├── include/
│   ├── config.hpp        // constants (refresh=500ms, colors, limits)
│   ├── types.hpp         // structs (ProcessInfo, CpuSnapshot, etc.)
│   ├── system/
│   │   ├── cpu.hpp
│   │   ├── memory.hpp
│   │   ├── disk.hpp
│   │   ├── network.hpp
│   │   ├── uptime.hpp
│   │   └── os.hpp
│   ├── process/
│   │   ├── process.hpp
│   │   └── proc_reader.hpp
│   └── ui/
│       ├── screen.hpp    // ncurses init / shutdown
│       ├── layout.hpp    // sec1 / sec2 geometry
│       ├── header.hpp    // OS | HawkPro | Uptime
│       ├── table.hpp     // process table + sorting
│       └── input.hpp     // mouse + key handling
├── src/
│   ├── main.cpp          // main loop (500ms tick)
│   ├── system/
│   │   ├── cpu.cpp
│   │   ├── memory.cpp
│   │   ├── disk.cpp
│   │   ├── network.cpp
│   │   ├── uptime.cpp
│   │   └── os.cpp
│   ├── process/
│   │   ├── process.cpp
│   │   └── proc_reader.cpp
│   └── ui/
│       ├── screen.cpp
│       ├── layout.cpp
│       ├── header.cpp
│       ├── table.cpp
│       └── input.cpp
└── build/
```

## 🧩 UI Design
``` 
+-----------------------------------------------------------------------------------------------+
| os-release                           HawkPro                                           Uptime |
+-----------------------------------------------------------------------------------------------|
| CPU Info      | CPU Usage: <total %>  | Memory Usage: <total %> | Total Disk: < Disk Size> GB |
| Memory Info   | Sys: <Sys %>          | Size: <Mem size> GB     | Available: <Avail Disk> GB  |
| Disk Info     | User: <User %>        | Used: <Mem used> GB     | Network: <Net Mbps>         |
| #Tasks        | Idle: <CPU Idle %>    | Free: <Mem free> GB     | IP: <ip addr>               |
|===============================================================================================|
| PID      USER(sort)      %CPU(sort)   %MEM(sort)   STATE   TIME+     COMMAND                  |
| 1234     root            1.2          0.5          S       00:01     bash                     |
| 5678     user            2.5          1.0          R       00:12     vim                      |
| ...      ...             ...          ...          ...      ...      ...                      |
+-----------------------------------------------------------------------------------------------+

```


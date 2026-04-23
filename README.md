# Operating Systems Project - Linux

This workspace contains two distinct projects developed for an **Operating Systems (OS) course** focusing on **Linux systems**. The projects demonstrate key OS concepts including file system management and CPU scheduling algorithms.

## Project Overview
This workspace contains two distinct projects: a C-based File Management System and a Python-based Priority Scheduling Algorithm. Below is a detailed explanation of each project.

---

## 1. File Management System (file.c)

### Overview
A comprehensive command-line file management system written in C that provides role-based access control with three user types: **Admin**, **Moderator**, and **Player**. Each user type has different permissions and capabilities for managing files and directories.

### Features

#### Admin Features
- **Change Permissions**: Modify file/directory permissions using chmod (e.g., 755, 644)
- **Create Directory**: Create new directories with default permissions (0755)
- **Delete Files/Directories**: Remove files or directories from the system
- **Create Symbolic Links**: Create symbolic links pointing to target files
- **Copy Files**: Copy files from source to destination
- **Find Files**: Search for files matching a pattern using the find command
- **Create Files**: Create new empty files
- **Delete Files**: Delete specific files
- **Create Aliases**: Create shell aliases for frequently used commands (saved to ~/.bashrc)

#### Moderator Features
- **View File Content**: Display file contents using cat, head, or tail commands
- **Move Files**: Move or rename files from one location to another
- **Search in Files**: Search for keywords inside files using grep command

#### Player Features
- **List Files/Directories**: Display contents of a directory with detailed information
- **Create/Update Files**: Create new files or append content to existing files

### How It Works
1. The program presents a main menu where users select their user type
2. Based on selection, the appropriate menu is displayed
3. Users can perform operations specific to their role
4. System commands (chmod, cp, mv, grep, find, etc.) are executed through the system() function

### Technical Details
- **Language**: C
- **System Calls**: Uses POSIX functions like `mkdir()`, `remove()`, `symlink()`, `fopen()`, etc.
- **External Commands**: Leverages Unix/Linux commands (chmod, cp, mv, grep, find, ls)
- **Platform**: Linux/Unix-based systems (requires bash shell)

### Compilation
```bash
gcc -o file_manager file.c
```

### Usage
```bash
./file_manager
```

### Important Notes
- The program requires Unix/Linux environment
- The `create_alias()` function appends aliases to `~/.bashrc`
- Buffer sizes are defined for security (256-2048 characters)
- Error handling uses `perror()` for system error reporting

---

## 2. Priority Scheduling Algorithm (file.py)

### Overview
A Python implementation of the **Priority Scheduling (Preemptive)** CPU scheduling algorithm, commonly studied in Operating Systems. This program simulates how a CPU scheduler allocates processor time to multiple processes based on their priorities.

### What is Priority Scheduling?
Priority Scheduling is a CPU scheduling algorithm where:
- Each process is assigned a **priority level** (lower number = higher priority)
- The CPU allocates time to the **highest priority** process that is ready
- It is **preemptive**, meaning a higher priority process can interrupt a currently running lower priority process
- It minimizes response time for important tasks

### Features

#### Input Handling
- User enters the number of processes
- For each process, input:
  - **Arrival Time**: When the process arrives in the ready queue
  - **Burst Time**: How long the process needs CPU time
  - **Priority**: Priority level (lower value = higher priority)
- Input validation prevents non-integer entries

#### Algorithm Implementation
The `priority_scheduling_preemptive()` function:
1. Tracks remaining burst time for each process
2. At each time unit, selects the highest priority process that has arrived
3. Executes it for 1 time unit
4. Handles idle times when no process is ready
5. Calculates metrics for completed processes

#### Metrics Calculated
- **Waiting Time**: Total time a process spends waiting for CPU (before execution completes)
- **Turnaround Time**: Total time from arrival to completion
- **Response Time**: Time from arrival to first execution on CPU

#### Output
- Displays a formatted table of all processes with their metrics using tabulate
- Shows average waiting time, turnaround time, and response time
- Saves results to `scheduling_results.txt` file

### How It Works

1. **Process Collection**: Gather process information from user input
2. **Scheduling Simulation**: 
   - Track time progression
   - Find highest priority ready process
   - Execute for 1 time unit
   - Update process state
3. **Metrics Calculation**: Compute performance metrics
4. **Results Display**: Print and save results

### Technical Details
- **Language**: Python 3
- **Dependencies**: `tabulate` (for formatted table display)
- **Algorithm Type**: Preemptive Priority-based Scheduling
- **Time Complexity**: O(n²) where n is the number of processes

### Installation & Dependencies
```bash
pip install tabulate
```

### Usage
```bash
python file.py
```

### Example Interaction
```
Priority Scheduling (Preemptive)
Welcome,sir <3
Enter the number of processes: 3
------...------
Process 1:
------...------
Arrival time: 0
------...------
Burst time: 5
------...------
Priority (lower value = higher priority): 2
...
```

### Output Example
```
Scheduling Results:
╒════╤════════════════╤════════════╤══════════════╤════════════╤═══════════════╤═════════════════╕
│ id │   arrival_time │ burst_time │   priority   │ waiting_time │ turnaround_time │ response_time │
├────┼─────────────────┼────────────┼─────────────┼──────────────┼──────────────────┼────────────────┤
│ P1 │        0        │     5      │      2      │     0.00     │      5.00        │     0.00       │
...
─────────────────────────────────────────────────────────────────
Average Waiting Time: 2.33
Average Turnaround Time: 7.33
Average Response Time: 1.50
─────────────────────────────────────────────────────────────────
Results saved to scheduling_results.txt
```

### Algorithm Visualization
```
Process: P1 (Arr=0, Burst=5, Pri=2)
Process: P2 (Arr=1, Burst=3, Pri=1)  ← Higher priority
Process: P3 (Arr=2, Burst=2, Pri=3)

Execution Timeline:
Time: 0-1: P1 executes
Time: 1-4: P2 executes (preempts P1, higher priority)
Time: 4-6: P3 executes
Time: 6-10: P1 executes (completes)
```

### Bug Note
- Line at the end: `if name == "main":` should be `if __name__ == "__main__":` for proper Python script execution

---

## File Structure
```
d:\New folder\New folder\
├── file.c              # File Management System
├── file.py             # Priority Scheduling Algorithm
└── README.md           # This documentation
```

---

## Summary

This Operating Systems project explores two fundamental OS concepts:

| Aspect | file.c | file.py |
|--------|--------|---------|
| **OS Concept** | File System Management | CPU Process Scheduling |
| **Purpose** | File system management with role-based access control | CPU scheduling simulation |
| **Language** | C (POSIX/Linux) | Python |
| **Key Topics** | File permissions, system calls, user roles | Scheduling algorithms, preemption, process states |
| **Users/Processes** | Admin, Moderator, Player | Multiple concurrent processes |
| **Platform** | Linux/Unix | Cross-platform |
| **Dependencies** | POSIX Standard C Library | tabulate module |
| **Output** | Interactive CLI menu system | Scheduling metrics & Gantt chart data |

---

## Learning Objectives (OS Course)

### Concepts Demonstrated

#### file.c - File System & Process Management
- **POSIX System Calls**: mkdir(), remove(), symlink(), fopen()
- **File Permissions**: chmod and permission handling
- **User Roles & Access Control**: Role-based permission model
- **Process Execution**: system() calls for external command execution
- **File Operations**: Create, read, write, delete, move, copy
- **Shell Integration**: Alias creation in bashrc configuration

#### file.py - CPU Scheduling
- **Scheduling Algorithms**: Priority-based preemptive scheduling
- **Process States**: Ready, Running, Waiting, Completed
- **Scheduling Metrics**: 
  - Waiting Time (time in ready queue)
  - Turnaround Time (total process time)
  - Response Time (first execution delay)
- **Preemption**: Higher priority process can interrupt lower priority
- **Algorithm Analysis**: Time complexity and performance evaluation

---

## Notes & Recommendations

### For file.c:
- Consider adding error handling for buffer overflow protection
- Test on Unix/Linux systems before deployment
- The program assumes bash shell is available

### For file.py:
- Fix the main entry point: Change `if name == "main":` to `if __name__ == "__main__":`
- Add input validation for edge cases (negative times, zero burst time)
- Consider adding visualization of the Gantt chart for better understanding
- Import `tabulate` at the top of the file for proper module management

---

**Created**: April 2026  
**Author**: Project Documentation
#

# What is a goroutine?
- A goroutine is a green thread implementation
- While threads are managed by the kernel, green threads are in the user space and managed by the runtime library

# Green threads vs OS threads
- Goroutines have smaller memory footprints than threads
  - Experiment
    - Create 1,000,000 threads and 1,000,000 goroutines
    - C++ program to create a million threads allocated 8.2 GB
    - Go program to create a million goroutines allocated 3.3 GB
    - I tried 10,000,000 threads and goroutines. Go allocated 12.5 GB; C++ program crashed
    - https://github.com/MakotoE/goroutines-experiement
  - Useful for cloud computing: memory = $$
- Threads are typically slower in context switching
  - Threads have to restore many registers on context switch because they can be preemptively switched at any point
  - Goroutines have predetermined yield points for switching. They are designed so that it only has to restore three registers (PC, SP, and DX).
  - https://riteeksrivastava.medium.com/a-complete-journey-with-goroutines-8472630c7f5c
- Goroutines are basically lightweight threads

# Where goroutines can yield
- System calls and timers, just like threads
  - `os.Open("file")`
- Channel operations
  - https://stackoverflow.com/questions/10095751/understanding-goroutines
- Function calls and loops
  - Prevent long-running functions from deadlocking the scheduler
  - https://go.dev/doc/go1.14#runtime

# Creating a goroutine


# Passing information

# CPU Scheduling Algorithms

This project implements a variety of CPU scheduling algorithms in C++ to simulate process scheduling in operating systems. The included algorithms are First Come First Serve (FCFS), Round Robin (RR) with variable quantum, Shortest Process Next (SPN), Shortest Remaining Time (SRT), Highest Response Ratio Next (HRRN), Feedback (FB), Feedback with varying time quantum (FBV), and Aging. Each algorithm is designed to address specific scheduling needs, balancing factors like fairness, efficiency, and responsiveness.

## Table of Contents
- [Algorithms](#algorithms)
- [Installation](#installation)
- [Input Format](#input-format)
- [Contributors](#contributors)

## Algorithms

1. **First Come First Serve (FCFS)**  
   A non-preemptive algorithm where processes are executed in the order they arrive. Simple to implement but may lead to long waiting times for short processes if a long process arrives first. Best suited for batch systems where process order matters.

2. **Round Robin (RR)**  
   A preemptive algorithm that allocates a time slice (quantum) to each process, with the quantum size configurable. Processes are cycled through a queue, reducing starvation and improving responsiveness for systems with mixed process lengths.

3. **Shortest Process Next (SPN)**  
   A non-preemptive algorithm that prioritizes processes with the shortest burst time. It minimizes average waiting time but may delay longer processes, leading to potential starvation for them.

4. **Shortest Remaining Time (SRT)**  
   A preemptive version of SPN, prioritizing processes with the shortest remaining execution time. It adapts dynamically to new arrivals, making it ideal for systems where burst times are unpredictable.

5. **Highest Response Ratio Next (HRRN)**  
   A non-preemptive algorithm that prioritizes processes based on their response ratio (waiting time divided by burst time). It balances fairness by favoring processes that have waited longer relative to their burst time.

6. **Feedback (FB)**  
   A preemptive algorithm using multiple priority queues. Higher-priority processes are executed first, and completed processes move to lower-priority queues. Suitable for systems with diverse process priorities.

7. **Feedback with Varying Time Quantum (FBV)**  
   Similar to FB but assigns different time quanta to each priority queue, optimizing CPU allocation by giving more time to higher-priority processes and less to lower-priority ones.

8. **Aging**  
   Prevents starvation in systems like Xinu by incrementing the priority of ready processes over time. The highest-priority process is selected for execution, with round-robin scheduling for equal priorities. Ensures all processes eventually get CPU time.

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   ```
2. Install g++ compiler and make:
   ```bash
   sudo apt-get install g++ make
   ```
3. Compile the code:
   ```bash
   make
   ```
4. Run the executable:
   ```bash
   ./<executable-name>
   ```

## Input Format

The input file follows a structured format to specify simulation details:

- **Line 1**: Mode of operation ("trace" for detailed execution timeline or "stats" for summary statistics).
- **Line 2**: Comma-separated list of algorithms to simulate, with parameters where applicable. Each algorithm is represented by a number:
  - 1: FCFS
  - 2: RR (e.g., `2-4` for quantum=4)
  - 3: SPN
  - 4: SRT
  - 5: HRRN
  - 6: FB (q=1 for all queues)
  - 7: FB (q=2^i for queue i)
  - 8: Aging (e.g., `8-1` for quantum=1)
- **Line 3**: Integer specifying the last time instant for the simulation.
- **Line 4**: Integer specifying the number of processes to simulate.
- **Line 5 onwards**: Process details, one per line:
  - For algorithms 1–7: `name,arrival_time,service_time` (e.g., `P1,0,5` for process P1 arriving at time 0 with 5 units of service time).
  - For Aging (algorithm 8): `name,arrival_time,priority` (e.g., `P1,0,3` for process P1 arriving at time 0 with priority 3).
  - Processes must be sorted by arrival time. If two processes have the same arrival time, the one with lower priority is assumed to arrive first.

## Contributors

Contributions are welcome! Feel free to submit pull requests, report issues, or suggest improvements to enhance the project. For major changes, please open an issue to discuss your ideas first.
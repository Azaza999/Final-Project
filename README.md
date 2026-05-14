# Final-Project
Final project for CIS 345
# xv6 Lottery Scheduler
**Author:** Pamela E. Duran

## Overview
This project implements a randomized Lottery Scheduler in the xv6 operating system. It replaces the default Round-Robin scheduler and includes a custom Linear Congruential Generator (LCG) for randomness.

## Modified Files
*   `kernel/proc.h`: Added `tickets` to the `proc` structure.
*   `kernel/proc.c`: Implemented `random()`, updated `allocproc()` to inherit tickets, and rewrote `scheduler()` to use a two-pass lottery system.
*   `kernel/sysproc.c`: Added the logic for `sys_settickets` and `sys_getpinfo`.
*   `kernel/syscall.c` & `kernel/syscall.h`: Routed the new system calls (Assigned to unused SYS_ numbers).
*   `user/user.h` & `user/usys.pl`: Added user-space prototypes and assembly routing.
*   `Makefile`: Added `$U/_lotterytest\` to `UPROGS`.

## New Files
*   `kernel/pstat.h`: Defines the statistics structure.
*   `user/lotterytest.c`: User-space program that forks 3 children with a 30:20:10 ticket ratio.

## How to Test
1. Run `make CPUS=1 qemu` (A single CPU is required to create the bottleneck for the scheduler).
2. Run `lotterytest` in the xv6 shell.

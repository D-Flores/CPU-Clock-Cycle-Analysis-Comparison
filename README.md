# CPU-Clock-Cycle-Analysis-Comparison
Brief comparison between some tools used to analyze CPU Clock Cycles

# DTrace [(dtrace4linux)](https://github.com/dtrace4linux/linux)
At first, DTrace seems like a viable option to use for measuring Clock Cycles. However, there are a number of major issues that immediately become apparent when trying to use it. To start off with, it wasn't originally designed to be used for Linux operating systems. Someone has attempted to single-handedly port the tool to Linux systems (linked above), but with only limited success. This is because, even though DTrace itself is now usable on Linux, most of the scripts needed to actually perform any analytical task have not been adapted to run on Linux. Also, after spending several hours searching across the internet, it appears that DTrace can't be used to measure CPU clock cycles, as no scripts could be found (adapted for Linux or otherwise) that were made to perform such a task.

Conclusion: DTrace may be usable, but it's likely that it will require a lot of work and patience in order to even get it fully operational in the first place.

# perf
In contrast to DTrace, perf actually seems to be the perfect tool for measuring CPU Clock Cycles. There's only one significant problem.
![My image](http://i.imgur.com/UYnGXZv.png?1)

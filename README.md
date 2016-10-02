# CPU-Clock-Cycle-Analysis-Comparison
Brief comparison between some tools used to analyze CPU Clock Cycles

# DTrace [(dtrace4linux)](https://github.com/dtrace4linux/linux)
At first, DTrace seems like a viable option to use for measuring Clock Cycles. However, there are a number of major issues that immediately become apparent when trying to use it. To start off with, it wasn't originally designed to be used for Linux operating systems. Someone has attempted to single-handedly port the tool to Linux systems (linked above), but with only limited success. This is because, even though DTrace itself is now usable on Linux, most of the scripts needed to actually perform any analytical task have not been adapted to run on Linux. Also, after spending several hours searching across the internet, it appears that DTrace can't be used to measure CPU clock cycles, as no scripts could be found (adapted for Linux or otherwise) that were made to perform such a task.

Conclusion: DTrace may be usable, but it's likely that it will require a lot of work and patience in order to even get it fully operational in the first place.

# perf
In contrast to DTrace, perf actually seems to be the perfect tool for measuring CPU Clock Cycles. As can be seen in the image below, it specifically counts Cycles by default whenever perf is run. There's only one significant problem.

![My image](http://i.imgur.com/UYnGXZv.png?1)

Perf appears to use the Hardware Performance Measuring Counters (HW PMCs) built into Linux systems. The virtual machine being used for all of the relevant experiments does not support HW PMCs. Because of this, perf can't function properly, explaining why it reports 0 cycles for the program it was asked to analyze.

Conclusion: Perf really is the perfect tool designed to measure CPU Clock Cycles. It's just really unfortunate that the used virtual machine doesn't fully support it. Of the two, this is definitely the one I would prefer using, but it'll also probably take a fair bit of work to get fully operational.

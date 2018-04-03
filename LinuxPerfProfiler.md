
## This file includes the details about linux performance profiler.

### Installation
`uname -r` <br /> 
`sudo apt install linux-tools-common` <br />
`perf list` <br />
`sudo apt-get install linux-tools-4.13.0-32-generic` <br />
`sudo apt-get install linux-cloud-tools-4.13.0-32-generic` <br />


### Reading

http://sandsoftwaresound.net/perf/perf-tutorial-hot-spots/ <br />
This link provides very good understanding of how perf tool works, how to generate 
report. 

https://perf.wiki.kernel.org/index.php/Tutorial <br />
This is official wiki page. It gives details of all the commands in perf.

https://fedoramagazine.org/performance-profiling-perf/ <br />
This document specifically talks about the overhead.

### Execution

Use the following file for execution. <br />
https://github.com/amanmaldar/Apriori/blob/master/fileGen.cpp

Compilation with gdb. We need symbol table as well. <br />
`g++ -std=c++11 -ggdb fileGen.cpp -o fileGen.o`

This command automatically creates default file perf.data <br />
`sudo perf record -e cpu-clock,faults ./fileGen.o`  <br />
`perf report` 

### Processor-wide mode
In per-cpu mode, samples are recorded from all threads running on the monitored CPUs. 
As as result, samples from many different processes may be collected. For instance, if we monitor across all CPUs for 5s: <br />
`perf record -a sleep 5` <br />
`perf report` <br />
`perf report --sort=cpu` <br />





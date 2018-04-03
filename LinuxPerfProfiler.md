
## This file includes the details about linux performance profiler.

### Installation
`uname -r` <br /> 
`sudo apt install linux-tools-common` <br />
`perf list` <br />
`sudo apt-get install linux-tools-4.13.0-32-generic` <br />
`sudo apt-get install linux-cloud-tools-4.13.0-32-generic` <br />


### Reading

Excellent Presentation to start with! <br />
https://events.static.linuxfound.org/sites/events/files/slides/ELCE%20-%20fighting%20latency.pdf

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


See the default setting <br />
`sudo perf evlist -F`
cpu-clock: sample_freq=4000 <br />
faults: sample_freq=4000


L1-dcache-loads 
There are no counter for above event. It is not supported by Intel. No performance measurement possible.

`sudo perf stat -e LLC-loads,LLC-load-misses,LLC-stores,LLC-prefetches ./linuxPerf`

sum = 150012 <br />

 Performance counter stats for './linuxPerf': <br />
 
 <not supported>      LLC-loads <br />
 <not supported>      LLC-load-misses <br />
 <not supported>      LLC-stores <br />
 <not supported>      LLC-prefetches <br />

  31.516254703 seconds time elapsed <br />



### Processor-wide mode
In per-cpu mode, samples are recorded from all threads running on the monitored CPUs. 
As as result, samples from many different processes may be collected. For instance, if we monitor across all CPUs for 5s: <br />
`perf record -a sleep 5` <br />
`perf report` <br />
`perf report --sort=cpu` <br />





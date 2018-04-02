
## This file includes the details about linux performance profiler.

### Installation
`uname -r`
`sudo apt install linux-tools-common`
`perf list`
`sudo apt-get install linux-tools-4.13.0-32-generic`
`sudo apt-get install linux-cloud-tools-4.13.0-32-generic`


### Reading

http://sandsoftwaresound.net/perf/perf-tutorial-hot-spots/ <br />
This link provides very good understanding of how perf tool works, how to generate 
report. 

https://perf.wiki.kernel.org/index.php/Tutorial <br />
This is official wiki page. It gives details of all the commands in perf.


### Execution

Use the following file for execution. <br />
https://github.com/amanmaldar/Apriori/blob/master/fileGen.cpp

Compilation with gdb. We need symbol table as well. <br />
`g++ -std=c++11 -ggdb fileGen.cpp -o fileGen.o`

`sudo perf record -e cpu-clock,faults ./fileGen.o` <br />
This command automatically creates default file perf.data




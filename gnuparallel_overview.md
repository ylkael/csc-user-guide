# GNU Parallel

[GNU Parallel](https://www.gnu.org/software/parallel/) is a open-source 
shell utility for executing jobs in parallel in single node.

The use GNU Parallel for jobs that contains many similar tasks whose  execution order 
irrelevant.

## Strengths of GNU Parallel:

* No databases or persistent manager process
* Easily scales to a very large number of tasks
* Efficient use of scheduler resources

## Disadvantages of GNU Parallel:

* User is required to do careful organization of input and output files
* Scaling up requires consideration of system I/O performance
* Modest familiarity with bash scripting recommended

## Supported with caveats

* When using multiple nodes ...

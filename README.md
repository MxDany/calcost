# calcost
Use linux ps and top command to calculate the average of process CPU and RSS.
# usage
```
Usage: $0 [-p pid]/[-c cmd] <-t interval> <-n times>
    Use top/ps command to calculate CPU and RSS and its average value.

    -p    The PID of the specified process, Prohibit use with -c.
    -c    The CMD of the specified process, Prohibit use with -p.
    -t    Optional parameters, Use it to specify the scan time interval, the
          default time is $time_ival seconds.
    -n    Optional parameters, Use it to specify the number of averaging times,
          The default number is 0, which indicates an infinite loop.
          When using Ctrl-C(SIGINT,2) to stop the script from running, it will 
          use the current number of executions to calculate the average.
    -h    display this help and exit.
```
# Example
Real-time monitoring of CPU and RSS consumption of a processes.
```
./calcost -c sshd
```

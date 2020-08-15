# calcost

`calcost` is a process resource(RSS/CPU) monitoring and averaging shell tool.

`calcost` use Linux `ps` and `top` command to monitor the resource consumption of a process, and then calculate the average value of CPU and RSS during this period.

# usage

```shell
Usage: ./calcost [-p pid]/[-c cmd] <-t interval> <-n times>
    Use top/ps command to calculate CPU and RSS and its average value.

    -p    The PID of the specified process, Prohibit use with -c.
    -c    The CMD of the specified process, Prohibit use with -p.
    -t    Optional parameters, Use it to specify the scan time interval, the
          default time is 2 seconds.
    -n    Optional parameters, Use it to specify the number of averaging times,
          The default number is 0, which indicates an infinite loop.
          When using Ctrl-C(SIGINT,2) to stop the script from running, it will 
          use the current number of executions to calculate the average.
    -h    display this help and exit.
```
# Example

## Real-time monitoring

Real-time monitoring of CPU and RSS consumption of a processes.

```shell
./calcost -c sshd
```

- If multiple processes are found by command name, then you need to select one process.

  As below, 3 processes were found according to `sshd`, I chose the first one.

- It will loop forever to display current CPU and RSS.

- And you can press keyboard CTRL-C(or send a SIGINT signal to `calcost`) to stop monitoring at any time, it will calculate the recorded CPU/RSS average.

  As below, I used ctrl-c to stop the monitoring, and it calculated the average of 2 times.

![](https://github.com/MxDany/calcost/blob/master/assets/usage01.png)

Or you can directly specify the process by PID. 

```shell
./calcost -c 858
```

![](https://github.com/MxDany/calcost/blob/master/assets/usage02.png)

## Average calculation

You can specify the number of cycles to calculate the average of CPU and RSS. Used to indicate the resource consumption of a process over a period of time.

```shell
./calcost -c sshd -t 1 -n 3
```

- It will loop 3 times at an interval of 1 second, then stop monitoring, and then calculate the average of CPU and RSS.

![](https://github.com/MxDany/calcost/blob/master/assets/usage03.png)

Or you can directly specify the process by PID. 

```shell
./calcost -c 858 -t 1 -n 3
```


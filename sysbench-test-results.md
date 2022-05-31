# Testing Details

- 4 threads
- 10 tables
- 250,000 table size
- 5 mins

## Test One

***Simple my.cnf with no tweeks.***

```text
SQL statistics:
    queries performed:
        read:                            83776
        write:                           23908
        other:                           20
        total:                           107704
    transactions:                        5976   (19.90 per sec.)
    queries:                             107704 (358.74 per sec.)
    ignored errors:                      8      (0.03 per sec.)
    reconnects:                          0      (0.00 per sec.)

General statistics:
    total time:                          300.2241s
    total number of events:              5976

Latency (ms):
         min:                                   65.95
         avg:                                  200.91
         max:                                 2390.26
         95th percentile:                      404.61
         sum:                              1200658.44

Threads fairness:
    events (avg/stddev):           1494.0000/10.46
    execution time (avg/stddev):   300.1646/0.04

real    5m0.371s
user    0m10.805s
sys     0m22.938s
```

## Test Two

***Following tweeks.***

- table_open_cache=500
- thread_cache_size=16
  
```test
SQL statistics:
    queries performed:
        read:                            87850
        write:                           25075
        other:                           17
        total:                           112942
    transactions:                        6267   (20.88 per sec.)
    queries:                             112942 (376.29 per sec.)
    ignored errors:                      8      (0.03 per sec.)
    reconnects:                          0      (0.00 per sec.)

General statistics:
    total time:                          300.1468s
    total number of events:              6267

Latency (ms):
         min:                                   66.13
         avg:                                  191.51
         max:                                 1718.87
         95th percentile:                      390.30
         sum:                              1200176.64

Threads fairness:
    events (avg/stddev):           1566.7500/23.66
    execution time (avg/stddev):   300.0442/0.05


real    5m2.219s
user    0m10.961s
sys     0m24.595s

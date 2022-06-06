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
        read:                            136388
        write:                           38922
        other:                           35
        total:                           175345
    transactions:                        9731   (32.40 per sec.)
    queries:                             175345 (583.91 per sec.)
    ignored errors:                      11     (0.04 per sec.)
    reconnects:                          0      (0.00 per sec.)

General statistics:
    total time:                          300.2848s
    total number of events:              9731

Latency (ms):
         min:                                   49.10
         avg:                                  123.36
         max:                                  731.66
         95th percentile:                      308.84
         sum:                              1200431.61

Threads fairness:
    events (avg/stddev):           2432.7500/21.70
    execution time (avg/stddev):   300.1079/0.09

real    5m0.447s
user    0m9.112s
sys     0m19.824s
```

## Test Two

***Following tweeks.***

- table_open_cache=500
- innodb-io-capacity=2000
- innodb-io-capacity-max=3000
- max_allowed_packet = 64M
- thread_cache_size=32
- open_files_limit=1000
- table_open_cache=1000
  
```test
SQL statistics:
    queries performed:
        read:                            137732
        write:                           39308
        other:                           35
        total:                           177075
    transactions:                        9829   (32.74 per sec.)
    queries:                             177075 (589.92 per sec.)
    ignored errors:                      9      (0.03 per sec.)
    reconnects:                          0      (0.00 per sec.)

General statistics:
    total time:                          300.1594s
    total number of events:              9829

Latency (ms):
         min:                                   49.18
         avg:                                  122.13
         max:                                  584.05
         95th percentile:                      308.84
         sum:                              1200380.63

Threads fairness:
    events (avg/stddev):           2457.2500/9.96
    execution time (avg/stddev):   300.0952/0.03

real    5m0.301s
user    0m10.330s
sys     0m19.166s
```

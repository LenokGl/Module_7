<p> without cache </p>
lenok@WIN-2IDRRNTM3EJ:~$ wrk -d 10 -t 10 -c 10 --latency -s ./get.lua http://localhost:8081/ <br> 
Running 10s test @ http://localhost:8081/ <br> 
  10 threads and 10 connections <br> 
  Thread Stats   Avg      Stdev     Max   +/- Stdev <br> 
    Latency    61.27ms  114.19ms 753.61ms   91.79% <br> 
    Req/Sec    33.94     18.47    80.00     71.29% <br> 
  Latency Distribution <br> 
     50%   25.21ms <br> 
     75%   43.45ms <br> 
     90%  125.66ms <br> 
     99%  644.21ms <br> 
  1842 requests in 10.06s, 277.02KB read <br> 
  Socket errors: connect 0, read 0, write 0, timeout 10 <br> 
  Non-2xx or 3xx responses: 1842 <br> 
Requests/sec:    183.02 <br> 
Transfer/sec:     27.52KB <br> 

<p> with cache </p>
lenok@WIN-2IDRRNTM3EJ:~$ wrk -d 10 -t 10 -c 10 --latency -s ./get.lua http://localhost:8082/ <br>
Running 10s test @ http://localhost:8082/ <br>
  10 threads and 10 connections <br>
  Thread Stats   Avg      Stdev     Max   +/- Stdev <br>
    Latency    82.41ms  166.38ms 932.33ms   90.50% <br>
    Req/Sec    37.36     17.35   101.00     62.52% <br>
  Latency Distribution <br>
     50%   24.80ms <br>
     75%   43.03ms <br>
     90%  230.58ms <br>
     99%  819.83ms <br>
  3099 requests in 10.18s, 466.06KB read <br>
  Non-2xx or 3xx responses: 3099 <br>
Requests/sec:    304.27 <br>
Transfer/sec:     45.76KB <br>

Даже при слабых аппаратных ресурсах производительность MongoDb  <br>
превыщает MariaDB. Но организация кэша при отсутствии достаточных  <br>
аппаратных ресурсов не приносит резкого взлета производительности <br>
для обоих БД.  <br>
Результаты для MariaDB на аналогичных данных ниже.  <br>

<p> without cache </p>
Running 1m test @ http://localhost:8081/
  10 threads and 10 connections <br>
  Thread Stats   Avg      Stdev     Max   +/- Stdev <br>
    Latency   126.24ms  234.79ms   1.76s    90.57% <br>
    Req/Sec    21.57     13.18    60.00     67.48% <br>
  Latency Distribution <br>
     50%   43.32ms <br>
     75%   85.25ms <br>
     90%  343.01ms <br>
     99%    1.27s <br>
  8197 requests in 1.00m, 1.20MB read <br>
  Socket errors: connect 0, read 3, write 0, timeout 30 <br>
  Non-2xx or 3xx responses: 8197 <br>
Requests/sec:    136.47 <br>
Transfer/sec:     20.52KB <br>

<p> with cache </p>
Running 1m test @ http://localhost:8082/
  10 threads and 10 connections <br>
  Thread Stats   Avg      Stdev     Max   +/- Stdev <br>
    Latency    44.21ms   28.95ms 250.46ms   84.83% <br>
    Req/Sec    24.69     10.09    70.00     71.51% <br>
  Latency Distribution <br>
     50%   37.80ms <br> 
     75%   52.24ms <br>
     90%   72.18ms <br>
     99%  162.84ms <br>
  14603 requests in 1.00m, 2.14MB read <br>
  Non-2xx or 3xx responses: 14603 <br>
Requests/sec:    243.11 <br>
Transfer/sec:     36.56KB <br>


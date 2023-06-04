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

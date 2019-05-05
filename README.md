# EchoServer (IO vs NIO vs Netty)
Using NIO (non-blocking IO) we have less thread context switch,
so it scales much better than the traditional thread-per-request model.

## Test implementations
Ignore the first run to give time the JVM to warmup.
```sh
# run the implementaton (io, nio, nio2, netty)
mvn clean compile exec:java -Pnio2

# test the TCP connection (Ctrl+C to quit)
nc -v localhost 9090

# raise number of clients and observe how it scales
mvn clean compile exec:java -Pclient \
    -Dhost=localhost -Dport=9090 -Dnum=500
```

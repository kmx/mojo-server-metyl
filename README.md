Mojo-Server-Metyl
=================

Pure perl multi-threading webserver (based on ithreads) capable to run 
[Mojolicious](http://mojolicio.us/) applications.

**BEWARE:** it's just a proof of concept, implemented only as a demo!

**BEWARE:** it was tested with Mojolicious 3.42, however it is very likely
that it will not work with future versions as it uses a hack into Mojolicious 
internals (not via public API).

usage
-----

    usage: metyl [OPTIONS] [APPLICATION]
    
      metyl script/mojoapp
      metyl /path/to/mojoapp.pl
      metyl -a 127.0.0.1 -p 80 mojoapp.pl

    These options are available:
      -a, --address <ip>  Set IP adress you want to listen on (default: localhost)
      -p, --port <num>    Set port number you want to listen on (default: 3000)
      -w, --workers <num> Set number of worker threads (default: 4)

todo
----

1. Hooking up threading vehicle to mojo's ioloop via event handler
   _Mojo::Reactor::recurring(0.5 => {...})_ is a bit suboptimal, 
   perhaps having _Mojo::Reactor::idle_ can help.

2. There is no loadbalacning when assigning accepted sockets to 
   worker threads. Even worse the used algorithm is a bit stupid as
   the first free worker takes all sockets currently available in 
   the queue.

3. Veeery slow when used without keep-alive (bechmark by sri @ dualcore macbook):
   * with keep-alive: hypnotoad at 1800 rps, metyl at 1100 rps, daemon at 1000 rps
   * without keep-alive: hypnotoad at 1100 rps, metyl at 50 rps, daemon at 800 rps


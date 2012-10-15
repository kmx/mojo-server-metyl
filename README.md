Mojo-Server-Metyl
=================

Pure perl multi-threading webserver (based on ithreads) capable to run 
[Mojolicious](http://mojolicio.us/) applications.

**BEWARE:** it's just a proof of concept, implemented only as a demo!

**BEWARE:** it was tested with Mojolicious 3.47, however it is very likely
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
   _Mojo::Reactor::recurring(0.02 => {...})_ is a bit suboptimal.

2. SSL enabled Mojo apps are ignored

Qth Garbage Collector
=====================

A small commandline utility which finds Qth properties which are retained by
the MQTT server but which aren't registered with the Qth registrar.


Usage
-----

Create some example garbage properties:

    $ mosquitto_pub -t example/foo -m null -r
    $ mosquitto_pub -t example/bar -m null -r

To just list garbage without deleting it:

    $ qth_gc
    example/bar
    example/foo
    WARNING: Not removing garbage topics (add -r for this)

To delete the garbage:

    $ qth_gc -r
    example/bar
    example/foo
    Delete these topics?
      (y/N):y

Enjoy:

    $ qth_gc
    No garbage to delete.

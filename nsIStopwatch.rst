============
nsIStopwatch
============

`mailnews/base/public/nsIStopwatch.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIStopwatch.idl>`_

Simple stopwatch mechanism for determining the amount of wall-clock time and
CPU time (user + system) that has elapsed.  It is not fancy.  It is either
running or it is not.  If you want coherent cpu and real time values, then
you had better stop it first.  It does not keep counting when stopped,
although one could add a resumeRetroactive or something to accomplish that.

Properties
==========

cpuTimeSeconds
--------------

``readonly attribute double cpuTimeSeconds``

The total CPU time (user + system) in seconds accumulated between calls to
start/resume and stop.  You have to stop the stopwatch to cause this value
to update.

realTimeSeconds
---------------

``readonly attribute double realTimeSeconds``

The total wall clock time in seconds accumulated between calls to
start/resume and stop.  You have to stop the stopwatch to cause this value
to update.

Methods
=======

start
-----

``void start()``

Start the stopwatch; all counters are reset to zero.  If you want to
keep the already accumulated values, use resume instead.

stop
----

``void stop()``

Stop the stopwatch.

resume
------

``void resume()``

Resume the stopwatch without clearing the existing counters.  Any time
already accumulated on cpuTime/realTime will be kept.

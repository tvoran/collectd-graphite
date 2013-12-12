collectd/Graphite on Docker
===========================

This repository contains the sources to build a collectd_/Graphite_ Docker_
image. collectd is configured to receive metrics from the network and to store
them to Graphite.

If you have Docker installed, you can try it out with::

   docker build -t collectd-graphite . # from the root of this repository
   docker run -P collectd-graphite

Then, using ``docker ps``, write down which port has been assigned to collectd
and which one has been assigned to the web interface.

Install collectd using your favorite package manager, open ``collectd.conf`` and
add::

   <Plugin network>
   	Server "<your-docker-host>" "<the-port-in-docker-ps-likely-49153>"
   </Plugin>
   
Restart collectd and point your browser to *http://<your-docker-host->:<the-other-port-in-docker-ps>*,
and you should see the Graphite UI. By navigating in the tree on the left, you
can start to build your own graphs:

If you want to save configured graphs, you can login into graphite with the
username “graphite” and the password “admin” (you change that from the
graphite/mkadmin.py script).

.. _collectd: https://www.collectd.org/
.. _Graphite: http://graphite.readthedocs.org/en/latest/
.. _Docker: http://www.docker.io/

.. vim: set tw=80 spelllang=en spell:

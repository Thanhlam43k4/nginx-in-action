# nginx-in-action
Repository includes all the knowledge from basic to advanced about nginx server and many use cases of this high-performance serverfor devops engineers.

<img src = "./image.png" alt = "nginx imgage" width = "600">

## Overview

`Nginx` [engine x] is an HTTP and reverse proxy server, a mail proxy server, and a generic TCP/UDP proxy server, originally written by *Igor Syoev*. For a long time, it has been running on many heavily loaded Russian sites.



## Basic HTTP server features

- Serving static and index files, autoindexing; open file descriptor cache;
- Accelerated reverse proxying with caching; load balancing and fault tolerance
- SSL and TLS SNI supports


## Architecture and Scalability

- One master and serveral worker processes; worker processes run under an unprivileged user;
- Flexible configuration.
- Reconfiguration and upgrade of an executable without interruption of the client servicing.

## Beginner's Guide

- Nginx has one master process and several worker processes. The main purpose of the master process s to read and evaluate configuration, and maintain worker processes. Worker processes do actual processing of requests. Nginx employs event-based model and OS-dependent mechanisms to efficiently distribute requests among worker processes. The number of worker processes is defined in the configuration file and may be fixed for a given configuration or automatically adjusted to the number of available CPU cores.

- The way nginx and its modules work is determined in the configuration file. By default, the configuration file is named `nginx.conf` and placed in the directory `/etc/nginx`


***Starting, Stopping, and Reloading Configuration***

- To start nginx, run the executable file. Once nginx is started, it can be controlled by invoking the executable with the -s parameter. Use the following syntax:

        nginx -s signal

- Where signal may be one of the following:

    - stop — fast shutdown
    - quit — graceful shutdown
    - reload — reloading the configuration file
    - reopen — reopening the log files


- Serving Static Content

    - An important web server task is serving out files(such as images or static HTML pages).
    - Create the `data/www` directory and put an index.html file with any context into it and the `/data/images` directory and place some images in it.
    
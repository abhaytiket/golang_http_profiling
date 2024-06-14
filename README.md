# golang_http_profiling

## Overview

A very basic application for understanding profiling of a golang web application using [chi](https://go-chi.io/#/). For profiling we will be using [net/http/pprof](https://pkg.go.dev/net/http/pprof) package.

## Local setup

We have used [devcontainers](https://containers.dev/) for local setup. First make sure that you have [docker desktop](https://www.docker.com/products/docker-desktop/) and [vscode editor](https://code.visualstudio.com/) installed on your machine. Then clone this project on your machine and open this project in vscode. Use the option to `reopen this project in container` when a notification popup appears on your screen. After opening project inside development container run project using `Run -> Run without debugging` option from editor's menubar after opening `main.go` in your editor. 

## Profiling 

To do profiling open 2 terminals in your vscode editor and in one of them type following command
```
$ hey -z 10m http://127.0.0.1:8090/
```
Because of this command [hey](https://github.com/rakyll/hey) will run a load test for 10 minutes.

Now to collect the profiling data for heap use following command
```
$ go tool pprof http://localhost:6060/debug/pprof/heap
```
After running this command in a few seconds pprof will switch to interactive mode where you can run certain commands. One of the command is `png`. One of the command is `png` which will generate a `png` image for the profiling data.

To collect profiling data for cpu in a duration of 30 seconds use following command
```
$ go tool pprof http://localhost:6060/debug/pprof/profile?seconds=30
```
After running this command in a few seconds pprof will switch to interactive mode where you can run certain commands. One of the command is `png` which will generate a `png` image for the profiling data.

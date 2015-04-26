# onyx-metrics

Onyx Lifecycle plugin for instrumenting workflows. Track throughput and metrics of your tasks and log the output to Timbre and/or dashboard.

#### Installation

In your project file:

```clojure
[com.mdrogalis/onyx-metrics "0.6.0-SNAPSHOT"]
```

In your peer boot-up namespace:

```clojure
(:require [onyx.lifecycle.metrics.throughput]
          [onyx.lifecycle.metrics.latency]
          [onyx.lifecycle.metrics.timbre])
```

#### Lifecycle entries

##### Throughput

Computes throughput in terms of segments per second for 10s, 30s, and 60s windows.

```clojure
{:lifecycle/task :my-task-name
 :lifecycle/calls :onyx.lifecycle.metrics.throughput/calls
 :throughput/retention-ms 60000
 :lifecycle/doc "Instruments a task's throughput metrics"}
```

##### Batch Latency

Computes the 50th, 90th, and 99th percentile latency in milliseconds per batch of segments for 10s, 30s, and 60s windows.

```clojure
{:lifecycle/task :my-task-name
 :lifecycle/calls :onyx.lifecycle.metrics.latency/calls
 :latency/retention-ms 60000
 :lifecycle/doc "Instruments a task's latency metrics per batch"}
```

##### Timbre Logging

Logs all statistics collected to Timbre.

```clojure
{:lifecycle/task :my-task-name
 :lifecycle/calls :onyx.lifecycle.metrics.timbre/calls
 :timbre/interval-ms 2000
 :lifecycle/doc "Prints task metrics to Timbre every 2000 ms"}
```

## License

Copyright © 2015 Michael Drogalis

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.

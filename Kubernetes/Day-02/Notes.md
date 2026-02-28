Worker Node:
-----------
    Where Application Runs.
    => Worker node is where containers actually run.

1> Kubelet:
   --------
   What is Kubelet:
   ----------------
       A Node Agent.
       Runs on every worker node.
       communicates with Kube-apiservers.
       
  What Kubelet does:
  ------------------
      => Registers node to cluster.
      => watches for assigned pods.
      => Pulls container images.
      => Starts containers.
      => Monitors COntainers health.
      => Reports node & Pods Status.

Flow Examples:
--------------
    When Schedular assign a pod:
        1. API Server updates pod spoc.
        2. Kubelet sees assigned pod.
        3. Kubelet talks to container runtime.
        4. Container is started.

What happens if kubelet stops ?
-------------------------------
    . Node becomes notreads.
    . pods may stop responding.
    . control plane cannot manage the node properly.

2> Kube-proxy:
   -----------
    What is Kube-proxy:
    -------------------
    =>  Networking proxy running on each node.
    => Maintains Network rules.
    
   
what it does:
-------------
        => Manages networking rules.
        => Implements services.
        => Handles Load balancing.

Ex:-
---
     Service --> Forwatds traffic to correct Pod.

Uses:
-----
     . iptables (or) IPVS

How does service load balancing work internally ?
------------------------------------------------
    . Kube - proxy updates iptables/IPVS rules.
    . Traffic distributed among backend pods.


3> Container Runtime:
   ------------------
       . This Actually runs the container.

Ex:
---
    . Containerd
    . CRI - O

What container runtime does:
----------------------------
    . Pull Image
    . Creates Container
. starts Container
. Manages Container Lifecycle.






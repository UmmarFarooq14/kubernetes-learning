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
  
  
  

what is ReplicaSet:
-------------------
=> It explains how kubernetes maintains pods automatically.

Definition:
-----------
    . A ReplicaSet ensures that a specified number of pods replicas are running at all times.
    
With ReplicaSet:
----------------

    . Automatically recreates pods.
    . Maintains desired number of pods.
    . Ensures High Availability.

Structure:
----------
    ReplicaSet
        |
        |
    Managing Pods

ReplicaSet Uses:
----------------
    . Labels & selectors to identify pods.

Desired State vs Actual State:
------------------------------
Ex:
       You define:
         </> YAML
      replicas : 3
      
  => Desired state = 3 Pods.
     Now actual state:
     only 2 pods running
  => ReplicaSet detects mismatch and creates 1 new pod.
  This is called "Reconciliayion loop"

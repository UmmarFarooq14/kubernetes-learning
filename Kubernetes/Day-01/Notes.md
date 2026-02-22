Kubernetes:
-----------
    Kubernetes is a portable, extensible, Open-Source Platform for managing containerized workloads and services that facilities both declarative configuration and automation.
    => Before Containers 
        . Application run on physical servers.
        . Then came Virtual Machines.
        . Managing Large - scale distributedapps become complex.
    => Currently 1.8 version Role Based Access Control General Availability.
    => It mainly works with containers like Docker.

RBAC GA in Kubernetes:
----------------------
RBAC was:
---------
    . Introduced as Alpha {Experimental, may change}
    . Moved to Beta {Mostly Stable, minor changes possible}
    . Become a GA {Stable} in Kubernetes V1.8(2017)
   
    => It is mainly works with containers like Docker.
    . Deployment
    . Scaling
    . Networking
    . Self - Healing
    . Load Balancing

Kubernetes Architecture:
------------------------
    A Kubernetes cluster has two main parts:
    1) Control Plane {Master Node}
    2) Worker Nodes

1) Control Plane {Brain of the Cluster}:
   -------------------------------------
       The Control Plane  manages the ebtire cluster.
       It makes decisions & Manintains desired state.
   
       1) Kube-apiserver:
         ----------------
         what it is:
         -----------
             The entry point of the cluster.
   
         what it does:
        --------------
             Accept REST API requests.
             Authenticates & Authorizes users.
             Validates requests.
             updates etcd.
             Communications with all components.

       Ex:-
       ----
           When you run:
      Kunectl get pods.
      
       
   
         
        

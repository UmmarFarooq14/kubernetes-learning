First Understnad the Pods Properly:
-----------------------------------
    In Kubernetes:
    -------------
       . Application runs inside the pods.
       . Pods have IP address.
       . Pods IP's are temporary.

    Ex:-
    ---
    Pod1 ---> 10.244.0.5
    Pod2 ---> 10.244.0.6
    Pod3 ---> 10.244.0.7

    
    => Now Imagine Pod2 crashes.
    New Pod2 gets: 10.244.1.9 (Ip Changed)

    => So, If Someone was calling 10.22.0.6 it breaks.

    What if Pod Dies:
    -----------------
    If one Pod Crashes:
        . Kubernetes removes it from service.
        . Traffic automatically goes to remaining Pods.
        . No Downtime.

    How Service Knows which pods to connect:
    ----------------------------------------
    Using Labels
    Ex:-  Pod
    ---
        </>  YAML

    Labels:
        app: backend
        
    Service:
        </> YAML

    Selector:
        app:backend
    
       => If label matches --> Service connect to that Pod. 
       => If label doesn't match --> Service Ignores it.
    
     What Happens when user senda requests:
     --------------------------------------
     Flow:
     -----
         1> User sends request to service IP.
         2> Service receives request.
         3> Service checks matching pods.
         4> Forwards request to one pod.
         5> Next request goes to another pod.
     These All are Load-Balancing.
    






Kubernetes Service - Internal Working (Deep Dive):
--------------------------------------------------
    What is Service:
    ----------------
        A Stable Virtual IP that exposes a set of pods using labels.

    It Provides:
    ------------
        => Stable IP.
        => Stable DNS Name
        => Load Balancing.
        => Pod Discovery.

    Internal Flow:
    --------------
        When we create a service:

    Step-1:
    -------
        API Server stores Services object in etcd.

    Step-2:
    -------
        . Endpoint Controller Creates Endpoint Object.
        . It tracks pods with matching labels.

    Step-3:
    -------
        kube - proxy detects sercice.

    Step-4:
    -------
        . iptables rules (or) IPVS
        .  Routing table.

    Step-5:
    -------
        Traffic routed to one of the pods (round - robin).

Types of Service
    
    
    

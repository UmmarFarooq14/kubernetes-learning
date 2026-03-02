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
    
    
    

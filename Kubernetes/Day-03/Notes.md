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
    Endpoint Controller Creates Endpoint Object.
    It tracks pods with matching labels.

    Step-3:
    -------
    kube - proxy detects sercice,
    
    

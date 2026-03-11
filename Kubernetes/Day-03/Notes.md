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
        kube - proxy detects service.

    Step-4:
    -------
        Kube-proxy updates.
        . iptables rules (or) IPVS
        .  Routing table.
        
        iptables:
        ---------
        . iptables(iptables is a linux firewall and protect-filtering system. It controls how the networking traffic enters, leaves or forwarded inside a linux machine).
        . IPVS it is a high-performance load balancer built in the linux kernel.
    Step-5:
    -------
        Traffic routed to one of the pods (round - robin).

Types of Service:
-----------------
    1> ClusterIp (Default)
    2> NodePort
    3> LoadBalancer
    4> External Name
       And one special case:
    5> Headless service

1> ClusterIp (Default):
-----------------------
    . It is the default service type.
    . It exposes the application only inside the kubernetes cluster.
    . This IP works only inside the cluster.

 Example YAML:
 -------------

    apiVersion: v1
    kind: Service
    metadata:
      name: backend-service
    spec:
      type: ClusterIP
      selector:
        app: backend
       ports:
       - port: 80
         targetPort: 8080

Explanation:
------------
     Service Port → 80
     Pod Port → 8080

     Flow:
     -----
     Frontend Pod
         ↓
     Service (ClusterIP)
         ↓
     Backend Pods

Example cluster IP:
 -------------------
       10.96.0.15

Common Usage:
 -------------
    . Backend APIs
    . Database Services.
    . Internal icroservices.

2> Nodeport:
  ----------
      NodePort exposes the service on a port of every node in the cluster.

Port range:
-----------
    30000 - 32767

Example YAML:
-------------
    apiVersion: v1
    kind: Service
    metadata:
      name: web-service
    spec:
      type: NodePort
      selector:
    app: web
  ports:
  - port: 80
    targetPort: 8080
    nodePort: 30007
    

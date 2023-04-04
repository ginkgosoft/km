# List egress IP and CIDR using the oc get hostsubnet command

OpenShift - List egress IP and CIDR using the oc get hostsubnet command

***

Egress provides a way for an application deployed on OpenShift to access an external URL, such as http://www.example.com.

Optionally, [NetNamespace is used to assign an egress IP address to one or more namespaces](http://www.freekb.net/Article?id=2475), so that all egress traffic from the namespace is using a dedicated IP address. By assigning a specific egress IP address to a namespace, all outbound (egress) requests from applications in the project will come from the dedicated egress IP address, making it easier to find the requests that came from applications in the project. This also makes it possible to have two (or more) different projects share the same egress IP address, as a way to group similar projects together.

An [OpenShift route](http://www.freekb.net/Article?id=1516) or an [Ingress route](http://www.freekb.net/Article?id=3861) will provide a URL such as http://route001-project001.apps.openshift.example.com:8080 which is used to route a request onto a service, which is then routed onto a pod, and then to the container in the pod, and finally to the application running in the container.

![](http://www.freekb.net/images/openshift\_route\_theory2.png)

Objects such as config maps, containers, deployments, pods, routes, secrets, services, et cetera run on a [worker node](http://www.freekb.net/Article?id=2473).

If you are not familiar with the oc command, refer to [OpenShift - Getting Started with the oc command](http://www.freekb.net/Article?id=2693).

The **oc get hostsubnet** command can be used to list the IP address, subnet and CIDR associated with each master, worker and edge node in your cluster. Each node is a virtual machine, such as an Amazon Web Services (AWS) EC2 instance or a VMWare virtual machine, and the Host IP is the IP address of the virtual machine. Something like this should be returned.

```
~]$ oc get hostsubnet
NAME                   HOST                   HOST IP        SUBNET         EGRESS CIDRS      EGRESS IPS 
node001-edge-4lrp9     node001-edge-4lrp9     10.10.100.1    10.10.0.0/23   ["10.10.100.0/24] ["10.10.100.1","10.10.100.2","10.10.100.3","10.10.100.4","10.10.100.5","10.10.100.6","10.10.100.7","10.10.100.8","10.10.100.9"]
node001-infra-68bb8    node001-infra-68bb8    10.10.100.2    10.10.0.0/23                                                                                                                                                                                                
node001-infra-cpdkz    node001-infra-cpdkz    10.10.100.3    10.10.0.0/23                                                                                                                                                                                                
node001-master-0       node001-master-0       10.10.100.4    10.10.0.0/23                                                                                                                                                                                                
node001-master-1       node001-master-1       10.10.100.5    10.10.0.0/23                                                                                                                                                                                                
node001-master-2       node001-master-2       10.10.100.6    10.10.0.0/23                                                                                                                                                                                                
node001-worker-4nplk   node001-worker-4nplk   10.10.100.7    10.10.0.0/23                                                                                                                                                                                               
node001-worker-78xkm   node001-worker-78xkm   10.10.100.8    10.10.0.0/23                                                                                                                                                                                                
node001-worker-7n2q9   node001-worker-7n2q9   10.10.100.9    10.10.0.0/23    
```

The [oc patch netnamespace](http://www.freekb.net/Article?id=2475) command can be used to assign an egress IP address to a project / namespace. By assigning a specific egress IP address to a project / namespace, all outbound requests from applications / services in the project will come from the egress IP address, making it easy to find the requests that came from applications / services in the project.&#x20;

> **AVOID TROUBLE**
>
> The egress IP address must be in the same subnet as the nodes primary IP address. For example, if the node's primary IP address is 10.7.1.2/8 then the egress IP adress would need to be in the 10.x.x.x/8 subnet.

```
~]# oc patch netnamespace project001 --type merge --patch '{ "egressIPs": [ "10.10.100.10" ] }'
netnamespace.network.openshift.io/project001 patched
```

The [oc get netnamespace](http://www.freekb.net/Article?id=4027) command can then be used to see that outbound requests from applications / services in the project will come from IP address 10.10.100.10.

```
~]# oc get netnamespace project001
NAME        NETID     EGRESS IPS
project001  6509873   ["10.10.100.10"]
```

Then the [oc patch hostsubnet](http://www.freekb.net/Article?id=4049) **** command can be used to assign the egress IP address one or more nodes.

```
~]# oc patch hostsubnet node001-edge-4lrp9 --type merge --patch '{ "egressIPs": [ "10.10.100.10" ] }'
hostsubnet.network.openshift.io/node001-edge-4lrp9 patched
```

The [oc get hostsubnet](broken-reference) command can then be used to see that the node has the egress IP address listed. In this example, node001-edge-4lrp9 now includes egress IP address 10.10.100.10.

```
~]$ oc get hostsubnet node001-edge-4lrp9
NAME                   HOST                   HOST IP        SUBNET         EGRESS CIDRS      EGRESS IPS 
node001-edge-4lrp9     node001-edge-4lrp9     10.10.100.1    10.10.0.0/23   ["10.10.100.0/24] ["10.10.100.1","10.10.100.2","10.10.100.3","10.10.100.4","10.10.100.5","10.10.100.6","10.10.100.7","10.10.100.8","10.10.100.9","10.10.100.10"]
```

***

#### Did you find this article helpful?

If so, consider buying me a coffee over at [![Buy Me A Coffee](http://www.freekb.net/images/buy\_me\_a\_coffee\_small.png)](https://www.buymeacoffee.com/jeremycanfield)

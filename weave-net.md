
# Weave Net

### About Weave Net
Weave Net creates a virtual network that connects Docker containers across multiple hosts and enables their automatic discovery. With Weave Net, portable microservices-based applications consisting of multiple containers can run anywhere: on one host, multiple hosts or even across cloud providers and data centers. Applications use the network just as if the containers were all plugged into the same network switch, without having to configure port mappings, ambassadors or links.

Services provided by application containers on the Weave network can be exposed to the outside world, regardless of where they are running. Similarly, existing internal systems can be opened to accept connections from application containers irrespective of their location.

### Feature Overview
- Virtual Ethernet Switch: Weave Net creates a virtual network that connects Docker containers deployed across multiple hosts.
- Fast Datapath
- Seamless Docker Integration (Weave Docker API Proxy): Weave Net includes a Docker API Proxy, which can be used to start containers using the Docker command-line interface or the remote API, and attach them to the Weave network before they begin execution.
- Weave Network Docker Plugin: Weave Net can also be used as a Docker plugin.
- Weave Network CNI Plugin: Weave can be used as a plugin to systems that support the Container Network Interface, such as Kubernetes.
- IP Address Management (IPAM): Containers are automatically allocated a unique IP address.
- Application Isolation: A single Weave network can host multiple, isolated applications, with each application’s containers being able to communicate with each other but not with the containers of other applications.
- Dynamic Network Attachment: attach and detach running containers to and from any network.
- Security
- Host Network Integration: Weave Net application networks can be integrated with a host’s network, and establish connectivity between the host and application containers anywhere.
- Managing Services: Exporting, Importing, Binding and Routing
- Multi-Cloud Networking: Weave can network containers hosted in different cloud providers or data centers.
- Multi-Hop Routing
- Dynamic Topologies: Hosts can be added to or removed from a Weave network without stopping or reconfiguring the remaining hosts.
- Container Mobility: Containers can be moved between hosts without requiring any reconfiguration or, in many cases, restarts of other containers.
- Fault Tolerance

### How Weave Net work?
Weave lets you define a virtual network, so that containers in other hosts can connect to each other transparently (optionally using encryption for added security), as if they were all on the same server. Weave behaves as a sort of giant switch, with all your containers connected in the same virtual network.
- A Weave network consists of a number of ‘peers’ (hosts), Weave Net routers residing on each peers.
- Each peer has a name (defaults to a MAC address), a nickname (for use in status and logging output)  and a unique identifier (UID).
- Weave Net routers establish TCP connections with each other.
- Peers also establish UDP “connections” which carry encapsulated network packets.
- Weave Net creates a network bridge on the host. Each container is connected to that bridge via a veth pair, the container side of which is given an IP address and netmask supplied either by the user or by Weave Net’s IP address allocator.
- Weave Net routes packets between containers on different hosts via two methods: a fast data path method and a fallback sleeve method.
  + Fast data path method: uses the Linux kernel’s Open vSwitch datapath module. This module enables the Weave Net router to tell the kernel how to process packets:
   ![] (https://www.weave.works/wp-content/uploads/7f69140149c9349ea5b76864a2625c64fc24a039.png)
  + Fall back sleeve method: packets are captured by the kernel and processed by the Weave Net router in user space, forwarded over UDP to weave router peers running on other hosts:
  ![] (https://www.weave.works/wp-content/uploads/049a8b89c3cb6526256b63378fd88d2fddc27884.png)
- Weave Net routers learn which peer host a particular MAC address resides on.
- Weave Net can route packets in partially connected networks with changing topology.
- For example, in this network, peer 1 is connected directly to 2 and 3, but if 1 needs to send a packet to 4 or 5 it must first send it to peer 3:

  ![] (https://www.weave.works/wp-content/uploads/2fd05eaf9caa4dcd2d008af3a36f6c64896e297d.png)
- UDP packet format:

  ![] (https://www.weave.works/wp-content/uploads/fe768a7fdde76a7359a8f32c018ee8b5e8974df1.png)
  
### REST API for Weave Net
- REST API is a deliberately undocumented implementation detail: https://groups.google.com/a/weave.works/forum/#!topic/weave-users/EOXCp6xi5u8
- Maybe use Remote Docker API???: 
  + https://github.com/weaveworks/weave/issues/312
  + https://github.com/weaveworks/weave/issues/236
#### ===> difficult

### Demo
#### Description
- Connect containers between 2 hosts
  + Install Docker on each host.
  + Install and launch Weave Net on each host.
  + Create a peer connection on each host.
- TestTesting Container Communications

Updating ...

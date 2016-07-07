# Weave Scope

### About Weave Scope
Weave Scope is a visualization, and monitoring tool for Docker and Kubernetes. It provides a top down view into your app as well as your entire infrastructure, and allows you to diagnose any problems with your distributed containerized app, in real time, as it being deployed to a cloud provider.

### Feature Overview
- Topology Mapping: Scope builds logical topologies of your application and infrastructure.
- Flexible Filtering: Nodes can be filtered by various properties and also display various metrics such as CPU and Memory usage in the nodes.
- Powerful Search
- Real-time App and Container Metrics: View contextual metrics, tags and metadata for your containers.
- Interact With and Manage Containers: Weave Scope you can control the entire container lifecycle across your cluster hosts from a single UI. Start, stop, pause and restart containers from the details panel, and toggle filters for stopped containers in the containers view.
- Troubleshoot Apps
- Generate Custom Metrics using the Plugin API

### API for Weave Scope
- Weave Scope has a simple REST API, but it's undocumented.
- Weave Scope have a web brower interface so we can directly query its API and get a feed of container connections and metrics.
- Simple Example:
  + GET http://localhost:4040/api/topology {   {name: "Containers", url: "/api/topology/containers"},   ... }
  + GET http://localhost:4040/api/topology/containers {   nodes: {    “123...”: {     “adjacency”: [‘456...“],   ...  } }
  + GET http://localhost:4040/api/topology/containers/123…

## Reference
- https://www.weave.works/docs/
- http://thenewstack.io/how-to-detect-map-and-monitor-docker-containers-with-weave-scope-from-weaveworks/

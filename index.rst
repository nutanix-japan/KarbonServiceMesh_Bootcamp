.. title:: Nutanix Karbon Service Mesh Bootcamp with Istio

.. toctree::
  :maxdepth: 2
  :caption: My Service Mesh on Kubernetes
  :name: _servicemesh_kubernetes
  :hidden:

  connect/connect_to_karbon
  application/prepare_deploy_access
  visualisation/application_traffic_visualisation
  control/application_traffic_control
  explore/virtual_services_explore
  cleanup/cleanup
  conclusion/conclusion

.. toctree::
  :maxdepth: 2
  :caption: Appendix
  :name: _appendix
  :hidden:

-------------------------------
Service Mesh on Kubernetes
-------------------------------

Service mesh has become quite popular recently in monitoring and directing application traffic management using software. This applies to microservices based workloads.

Service mesh offers fast, reliable and secure communications between microservices. Service mesh offers useful capabilities such as (not limited to):

- Load balancing
- Traffic management
- Authentication and authorization
- Encryption
- Monitoring

Istio being one of the easy-to-implement and popular service mesh, has the support of major software vendors by implementing it in production environments. There are other service mesh providers out there like Hashicorp, Buoyant, etc.

-------------------------------
Isito Service Mesh Architecture
-------------------------------

Istio Service Mesh has control and data planes. 

- The control plane is used to manage the service mesh and
- The data plane collects and implements desired service mesh functionalities on the application

Istio Service Mesh control plane runs in its own kubernetes namespace called **istio-system** once installed on a kubernetes cluster of choice

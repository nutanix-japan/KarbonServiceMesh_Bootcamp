.. _prepare_deploy_access:

.. title:: Preparing and Deploying Application

------------------------------------
Preparing and Deploying Application
------------------------------------

Preparing your Environment
+++++++++++++++++++++++++++

#. Create a namespace to deploy your application (xyz here is your initials)

   .. code-block:: bash

    kubectl create ns xyz-ns

   .. figure:: images/createns.png

#. Label the ``xyz-ns`` namespace as following

   .. code-block:: bash

    kubectl label namespace xyz-ns istio-injection=enabled

   .. figure:: images/labelns.png

   .. note::

     This is a very important step to enable side-car injection. If this step is not done, Istio will not be able to manage or monitor any resources in the ``xyz-ns`` namespace

#. Change your current working namespace to your namespace you created in Step 1 (xyz-ns), so that you don’t have to specify (-n or --namespace) in your kubectl command anymore.

   .. code-block:: bash

 	  k config set-context --current --namespace=xyz-ns

Deploying your Application
++++++++++++++++++++++++++++

#. Deploy your application (make sure you are in your home folder where you downloaded Istio)

   .. code-block:: bash

	  k apply -f /home/<yourdir>/istio-x.x.x/samples/bookinfo/platform/kube/bookinfo.yaml

   .. figure:: images/installapp.png

#. Once application is deployed. Inspect pods, containers and services. Wait until all the pods are in ``Running`` state

   .. code-block:: bash

    watch kubectl get pods,svc

   .. figure:: images/appresources.png

   .. note::

     Did you observe that the pods have two containers? What is the other pod? Why are there two pods?
     Get the names of the containers in anypods using the following command and explore.

     .. code-block:: bash

      kubectl get pods -o=jsonpath='{range .items[*]}{"\n"}{.metadata.name}{":\t"}{range .spec.containers[*]}{.image}{", "}{end}{end}' | sort

     .. figure:: images/containernames.png

     You will notice that the second container in each pod is a Istio proxy container (that implements the service mesh). This is the container that intercepts all traffic to and from the other application container.

Accessing your Application
++++++++++++++++++++++++++++

We will be now access the application we deployed using port-forwarding feature of kubernetes

#. First we will list all the services to decide which one we need to access

   .. code-block:: bash

    k get svc

   .. figure:: images/clusterip.png

   You will notice that the type is `ClusterIP <https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types/>`_ which means the service is only available inside the kubernetes cluster.

#. To be able to access this ``productpage`` service outside the cluster we will create a port-forwarding service to your CentOS VM

   .. code-block:: bash

  	k port-forward svc/productpage 9080:9080 &

   .. figure:: images/portforwardsvc.png

   .. note::

    We have sent the application to the background so you can continue using the shell. We can bring this process to foreground using the command #fg

#. Access the application in a web browser by visiting the following URL

   .. code-block:: bash

    http://localhost:9080/productpage

   You should see the application's webpage as shown below

   .. figure:: images/bookinfoview.png

   Now that we have successfully deployed our application, we can move on to traffic shaping exercise section.

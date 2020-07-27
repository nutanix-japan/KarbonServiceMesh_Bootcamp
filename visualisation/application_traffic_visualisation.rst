.. _application_traffic_visualisation:

.. title:: Visualise Bookinfo Application

--------------------
Application Traffic
--------------------

Generate Application Traffic
+++++++++++++++++++++++++++++

#. Open a new command shell

#. Export the KUBECONFIG variable using the following command

   .. code-block:: bash

     export KUBECONFIG=<PATH-TO-KUBECONFIG-FILE>

   .. note::

    You can re-download the KUBECONFIG file from Karbon or use the file from the last time you downloaded KUBECONFIG file from Karbon UI

#. We will now simulate traffic pattern to the applciation by accessing it. To automate the access of the application website we will run the following command:

   .. code-block:: bash

    while true;do curl -s -o /dev/null  http://localhost:9080/productpage; sleep 1;done

   .. note::

    The command accesses the product page every second until cancelled. All output of curl command is sent to a null device

Visualise Application Traffic
+++++++++++++++++++++++++++++

Istio service mesh comes in handy with a application and traffic visualization tool called Kiali.

Kiali aslo enables users to manage traffic between various components of the application deployed in your kubernetes cluster.


#. Access the Kiali web application by port forwarding service port to your linux mint VM

   .. code-block:: bash

    k -n istio-system port-forward svc/kiali 20001:20001 &

#. Now access the Kiali service on the following URL in a browser

   .. code-block:: bash

    http://localhost:20001/kiali/

#. Use ``admin`` as username  and ``admin`` as password to login to Kiali UI

#. Once logged in you should be able to see all the namespaces, applications and traffic information in your kubernetes cluster

   .. figure:: images/kialiindex.png

#. Select **Graph > Choose your `xyz-ns` namespce > Choose ‘Versioned app graph’**

#. Click on **Display** and choose **Requests Percentage** and **Traffic Animation options**

   .. figure:: images/initialtrafficpattern.png

#. You will now be able to see packets flowing between various services and ultimately reaching a pod. Notice how the traffic is evenly distributed between the v1,v2 and v3 pods of the reviews app by the reviews service. It might take up to a minute for the traffic pattern to show in Kiali console.

   .. figure:: images/revsvctrafficflow.png

   You should be able to visualise application traffic and that it is distributed evenly across three versions of the application. This is default behaviour dictated by the virtual service.

   .. note::

    Further reading for virtual services and CRD are `here <https://istio.io/latest/docs/reference/config/networking/virtual-service/>`_

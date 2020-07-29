.. _cleanup:

.. title:: Cleaning up your namespace and Istio installation

--------
Cleanup
--------

Cleanup port-forwarding for kiali and product-page(of your application). Just `ctrl+c` the commands.

If you have sent these commands to background, you can bring them to foreground by using

.. code-block:: bash

 fg

Cleanup your namespace. This will also delete all the resources inside the namespace.

.. code-block:: bash

 k delete ns -n xyz-ns

Cleanup Istio

.. code-block:: bash

 k delete ns -n istio-system

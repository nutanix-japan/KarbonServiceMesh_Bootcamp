.. _connect:

.. title:: Connecting to Your Karbon cluster

-----------------------------
Connect to Kubernetes Cluster
-----------------------------

In this exercise we will connect to an existing kubernetes cluster deployed using Nutanix Karbon.

High Level Steps
+++++++++++++++++

1. Create a Linux Mint VM (If one is not deployed already please use the instructions here linux_tools_vm_ to deploy one)
2. Connect to Linux Mint VM and install kubectl tool
3. Access you Karbon page and download KUBECONFIG file to Linux Mint VM
5. Access your Karbon deployed kubernetes cluster


Connect to your LinuxMintVM
++++++++++++++++++++++++++++

#. Logon to your LinuxMint VM console as `nutanix` user (default password) and open terminal

   .. note::

       If you are using your PC/Mac Computer you can also ssh/putty to your LinuxMint VM

       .. code-block:: bash

        ssh -l nutanix <LinuxMint VM IP address>

#. Paste the command in clipboard to the shell in your LinuxMint VM

   .. code-block:: bash

     sudo apt-get update && sudo apt-get install -y apt-transport-https gnupg2
     curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
     echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
     sudo apt-get update
     sudo apt-get install -y kubectl

#. Verify your kubectl installation

   .. code-block:: bash

      alias 'k=kubectl'
      kubectl version --client

Access you Karbon Page
++++++++++++++++++++++

#. Logon to your Prism Central **https://<PC VM IP>:9440**

#. Go to **Menu > Services > Karbon**

   .. figure:: images/choosekarbon.png

#. Select your karbon cluster

#. Click on Actions > Download Kubeconfig

   .. figure:: images/selectcluster.png

#. Click on **Copy the command to clipboard**

#. Paste the clipboard in your Linux Tools VM shell

#. Run the following command to verify your connectivity and display the nodes in the cluster

   .. code-block:: bash

    k get nodes -o wide

   .. figure:: images/nodelist.png

#. You can list the namespaces, storage claims, physical volumes and physical volume claims using the following commands

   .. code-block::
    k get ns
    k get sc,pv,pvc

   .. figure:: images/klistresources.png

   .. note::

     Nutanix Karbon has automatically provised these kubernetes resources so it is ready to use. You have the option to provision additional storage claims, physical volumes, etc by using the Kargon console or using kubectl with YAML files

Now that you have an understanding of your kubernetes cluster and available resources, go ahead and install istio using the instruction in next section.

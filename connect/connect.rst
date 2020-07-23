.. _connect:

.. title:: Connecting to Your Karbon cluster

-----------------------------
Connect to Kubernetes Cluster
-----------------------------

In this exercise we will connect to an existing kubernetes cluster deployed using Nutanix Karbon.

If one is not deployed already please use the instructions here to deploy one

URL --- LINK for Karbon basics lab

Connect to your LinuxMintVM  (using console or ssh/putty)

#. Logon to your LinuxMint VM as `nutanix` user (default password)

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

#. Logon to your PC `https://<PC VM IP>:9440`

#. Go to **Menu > Services > Karbon**

#.

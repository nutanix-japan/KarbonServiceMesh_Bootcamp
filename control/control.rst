.. _control_application_traffic:

.. title:: Controlling Application Traffic using Virtual Service CDR

--------------------------------
Controlling Application Traffic
--------------------------------

In this section we will learn how to control application traffic to different versions of the Reviews application.

Scenario: Let’s say one day your management wants all traffic to go to v3 (latest) of the Reviews app as it is the latest and testing has proven that it has worked properly. How would you do this?

#. In Kiali, click on Services option and select `reviews` service (we will attempt to redirect traffic to v3 pods here

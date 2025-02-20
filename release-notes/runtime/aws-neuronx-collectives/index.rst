.. _neuron-collectives-rn:

Neuron Collectives Release Notes
================================

Neuron Collectives refers to a set of libraries used to support collective compute operations within the Neuron SDK.  The collectives support is delivered via the aws-neuronx-collectives package and includes a pre-built version of the OFI plugin required for use of collectives with Elastic Fabric Adapter (EFA).

.. contents:: Table of contents
   :local:
   :depth: 1

Neuron Collectives [2.15.16.0]
------------------------------
Date: 8/09/2023

New in this release:

* minor bug fixes and enhancements


Neuron Collectives [2.15.13.0]
------------------------------
Date: 7/19/2023

New in this release:

* AllReduce with All-to-all communication pattern enabled for 16 ranks on TRN1/TRN1N within the instance (intranode); choice of 16 ranks is limited to NeuronCores 0-15 or 16-31.

Bug Fixes:

* Fix incorrect mask calculation for 16 ranks when using NeuronCores 16-31
* Fix channels for 16 ranks to avoid failures in the runtime; restrict participating ranks to 0-15 or 16-31



Neuron Collectives [2.14.9.0]
------------------------------
Date: 6/14/2023

New in this release

* Added check for FI_EFA_FORK_SAFE environment variable; now forcing the flag to be set to 1 for multinode runs executing on Linux kernels older than 5.15. 


Neuron Collectives [2.13.7.0]
------------------------------
Date: 05/01/2023

New in this release

* Added support for dma_buf - required for future EFA and Linux kernel updates. 
* Reduced benign reporting of timeouts. Previous implementations reported “Timeout waiting for incoming connection” too frequently (log spam).



Neuron Collectives [2.12.35.0]
------------------------------
Date: 04/19/2023

Bug Fixes

* Fixed support for SOCKET_IFNAME config that was affecting EKS users at scale on large training jobs.



Neuron Collectives [2.12.22.0]
------------------------------
Date: 03/28/2023

New in this release

* Added support for TRN1N.
* Added support for 16 channels and 16 EFA devices, which is required for enabling EC2 TRN1N instances with Neuron.
* Added support for hierarchical All-Reduce and Reduce-Scatter. These implementations are now used by default and provides up to 75% reduction in latency for 2MB buffers across 256 ranks.


Neuron Collectives [2.11.47.0]
------------------------------
Date: 02/08/2023

New in this release

* Added support for Inf2. 



Neuron Collectives [2.10.20.0]
-----------------------------
Date: 10/10/2022

New in this release

* Improved logging to appear similar in style to Neuron Runtime

Bug Fixes

* Fixed memory registration to support 2GB+ sizes
* Fixed association of network devices to channels (removes previous hard-coding).


Neuron Collectives [2.9.86.0]
-----------------------------
Date: 10/10/2022

New in this release

* Added support for All-Reduce, Reduce-Scatter, All-Gather, and Send/Recv operations.


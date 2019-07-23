---
layout: post
title: Keystone Paper and Customizable TEEs
author: dkohlbre
description: The Keystone paper is now available, along with the first entry in a series summarizing it.
---

We're happy to announce the release of the Keystone paper! The
current version is now available on the Keystone website
[here](https://keystone-enclave.org/files/keystone_paper_v1.pdf).

We'll be running a multi-part blog series covering different aspects
of the paper. The first installment will cover the _customizable TEE_
model that Keystone provides.

# Customizable TEEs

We believe the right way to build Trusted Execution Environments
(TEEs) is with highly flexible and minimal primitives that present
clear abstractions. 

## Need for Customizable TEEs

ARM TrustZone and Intel SGX are the widely available
Implementations today. We take some valuable lessons we learned from
these existing standard TEEs as an inspiration. Specifically, all these TEEs
make fixed design-decisions based on either the target applications (e.g.,
crypto libraries, client apps, server apps, embedded apps) or threat models
(e.g., remote adversary, side-channel adversary). 

Although these TEEs do meet
the requirements of the workloads and use-cases they were designed for,
the proliferation of TEEs and need for secure computation has led  to a wave
of repurposing these TEEs to adapt to a different set of workloads (e.g.,
Intel SGX is now being used for server-side deployments). Further,  both
academia and industry are putting in a lot of effort towards adding  more
support for flexible application porting to TEEs, better defenses against
side-channels,  performance optimizations, repurposing existing hardware
features to improve the security of  TEE-bound applications. 

TEEs have not previously been designed with the goal of maintaining flexibility
for enclave-developers nor extensibility if and when a new hardware
feature becomes available.  Further, reducing the enclave TCB has been a
Long-standing objective for all TEE platforms to varying degrees of success.  

To this end, when designing
Keystone,  we considered  flexibility, customizability, and TCB minimization as
the main guiding principles. We have developed clear abstractions and a
modular programming model which made it significantly  easier to realize our
goals. 


## Defining a Customizable TEE

We define three logical actors involved in the customizable TEE
ecosystem: the manufacturer (who build the hardware), the platform
provider (who operates the hardware, eg. a cloud provider), and the
enclave developer (who writes software that they run in enclaves).

In a customizable TEE, in contrast to a standard TEE, the security
guarantees provided and features enabled are a combination of
decisions by all 3 actors. This is analogous to the differences
between classical networking hardware and Software Defined Networking
(SDN). The switch to a minimal easily reconfigurable hardware layer, with a programmable software layer performing the majority of the work leads to a far more agile system.

We believe this will accelerate research in the area as well as make
for safer deployments with faster updates.

The Keystone Framework provides customizable TEEs by using standard
RISC-V hardware for flexibility along with multiple software layers to
ensure minimal TCBs and maximum enclave capability.


## Keystone and Customization

In a Keystone compatible platform, there are no modifications needed
to the RISC-V cores. Any available additional features the SoC or
peripherals supply are handled by plugins to the Keystone SM. These
may be developed by the manufacturer, or the platform provider, who
determines what specific set to include in the deployed
platform. These decisions are not permanent and may be changed by
compiling a new SM and installing it.

Above this layer, each enclave may deploy its own customized runtime
binary. We maintain the Eyrie modular runtime, which supports a growing
set of use-cases while minimizing the code present in the TCB.

Existing frameworks, defenses, enhancements, etc. to other TEE systems
are generally portable to Keystone. Secure filesystems and other safe
I/O operations can be integrated directly into the runtime, without
affecting the enclave application itself. 

We are excited to see what the community brings to the Keystone Framework!


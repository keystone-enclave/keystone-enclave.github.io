---
layout: post
title: What is Keystone and its first open-source release?
author: dkohlbre
description: Keystone is the first open-source enclave framework for RISC-V processors.
---
<meta name="twitter:card" content="summary" />
<meta name="twitter:title" content="What is the Keystone Enclave?" />
<meta name="twitter:image" content="https://keystone-enclave.org/img/keystone-header.png" />

# What is Keystone?

Secure enclaves open up many new opportunities and improvements to secure computing. They can allow safely running computation in the cloud on sensitive data without the need to trust the cloud provider and with additional safety from other cloud tenants, enable building trusted IoT sensors, or simply provide additional trust and isolation for critical tasks. Keystone is the first open-source secure enclave system you can download and run today.
Keystone will provide a new framework for running applications in these environments that is more transparent, secure, and extensible than existing solutions.

> <b>Keystone is available today on <a href="https://github.com/keystone-enclave">github</a>.</b>

## What are Trusted Execution Environments (TEEs) and Enclaves?

A TEE is an environment that provides security guarantees for a program
even against malicious privileged attackers, such as the operating
system. Generally a TEE provides confidentiality and integrity as
baseline guarantees for code executing inside. We refer to the
encapsulation of the secure process as an enclave.

## What are enclaves for?

Enclaves have many uses; from adding additional layers of defense to existing programs, to enabling minimal trust in cloud providers.

One of the most promising uses is in enabling the use of cloud computing without trusting the cloud provider or other cloud tenants at low overhead. In this model, the only party the client trusts in the manufacturer of the CPU in the cloud. The network, operating system, and even other parts of the hardware can be distrusted and your data and code can remain safe.

## Why build Keystone?

Enclaves and trusted execution environments (TEEs) are not a new
concept, and there are several existing and actively developed
commercial solutions. We believe that an open-source and extensible
enclave framework is a better model, and that is why we are building
Keystone.

Most existing TEEs (Intel SGX, AMD SEV, ARM TrustZone, etc) are
closed-source and hard to modify. This has prevented significant
research into the possible designs, defensive mitigations, and
engineering tradeoffs from being made. When serious attacks against
these TEEs have been made public, the community has been unable to
evaluate the details of the exploit, find related problems, or evaluate
the impact of patches easily.

We believe that an open-source enclave framework on RISC-V solves
these problems. Open-source provides Keystone with a number of
benefits. The most obvious are that anyone can see how it works,
understand the threat model it can operate under, and verify how
exploits/patches function.

Equally important is the ability for researchers to explore the design
space for TEEs in general, and share that work easily with others. The
use cases for enclaves have steadily evolved over the past few years,
from DRM schemes to smart contracts and more. Thus, we believe an agile,
software-based and open-source design is the right choice.


## Why build Keystone on RISC-V?

RISC-V presents us with a number of benefits besides just being open-source:

RISC-V has added security-oriented primitives (notably Physical Memory Protection) that enable efficient isolation.
RISC-V is an evolving and community-driven ISA. Keystone can explore the design space of useful security features, and feed good ideas back into the standards themselves.
RISC-V has a constantly expanding world of open-source cores and products. This gives Keystone a wide variety of potential platforms and different deployment scenarios it can adapt to.


## What will Keystone be?

Keystone is an enclave framework. It will contain the core
features required for any enclave design:

Mechanisms for secure management and isolation of enclave memory.
A secure boot process. This allows Keystone to prove that it booted the correct SM and enclave software.
Remote attestation mechanisms. These are how a Keystone enclave proves to a remote client that it is running correctly and safely.
In Keystone, the Security Monitor (SM) is key to all of these features. The SM:
Manages and isolates enclaves
Is the final software booted in a trusted boot process
Facilitates the remote attestation process.

We will also be building many other components for Keystone. Our goal is to support a wide variety of use cases and threat models. We will be building a modular system that can support diverse applications, from minimal trusted libraries to complete para-virtualized Linux enclaves.
Different target uses may require modifications to different parts of the Keystone framework, or new toolchains.

We believe that this will be a fantastic research opportunity for trusted systems design and software/hardware co-design.

## Where is Keystone now?

Currently, Keystone supports the features needed to perform secure boot, remote attestation, and execution of simple statically linked enclave applications.

To support this, we’ve constructed a minimal enclave runtime that proxies data from the enclave to the insecure OS. Future supported targets will require extensions to the runtime, or entirely separate runtimes (ex: Linux). We’ve also built an SDK that contains libraries and tools that target this minimal runtime, as well as being useful for any development on Keystone.

We’ve built a demo application that is capable of remote attestation, secure channel establishment using libsodium, and simple secure computation on data sent over the channel. It is available as well at [github](https://github.com/keystone-enclave/keystone-demo).

We’ve tested Keystone on qemu (our default development target), FireSim (a simulation system) as well as on the HiFive Unleashed development board (a real RISC-V chip). Other RISC-V platforms that support the minimum requirements should be easy to adapt to as well.


You can also check out our (constantly evolving) documentation here:
[Documentation](http://docs.keystone-enclave.org/en/latest/).

You can start working with
[Keystone](https://github.com/keystone-enclave) on github today.

Date: December 13, 2018

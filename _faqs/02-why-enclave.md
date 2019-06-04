---
title: Why do we need secure hardware enclaves?
category: [presale]
---

Secure computation is a powerful abstraction, protecting the integrity and
confidentiality of computations over confidential data. While there are already
many applications for secure computing, it will continue to grow in importance.
First, the shift towards cloud computing has driven high demand for security in
the cloud, because it requires all of the data computation and storage to take
place on remote machines. Second, there is a growing need to compute over
private data from multiple sources. For example, mutually distrusting
organizations may want to train collaborative machine learning models over
confidential data.

One way to enable secure computation is to use crypto-based techniques such as
*homomorphic encryption* and *multi-party computation*. However, state-of-the-art
techniques in this domain are many orders of magnitude slower than native
computation, limiting their practical applications.

Secure hardware enclaves provide another solution to secure computation with
little or no performance overhead over native computation. Hardware enclaves
enable computation over confidential data, providing strong isolation from
other applications, the operating system, and the host. The secure enclave can
also attest to the correct execution of a program to a remote party. Because
secure enclaves has low performance overhead, they enable secure computation
with a wide range of real-world applications.

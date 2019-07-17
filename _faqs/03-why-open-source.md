---
title: Why should it be open-source?
---

Although many TEEs have been proposed by both industry (e.g., Intel
SGX) and academia (e.g., Sanctum), no full-stack implementation has
been open-sourced for use. Commercial TEEs often take advantage of
*security by obscurity*; most parts of the designs (especially the
hardware stack) are not open-sourced and remain undocumented. Most
security guarantees of commercial TEEs rely on trusting the design,
implementation, and supply-chain management of hardware vendors. Also,
currently TEE users often rely on a single party such as Intel in the
case of SGX for remote attestation and key revocation.

Keystone follows the philosophy of *open security*. While there is no
industry agreement on the “right solution” for everything, we believe
open-source design allows the community to more effectively share
insights, improve designs, and iterate on problems towards the goal of
secure hardware enclaves.

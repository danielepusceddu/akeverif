# Formal Verification of AKE Protocols
This repository contains automated formal analyses and the resulting proofs or counterexamples for authentication properties in two Authenticated Key Exchange protocols:
- The **PACE protocol** (Password-Authenticated Connection Establishment protocol) is part of a global protocol suite for machine-readable travel documents (electronic passports and identity cards). 
  It is used to establish a secure channel between a terminal and the RFID chip embedded in these documents. 
  Starting with a low-entropy shared secret, such as the six-digit Card Access Number (CAN) or data from the Machine-Readable Zone (MRZ), PACE uses a Diffie-Hellman key exchange to derive a session key.
- The Authenticated Key-Exchange of **the OTR v1 protocol** (Off-The-Record protocol), used for secure messaging.
  The OTR protocol was developed as a solution for end-to-end encryption in instant messengers and served as inspiration for the Signal protocol.
  Here too the key exchange protocol is based on Diffie-Hellman, but the initial setup includes knowledge of the public keys of the parties with which the client whishes to communicate.

The properties we will consider are:
- Secrecy of the established shared key.
- Perfect Forward Secrecy of the established shared key.
- Non-Injective Agreement from the perspective of the Initiator as well as from the Responder's.
- Injective Agreement, again from both perspectives.

We use [the Tamarin prover](https://tamarin-prover.com/) as our verification tool of choice. We build up to these protocols through a series of increments, starting from an overly näive version.

## Repository Structure
- The `/theories` subdirectory contains the security protocol theory source files we have written by hand.
  These source files contain our formalizations of the protocols as Multiset Rewriting Systems, as well as the definitions of the properties we wish to prove or disprove as temporal first-order logic properties.
- The `/proofs` subdirectory contains the outputs given by Tamarin 1.8.0 for the files in the above subdirectory.
  They contain post-processed versions of our definitions as well as automatically generated proofs or counterexamples for all of the properties.

## Credits
This analysis has been a collaborative effort by [Giacomo Fiorindo](https://github.com/giacomofiorindo) and [Daniele Pusceddu](https://github.com/danielepusceddu). 
We thank the Information Security group at ETH Zürich for their fantastic Formal Methods course, without which we would not have had the necessary know-how for this project.

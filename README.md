# OIDC Tamarin Verification
# OpenID Connect Formal Verification using Tamarin Prover

## Overview

This repository contains formal Tamarin models for the verification of the **OpenID Connect (OIDC)** protocol.

The project focuses on modeling and verifying different OIDC authentication flows and analyzing their security properties under the symbolic attacker model.

This work is part of a Master's thesis on the formal verification of authentication protocols.

---

## Implemented Models

* **Authorization Code Flow**
* **Implicit Flow**
* **Authorization Code Flow with Client Authentication**

Each model is implemented in the Tamarin specification language (`.spthy`) and can be verified using the Tamarin Prover.

---

## Repository Structure

```text
.
├── models/
│   ├── 01_authorization_code_flow.spthy
│   ├── 02_implicit_flow.spthy
│   └── 03_code_flow_client_auth.spthy
│
├── results/        # Verification outputs
├── docs/           # Thesis documents and references
└── README.md
```

---

## Requirements

* Tamarin Prover
* Maude
* Graphviz

---

## Running a Model

```bash
tamarin-prover 01_authorization_code_flow.spthy
```

or launch the interactive interface:

```bash
tamarin-prover interactive 01_authorization_code_flow.spthy
```

---

## Reference

The models are inspired by previous formal analyses of OpenID Connect and adapted for verification in the Tamarin Prover framework.

---

## Author

**Mahnoush Changizi**

Master's Thesis Project – Formal Verification of OpenID Connect using Tamarin Prover

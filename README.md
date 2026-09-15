# OpenID Connect — Formal Verification with Tamarin

Formal analysis of the OpenID Connect Authorization Code Flow using the
Tamarin Prover. Author: Mahnoush Changizi (University of Genova / IRIT Toulouse).

## Requirements

- Tamarin Prover 1.8.0
- Maude 3.2 (a version warning is harmless)

## How to run

To verify a single model:

    tamarin-prover --prove <model>.spthy

To open a model interactively (GUI at http://127.0.0.1:3001):

    tamarin-prover interactive <model>.spthy

The `result_<model>.txt` files contain the full output of
`tamarin-prover --prove` for each model.

## Models

Each model isolates one security mechanism, so that its necessity can be tested.

| File | Description |
|------|-------------|
| 01_authorization_code_flow | Baseline Authorization Code Flow (reproduces Lu et al.) |
| 01_fries_code_flow | Baseline with redirect and issuer checks |
| 02_implicit_flow | Implicit Flow |
| 03_code_flow_client_auth | Code Flow with client authentication |
| 04_authorization_code_flow_secure_channel | Adds TLS (secure channel) |
| 04_fries_secure_channel | Fries flow over TLS |
| 06A_registry_secure | Signature verified with pre-registered key |
| 06B_embedded_insecure | Signature verified with key embedded in token |
| 07_state_exp | State and expiry checks present |
| 07B_state_exp_missing | State and expiry checks removed |
| 08_complete_secure | All six mechanisms present |
| 09A_no_iss_check | Complete model minus issuer check |
| 09B_no_redirect_check | Complete model minus redirect check |

## Main result

The Authorization Code Flow is secure if and only if six mechanisms hold
together: TLS protection, redirect URI validation, registry-based key
verification, issuer binding, state validation, and expiry validation.
Model 08 shows they are jointly sufficient; the isolation models show each is
necessary, except that issuer binding is subsumed by registry-based key
verification (Model 09A).

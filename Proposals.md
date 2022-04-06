SDK core proposals
===

## Features

- [ ] Request payment
- [ ] Request transfer
- [ ] Withdrawal (payout)
- [ ] Request instant payout (xpress cash token, bank, mobile money)
- [ ] Request for transaction fees
- [ ] Request for transaction status
- [ ] Webhook handler (add, update, remove, retry callback, verify webhook signature)
- [ ] Request payment link
- [ ] Request for receipt
- [ ] Request for the last 10 transactions (success, pending, failed)
- [ ] Request for business information
- [ ] Setup payout information

## Achitecture

### High level description

The `core` communicates with the KKiaPay service in the same way that existing SDKs today do, via HTTPs.

The `sdk-lang` side communicates with `sdk-core` via either C bindings, or (later) bindings to a WASM interface. Many languages already have nice support for calling into Rust code - generally speaking these implementations are using C bindings under the hood. For example, we use [neon](https://neon-bindings.com/) to support the TS/JS sdk, and we will likely use [PyO3](https://github.com/PyO3/pyo3) for Python. It is expected that such usages will layer another crate on top of `core` which brings in these language specific libraries to expose `core` to that language in an ergonomic manner.
As a general note, the more we can push from `sdk-lang` into `sdk-core`, the easier our ecosystem is to maintain in the long run as we will have less semantically identical code.


### Core SDK Responsibilities

### Language Specific SDK Responsibilities

### Example Sequence Diagrams

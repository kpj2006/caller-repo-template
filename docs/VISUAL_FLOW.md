# Visual Flow (Caller to Reusable)

This document shows the handoff between caller workflow and reusable settlement workflow.

## Sequence

```text
Contributor opens PR
  -> caller workflow posts welcome message

Contributor comments wallet
  -> format: x402-wallet: 0x...
  -> caller workflow stores/accepts wallet

Maintainer comments /send <amount>
  -> caller workflow checks permission
  -> caller workflow resolves recipient wallet
  -> caller workflow dispatches reusable workflow

Reusable workflow executes settlement
  -> validate inputs
  -> send on-chain mint transaction
  -> produce tx hash + explorer URL

Reusable workflow posts callback status
  -> PR receives success/failure comment
```

## Responsibility Split

Caller repository:

- command parsing
- permission checks
- wallet collection UX

Reusable repository:

- blockchain transaction execution
- network/contract validation
- settlement output generation

See reusable architecture for settlement internals:
[x402_workflow/docs/ARCHITECTURE.md](https://github.com/manashatwar/x402_workflow/blob/main/docs/ARCHITECTURE.md)

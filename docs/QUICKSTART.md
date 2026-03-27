# Quick Start (Caller Repository)

Use this guide to enable PR-based reward commands in your repository.

Settlement execution details are in reusable repo docs:
[x402_workflow/docs/README.md](https://github.com/manashatwar/x402_workflow/blob/main/docs/README.md)

## Prerequisites

- Access to a deployed reusable x402_workflow repo
- Personal access token with repo + workflow scope
- Server wallet private key funded with MON
- SCORE token contract address
- Monad RPC URL

## Setup Steps

1. Copy workflow template into your repo:
   .github/workflows/pr-x402-trigger.yml
2. Update reusable repo owner/name/ref in the workflow file.
3. Add caller secrets in repository settings.
4. Run end-to-end test on a test PR.

## Caller Secrets

| Secret Name               | Description                          |
| ------------------------- | ------------------------------------ |
| X402_WORKFLOW_TOKEN       | Token used to dispatch reusable flow |
| X402_SERVER_WALLET        | Server wallet private key            |
| X402_SCORE_TOKEN_CONTRACT | SCORE token contract address         |
| X402_RPC_URL              | Monad RPC endpoint                   |

If reusable workflow requires an extra callback token, configure it in the reusable repository.

## End-to-End Test

1. Open a PR.
2. Confirm welcome comment appears.
3. As PR author, comment wallet:

```text
x402-wallet: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
```

1. As maintainer, comment:

```text
/send 100
```

1. Confirm settlement completion comment includes transaction hash.

## Common Issues

No dispatch:

- Verify token scope and reusable repo reference.

No wallet found:

- Ensure PR author posted wallet in exact format.

Settlement failure after dispatch:

- Check reusable repo workflow logs and chain credentials.

## Next Docs

- [MAINTAINER_GUIDE.md](MAINTAINER_GUIDE.md)
- [VISUAL_FLOW.md](VISUAL_FLOW.md)

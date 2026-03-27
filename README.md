# PR x402 Settlement Caller Template

Template for repositories that want PR-driven rewards with maintainer-controlled settlement.

This template handles GitHub-side UX:

- welcome comment on PR open
- wallet capture from PR author
- maintainer command /send amount
- trigger to reusable settlement workflow

On-chain execution is handled by the reusable repository:
[manashatwar/x402_workflow](https://github.com/manashatwar/x402_workflow)

## Cross-Repo GitHub Links

- Caller template repo: [https://github.com/kpj2006/caller-repo-template.git](https://github.com/kpj2006/caller-repo-template.git)
- Reusable engine repo: [https://github.com/manashatwar/x402_workflow.git](https://github.com/manashatwar/x402_workflow.git)

## Documentation Map

- [docs/README.md](docs/README.md): caller doc index
- [docs/QUICKSTART.md](docs/QUICKSTART.md): setup in a new repo
- [docs/MAINTAINER_GUIDE.md](docs/MAINTAINER_GUIDE.md): day-to-day maintainer usage
- [docs/VISUAL_FLOW.md](docs/VISUAL_FLOW.md): end-to-end sequence diagram

## Fast Setup Checklist

1. Copy workflow template into your repository at .github/workflows/pr-x402-trigger.yml.
2. Configure reusable repo owner/name/branch reference in that workflow.
3. Add required caller secrets.
4. Open test PR, submit wallet comment, then run /send amount as maintainer.

Detailed steps are in [docs/QUICKSTART.md](docs/QUICKSTART.md).

## Required Caller Secrets

| Secret Name                | Purpose                                            |
| -------------------------- | -------------------------------------------------- |
| X402_WORKFLOW_TOKEN        | Token able to dispatch reusable workflow           |
| X402_SERVER_WALLET         | Server wallet private key                          |
| X402_SCORE_TOKEN_CONTRACT  | SCORE token contract address                       |
| X402_RPC_URL               | Monad RPC endpoint                                 |

If your reusable workflow expects additional callback token/secret, configure it in the reusable repo as documented there.

## Command Contract

Contributor wallet submission format:

```text
x402-wallet: 0x<40-hex-chars>
```

Maintainer settlement trigger format:

```text
/send <amount>
```

## Ownership Boundary

Caller template owns:

- PR comment handling
- permission gate for /send
- amount policy and maintainer UX

Reusable repo owns:

- chain execution
- transaction generation
- explorer output

See reusable docs index for settlement-side details:
[x402_workflow/docs/README.md](https://github.com/manashatwar/x402_workflow/blob/main/docs/README.md)

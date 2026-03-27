# Maintainer Guide (/send)

This guide is for maintainers operating caller-side reward commands.

Settlement internals are in reusable docs:
[x402_workflow/docs/WORKFLOWS.md](https://github.com/manashatwar/x402_workflow/blob/main/docs/WORKFLOWS.md)

## Command Contract

Use this format in PR comments:

```text
/send <amount>
```

Examples:

```text
/send 50
/send 100
/send 250
```

## Required Preconditions

1. You have write or admin permission in the repository.
2. PR author has submitted wallet in valid format.
3. Caller and reusable secrets are configured.

## Maintainer Workflow

1. Review PR quality and impact.
2. Confirm wallet is available from PR author comment.
3. Post /send amount.
4. Wait for completion callback with transaction details.

## Suggested Reward Bands

| Contribution Type      | Suggested Range |
| ---------------------- | --------------- |
| Docs and small fixes   | 25 to 100       |
| Bug fixes              | 75 to 300       |
| Features and refactors | 150 to 1000     |

## Troubleshooting

Permission denied:

- Verify write/admin access and account context.

No wallet found:

- Verify PR author posted wallet using exact prefix x402-wallet:.

Invalid /send format:

- Use whole-number amount and include space after /send.

Settlement failed after trigger:

- Check reusable workflow run logs and chain credentials.

## Policy Tip

Document your reward scale in CONTRIBUTING.md so contributors know how rewards are decided.

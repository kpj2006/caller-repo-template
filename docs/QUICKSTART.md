# 🚀 Quick Start Guide

Get your maintainer-controlled PR x402 settlement system running in 5 minutes!

## ⚡ Prerequisites Checklist

- [ ] x402_workflow repository is set up and working
- [ ] You've tested x402-settlement-demo.yml manually
- [ ] You have a GitHub Personal Access Token with `workflow` scope
- [ ] You have all the required secrets ready

## 🎯 5-Minute Setup

### 1️⃣ Copy Files (1 minute)

Copy the entire `caller-repo-template` folder to your target repository:

```bash
# Copy the workflow
cp -r caller-repo-template/.github/workflows /path/to/your/repo/.github/

# Or manually create: .github/workflows/pr-x402-trigger.yml
```

### 2️⃣ Update Configuration (1 minute)

Edit `.github/workflows/pr-x402-trigger.yml`:

**Line 97**: Change repository owner
```yaml
X402_REPO_OWNER: 'YOUR_GITHUB_USERNAME'  # Change this!
```

**Line 98**: Change repository name
```yaml
X402_REPO_NAME: 'x402_workflow'  # Change if different
```

**Line 102**: Verify your default branch
```yaml
ref: 'main',  # Change to 'master' if needed
```

### 3️⃣ Add Secrets (2 minutes)

Go to: **Your Repo → Settings → Secrets → Actions → New repository secret**

Add these 4 secrets:

```
X402_WORKFLOW_TOKEN      = ghp_your_token_here
X402_SERVER_WALLET       = 0x_your_private_key
X402_SCORE_TOKEN_CONTRACT = 0x_contract_address  
X402_RPC_URL             = https://testnet.monad.xyz
```

### 4️⃣ Test It! (1 minute)

1. Create a test PR
2. See the welcome message
3. Comment: `x402-wallet: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266`
4. As maintainer, comment: `/send 100`
5. Watch the magic happen! ✨

## 🎬 What Happens Next?

### For Contributors:

1. **Open PR**: Create your pull request
2. **Get Welcome**: Bot asks for your wallet address
3. **Submit Wallet**: Comment `x402-wallet: 0xYourAddress`
4. **Wait for Review**: Maintainer reviews your PR
5. **Receive Tokens**: When maintainer approves with `/send <amount>`

### For Maintainers:

1. **Review PR**: Check code quality and impact
2. **Verify Wallet**: PR author should have already submitted wallet
3. **Send Tokens**: Comment `/send 100` (or any amount you choose)
4. **Confirmation**: ~1-2 minutes later, success message with TX hash

## 📝 Command Reference

### For PR Authors (Contributors)
```
x402-wallet: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
```

### For Maintainers (NEW!)
```
/send 50      # Small fixes, docs
/send 100     # Bug fixes, minor features
/send 200     # Medium features
/send 500     # Major features
```

## 🐛 Quick Troubleshooting

### Nothing happens after commenting wallet?

1. Wallet is saved - this is correct! Wait for maintainer approval
2. Verify wallet format: `x402-wallet: 0x...` (exactly)
3. Check you're the PR author (not someone else)

### "Permission Denied" when using /send?

1. Only maintainers with write/admin access can use `/send`
2. Verify you have proper permissions in repository settings
3. Check you're in the correct repository

### "No Wallet Address Found" when using /send?

1. PR author must submit wallet first
2. Wallet must be in format: `x402-wallet: 0x...`
3. Must be commented by the PR author (not co-authors)

### "Failed to trigger workflow"?

1. Verify `X402_WORKFLOW_TOKEN` has `workflow` scope
2. Double-check `X402_REPO_OWNER` and `X402_REPO_NAME`
3. Ensure x402-settlement-demo.yml exists in x402_workflow repo
4. Check the `ref` branch name is correct

### Workflow triggers but settlement fails?

Check x402_workflow repository:
- Secrets configured? (THIRDWEB_SECRET_KEY, etc.)
- Server wallet funded?
- Contract address correct?

## 📋 Pre-flight Checklist

Before going live:

- [ ] Tested on a private/test repository first
- [ ] Verified all secrets are correct
- [ ] Tested wallet submission as PR author
- [ ] Tested `/send` command as maintainer
- [ ] Checked transaction on Monad explorer
- [ ] Using testnet (not mainnet yet!)
- [ ] Defined your token reward scale
- [ ] Updated CONTRIBUTING.md with reward info (optional)

## 🎓 Learning Resources

- [Maintainer Guide](../MAINTAINER_GUIDE.md) - How to use `/send` command
- [Workflow Update](../WORKFLOW_UPDATE.md) - What changed in the new system
- [x402_workflow](https://github.com/manashatwar/x402_workflow) - Settlement engine
- [Monad Testnet](https://testnet.monad.xyz) - Test network

## 💡 Pro Tips

1. **Test First**: Always test on testnet before mainnet
2. **Define Scale**: Document your token amounts (25 for docs, 100 for bugs, etc.)
3. **Monitor Gas**: Keep server wallet funded with MON
4. **Be Consistent**: Use similar amounts for similar contributions
5. **Communicate**: Tell contributors about the reward system in CONTRIBUTING.md

## 🎉 Success Indicators

You'll know it's working when:

✅ PR opened → Welcome message appears  
✅ Wallet commented → "Wallet Address Saved!" message  
✅ Maintainer uses `/send` → "Settlement Triggered" message
✅ 1-2 minutes → "Settlement Completed!" with TX hash  
✅ Wallet shows new tokens on Monad network  

## 🚨 Common Mistakes

1. ❌ Forgetting to change `X402_REPO_OWNER` in workflow file
2. ❌ Using wrong branch name in `ref:` field
3. ❌ Token without `workflow` scope
4. ❌ Non-maintainer trying to use `/send` command
5. ❌ Wrong wallet format (missing `x402-wallet:` prefix)
6. ❌ Using `/send` before PR author submits wallet
7. ❌ Forgetting space in `/send 100` (must be `/send 100` not `/send100`)

## 🎊 You're Ready!

Once setup is complete:

**Contributors can:**
1. Open PRs
2. Submit wallets
3. Get rewarded based on quality

**Maintainers can:**
1. Review PRs thoroughly
2. Decide appropriate rewards
3. Use simple `/send <amount>` command

**Flexible, fair, and automated!** 🚀

---

Need help? Check [MAINTAINER_GUIDE.md](../MAINTAINER_GUIDE.md) or review workflow logs in the Actions tab.

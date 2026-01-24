# 🚀 Quick Start Guide

Get your PR x402 settlement system running in 5 minutes!

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

**Line 97-98**: Change repository details
```yaml
X402_REPO_OWNER: 'YOUR_GITHUB_USERNAME'  # Change this!
X402_REPO_NAME: 'x402_workflow'           # Change if different
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

After you comment with your wallet:

1. **Instant**: "✅ Wallet Address Saved!" message
2. **Wait**: Maintainer reviews your PR
3. **Maintainer approval**: Maintainer comments `/send 100` (or another amount)
4. **~30 seconds**: x402 settlement workflow triggers in x402_workflow repo
5. **~1-2 minutes**: Token minting on Monad
6. **Result**: "🎉 Settlement Completed!" message with transaction hash

## 🐛 Quick Troubleshooting

### Nothing happens after commenting wallet?

1. Check if you're the PR author (only PR authors can trigger)
2. Verify wallet format: `x402-wallet: 0x...` (exactly)
3. Check Actions tab for error logs

### "Failed to trigger workflow"?

1. Verify `X402_WORKFLOW_TOKEN` has `workflow` scope
2. Double-check `X402_REPO_OWNER` and `X402_REPO_NAME`
3. Ensure x402-settlement-demo.yml exists in x402_workflow repo

### Workflow triggers but settlement fails?

Check x402_workflow repository:
- Secrets configured? (THIRDWEB_SECRET_KEY, etc.)
- Server wallet funded?
- Contract address correct?

## 📋 Pre-flight Checklist

Before going live:

- [ ] Tested on a private/test repository first
- [ ] Verified all secrets are correct
- [ ] Tested with a real wallet address
- [ ] Checked transaction on Monad explorer
- [ ] Using testnet (not mainnet yet!)
- [ ] Customized welcome message (optional)
- [ ] Set appropriate token amount

## 🎓 Learning Resources

- [Full README](README.md) - Complete documentation
- [x402_workflow](https://github.com/manashatwar/x402_workflow) - Settlement engine
- [Monad Testnet](https://testnet.monad.xyz) - Test network explorer

## 💡 Pro Tips

1. **Test First**: Always test on testnet before mainnet
2. **Small Amounts**: Start with small token amounts (10-100)
3. **Monitor Gas**: Keep server wallet funded with MON
4. **Custom Messages**: Personalize the welcome message for your project
5. **PR Templates**: Add instructions in your PR template

## 🎉 Success Indicators

You'll know it's working when:

✅ PR opened → Welcome message appears  
✅ Wallet commented → Acknowledgment message  
✅ 1-2 minutes → Settlement success message with TX hash  
✅ Wallet shows new tokens on Monad network  

## 🚨 Common Mistakes

1. ❌ Forgetting to change `X402_REPO_OWNER`
2. ❌ Using wrong branch name in `ref:`
3. ❌ Token without `workflow` scope
4. ❌ Commenting from different account than PR author
5. ❌ Wrong wallet format (missing `x402-wallet:` prefix)

## 🎊 You're Ready!

Once setup is complete, every PR author can:
1. Open a PR
2. Get welcomed
3. Submit their wallet
4. Receive tokens automatically

**No manual intervention needed!** 🚀

---

Need help? Check the [Full README](README.md) or review workflow logs in the Actions tab.

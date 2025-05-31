# Quick Implementation Guide

## Solution 1: MkDocs EncryptContent Plugin (FASTEST - 2 hours)

### Step 1: Install Plugin
```bash
# In your project directory
pip install mkdocs-encryptcontent-plugin

# Or if using uv (as your project suggests)
uv add mkdocs-encryptcontent-plugin
```

### Step 2: Update mkdocs.yml
Add to your existing `mkdocs.yml` plugins section:

```yaml
plugins:
  - search:
      separator: '[\s\-,:!=\[\]()"/]+|(?!\b)(?=[A-Z][a-z])|\.(?!\d)|&[lg]t;'
  - git-revision-date-localized:
      enable_creation_date: true
      type: timeago
  - encryptcontent:
      global_password: !ENV WIKI_PASSWORD
      password_button_text: 'Access Campaign Wiki'
      decryption_failure_message: 'Invalid password. Contact campaign team for access.'
      remember_password: true
      session_storage: true
      encrypted_something:
        material_theme: true
      search_index: 'dynamically'
```

### Step 3: Set Up Environment Variable
```bash
# For local testing
export WIKI_PASSWORD="BlackFlag2025!"

# Test locally
mkdocs serve
```

### Step 4: Configure GitHub Actions Secret
1. Go to your GitHub repository
2. Settings → Secrets and variables → Actions
3. Add new secret: `WIKI_PASSWORD` = `BlackFlag2025!`

### Step 5: Update GitHub Actions Workflow
Create `.github/workflows/deploy.yml` if it doesn't exist:

```yaml
name: Deploy MkDocs
on:
  push:
    branches: [ main ]
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - uses: actions/setup-python@v4
      with:
        python-version: '3.x'
    - run: pip install mkdocs mkdocs-material mkdocs-encryptcontent-plugin
    - run: mkdocs gh-deploy --force
      env:
        WIKI_PASSWORD: ${{ secrets.WIKI_PASSWORD }}
```

### Step 6: Deploy and Test
```bash
git add .
git commit -m "Add password protection to wiki"
git push
```

**Total time: ~2 hours**

---

## Solution 2: Hybrid Public/Private Approach (SUSTAINABLE - 4 hours)

### Step 1: Install Plugin (same as above)
```bash
uv add mkdocs-encryptcontent-plugin
```

### Step 2: Content Strategy
Organize your content:
- **Public:** Homepage, basic campaign info, public statements
- **Private:** Internal strategy, contact lists, tactical planning, actionables

### Step 3: Update mkdocs.yml for Hybrid
```yaml
plugins:
  - search:
      separator: '[\s\-,:!=\[\]()"/]+|(?!\b)(?=[A-Z][a-z])|\.(?!\d)|&[lg]t;'
  - git-revision-date-localized:
      enable_creation_date: true
      type: timeago
  - encryptcontent:
      password_inventory:
        campaign_team: !ENV CAMPAIGN_TEAM_PASSWORD
        strategy_docs: !ENV STRATEGY_PASSWORD
      password_button_text: 'Enter Access Code'
      decryption_failure_message: 'Access denied. Contact campaign coordinator.'
      remember_password: true
      session_storage: true
      search_index: 'clear'  # Allow search on public content
```

### Step 4: Mark Private Content
Add to the top of sensitive documents:

```yaml
---
level: campaign_team
---

# Internal Campaign Strategy
This content is for campaign team members only...
```

### Step 5: Reorganize Navigation
Update your `mkdocs.yml` nav to separate public/private:

```yaml
nav:
  - Home: index.md
  - Campaign Info: 
      - About the Issue: about.md
      - Public Position: position.md
  - Team Resources:
      - Internal Strategy: strategy/internal-strategy.md  # level: campaign_team
      - Action Items: strategy/actionables.md  # level: campaign_team
      - Contact Database: team/contacts.md  # level: campaign_team
```

### Step 6: Environment Variables
Set up multiple passwords:
```bash
# Local testing
export CAMPAIGN_TEAM_PASSWORD="TeamAccess2025"
export STRATEGY_PASSWORD="StrategyDocs2025"
```

### Step 7: GitHub Secrets
Add multiple secrets:
- `CAMPAIGN_TEAM_PASSWORD`
- `STRATEGY_PASSWORD`

### Step 8: Deploy
```bash
git add .
git commit -m "Implement hybrid public/private wiki structure"
git push
```

**Total time: ~4 hours**

## Quick Decision Matrix

| Need | Choose |
|------|--------|
| **Protect everything ASAP** | Solution 1 (EncryptContent) |
| **Public campaign presence + private team area** | Solution 2 (Hybrid) |
| **Simplest possible** | Solution 1 |
| **Long-term flexibility** | Solution 2 |
| **SEO for public content** | Solution 2 |

## Testing Checklist

- [ ] Password protection works on deployed site
- [ ] Session persists across page navigation  
- [ ] Search functionality works as expected
- [ ] Mobile devices can authenticate
- [ ] Password not visible in browser source
- [ ] Deployment pipeline runs without errors

## Troubleshooting

### Common Issues:
1. **Environment variable not working**: Check GitHub Actions logs for `WIKI_PASSWORD` being set
2. **Plugin not loading**: Verify plugin is in requirements and mkdocs.yml syntax is correct
3. **Session not persisting**: Check browser localStorage/sessionStorage settings
4. **Search not working**: Adjust `search_index` setting in plugin config

### Support Commands:
```bash
# Check if plugin is installed
mkdocs plugins

# Test build locally
mkdocs build --verbose

# Clear site and rebuild
rm -rf site/ && mkdocs build
```
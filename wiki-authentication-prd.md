# Black Flag Wiki Authentication - Product Requirements Document

## Executive Summary

This PRD outlines approaches to implement password protection for the Black Flag campaign wiki while maintaining the MkDocs + GitHub Pages architecture. The goal is to secure campaign-sensitive content with minimal complexity while preserving the current deployment workflow.

## Requirements Analysis

### Functional Requirements
- **Single password protection** for entire wiki access
- **Session persistence** across page navigation  
- **Minimal user friction** once authenticated
- **Integration with existing MkDocs Material setup**
- **Compatibility with GitHub Pages static hosting**

### Technical Constraints
- **Public repository** - no plaintext secrets in code
- **Static hosting only** - GitHub Pages limitations
- **No server-side processing** capability
- **Must maintain current deployment pipeline** (`mkdocs gh-deploy`)
- **Browser-based solution** required

### Security Requirements
- **Password not visible** in repository or browser source
- **Session timeout** capability (optional)
- **Protection against basic reconnaissance**
- **Reasonable security** for campaign-sensitive content

## Solution Architecture Options

### Solution 1: MkDocs EncryptContent Plugin ⭐ **RECOMMENDED**
**Ease: 9/10 | Security: 8/10**

**Description:** Use the mature `mkdocs-encryptcontent-plugin` to encrypt all content with AES-256 and decrypt client-side.

**Implementation:**
```yaml
# mkdocs.yml
plugins:
  - encryptcontent:
      global_password: 'campaign-password-2025'
      password_button_text: 'Enter Campaign Password'
      decryption_failure_message: 'Invalid password - contact campaign team'
      remember_password: true
      session_storage: true
```

**Pros:**
- ✅ Mature, actively maintained plugin
- ✅ True content encryption (AES-256)
- ✅ Session persistence via localStorage
- ✅ Zero infrastructure changes
- ✅ Password not in repository (environment variable)
- ✅ Search works after decryption

**Cons:**
- ❌ Password visible in built HTML (can be mitigated)
- ❌ Requires additional dependency

**Security Level:** High - Content is genuinely encrypted

---

### Solution 2: Custom JavaScript Gate with Environment Variables
**Ease: 7/10 | Security: 6/10**

**Description:** Custom login page with password hash stored as environment variable, injected during build.

**Implementation:**
```javascript
// Password hash stored in GitHub Actions secret
// Injected into built site during deployment
const EXPECTED_HASH = '{{ PASSWORD_HASH }}';

function checkPassword() {
    const input = document.getElementById('password').value;
    const inputHash = sha256(input);
    if (inputHash === EXPECTED_HASH) {
        sessionStorage.setItem('authenticated', 'true');
        showContent();
    }
}
```

**Pros:**
- ✅ Full control over implementation
- ✅ Password hash not in repository
- ✅ Can integrate seamlessly with Material theme
- ✅ Session persistence

**Cons:**
- ❌ Content still accessible to determined users
- ❌ More custom code to maintain
- ❌ Hash visible in built site

**Security Level:** Medium - Obfuscation rather than encryption

---

### Solution 3: GitHub Actions Dynamic Build
**Ease: 4/10 | Security: 9/10**

**Description:** Use GitHub Actions to build different versions based on authentication, with protected content only in authenticated builds.

**Implementation:**
- Separate content in `private/` directory
- GitHub Actions builds public + private content based on authentication
- Deploy to different URLs or use branch-based deployment

**Pros:**
- ✅ True content separation
- ✅ High security - protected content not in public builds
- ✅ Flexible access control

**Cons:**
- ❌ Complex deployment pipeline
- ❌ Requires significant workflow changes
- ❌ May need multiple deployment targets

**Security Level:** Very High - Content truly separated

---

### Solution 4: Hybrid Approach - Public/Private Split
**Ease: 6/10 | Security: 7/10**

**Description:** Keep general campaign info public, move sensitive content to password-protected section using EncryptContent plugin.

**Implementation:**
```yaml
# mkdocs.yml
plugins:
  - encryptcontent:
      password_inventory:
        campaign_internal: 'internal-password-2025'

# In sensitive pages:
---
level: campaign_internal
---
```

**Pros:**
- ✅ Balanced approach - public face + protected internals
- ✅ SEO benefits for public content
- ✅ Simpler than full protection
- ✅ Granular control

**Cons:**
- ❌ More complex content management
- ❌ Need to classify all content

**Security Level:** High for protected content, none for public

---

### Solution 5: External Hosting with Basic Auth
**Ease: 3/10 | Security: 10/10**

**Description:** Move to hosting provider supporting server-side authentication (Netlify, Vercel, etc.)

**Implementation:**
- Deploy to Netlify with password protection
- Use `_redirects` file for basic auth
- Maintain MkDocs build process

**Pros:**
- ✅ True server-side authentication
- ✅ Industry-standard security
- ✅ Professional authentication flows

**Cons:**
- ❌ Abandons GitHub Pages
- ❌ Potential hosting costs
- ❌ More complex deployment

**Security Level:** Very High - Server-side protection

## Recommended Implementation Ranking

### Rank 1: MkDocs EncryptContent Plugin
**Best balance of ease and security for this use case**

- Fastest implementation (2-3 hours)
- Genuine content protection
- Stays within MkDocs ecosystem
- Professional appearance

### Rank 2: Hybrid Public/Private Approach  
**Best long-term strategy**

- Allows public campaign visibility
- Protects sensitive internal content
- More sustainable for campaign growth

### Rank 3: Custom JavaScript Solution
**If you need full control**

- Complete customization possible
- Good for specific branding needs
- Moderate security

## Implementation Timeline

### Phase 1: Quick Protection (1-2 days)
1. Implement EncryptContent plugin
2. Set up environment variable for password
3. Test deployment pipeline
4. Verify session persistence

### Phase 2: Optimization (1 week)
1. Evaluate hybrid approach
2. Implement better password management
3. Add session timeout
4. Custom styling integration

## Technical Specifications

### Password Management
- Use GitHub Actions secrets for sensitive values
- Environment variable injection during build
- No plaintext passwords in repository

### Session Handling
- localStorage/sessionStorage for persistence
- Configurable timeout (default: 24 hours)
- Clear session on browser close (optional)

### User Experience
- Single password entry point
- Seamless navigation post-authentication
- Clear authentication status indicator
- Mobile-responsive login interface

## Security Considerations

### Threat Model
- **Primary threat:** Casual discovery of campaign content
- **Secondary threat:** Competitor intelligence gathering
- **Acceptable risk:** Determined technical attack

### Mitigation Strategies
- Content encryption over obfuscation
- Environment variable password storage
- Session management
- Regular password rotation capability

## Success Metrics

- **Implementation time:** < 4 hours for basic protection
- **User friction:** Single password entry per session
- **Deployment compatibility:** Zero changes to existing pipeline
- **Security effectiveness:** Content not accessible without password

## Appendix: Quick Start Commands

```bash
# Install EncryptContent plugin
pip install mkdocs-encryptcontent-plugin

# Add to mkdocs.yml
plugins:
  - encryptcontent:
      global_password: !ENV WIKI_PASSWORD

# Set environment variable for local testing
export WIKI_PASSWORD="your-campaign-password"

# Deploy normally
mkdocs gh-deploy
```

---

*This PRD provides a comprehensive analysis of authentication options for the Black Flag campaign wiki, prioritizing rapid implementation while maintaining security appropriate for political campaign content.*
# Changelog since v2.0.18
- Merge pull request #192 from brenner-tobias/options_clean-up_part1_quick-tunnel_reset

Remove "reset-cloudflared_files" and "quick_tunnel" options 
- Remove "reset-cloudflared_files" and "quick_tunnel" options 
- Merge pull request #189 from AlecRust/patch-1

Update docs with mentions of security 
- Fix lint 
- Update docs with mentions of security

It seems common to set up WAF rules and utilise Cloudflare Access as an interstitial page before redirecting to Home Assistant.

This updates the docs to include mention of these approaches, with links.

I've also moved this under the main setup instructions. First time I read it I assumed "Securing access to the Cloudflare account" was part of initial setup, but it actually seems more of a troubleshooting section. 
- Update config.yml 

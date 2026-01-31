# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Shadowrocket proxy configuration repository for iOS. Shadowrocket is a rule-based proxy utility for iOS devices.

## Configuration Files

Each `.conf` file contains sections:
- **[General]** - Global settings (DNS servers, bypass rules, IPv6 settings)
- **[Rule]** - Traffic routing rules determining what goes through PROXY vs DIRECT
- **[Host]** - Custom host mappings

### ru_direct.conf

"Proxy blocked services, direct everything else" approach:
- **PROXY** - Services blocked/restricted in Russia: YouTube, Instagram, TikTok, Spotify, Facebook, LinkedIn, OpenAI, Discord, WhatsApp, Google services, GitHub Copilot
- **DIRECT** - AppStore, iCloud, Telegram, `.ru` domains, LAN addresses
- **FINAL,DIRECT** - Default fallback

### ru_proxy.conf

"Direct local, proxy everything else" approach:
- **DIRECT** - Domains `.ru`, `.рф`, `.su`, `.cn`, Apple services, LAN addresses
- **FINAL,PROXY** - All other traffic goes through proxy

## External Rule Sets

Rules are pulled from [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Shadowrocket) repository. When adding new services, find the rule set in that repository and use:
`https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/{ServiceName}/{ServiceName}.list`

## Configuration Update

The config auto-updates from:
`https://raw.githubusercontent.com/ar2r/shadowrocket-config/main/ru_direct.conf`
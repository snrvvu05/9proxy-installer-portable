# 9proxy download for pc: Windows installer vs portable ZIP, setup steps, and the plan that fits your workload

Most people searching for a 9Proxy download for PC are stuck on the same three things: the official site keeps the client behind an account, there are half a dozen mirror sites offering "9Proxy for Windows" installers that have nothing to do with 9Proxy, and nobody explains that the desktop app is only needed for one of the two proxy models. So here's the whole thing in order — what you download, what your machine needs, how to install it, and which package actually makes sense once the client is running.

Quick version: there are exactly two Windows builds, an installer and a portable ZIP. Both come from 9proxy.com. There is no official Android app, so any "9Proxy APK" you find is someone else's file.

## What the 9Proxy PC app actually does

9Proxy is a residential proxy network with a pool advertised at 20 million+ IPs across 90+ countries, supporting HTTP(S) and SOCKS5. The desktop client is a local port-forwarding tool: you pick residential IPs in the app, it binds each one to a port on your machine, and you point whatever software you're running at something like `127.0.0.1:8000`. That means programs with no built-in proxy settings still get routed, because from their point of view they're talking to localhost.

A user on a proxy forum described the workflow roughly the same way — select the IP and country you need, let the app generate a list of localhost addresses on separate ports, then paste that list into your automation or anti-detect tool. It's a workable setup, and it's the reason people download the client at all instead of just copying credentials into a browser.

Worth knowing before you install anything: the app is only mandatory for IP-based packages. If you buy a bandwidth (GB) package, everything runs from the web dashboard — proxy generator, rotation settings, exports — with no software on your machine at all. More on that below, because it changes which package you should buy.

## System requirements

The Windows build is not demanding, but it does have a couple of hard edges:

- Windows 8, 8.1, 10, or 11 — 64-bit recommended
- 2 GHz CPU or faster
- 4 GB RAM minimum
- 200 MB free disk space
- Administrator rights if you're using the installer version (the portable build skips this in most cases)
- .NET Framework 4.7.2 or later, which is what makes the difference between "app opens" and "app does nothing" on older systems

If you're running Windows 7 or a 32-bit install, plan on a different machine. There's no documented build for either.

## Installer or portable? Pick based on where the machine lives

| Build | How it behaves | Reason to choose it |
| --- | --- | --- |
| Windows Installer (.exe) | Standard install to `C:\Program Files\9Proxy` by default, desktop shortcut, auto-updates | Your own machine, and you want it to be a normal installed app |
| Windows Portable (.zip) | Extract and run, no registry changes, no admin prompt for basic use, still auto-updates via in-app notification | Shared or locked-down PCs, USB drives, or when you don't want a permanent install |

One detail that trips people up: the two builds store their settings separately. If you install both, the IP lists and configuration won't carry over between them. Run one or the other unless you have a specific reason not to.

### Installing the .exe

1. Download `9proxy-windows-installer.exe`.
2. Right-click it and choose **Run as administrator** — skipping this is the most common cause of the setup failing partway through.
3. Work through the wizard: accept the licence, pick an install directory if the default doesn't suit you, decide on the desktop shortcut.
4. Click **Install**, then **Finish** to launch it right away. You can also start it later from the Start menu.
5. Log in with your 9Proxy account. The IP list loads in the client.
6. Test a connection before you wire it into anything important — bind an IP, check it, then deploy.

### Installing the portable ZIP

1. Download `9proxy-windows-portable.zip` from the same download page.
2. Right-click → **Extract All** to a folder you control, for example `D:\Apps\9ProxyPortable`.
3. Open the extracted folder and run `S9Proxy.App.exe`.
4. Sign in. When a new release drops, the app shows an update prompt — click Update and it handles the rest.

The one place the portable build still behaves like a normal program is system-wide proxy configuration, which on Windows can require elevated rights. Per-app routing through localhost ports doesn't.

## The two things that stop a clean install

**Windows SmartScreen blocks the file.** Click **More info**, then **Run anyway**. If SmartScreen is flagging a file you downloaded from somewhere other than the official site, don't run it at all — that's the whole reason the mirror sites are a bad idea.

**The app installs but won't launch.** Check .NET Framework 4.7.2 first. If that's fine, open Task Manager and look for an existing `S9Proxy.App` process. 9Proxy can keep running in the background after you close the window, and a leftover process means a second launch silently does nothing. End the task and start it again.

## Sign up before you download, because the client lives behind your account

The download links sit on the official site, but the dashboard version of the client — and the packages, balance, share codes, and IP list — only appear once you're logged in. Registering through an invite link is also where the referral discount gets attached to your account, which is cheaper than showing up empty-handed:

👉 [Create your 9Proxy account and register with the invite code applied](https://bit.ly/9-Proxy)

9Proxy's affiliate program advertises a 5% discount for users who sign up through a referral link, plus a limited free trial for new accounts when capacity allows. Treat the trial as a bonus rather than a plan — availability varies.

If you bought credit in the form of a share code from a reseller, redeem it on the dashboard's share code page before doing anything else. The balance lands on your account immediately, and only then does the client show usable IPs.

## Do you even need the client?

This is the decision that matters more than installer versus portable, and it's the part most download guides skip.

|  | IP-based packages | GB-based packages |
| --- | --- | --- |
| How you're billed | Per IP, unlimited bandwidth while the IP is active | Per gigabyte of traffic |
| Client required | Yes — desktop app does local port forwarding | No — works straight from the dashboard |
| Endpoints | One IP = one slot when forwarded | Unlimited proxy endpoints generated on demand |
| Session behaviour | Set IP kept until it drops, roughly a few hours up to ~24h | Sticky or rotating, configurable per session |
| Authentication | App-managed, with optional proxy authentication | Username/password or IP whitelist |
| Expiry | Unused IPs don't expire | 180 days on standard plans, unlimited on Enterprise |
| Targeting | Country, city, ISP, ZIP | Country, state, city, ZIP, ISP |

If your task is account-based — logged-in sessions, shopping flows, anything where the same IP has to persist — you want IP-based packages and the client. If you're rotating through thousands of endpoints for scraping, ad verification, or geo-checks, the GB model is cheaper per request and you can skip the download entirely.

There's also a middle path: Proxy2Web runs on standard username/password credentials in the browser, so a quick manual geo-check needs zero installation. And if your mobile devices are the ones holding the residential IPs, ProxyHub handles that — ProxyHub Pro lives inside the desktop app, ProxyHub Lite runs on the device itself.

## Full 9Proxy pricing

Prices below are the published rates after 9Proxy's June 1, 2026 adjustment, which changed IP-based and bundle pricing. GB-based pricing was left untouched in that update.

**IP-based packages** (unlimited bandwidth per IP, unused IPs don't expire):

| Package | Effective rate | Total | Order |
| --- | --- | --- | --- |
| 100 IPs | $0.24/IP | $24 | [Get the 100-IP package](https://bit.ly/9-Proxy) |
| 500 IPs | $0.144/IP | $72 | [Get the 500-IP package](https://bit.ly/9-Proxy) |
| 1,000 IPs + 500 bonus | $0.084/IP | $126 | [Get the 1,000 + 500 bonus IP package](https://bit.ly/9-Proxy) |
| 2,500 IPs | $0.084/IP | $210 | [Get the 2,500-IP package](https://bit.ly/9-Proxy) |
| 5,000 IPs | $0.072/IP | $360 | [Get the 5,000-IP package](https://bit.ly/9-Proxy) |
| 15,000 IPs | $0.048/IP | $720 | [Get the 15,000-IP package](https://bit.ly/9-Proxy) |
| 25,000 IPs | $0.035/IP | $863 | [Get the 25,000-IP package](https://bit.ly/9-Proxy) |
| 50,000 IPs | $0.029/IP | $1,438 | [Get the 50,000-IP package](https://bit.ly/9-Proxy) |

**Business IP packages**, for operations running six figures of IPs: 100,000 IPs at $2,300, 200,000 IPs at $4,140, and 500,000 IPs at $8,625.

**GB-based packages** (180-day validity, unlimited endpoints):

| Package | Rate | Total | Order |
| --- | --- | --- | --- |
| 5 GB | $3.00/GB | $15 | [Buy 5 GB of traffic](https://bit.ly/9-Proxy) |
| 50 GB + 5 GB bonus | $2.10/GB | $105 | [Buy the 50 GB + 5 GB package](https://bit.ly/9-Proxy) |
| 100 GB | $1.50/GB | $150 | [Buy 100 GB of traffic](https://bit.ly/9-Proxy) |
| 200 GB | $1.00/GB | $200 | [Buy 200 GB of traffic](https://bit.ly/9-Proxy) |
| 1,000 GB | $0.80/GB | $800 | [Buy 1,000 GB of traffic](https://bit.ly/9-Proxy) |
| 2,000 GB | $0.75/GB | $1,500 | [Buy 2,000 GB of traffic](https://bit.ly/9-Proxy) |

At the top of the GB ladder the rate falls to $0.68/GB. Enterprise GB plans drop the 180-day limit entirely, add team mode (one owner plus up to five members with shared bandwidth that doesn't expire), per-member traffic controls, activity logs, and unlimited share-code creation. Enterprise pricing is quoted rather than listed.

**Bundle packages** mix both models:

| Bundle | Contents | Price | Order |
| --- | --- | --- | --- |
| Starter | 100 IPs + 5 GB | $30 | [Get the Starter bundle](https://bit.ly/9-Proxy) |
| Popular | 1,500 IPs + 50 GB | $180 | [Get the Popular bundle](https://bit.ly/9-Proxy) |
| Pro | 5,000 IPs + 500 GB | $720 | [Get the Pro bundle](https://bit.ly/9-Proxy) |

9Proxy's own payment documentation shows the 5,000 IP + 500 GB bundle carrying a 16.28% discount, $140 off the $860 figure on the checkout screen. Bundle traffic keeps the same 180-day validity as standalone GB plans.

## Which package to actually buy

If you're downloading the PC client for the first time, the sensible entry point is the 100 IP package at $24 or, if you want to see how the client behaves on a real workload, the 1,000 + 500 IP tier at $126. That tier is the one 9Proxy labels as the most popular, and the math supports it: the effective per-IP cost drops by roughly two-thirds compared with the smallest package, without committing you to five figures' worth of inventory.

Two buying rules worth remembering. First, don't stockpile IPs you don't need yet — the IP-based model is prepaid inventory, and even though the balance never expires, $360 sitting unused isn't free money. Second, if your workflow is request-heavy but light on data (search result checks, price lookups, geo-verification), paying $0.24 per IP is expensive compared with $3.00/GB on the small GB tier. The two models are not interchangeable, and treating the cheaper headline number as the cheaper option is the most common mistake here.

## What reviewers and users say

Third-party coverage is positive but not unanimously so. ProxyLook's comparison directory rates 9Proxy 3.9 out of 5 and positions it as a budget residential option that wins on price per gigabyte against most of its comparison set. Caproxy scores it higher on its editorial scale, around 4.78, with a 4.33 user score — though that user figure comes from only a handful of reviews, so don't read much into the decimal.

User comments in the same directory are mixed in a way that's worth knowing about before you commit a budget. One reviewer in March 2026 reported stable, fast IPs and good results with anti-detect tools like Dolphin Anty and AdsPower at a reasonable price. Another, in July 2026, reported the service being unreachable for about a week, and the site's own reply said it wasn't clear whether the cause was technical or network-related. 9Proxy is a smaller operation than the enterprise-tier providers, and that kind of incident is the trade-off that comes with the price.

Two features exist specifically to blunt the IP-lifetime problem: proxies that fail within the first 60 seconds of activation can be credited back, and the Today List lets you reuse any IP you've already touched in the last 24 hours at no extra charge. On a network where individual residential IPs typically live a few hours and occasionally die much sooner, both of those matter more than they sound.

Payments go through credit cards, bank cards, crypto (USDT, BTC, ETH, LTC, DOGE and others), Alipay, Apple Pay, and Google Pay. Support is human-staffed 24/7.

## Questions that come up before the first install

**Is the app a subscription?** No. Packages are prepaid balance — you buy IPs or gigabytes once and use them until they're consumed. IP balances don't expire; GB balances last 180 days on standard plans.

**Can I use it on a Mac?** There's a macOS build on the same download page. The install steps differ but the login and IP-list behaviour is the same.

**Is there a 9Proxy Android app?** Not an official one. Mobile device proxies are handled through ProxyHub, which is a different tool with a different purpose. Any APK offered as "9Proxy for Android" is third-party and shouldn't be installed.

**Do I need admin rights?** Only for the installer build. The portable ZIP gets you running without them for most configurations.

**How many devices can I connect?** There's no per-device licence on the desktop client — the constraint is your IP or traffic balance. Account sharing and sub-accounts are supported through share codes.

## Before you click download

Get the account sorted first, because that's where the client, the balance, and the invite-code discount all live, and it takes about two minutes:

👉 [Sign up for 9Proxy with the invite code and download the Windows client](https://bit.ly/9-Proxy)

Then pick the build that matches the machine — installer if it's yours, portable if it isn't — install, sign in, and test a single IP before you point anything important at it. Skip that last step and you'll be debugging a proxy problem when the actual issue is a firewall rule.

# Minecraft Bedrock server hosting: RAM, slots and the real monthly price for a 5–20 player world

Search "Minecraft Bedrock server hosting" and you get a wall of guides written for the Java edition. RAM calculators built around modpacks. Advice about plugins and Paper forks. Almost none of it applies to Bedrock, because Bedrock Dedicated Server (BDS) is a different program with a different memory profile, a different network protocol, and a completely different set of things that will ruin your evening.

So here's the version that actually corresponds to the search: what a Bedrock server needs, how much RAM each player count really eats, why the hosting panel matters more than the CPU badge, and what a provider like Rainyun sells for this exact job — including the prices, the trials and the refund window.

## Bedrock is not Java, and that changes your shopping list

Three differences matter when you're choosing a host.

**There are no mods, only add-ons.** Bedrock runs behavior packs and resource packs, not Forge or Fabric mods. A 200-mod Java pack and a Bedrock realm with a few add-ons are not comparable workloads, so ignore RAM charts built for modded Java servers. On Bedrock, the memory ceiling tends to come from entity count, simulation distance and the number of connected players — not from a pile of loaded mods.

**It's UDP, not TCP.** Bedrock uses UDP on port 19132 by default. Some hosts that advertise "Minecraft hosting" only whitelist TCP 25565 because they built their stack around Java. If a provider can't tell you clearly that Bedrock UDP is supported end-to-end, that's your answer.

**Console players complicate things.** Windows, Android, iOS and most Bedrock clients can add a server by typing an address. Consoles (Switch, PlayStation, Xbox) generally can't — they either stick to the featured servers or need DNS-level workarounds. Worth knowing before you promise your group a custom world.

## How much RAM a Bedrock server actually needs

The official Bedrock Dedicated Server documentation is unusually blunt about this: on Windows 10 or Windows Server, budget around 6 GB of memory for the operating system *and* the server combined, and expect that figure to climb past ten players . That's the Windows overhead talking. On Linux the same server runs in a much smaller footprint, which is why most game panels use Linux containers underneath.

Community figures land where you'd expect for vanilla play — roughly 2 GB covers a vanilla server up to about ten players . Practical tiers, cross-referencing both:

| Players | Vanilla Bedrock | With add-ons / higher simulation distance |
| --- | --- | --- |
| 1–5 | 2 GB | 3–4 GB |
| 6–10 | 2–4 GB | 4–6 GB |
| 11–20 | 4–6 GB | 6–8 GB |
| 20+ | 8 GB+ | 8–12 GB |

Two caveats. First, simulation distance is a bigger RAM lever than player count on Bedrock — cranking it up to keep distant mobs ticking costs memory fast. Second, CPU single-core clock speed matters more than core count for a small server. Minecraft's server loop is heavily single-threaded; four fast cores beat sixteen slow ones every time. A provider selling old 2.0 GHz Xeons as "16 vCPU" is selling you something a Bedrock server can't use.

## The three real options, and who each one suits

**Official Realms.** Cheapest and simplest, capped at 10 players plus the owner, and you don't touch a config file. You also don't get add-on freedom, backups you control, or any way to run more than one world. Fine for a family; useless at 20 players.

**A VPS you manage yourself.** You get root, you install BDS, you handle systemd, you handle backups, you handle the inevitable night when the world corrupts. This is the cheapest path per gigabyte and the most expensive path in hours.

**A game panel.** The panel installs the Bedrock server, exposes the port, and gives you a console and file manager in a browser. This is the middle option, and it's what the "Minecraft hosting" market mostly sells. Rainyun sits here — it's a Chinese cloud provider founded in 2018 that runs cloud servers, bare-metal machines and a dedicated game cloud line tuned for high-clock CPUs and Chinese BGP routing .

## What to check before you pay anyone

The provider matters less than these five things:

1. **Bedrock listed as an actual one-click option.** Not "you can install it manually." Rainyun's panel ships Bedrock, Java, Terraria, Don't Starve and Palworld as preinstalled templates, and the company publishes a dedicated walkthrough for standing up a Bedrock server on its VPS line .
2. **The billing model.** Rainyun is unusual here: alongside fixed monthly billing it offers dynamic billing, where CPU usage is metered and you pay for what the server actually consumes . If your group plays four evenings a week, that can beat a flat rate — the tradeoff is a bill that moves around.
3. **Port control.** Bedrock needs UDP 19132 reachable from the internet. Rainyun's NAT public IP option opens 15 ports, which is more than enough for one server plus a query port or two .
4. **Backups.** Ask how often, and whether restoring is self-service. A weekly backup is decoration if your world dies on Tuesday.
5. **Region vs. your players.** Rainyun's network is built around Chinese BGP routes with additional overseas regions including Japan and South Korea . If your group is in Europe or North America, latency is the one number you should test before committing months of prepaid billing. The panel makes this easy to trial cheaply.

> Rainyun runs a ¥1 one-day trial on its cloud servers  and a 7-day no-questions refund policy on game cloud , so testing ping with your actual players costs less than a coffee.

## What Rainyun's game cloud costs for Bedrock

This is where the honest answer is messier than a marketing page would like. Rainyun sells several distinct game cloud lines — a managed panel product, a bare VPS version, and per-player-count templates across different CPU brands and regions. Public write-ups therefore quote different entry points, because they're describing different things.

Here's what the sources say, with the context attached:

| Line | Typical spec | Published price | Notes |
| --- | --- | --- | --- |
| Player-tier template, ~5 people | 2 vCPU / 4 GB / 50 Mbps | ~¥30/month | Third-party summaries of the small-friend-group tier |
| Player-tier template, ~10 people | 4 vCPU / 8 GB / 50 Mbps | ~¥75/month | Same sources |
| Player-tier template, ~15 people | 6 vCPU / 12 GB / 50 Mbps | ~¥130/month | Same sources |
| Game cloud panel (RGP), entry | 2 vCPU / 4 GB | from ~¥58/month | Annual payment runs about 30% off; the 2C4G panel plan works out near ¥487/year |
| Game cloud bare VPS, entry | 2 vCPU / 4 GB | from ~¥68/month | You run your own panel; more control, slightly more work |
| Ultra tier | 6 vCPU / 12 GB | from ¥148/month | Aimed at 20+ vanilla players |
| General cloud server (RCS) | Flexible, not game-tuned | from ¥15/month | Cheapest path if you're comfortable managing BDS yourself |
| Dynamic billing | Usage-metered CPU | Varies | Cheaper for intermittent play, less predictable |

Two things worth flagging. Prices are quoted in Chinese yuan, which matters if you're paying from outside China — check what your card actually gets charged. And game cloud inventory moves; community posts mention tiers going out of stock and restocking, with evening hours often the best time to check .

Annual billing is where the arithmetic gets interesting. Roughly 30% off for a year upfront brings the entry panel plan to about ¥40/month equivalent . If your group has survived longer than one summer, that's a real discount. If it's a school-holiday server, pay monthly.

New accounts also get a first-month 50% discount, distributed through limited coupon batches on the homepage rather than a permanent price cut .

## Setting up Bedrock on a panel

The workflow is short enough to describe properly:

1. Pick the game cloud line, choose a region, and select the Minecraft template — Bedrock specifically, not Java.
2. Choose fixed or dynamic billing. Fixed for a permanent server, dynamic for a server that idles most of the week.
3. Set the public IP option. NAT gives you 15 ports and is enough for one Bedrock server; a dedicated IP is only worth it if you need the clean address.
4. Boot the instance and set the difficulty, world seed, player limit and simulation distance in the panel.
5. Share `your-address:19132` with your group. Windows and mobile players add it directly; console players may not be able to.
6. Turn on backups before you build anything you'd be upset to lose.

The whole thing is a browser session, not an SSH session. Rainyun publishes its own documentation and forum tutorials for both the panel and the manual Bedrock route, so you're not reverse-engineering the interface .👉 [Check the current Rainyun game cloud plans and live stock](https://www.rainyun.com/MzA2MTc2_)

## Which tier fits your group

Money aside, the decision tree is straightforward.

- **2–5 friends, vanilla, evenings only.** The smallest tier or a dynamic-billed instance. Resist the urge to buy 8 GB "for headroom" — a Bedrock vanilla server with five players will not use it, and dynamic billing will charge you less for exactly this scenario.
- **8–10 players, a few add-ons, a base you care about.** 4 cores / 8 GB, annual billing if you're confident the group lasts.
- **15–20 players or a high simulation distance.** 6 cores / 12 GB, and check the CPU clock speed rather than the core count.
- **You want to run your own panel, schedule restarts, manage multiple worlds.** The bare VPS game cloud line, or a general cloud server if you want to build the stack yourself.

One thing to be clear-eyed about: Rainyun's documentation, panel and support are Chinese-first. If you're an English-only admin and the panel's untranslated corners will bother you, factor that in — the product is real and the prices are low, but the audience it was built for is in China.

👉 [See Rainyun's pricing and current promotions](https://www.rainyun.com/MzA2MTc2_)

## Questions people ask before buying

**Is Bedrock harder to host than Java?** No, it's easier. No Java runtime, no heap tuning flags, no launcher mismatch. BDS is one executable and a config file. The complication is the UDP port and console-client access, not the installation.

**Can I run Bedrock and Java on the same plan?** Not on the same port and not from one process. Geyser bridges the two so Bedrock clients can join a Java server, which is a different project from hosting BDS natively. If cross-play is your actual goal, that's the route to look at.

**Does 2 GB really work?** For vanilla with under ten players, yes . Turn simulation distance up and add automated farms, and it gets tight quickly.

**What about the 6 GB figure?** That's the Windows requirement including the operating system, not the server's isolated footprint . It's also a reason Linux-based panels can offer smaller plans.

**Can I get my money back?** Rainyun lists a 7-day refund window , and the ¥1 daily trial lets you test ping before committing at all . Test with your actual players in their actual locations; a server that feels fine to you in one city can be unplayable for a friend in another.

## The short version

Bedrock server hosting comes down to three things: enough RAM for your player count and simulation distance, CPU clock speed rather than core count, and a panel that treats Bedrock as a first-class option rather than a manual install. Rainyun covers all three with entry prices in the ¥30–148/month range depending on the line and tier, dynamic billing for servers that idle, a nearly free trial, and a refund window that makes testing low-risk .

Buy the smallest tier that matches your group, test ping with real players during the trial period, and only then decide whether annual billing's discount is worth locking in. That's the whole game.

# Cheap Frankfurt VPS: What €3.49 a Month Really Buys, Which Extras Move the Bill, and Is 1 GB of RAM Enough?

Frankfurt entry plans currently start at €3.49, $3.89, $3.99, €4.99 and $7.71 a month across the five providers that publish their prices. That is two currencies with no published exchange rate between them, so treat the ordering as approximate, and the individual numbers as exact.

The monthly sticker is also the least informative figure on any of those pages. Two plans that both look like “about four a month” can end up €5 apart once you add a second IPv4, a Windows image, or the backup schedule you assumed was included. What follows is the current market benchmark, the add-ons that get billed separately, and a sizing rule for each common workload, so you can pick a plan without paying for capacity you will never touch.

> **Quick rule of thumb.** A small site, a WireGuard endpoint or a monitoring box runs fine on 1 vCPU / 1 GB. Anything with a database that takes real writes should start at 4–8 GB, where the price per GB drops sharply. Windows RDP needs at least 2 vCPU before RAM even matters.
>
> 👉 [See AkkoCloud's current Frankfurt plans and prices](https://bit.ly/akkocloud)

## The price table, before add-ons

| Provider | Cheapest published plan | Starting price | Traffic | Hourly billing |
| --- | --- | --- | --- | --- |
| Wolkra (fra1) | 1 vCPU / 1 GB / 15 GB | €3.49/mo | Unmetered, fair use | Yes, capped at monthly price |
| Arct Cloud | Entry Frankfurt plan, AMD EPYC Milan 7003 | $3.89/mo | Not stated on the plan page | Not listed |
| OliveVPS (Interxion FRA8) | 1 vCPU / 1 GB / 25 GB NVMe | $3.99/mo | 1 TB, then $0.005/GB | Not listed |
| EDIS Global (Equinix FR5) | 1 vCPU / 1 GB / 15 GB | €4.99/mo | 1 TB plus 100 GB starter credit | Not listed |
| LightNode | 1 vCPU / 2 GB / 50 GB NVMe | $7.71/mo | 1 TB | Yes, $0.012/h |

Three details in that table matter more than the prices.

Wolkra bills per started hour against a prepaid balance, caps the charge at the monthly price, and charges no setup fee with no contract. Traffic is not billed at all.

Arct Cloud states plainly that it has no free tier in Frankfurt, so $3.89 is the floor rather than a promotional entry point that disappears after a trial.

The port speed figures are not comparable. Wolkra's “up to 10 Gbit/s” is a shared port, EDIS lists 2×10 Gbps uplinks per plan, and OliveVPS and LightNode sell 1 Gbps. A bigger number in that column does not mean a faster single server.

## The number the plan pages bury: price per GB of RAM

Divide each monthly price by its RAM and the entry tiers stop looking like the cheap option. Wolkra's €3.49 plan is the worst value per GB in its own lineup at €3.49/GB; the 8 GB plan at €12.49 works out to **€1.56/GB**. Paying €9 more than the entry plan buys 8× the memory, a second vCPU and 35 GB more disk.

| Provider | Plan | RAM | Monthly price | Per GB of RAM |
| --- | --- | --- | --- | --- |
| Wolkra | S0 | 1 GB | €3.49 | €3.49 |
| Wolkra | S3 | 8 GB | €12.49 | €1.56 |
| EDIS Global | 4 GB tier | 4 GB | €14.69 | €3.67 |
| OliveVPS | Premium | 4 GB | $15.99 | $4.00 |
| LightNode | Start | 2 GB | $7.71 | $3.86 |
| LightNode | Premium | 8 GB | $27.70 | $3.46 |

EDIS and LightNode show the same direction with a much smaller spread, and OliveVPS sits flat at roughly $4/GB across its three plans. These are list-price divisions, not invoices. IPv4, backups and Windows licensing all sit outside them, which is the next section.

## What a cheap Frankfurt VPS does not include

**IPv4 is billed separately at two of the five.** Wolkra includes IPv6 and charges €0.89/month for the primary IPv4, which puts the real entry cost at €4.38. EDIS charges €5/month for each extra IPv4, up to 10 addresses. OliveVPS includes a static IPv4 plus a routed /64, and LightNode includes a dedicated German IP.

**Windows has a hardware floor, not just a licence fee.** Arct requires at least 2 vCPU for Windows Server and administrator RDP. OliveVPS's $3.99 Starter plan is Linux-only, and Windows begins at the $7.99 Pro plan, which the company says already includes the licensing surcharge. EDIS offers Windows Server 2025, 2022 and 2019 plus Windows 10 and 11 images across its plan range with OS reinstalls at any time. LightNode sells Windows deployments with RDP access.

**Traffic overage is real money at one provider.** OliveVPS bills $0.005/GB beyond the allowance, so an extra terabyte costs about $5. EDIS gives every VPS a 100 GB starting credit and runs a traffic pool that never expires. Wolkra does not meter traffic but caps port speed instead. LightNode bundles 1–4 TB depending on tier.

👉 [See the traffic allowance on AkkoCloud's Frankfurt plans](https://bit.ly/akkocloud)

**Backups are a percentage, not a line item you can guess.** Wolkra prices daily backups at 20% of the server price with 7 restore points, which works out to about €0.70/month on the €3.49 plan and about €2.50/month on the 8 GB plan. Snapshots are on demand and priced separately again.

**Vertical scaling has its own price list.** EDIS charges €10/month for one extra vCPU (up to 8 cores) and from €3.60/month for a storage boost of 10–400 GB, with a 500 GB ceiling per VPS.

## Hourly billing does not lower a monthly bill

Two providers publish hourly rates, and both rates cost more than the monthly price if you leave the server running.

Wolkra's smallest plan is €0.0056/hour. Multiply by 730 hours in a month and you get €4.09, above the €3.49 cap. LightNode's $0.012/hour comes to $8.76 over 730 hours against a $7.71 monthly price.

The cap is the point. Hourly billing exists so you can create the smallest box, check latency from the network your users actually sit on, and delete it an hour later for a few cents. Wolkra says as much itself: run a two-hour test before committing. For anything that stays up, the monthly price is what you pay.

## Sizing by workload

**Static site or a low-traffic blog.** 1 vCPU / 1 GB / 15–25 GB covers it. WordPress with a database and a caching plugin fits in 1 GB but not comfortably, so keep swap enabled and watch memory before you add plugins.

**WireGuard, a proxy or uptime monitoring.** 1 vCPU / 1 GB is more than enough; the traffic model is the real constraint. A metered 1 TB allowance is about 33 GB a day, which is a lot of tunnel traffic and not a lot of video.

**An application with a database.** Go straight to the 4–8 GB tiers and use the per-GB table above. The 8 GB Wolkra plan at €12.49 costs €3.57 more than the 4 GB plan at €8.99 and doubles the RAM, which is the cheapest upgrade in this entire comparison.

**Windows remote desktop.** Budget at least 2 vCPU before anything else. That means Arct's 2 vCPU minimum, OliveVPS from $7.99, a LightNode Windows deployment, or an EDIS plan with a Windows image.

**Several servers on one private network.** Wolkra runs private networks with your own IP ranges, NAT gateways for outbound access on private-only servers, floating IPs, placement groups, layer 4 and HTTP load balancers, and free stateful firewalls, all inside fra1. If your architecture needs any of that, it constrains the choice more than price does.

Vendor performance figures are worth reading with the label attached. OliveVPS publishes 1–3 ms local latency, 16 ms to London and 240 ms to Tokyo, plus Geekbench 6 scores around 2,250 single-core and 4,400 multi-core on its Pro tier and roughly 8,000 Postgres TPS. EDIS published a 16,699 Mbps download and 9,398 Mbps upload Speedtest from its Frankfurt host platform, and states in the same breath that this is not a guarantee of what an individual VPS will get to any destination. Both sets are the operators' own numbers.

## If your users are in mainland China, the price table is the wrong table

The five plans above peer through public exchanges such as DE-CIX, which is exactly what you want for visitors in Germany, Austria, Switzerland and the rest of Europe. From mainland China those routes degrade badly at peak hours, and no amount of extra RAM fixes it.

AkkoCloud's Frankfurt line runs on CN2 GIA, the premium China Telecom path, alongside a London line and a US location. It sells on monthly, quarterly and annual cycles. If most of your traffic originates in China, routing is the first thing you are paying for and the €3.49-to-$4.99 band above stops being the relevant comparison.

👉 [View AkkoCloud's current Frankfurt configurations and prices](https://bit.ly/akkocloud)

## Six checks before you pay

1. **Currency and cycle.** €3.49 and $3.89 are not the same money, and an annual price is only cheaper if you keep the server for the year.
2. **Is IPv4 included?** It is €0.89/month at Wolkra and €5/month per extra address at EDIS, and included at OliveVPS and LightNode.
3. **How is traffic counted?** Unmetered under fair use, a metered terabyte with $0.005/GB overage, and a non-expiring pool are three different products.
4. **What is the refund position?** Among these five, only OliveVPS states a 7-day no-questions refund. Arct states no free tier in Frankfurt. Do not assume a refund window that a provider has not published.
5. **Does resizing require a shutdown?** EDIS requires a full shutdown and restart for RAM, vCPU and storage changes, and after a storage upgrade you expand the partition and filesystem yourself. OliveVPS upgrades take a single reboot of 60–90 seconds, while downgrades need a backup and restore.
6. **Windows licence, included or added?** OliveVPS folds the surcharge into the Pro and Premium prices. Elsewhere, confirm it before checkout.

Final rules, in the order that saves the most money. One small service: take the cheapest 1 GB plan and check whether IPv4 costs extra. A database: jump to the 8 GB tier, where per-GB pricing halves. Windows: start at 2 vCPU and work upward. Chinese visitors: pick the route first, then the plan. LightNode's first top-up bonus of up to $15 is worth using if you go that way, but it does not change the monthly arithmetic.

👉 [See what AkkoCloud's Frankfurt line costs today](https://bit.ly/akkocloud)

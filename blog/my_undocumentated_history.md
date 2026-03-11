
# Development Log: The Road to Zero Cut(2026)

### Prologue

My dev life, around 4 years are undocumentated, my blog, thus, is going to cover this first.
PS - This entire article is AI assisted, I am not at all a a good author, or blogger, the ideas are mine, its just that the sentences aren't.

## Phase 1: The Abstraction Layer (Age 7–11)
I started coding at 7. It was all React at first—component lifecycles, state management, the standard learning curve. By 11, I had moved deep into the Next.js ecosystem. I was shipping products, but I was building on rented land.

I relied heavily on the Vercel dashboard and their edge functions. It was convenient until it wasn't. I hit rate limits hard. 

*   **The Failure:** My architecture depended on centralized serverless functions. When traffic spiked or I looped too many API calls, Vercel throttled the execution.
*   **The Realization:** I was locked into a proprietary black box. I didn't control the compute; I was just borrowing it. That was the first crack in the foundation. I realized that if I couldn't control the infra, I couldn't scale the product.

## Phase 2: The Physical-Digital Bridge & The KYC Wall (Age 12)
I shifted focus from pure software to product engineering. I wanted to build a commerce engine. I integrated with Gelato and Printify to handle print-on-demand (PoD) logistics.

I built the frontend, connected the APIs, designed the mockups. But I hit a wall that code couldn't fix: **KYC**

*   **The Block:** To receive payouts or act as a merchant on these platforms, I needed to verify my identity. Being 12, that was a non-starter.
*   **The Technical Takeaway:** Traditional fintech and Web2 commerce rails are permissioned by design. They require a trusted third party to verify identity and custody funds. I was building on rails that assumed I had government-issued ID and a bank account. The system was closed. I couldn't innovate inside a permissioned ledger.

## Phase 3: Zero Cut (Current)
This is the synthesis of the last four years. Zero Cut isn't just another project; it's the fix for the problems I kept hitting.

I’m building a crypto payment processor and digital store that combines the UX of Gumroad and Sellix but strips out the friction: **No fees. No KYC. Self-hosted.**

### Architecture & Logic

**1. The Sovereign Storefront:**
I’m moving away from the Vercel dependency. The stack is designed to be forkable. You clone the repo, you run the docker container, and you own the instance. It resolves the rate-limiting issue I faced in Phase 1 by giving the operator full control over the node. The entire design is **frontend only** and **static** by defualt.

**2. Bypassing the Middleman:**
Because it’s crypto-native, I solve the KYC issue from Phase 2.
*   **Settlement:** Payments go straight from the buyer’s wallet to the merchant’s wallet. There is no "platform" account holding funds.
*   **Verification:** The blockchain acts as the settlement layer. I don't need to verify who you are; the cryptography verifies the transaction.

**3. The Product Stack:**
*   **Digital Goods:** IPFS/Arweave hosting for files (no AWS bills).
*   **Payments:** Solana for sub-second finality.
*   **Fees:** Literally zero. The protocol doesn't take a cut. The only cost is network gas.

### Implementation Status
[**Github Repo**](https://github.com/Aevon-the-Great/zero-cut)

**The Vision:**
This is the tool I wished I had at 12. A way to sell digital products and merchandise without asking for permission, without paying a platform tax, and without worrying about a hosted service pulling the plug. It's Gumroad, but sovereign.

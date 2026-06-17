# Zunami Protocol — Chain of Evidence
## Independent Blockchain Forensic Investigation

---

| Field | Details |
|-------|---------|
| **Case Reference** | ZNM-NANOJS02-INV |
| **Investigator** | NanoJS10 |
| **Incident Date** | January 2023 – May 2025 |
| **Report Date** | June 17, 2026 |
| **Classification** | Public Research |
| **Tools Used** | Etherscan.io · MetaSleuth.io |
| **Blockchain** | Ethereum Mainnet |
| **Status** | ACTIVE — Subject wallets operational as of May 2026 |

---

## ABOUT THIS INVESTIGATION

This repository documents an independent blockchain forensic investigation into the Zunami Protocol exploits of 2023 and 2025. All data was sourced exclusively from publicly available Ethereum blockchain records.

The investigation successfully traced stolen funds from the exploit wallet through Tornado Cash, across multiple intermediate wallets, and into verified centralized exchange accounts all holding mandatory KYC records.

This investigation has been accepted for publication by **Rekt News** under a new editorial category they created specifically for this work: **Chain of Evidence** stories where forensics have been packaged, exchanges have been notified, and the next move belongs to law enforcement.

**Total documented losses: ~$2,969,000 (1,562 ETH)**

---

## KEY FINDINGS

### 1. Insider Connection Established
sterx.eth funded the Zunami Protocol deployer wallet at launch, continues to receive funds from it in 2026, and executed a direct transaction to zunamiteam.eth in April 2026. The deployer wallet sent a direct transaction to the exploiter wallet three days after the August 2023 attack. **This deployer-to-exploiter link sat undetected on Etherscan for three years.**

### 2. sterx.eth Identity Confirmed
ENS lookup confirms sterx.eth resolves to `0xF9605D8c4c987d7Cb32D0d11FbCb8EeeB1B22D5d`, which also controls **zunamidao.eth**. Rekt News independently confirmed sterx.eth as the Zunami CEO (@kirill_zunami) in their June 2025 Rekt II article. The Zunami Deployer sent 0.014 ETH directly to this wallet on **April 26, 2026** — confirming shared custody.

### 3. Attack Was Pre-Planned — 143-Day Staging Chain
The 2023 exploit was funded via OKX and Binance 143 days before the attack. The OKX-funded staging wallet (Wallet A) was not merely pre-staged it was **actively used as a swap intermediary on the day of the exploit itself**, routing USDT through the 0x Exchange Proxy back to the exploiter. Deliberate advance staging using two separate CEX accounts is inconsistent with opportunistic exploitation.

### 4. Five CEX Identity Trails Available
Binance, OKX, Coinbase, and ByBit all hold KYC-verified identity records directly linked to this exploit chain all accessible via formal legal process.

### 5. Repeat Pattern Confirmed — May 14, 2025
The identical deployer-to-exploiter pattern repeated on May 14, 2025. The Zunami Deployer granted admin roles to two privileged contracts within 12 seconds. Six minutes later, the attacker drained both contracts. The entire operation from role grant to final Tornado Cash deposit completed in **29 minutes 24 seconds**.

### 6. Operation Remains Active
Subject confirmed active on-chain as recently as May 2026. Both the Zunami Deployer and sterx.eth wallet are actively transacting.

### 7. Exchange Responses Received
ByBit and Coinbase have both formally responded to submissions. Coinbase Sr. Director engaged directly. Five Coinbase hot wallets confirmed as receiving exploit proceeds totalling ~96 ETH.

---

## THE SMOKING GUN TRANSACTION

```
From  : Zunami Protocol Deployer
        0xe9b2B067eE106A6E518fB0552F3296d22b82b32B

To    : Zunami Protocol Exploiter
        0x5f4C21c9Bb73c8B4a296cC256C0cDe324dB146DF

TX    : 0x91b41d5b5b30a941c65d5da952c4b11390f364b41cf81a1a87fba9b67b69fe22

Block : 17928584
Value : 0 ETH
Date  : 2023-08-16 16:28:47 UTC
```

> In a genuinely external third-party hack, no transactional relationship should exist between a protocol's deployer and the attacker's wallet. This transaction establishes either shared key custody or operational control of both wallets by the same party.

---

## THE 143-DAY PRE-STAGING CHAIN

### OKX Funding — Day 1

```
TX   : 0x1b315017748bf8b7aca7d58771e172e88a5d9b08a972f8f7027dc7014433b5cb
FROM : OKX Hot Wallet 0x4E7b110335511F662FDBB01bf958A7844118c0D4
TO   : Wallet A 0xF00d0e11AcCe1eA37658f428d947C3FFFAeaDe70
AMT  : 15.999 ETH
DATE : 2023-03-23 08:36:35 UTC | Block 16889095
```

### Full Timeline

| Day | Date | Amount | TX Hash |
|-----|------|--------|---------|
| 1 | 2023-03-23 | 15.999 ETH from OKX | `0x1b315017748bf8b7aca7d58771e172e88a5d9b08a972f8f7027dc7014433b5cb` |
| 46 | 2023-04-07 | 0.00036 ETH Wallet A→B | `0x5ad68e8ae2b68b3ffc76f94dbf6933ce234b5c0f47c2f310bb7f07f744ed770a` |
| 75 | 2023-05-07 | 0.092 ETH Wallet A→B | `0x2a1dc84d940feeb0253f926affe9d7a7639768c5475a2296401d1d099b111b17` |
| 96 | 2023-05-27 | 34.998 ETH Binance→Wallet A | `0x27f5665edacc30a7bae57d27e964272087b7b9f8276c468a48b6b6fe13e653a1` |
| 107 | 2023-06-06 | 1.41 ETH Wallet A→B | `0x216f1585d7e921c3fb5008a28ef8f09dadc69d214a8235cb7b7b90bd7a969af9` |
| 136 | 2023-07-07 | 3.88 ETH Wallet A→B | `0x297ca310dbe55b65a3b86a3fd5a88924c8dbdfc4835bfbe936d8fb7b3ce92bba` |
| 143 | 2023-08-06 | 5.19 ETH Wallet A→B (final staging) | `0x6317de0fc0aacbbe8a95fb846001452ddd7746c25056cc9128bcbae069656ef2` |
| 143 | 2023-08-13 | 1,265 USDT Exploiter via Wallet A | `0x76b70f7c6a9a58388ffa98be0ff2b68f97c05237686693c5cf1c92da29dd713f` |
| 143 | 2023-08-13 | 1,152 ETH stolen — PRIMARY | `0x2aec4fdb2a09ad4269a410f2c770737626fb62c54e0fa8ac25e8582d4b690cca` |
| 143 | 2023-08-13 | ~26 ETH stolen — SECONDARY | `0x0788ba222970c7c68a738b0e08fb197e669e61f9b226ceec4cab9b85abe8cceb` |

### Exploit-Day Operational Link

```
TX   : 0x76b70f7c6a9a58388ffa98be0ff2b68f97c05237686693c5cf1c92da29dd713f
FROM : Zunami Exploiter 0x5f4C21c9Bb73c8B4a296cC256C0cDe324dB146DF
VIA  : 0x Exchange Proxy 0xDef1C0ded9bec7F1a1670819833240f027b25EfF
XFER1: Exploiter → Wallet A — 1,265.457045 USDT
XFER2: Wallet A → 0x Proxy — 0.687995 WETH back to Exploiter
BLOCK: 17908983 | DATE: 2023-08-13 22:41:35 UTC
```

---

## MAY 14, 2025 — REPEAT EXPLOIT — 29 MINUTES

### The Two Confirmed Key Transactions

```
GRANT ROLE TX:
0x2697a6f04bb4aff65f9ce2e7a3cac8addeafc52131495ef4d1760316b5aee3b0
FROM : Deployer 0xe9b2B067eE106A6E518fB0552F3296d22b82b32B
TO   : Contract 1 0xadFa8e4C7004a9373426aC4F37F146a42aE699AB
TIME : 2025-05-14 21:36:47 UTC

EXPLOIT TX:
0xd7ce50992b36acbc746a821a74e5600230cfe5b36cfc155841581e376f4c14d2
FROM : Attacker 0x051370419b871F7C05dEE8f7134401530832e250
TO   : Contract 1 0xadFa8e4C7004a9373426aC4F37F146a42aE699AB
TIME : 2025-05-14 21:43:23 UTC
GAP  : 6 minutes 36 seconds
```

### Complete Timeline

| Time UTC | Block | Action |
|----------|-------|--------|
| 21:36:47 | 22484113 | Deployer GRANTS ROLE → Contract 1 |
| 21:36:59 | 22484114 | Deployer GRANTS ROLE → Contract 2 |
| 21:42:47 | 22484143 | Attacker withdrawEmergency() Contract 2 |
| 21:43:23 | 22484146 | Attacker withdrawStuckToken() Contract 1 |
| 21:52:59–22:01:35 | 22484194–22484237 | 20× Tornado Cash — 10 ETH each = 200 ETH |
| 22:02:35–22:04:59 | 22484242–22484253 | 6× Tornado Cash — 1 ETH each = 6 ETH |
| 22:06:11 | 22484260 | Final deposit — ~204.2 ETH laundered — COMPLETE |

---

## INCIDENT TIMELINE

| Incident | Date | Method | Loss (ETH) | Loss (USD) |
|----------|------|--------|------------|------------|
| Mempool Sandwich | Jan 2023 | Slippage Manipulation | 27 ETH | ~$49,000 |
| Flash Loan | Feb 2023 | LP Price Manipulation | 143 ETH | ~$260,000 |
| Main Exploit | Aug 13, 2023 | calcTokenPrice Logic Error | 1,178 ETH | ~$2,160,000 |
| Admin Key Abuse | May 14, 2025 | withdrawStuckToken() | 214 ETH | ~$500,000 |
| **TOTAL** | | | **1,562 ETH** | **~$2,969,000** |

---

## COMPLETE WALLET REGISTRY

| Label | Address | Role | Status |
|-------|---------|------|--------|
| sterx.eth / zunamidao.eth | `0xF9605D8c4c987d7Cb32D0d11FbCb8EeeB1B22D5d` | Primary insider identity | ACTIVE May 2026 |
| Zunami Deployer | `0xe9b2B067eE106A6E518fB0552F3296d22b82b32B` | Protocol deployer | ACTIVE Apr 2026 |
| 2023 Exploiter | `0x5f4C21c9Bb73c8B4a296cC256C0cDe324dB146DF` | Aug 2023 attack wallet | DORMANT Aug 2023 |
| 2023 Attack Contract | `0xa21a2b59d80dc42d332f778cbb9ea127100e5d75` | Exploit execution | DORMANT |
| 2025 Attacker | `0x051370419b871F7C05dEE8f7134401530832e250` | May 2025 attack wallet | DORMANT May 2025 |
| 2025 Attack Contract 1 | `0xadFa8e4C7004a9373426aC4F37F146a42aE699AB` | withdrawStuckToken() | DORMANT May 2025 |
| 2025 Attack Contract 2 | `0x72A2394c42521038a91c94f5b4C421fAa45E0719` | withdrawEmergency() | DORMANT May 2025 |
| Wallet A (OKX-funded) | `0xF00d0e11AcCe1eA37658f428d947C3FFFAeaDe70` | Pre-exploit staging | DORMANT Aug 2023 |
| Wallet B | `0x12e98c4EBD742ca9465789570e5cf4Df9EEd0Fb0` | Primary cashout | Historical |
| Wallet C | `0x119bDFB802f7723bCDEc281e6BEc12F1A2A9F231` | Intermediate | Historical |
| Wallet D | `0x2ad9a351b98Fd39C30DDb52D37415D0f01eF5D00` | Intermediate | Historical |
| Wallet E | `0x2A06c43A6f9805739893C0553A0fa8A062F5B22D` | Intermediate | Historical |
| Wallet F | `0x62ADe071746Cb288Ece3022F89ABd0df5Af53322` | Intermediate | Historical |
| Wallet G | `0x0d7ED915293dC004851f5738A080eD4e22da04293` | Intermediate | Historical |
| zunamiteam.eth | Resolve via ENS | Official team wallet | ACTIVE Apr 2026 |
| phil10k.eth | `0x62c8aCc91b488F5749D8e43C7711eDf76841b206` | Secondary connected wallet | Active Sep 2025 |
| newstones.eth | `0xac5a463a9b498bb79ea8f776c2c3e055d7b25e75` | Downstream recipient | Requires investigation |
| MEV Bot_0xeda0 | `0xeda83592fc94bbd1ddbbd513be6e6d225e3249ec` | Downstream recipient | Active Apr 2026 |
| Tornado Cash Router | `0xd90e2f925DA726b50C4Ed8D0Fb90Ad053324F31b` | Laundering | — |

---

## EXCHANGE KYC IDENTITY TRAILS

| Exchange | Hot Wallet | Amount | Date | Notes |
|----------|------------|--------|------|-------|
| Binance | `0x564286362092D8e7936f0549571a803B203aAceD` | 4.995 ETH | 2020-08-22 | To sterx.eth |
| Binance | `0x3f5CE5FBFe3E9af3971dD833D26bA9b5C936f0bE` | 12.72 ETH | 2020-08-22 | To sterx.eth |
| Binance | `0x4976A4A02f38326660D17bf34b431dC6e2eb2327` | 34.99 ETH | 2023-05-27 | To Wallet A — pre-staging |
| OKX | `0x4E7b110335511F662FDBB01bf958A7844118c0D4` | 15.999 ETH | 2023-03-23 | To Wallet A — Day 1 of 143 |
| Coinbase | `0xb739d0895772dbb71a89a3754a160269068f0d45` | 21.354 ETH | 2023-11-10 | Exploit proceeds |
| Coinbase | `0x77696bb39917C91A0c3908D577d5e322095425cA` | 16.955 ETH | 2024-02-08 | Exploit proceeds |
| Coinbase | `0x95A9bd206aE52C4BA8EecFc93d18EACDd41C88CC` | 7.460 ETH | 2024-03-25 | Exploit proceeds |
| Coinbase | `0xA9D1e08C7793af67e9d92fe308d5697FB81d3E43` | 23.291 ETH | 2024-07-11 | Exploit proceeds |
| Coinbase | `0xb5d85CBf7cB3EE0D56b3bB207D5Fc4B82f43F511` | 6.162 ETH | 2025 | Exploit proceeds |
| ByBit | `0xA7b7Bc3fC962614d51553829717D6e1884458039` | Multiple | 2026-05-02 | From sterx.eth — ACTIVE |

---

## COMPLETE FUND FLOW

```
Binance (2020) ──────────────────────────────► sterx.eth
                                                    │
                                         2022-03-09 │ 2 ETH
                                                    ▼
OKX + Binance (2023) ───────► Wallet A ──► Zunami Deployer
[143 days pre-exploit]             │             │
                                   │             │ [Smoking Gun TX]
                                   ▼             ▼
                               Wallet B ◄── Zunami Exploiter
                                   │             │
                                   │             ▼
                                   │        Tornado Cash
                                   │        (35+ deposits)
                                   │
                     ┌─────────────┼──────────────┐
                     ▼             ▼               ▼
               Coinbase C    Coinbase D      Coinbase E
               (Feb 2024)   (Mar 2024)      (Jul 2024)
                     │             │               │
                     └─────────────┴───────────────┘
                                   │
                               Coinbase
                           (6 accounts confirmed)
                          2023-11-10 → 2025-10-05

sterx.eth ──────────────────────────────────► ByBit
                                    2026-05-02 [ACTIVE]
```

---

## COMPLETE TRANSACTION HASH REFERENCE

### Phase 1 — Funding
```
A1: 0x4694566855ce96809a9266d9cfa64e30fea5843234089c84771757b8843e1d29
A2: 0xf46c03f33110ad986dd9ee3d9ab1ff274933d17710c736cfcbb5ee9664cf3fd0
A3: 0x5d819c702a6f8c153c62222592356d240edb8eeda67a31f830741c7907e9ca3a
A4: 0x831e265fd6eb52752854f88c57b9789fd287f1c7d41544a8c39ab91a8a23d2c4
```

### Phase 2 — Pre-Exploit Staging (143-Day Chain)
```
B1: 0x1b315017748bf8b7aca7d58771e172e88a5d9b08a972f8f7027dc7014433b5cb  [OKX → Wallet A — Day 1]
B2: 0x27f5665edacc30a7bae57d27e964272087b7b9f8276c468a48b6b6fe13e653a1  [Binance → Wallet A — Day 96]
B3: 0x216f1585d7e921c3fb5008a28ef8f09dadc69d214a8235cb7b7b90bd7a969af9  [Wallet A → B — Day 107]
B4: 0x76b70f7c6a9a58388ffa98be0ff2b68f97c05237686693c5cf1c92da29dd713f  [Exploit-day link — Wallet A used]
B5: 0x6317de0fc0aacbbe8a95fb846001452ddd7746c25056cc9128bcbae069656ef2  [Final staging — Day 143]
```

### Phase 3 — Exploit and Tornado Cash
```
C1: 0x91b41d5b5b30a941c65d5da952c4b11390f364b41cf81a1a87fba9b67b69fe22  [SMOKING GUN — Deployer → Exploiter]
C2: 0x2aec4fdb2a09ad4269a410f2c770737626fb62c54e0fa8ac25e8582d4b690cca  [Primary exploit TX — 1,152 ETH]
C3: 0x0788ba222970c7c68a738b0e08fb197e669e61f9b226ceec4cab9b85abe8cceb  [Secondary exploit TX — ~26 ETH]
C4: 0xccd44b6ab6e43030fbfdd759cee49bdf5cba2c9364689a0f37c666c1261c95b5  [Tornado Cash deposit]
```

### Phase 4 — Coinbase Cashouts
```
D1:  0x9e323610282c86c356be8792b864f820e86b6cc3ea2cf42ab4eeb7927d98c6e1
D2:  0x3968f5639e357ddf4a206f6255b376eacbaf8f24488a6526d7cd3dd1eafc01b4
D3:  0x2aee51b7fd22c6979db0010fd9a3835bafc2d5a3efeefb1f611e71105a74fe44
D4:  0xfcb85ffa3ee50091f128996e2d4679c8d4aaeca7d8245f01d68ed18e62cd897f
D5:  0x83c88cab219a9b9e803b1a3f0606ae74934756b3687abc2a25729e3087ab3e0f
D6:  0xabb8c57d57f5b30dd4ecb3ac451b9a3eb13ca72431835c158d8f4a36ecfada0c
D7:  0xecb51867e0e6327c947b7aa248ee484e5a24f0ae742f7f9fa7bdf54525aa8e68
D8:  0xff527b48e6eb4469af56cf1bb0eaba0d767720d928f015e1cdd1049ef1b91aaa
D9:  0xa380a9278cc38da7ff629c41336528364d51ad973aef5c6bb65cf206ae345002
D10: 0xbd1907140754f805acf15daf8dfcb6ae740dca53b8af2ea63ef0eb285c55f2f5
D11: 0x7f5aab8ebd4c60e9748a2d6eb7009a4d8bffdc8afa9514be03c94e1cde7dcb8c
D12: 0x8a77cd859d68d93206e58e5e5a06b735853b4cb14cbe1a757189caaeb5fc435b
D13: 0xcc14e9f0804a088cf03399fafb7e78844cc5383a6dff617b5b8dee4d49fdbec1
```

### Phase 5 — 2025 Repeat Exploit (May 14, 2025)
```
E1: 0x2697a6f04bb4aff65f9ce2e7a3cac8addeafc52131495ef4d1760316b5aee3b0  [Grant Role — Deployer → Contract 1]
E2: 0xd7ce50992b36acbc746a821a74e5600230cfe5b36cfc155841581e376f4c14d2  [withdrawStuckToken() — EXPLOIT]
```

### Phase 6 — Ongoing 2025–2026
```
F1: 0x456189d606fcade0a47221ec3e054c655d3134c3be0f0caff8843faa5512881d
F2: 0x8d44d722c7bc99606b086fe01f8084767713369aa1a5bfe06078d47e0aea3b60
F3: 0x92610d6c92a34dbd68f887f114d886b1f8d7eb54867d955cb171e838054c8cf3
F4: 0xe772dcbe19b3ec62e2ee0a43b18a369cebb18fdd3a7aae935d6336c2698984a2
F5: 0x3370d955b854a98b6578212e085c67ab94329740856dbd4da23ca05f0200d182  [Deployer → sterx.eth — Apr 26 2026]
F6: 0xbe673db1fa9027c3380abe3b2da09ba418d12d8010cb431a39ca88ccd6fde70f
F7: 0xbf03b63adb606901a3d6db1b7b47ba17682267cd7468f510a87c5ca18a01ef8a
```

---

## EXCHANGE RESPONSES AND INVESTIGATION UPDATES

### UPDATE — June 17, 2026

Investigation report delivered to Rekt News. Chain of Evidence category created.

---

### ByBit — Response Received

**Date:** May 17, 2026
**Status:** Acknowledged Directed to Law Enforcement Channel

ByBit Support acknowledged receipt of the forensic report and confirmed cooperation with authorized law enforcement agencies.

```
Law Enforcement Contact: law_enforcement@bybit.com
```

---

### Coinbase — Response Received

**Date:** May 17, 2026
**Status:** Active Review — Sr. Director Engaged

A Senior Director at Coinbase personally reviewed the submitted forensic report. The five Coinbase hot wallet addresses under active review:

```
1. 0xb739d0895772dbb71a89a3754a160269068f0d45  |  21.354 ETH  |  2023-11-10
2. 0x77696bb39917C91A0c3908D577d5e322095425cA  |  16.955 ETH  |  2024-02-08
3. 0x95A9bd206aE52C4BA8EecFc93d18EACDd41C88CC  |   7.460 ETH  |  2024-03-25
4. 0xA9D1e08C7793af67e9d92fe308d5697FB81d3E43  |  23.291 ETH  |  2024-07-11
5. 0xb5d85CBf7cB3EE0D56b3bB207D5Fc4B82f43F511  |   6.162 ETH  |  2025
```

---

### Current Investigation Status

| Body | Submission | Response | Status |
|------|-----------|----------|--------|
| Rekt News | Jun 2026 | ✅ Accepted | Chain of Evidence — pending publication |
| ByBit | May 16, 2026 | ✅ Received | Directed to LE |
| Coinbase | May 16, 2026 | ✅ Received | Active review — Sr. Director engaged |
| MEXC | May 2026 | ✅ FREEZE CONFIRMED | Ticket #20260507000124 (MerlinDEX NanoJS01) |
| Binance | May 16, 2026 | Pending | — |
| OKX | May 16, 2026 | Pending | — |
| FBI IC3 | May 16, 2026 | Filed | Complaint active |
| Interpol | May 16, 2026 | Pending | — |
| Europol EC3 | Recommended | — | ec3@europol.europa.eu |
| Chainalysis | Pending | — | — |
| TRM Labs | Pending | — | — |

---

## CURRENT WALLET STATUS — JUNE 2026

| Wallet | Address | Balance | Last Active | Status |
|--------|---------|---------|-------------|--------|
| Zunami Deployer | `0xe9b2B067eE106A6E518fB0552F3296d22b82b32B` | $3.19 | Apr 26, 2026 | **ACTIVE** |
| sterx.eth | `0xF9605D8c4c987d7Cb32D0d11FbCb8EeeB1B22D5d` | $2,655.99 | May 2026 | **ACTIVE** |
| OKX Wallet A | `0xF00d0e11AcCe1eA37658f428d947C3FFFAeaDe70` | — | Aug 13, 2023 | DORMANT |
| 2023 Attacker | `0x5f4c21c9bb73c8b4a296cc256c0cde324db146df` | $160.61 | Aug 16, 2023 | DORMANT |
| 2025 Attacker | `0x051370419b871F7C05dEE8f7134401530832e250` | $136.06 | May 14, 2025 | DORMANT |

---

## REPORTING CONTACTS

| Priority | Body | Contact | Reason |
|----------|------|---------|--------|
| URGENT | ByBit Compliance | law_enforcement@bybit.com | Active deposit May 2, 2026 |
| HIGH | FBI IC3 | ic3.gov/complaint | US jurisdiction — Coinbase cashouts |
| HIGH | Coinbase | coinbase.com/legal/law_enforcement | 6 cashout deposits confirmed |
| HIGH | Binance | law-enforcement@binance.com | Oldest identity trail — 2020 |
| HIGH | OKX | compliance@okx.com | Pre-exploit funding confirmed |
| HIGH | Europol EC3 | ec3@europol.europa.eu | Cross-border coordination |
| HIGH | Chainalysis | chainalysis.com/contact | Tornado Cash tracing |
| HIGH | TRM Labs | trmlabs.com/contact | Exchange flagging |
| MEDIUM | DOJ Cybercrime | cybercrime@usdoj.gov | Federal prosecution |
| MEDIUM | ZachXBT | @zachxbt on X | Community investigation |
| MEDIUM | Rekt News | rekt.news | Publication — Chain of Evidence |

---

## HOW TO HELP

If you are a law enforcement officer, blockchain security researcher, or have additional information on any of the wallets identified in this investigation, please open a GitHub Issue.

Law enforcement agencies are encouraged to contact exchanges directly using the confirmed channels above and reference:

```
Case Reference : ZNM-NANOJS02-INV
FBI IC3        : Complaint filed May 16, 2026
Full Report    : github.com/NanoJS10/Zunami-protocol-Investigation-
```

---

## DISCLAIMER

All data in this repository was obtained exclusively from publicly available records on the Ethereum mainnet via Etherscan.io and MetaSleuth.io. No private or non-public data was accessed.

No individual is named, accused, or identified. All wallet addresses are publicly recorded on the Ethereum blockchain and independently verifiable by any party.

This investigation was conducted voluntarily in the public interest to assist potential victims and relevant law enforcement agencies. This repository does not constitute legal advice.

---

*Case Reference: ZNM-NANOJS02-INV | Investigator: NanoJS10*
*Report Date: June 17, 2026 | Blockchain: Ethereum Mainnet*
*Verify all data: etherscan.io | metasleuth.io*

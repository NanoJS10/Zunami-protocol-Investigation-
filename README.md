# Zunami-protocol-Investigation

# ZUNAMI PROTOCOL EXPLOIT
## Independent Blockchain Forensic Investigation

---

**Case Reference** : ZNM-NANOJS02-INV
**Investigator**   : NanoJS
**Incident Date**  : January 2023 – May 2025
**Report Date**    : May 16, 2026
**Classification** : Public Research
**Tools Used**     : Etherscan.io | MetaSleuth.io
**Blockchain**     : Ethereum Mainnet
**Status**         : ACTIVE — Subject wallets operational as of May 2, 2026

---

## ABOUT THIS INVESTIGATION

This repository documents an independent blockchain forensic investigation
into the Zunami Protocol exploits of 2023 and 2025. All data was sourced
exclusively from publicly available Ethereum blockchain records.

The investigation successfully traced stolen funds from the exploit wallet
through Tornado Cash, across multiple intermediate wallets, and into
verified centralized exchange accounts all holding mandatory KYC records.

**Total documented losses: ~$2,969,000 (1,562 ETH)**

---

## KEY FINDINGS

**1. Insider Connection Established**
sterx.eth funded the Zunami Protocol deployer wallet at launch, continues
to receive funds from it in 2026, and executed a direct transaction to
zunamiteam.eth in April 2026. The deployer wallet sent a direct transaction
to the exploiter wallet three days after the August 2023 attack.

**2. Attack Was Pre-Planned**
The 2023 exploit was funded via OKX and Binance 143 days before the attack.
Deliberate advance staging using two separate CEX accounts is inconsistent
with opportunistic exploitation.

**3. Five CEX Identity Trails Available**
Binance, OKX, Coinbase, and ByBit all hold KYC-verified identity records
directly linked to this exploit chain — all accessible via formal legal process.

**4. Operation Remains Active**
Subject confirmed active on-chain as recently as May 2, 2026.

**5. Structured Laundering Confirmed**
Placement via Tornado Cash, layering through 7+ wallets and 12+ token types,
and integration via Coinbase across a 24-month cashout window.

---

## VISUAL EVIDENCE

### Evidence 1 — MetaSleuth: Full Exploiter Transaction Flow Map

![MetaSleuth Full Flow Map](evidence/screenshots/metasleuth_full_exploiter_map.png)

Complete MetaSleuth visual map of the Zunami Protocol Exploiter wallet
showing the full fund flow from Tornado Cash inputs through intermediate
wallets, DEX swaps (Uniswap V2/V3, 1inch), and final exchange cashout
destinations. The map confirms active transactions through April 2026.

Key nodes visible:
- Zunami Protocol Exploiter (bottom center)
- Tornado Cash 10 ETH pool (left)
- Ox Exchange Proxy (left)
- CeFi Protocol SP Settlement (center left)
- MetaMask Swaps Spender (center left)
- Coinbase Proxy (center)
- Tornado Cash Router (center)
- Uniswap V2/V3 pools (multiple)
- Disperse contract (center)
- Ox Exchange Proxy Flash (right center)
- Multiple downstream destinations (right)

---

### Evidence 2 — Etherscan: Exploiter Wallet Transaction List

![Etherscan Exploiter Transactions](evidence/screenshots/etherscan_exploiter_txlist.png)

Etherscan transaction list for the Zunami Protocol Exploiter wallet
`0x5f4C21c9Bb73c8B4a296cC256C0cDe324dB146DF` confirming:

| TX Hash | Method | Block | Age | From | Direction | To | Amount |
|---------|--------|-------|-----|------|-----------|----|--------|
| 0x91b41d5b... | Transfer* | 17928584 | 996 days | Zunami Protocol: Dep... | **IN** | Zunami Protocol Expl... | 0 ETH |
| 0xccd44b6ab6... | Deposit | 17909139 | 999 days | Zunami Protocol Expl... | OUT | Tornado.Cash: Rou... | 0.1 ETH |
| 0x64782d6e9c... | Deposit | 17909132 | 999 days | Zunami Protocol Expl... | OUT | Tornado.Cash: Rou... | 0.1 ETH |
| 0x5dde054463... | Deposit | 17909131 | 999 days | Zunami Protocol Expl... | OUT | Tornado.Cash: Rou... | 0.1 ETH |
| 0x4f0fbc39a5e... | Deposit | 17909120 | 999 days | Zunami Protocol Expl... | OUT | Tornado.Cash: Rou... | 0.1 ETH |
| 0x6f5845d97eb... | Deposit | 17909106 | 999 days | Zunami Protocol Expl... | OUT | Tornado.Cash: Rou... | 0.1 ETH |
| 0x08a9d51e7d... | Deposit | 17909105 | 999 days | Zunami Protocol Expl... | OUT | Tornado.Cash: Rou... | 0.1 ETH |

**The first row is the smoking gun:** Transfer IN from the Zunami Protocol
Deployer to the Exploiter at Block 17928584. In a genuine external hack,
no transactional relationship should exist between these two wallets.

Full TX hash:
```
0x91b41d5b5b30a941c65d5da952c4b11390f364b41cf81a1a87fba9b67b69fe22
```
Date: 2023-08-16 16:28:47 UTC | Block: 17928584 | Value: 0 ETH

---

### Evidence 3 MetaSleuth: Wallet B to Coinbase Flow Confirmation

![MetaSleuth Coinbase Flow](evidence/screenshots/metasleuth_walletB_coinbase.png)

MetaSleuth visual trace confirming direct sequential fund flow from
Wallet B to Coinbase Exchange Hot Wallet on November 10, 2023:

```
Wallet B
0x12e98c4EBD742ca9465789570e5cf4Df9EEd0Fb0
        |
        | [2023-11-10 23:38:11] 21.35 ETH
        v
0x10e3d0099b2eFa3Af238B88bbFEecc971BcCbf83
        |
        | [2023-11-10 23:39:47] 21.35 ETH
        v
Coinbase Exchange: Hot Wallet
0xb739d0895772dbb71a89a3754a160269068f0d45
```

MetaSleuth Risk Rating on Coinbase wallet:  NO RISK
Confirms this is a verified, operational Coinbase exchange hot wallet.
Coinbase holds custody of the received funds and can associate deposits
with a specific KYC-verified account holder.

---

## INCIDENT TIMELINE

| Incident | Date | Method | Loss (ETH) | Loss (USD) |
|----------|------|--------|------------|------------|
| Mempool Sandwich | Jan 2023 | Slippage Manipulation | 27 ETH | ~$49,000 |
| Flash Loan | Feb 2023 | LP Price Manipulation | 143 ETH | ~$260,000 |
| Main Exploit | Aug 13, 2023 | calcTokenPrice Logic Error | 1,178 ETH | ~$2,160,000 |
| Admin Key | May 15, 2025 | Unauthorized withdrawStuckToken() | 214 ETH | ~$500,000 |
| **TOTAL** | | | **1,562 ETH** | **~$2,969,000** |

---

## WALLET REGISTRY

| Label | Address | Role | Status |
|-------|---------|------|--------|
| sterx.eth | `0xF9605D8c4c987d7Cb32D0d11FbCb8EeeB1B22D5d` | Primary founding wallet | ACTIVE May 2026 |
| Zunami Deployer | `0xe9b2B067eE106A6E518fB0552F3296d22b82b32B` | Protocol deployer | ACTIVE Apr 2026 |
| Zunami Exploiter | `0x5f4C21c9Bb73c8B4a296cC256C0cDe324dB146DF` | Aug 2023 attack wallet | Historical |
| zunamiteam.eth | Resolve via ENS | Official team wallet | Active Apr 2026 |
| phil10k.eth | `0x62c8aCc91b488F5749D8e43C7711eDf76841b206` | Secondary connected wallet | Active Sep 2025 |
| Wallet A | `0xF00d0e11AcCe1eA37658f428d947C3FFFAeaDe70` | Pre-exploit staging | Historical |
| Wallet B | `0x12e98c4EBD742ca9465789570e5cf4Df9EEd0Fb0` | Primary cashout | Historical |
| Wallet C | `0x119bDFB802f7723bCDEc281e6BEc12F1A2A9F231` | Intermediate | Historical |
| Wallet D | `0x2ad9a351b98Fd39C30DDb52D37415D0f01eF5D00` | Intermediate | Historical |
| Wallet E | `0x2A06c43A6f9805739893C0553A0fa8A062F5B22D` | Intermediate | Historical |
| Wallet F | `0x62ADe071746Cb288Ece3022F89ABd0df5Af53322` | Intermediate | Historical |
| Wallet G | `0x0d7ED915293dC004851f5738A080eD4e22da04293` | Intermediate | Historical |
| newstones.eth | `0xac5a463a9b498bb79ea8f776c2c3e055d7b25e75` | Downstream recipient | Requires investigation |
| MEV Bot_0xeda0 | `0xeda83592fc94bbd1ddbbd513be6e6d225e3249ec` | Downstream recipient | Active Apr 2026 |

---

## EXCHANGE KYC IDENTITY TRAILS

| Exchange | Hot Wallet | Amount | Date | Recipient |
|----------|------------|--------|------|-----------|
| Binance | `0x564286362092D8e7936f0549571a803B203aAceD` | 4.995 ETH | 2020-08-22 | sterx.eth |
| Binance | `0x3f5CE5FBFe3E9af3971dD833D26bA9b5C936f0bE` | 12.72 ETH | 2020-08-22 | sterx.eth |
| Binance | `0x4976A4A02f38326660D17bf34b431dC6e2eb2327` | 34.99 ETH | 2023-05-27 | Wallet A |
| OKX | `0x4E7b110335511F662FDBB01bf958A7844118c0D4` | 15.999 ETH | 2023-03-23 | Wallet A |
| Coinbase | `0xb739d0895772dbb71a89a3754a160269068f0d45` | 21.354 ETH | 2023-11-10 | received |
| Coinbase | `0x77696bb39917C91A0c3908D577d5e322095425cA` | 16.955 ETH | 2024-02-08 | received |
| Coinbase | `0x95A9bd206aE52C4BA8EecFc93d18EACDd41C88CC` | 7.460 ETH | 2024-03-25 | received |
| Coinbase | `0xA9D1e08C7793af67e9d92fe308d5697FB81d3E43` | 23.291 ETH | 2024-07-11 | received |
| Coinbase | `0xb5d85CBf7cB3EE0D56b3bB207D5Fc4B82f43F511` | 6.162 ETH | 2025 | received |
| ByBit | `0xA7b7Bc3fC962614d51553829717D6e1884458039` | Multiple | **2026-05-02** | from sterx.eth |

---

## THE SMOKING GUN TRANSACTION

```
From  : Zunami Protocol Deployer
        0xe9b2B067eE106A6E518fB0552F3296d22b82b32B

To    : Zunami Protocol Exploiter
        0x5f4C21c9Bb73c8B4a296cC256C0cDe324dB146DF

TX    : 0x91b41d5b5b30a941c65d5da952c4b11390f364b41
        cf81a1a87fba9b67b69fe22

Block : 17928584
Value : 0 ETH
Date  : 2023-08-16 16:28:47 UTC
```

In a genuinely external third-party hack, no transactional relationship
should exist between a protocol's deployer and the attacker's wallet.
This transaction establishes either shared key custody or operational
control of both wallets by the same party.

---

## COMPLETE FUND FLOW

```
Binance (2020) ──────────────────────────────► sterx.eth
                                                    │
                                         2022-03-09 │ 2 ETH
                                                    ▼
OKX + Binance (2023) ───────► Wallet A ──► Zunami Deployer
[143 days pre-exploit]             │             │
                                   │             │ [Smoking Gun]
                                   ▼             ▼
                               Wallet B ◄── Zunami Exploiter
                                   │             │
                                   │             ▼
                                   │        Tornado Cash
                                   │        (35 deposits)
                                   │
                     ┌─────────────┼──────────────┐
                     ▼             ▼               ▼
               Coinbase C    Coinbase D      Coinbase E
               (Feb 2024)   (Mar 2024)      (Jul 2024)
                     │             │               │
                     └─────────────┴───────────────┘
                                   │
                               Coinbase
                           (multiple accounts)
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

### Phase 2 — Pre-Exploit Staging
```
B1: 0x1b315017748bf8b7aca7d58771e172e88a5d9b08a972f8f7027dc7014433b5cb
B2: 0x27f5665edacc30a7bae57d27e964272087b7b9f8276c468a48b6b6fe13e653a1
B3: 0x216f1585d7e921c3fb5008a28ef8f09dadc69d214a8235cb7b7b90bd7a969af9
B4: 0x74454ddcdea146a6a0006acc1cef4adf9142475037f9c52ea517f7493cf05e7c
B5: 0x74454ddcdea146a6a0006acc1cef4adf9142475037f9c52ea517f7493cf05e7c
```

### Phase 3 — Exploit and Tornado Cash
```
C1: 0x91b41d5b5b30a941c65d5da952c4b11390f364b41cf81a1a87fba9b67b69fe22
C2: 0xccd44b6ab6e43030fbfdd759cee49bdf5cba2c9364689a0f37c666c1261c95b5
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

### Wallet B Additional Transactions
```
E4:  0x65995e4163368fe89d8c46b6f25c06c4d5fe5de905faf1850154261334601019
E5:  0xfb9abc054b269e36ea389ef0cf3b300115f814d9ff7d0f258be5b63de680b850
E6:  0xe3d60d38e8e21da7336c128057febbfadcd181566638a29cd00795e35c9fe7b5
E7:  0x4d521d87fc77d1fe287600375be6e908cabc5231724d12a62018acc085083d86
E8:  0xe2771e00af3bde146897bf7866d90000cd13b6883e6b0dc172bc906a36b73291
E9:  0xd41f954c53d28de049d2e9fad3676025c115d567d80cfef2eeef6bff812d2e97
E10: 0xb5636839360800b96f438d735b1c7f91c63265461c10c899e507deb72059b808
E11: 0x3df6a2a394f786673de60085511259a76153db7e165599196095fabe9d9d1041
```

### Phase 5 — Ongoing 2025–2026
```
F1: 0x456189d606fcade0a47221ec3e054c655d3134c3be0f0caff8843faa5512881d
F2: 0x8d44d722c7bc99606b086fe01f8084767713369aa1a5bfe06078d47e0aea3b60
F3: 0x92610d6c92a34dbd68f887f114d886b1f8d7eb54867d955cb171e838054c8cf3
F4: 0xe772dcbe19b3ec62e2ee0a43b18a369cebb18fdd3a7aae935d6336c2698984a2
F5: 0x3370d955b854a98b6578212e085c67ab94329740856dbd4da23ca05f0200d182
F6: 0xbe673db1fa9027c3380abe3b2da09ba418d12d8010cb431a39ca88ccd6fde70f
F7: 0xbf03b63adb606901a3d6db1b7b47ba17682267cd7468f510a87c5ca18a01ef8a
```

---

## REPORTING CONTACTS

| Priority | Body | Contact | Reason |
|----------|------|---------|--------|
| URGENT | ByBit Compliance | compliance@bybit.com | Active deposit May 2, 2026 |
| HIGH | FBI IC3 | ic3.gov/complaint | US jurisdiction — Coinbase cashouts |
| HIGH | Coinbase | coinbase.com/legal/law_enforcement | 6 cashout deposits confirmed |
| HIGH | Binance | law-enforcement@binance.com | Oldest identity trail — 2020 |
| HIGH | OKX | compliance@okx.com | Pre-exploit funding confirmed |
| HIGH | Chainalysis | chainalysis.com/contact | Tornado Cash tracing |
| HIGH | TRM Labs | trmlabs.com/contact | Exchange flagging |
| MEDIUM | DOJ Cybercrime | cybercrime@usdoj.gov | Federal prosecution |
| MEDIUM | Europol EC3 | europol.europa.eu/report-a-crime | Cross-border coordination |
| MEDIUM | ZachXBT | @zachxbt on X | Community investigation |
| MEDIUM | Rekt.news | rekt.news | Public disclosure |

---

## DISCLAIMER

All data in this repository was obtained exclusively from publicly
available records on the Ethereum mainnet via Etherscan.io and
MetaSleuth.io. No private or non-public data was accessed.

No individual is named, accused, or identified. All wallet addresses
are publicly recorded on the Ethereum blockchain and independently
verifiable by any party.

This investigation was conducted voluntarily in the public interest
to assist potential victims and relevant law enforcement agencies.
This repository does not constitute legal advice.

---

*Case Reference: ZNM-NANOJS02-INV | Investigator: NanoJS*
*Report Date: May 16, 2026 | Blockchain: Ethereum Mainnet*
*Verify all data: etherscan.io | metasleuth.io*

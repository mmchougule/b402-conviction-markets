# b402 — ZK Ownership and Private Agent Execution

## Problems we're solving

**#1: Funding without equity.** Capital enters a ZK commitment pool. Contributors receive encrypted notes in a shared merkle tree — provable claims on revenue or future value, without cap tables, lawyers, or corporate structure. The "cap table" is a merkle tree. Exits happen via ZK-proven redemptions. No entity required.

**#2: Ownership without cap tables.** Two people build something over a weekend. Each holds an encrypted note in a Railgun privacy pool representing their share. The note is cryptographically owned by their 0zk identity — provable on-chain without revealing who holds what or how much. When one of them is an agent, the same primitive works. Agents hold notes. Notes represent claims. Claims are programmable.

**#7: Cost governance for agents.** Agents spend money autonomously — calling APIs, executing trades, deploying capital. b402 wraps every agent payment in a privacy pool. The spending is real and on-chain, but the strategy behind it is hidden. Competitors can't reverse-engineer your agent's behavior from its transaction history. The same pool tracks cumulative spend, enforces caps, and settles payments — all via ZK proofs.

**#4: Verification without managers.** Our x402 implementation (HTTP 402 payment standard) creates cryptographic proof of payment at every API call boundary. Agent hits endpoint → pays via privacy pool → receives service → proof of payment is on-chain. No manager needed to verify the work was done. The payment IS the verification.

**#10: New moats.** When code gets cloned in a day, what's the moat? The anonymity set. 70,000+ wallets share the Railgun privacy pool across 3 chains. Every new user inherits the privacy of everyone already in the pool. Clone the code — you get zero users, zero privacy. The pool is the moat.

## What's live (on-chain, proven)

**Privacy execution layer** — deployed on Base, Arbitrum, BSC. Railgun fork, 0% protocol fees:
- Private swap (Odos/Aerodrome via RelayAdapt — atomic, untraceable)
- Private lend/redeem (Morpho vaults — vault sees RelayAdapt, never the user)
- Private cross-chain (LI.FI routing, 30 bridges — source and destination unlinkable)
- Gasless via ERC-4337 paymaster

**Agent infrastructure:**
- `@b402ai/sdk` on npm — one import, every private DeFi operation
- `b402-mcp` on npm — Claude Desktop / Cursor / any MCP client can execute private DeFi
- Virtuals ACP — privacy-for-hire service on the agent marketplace
- Kohaku adapter — compatible with Ethereum Foundation's wallet privacy standard
- Biconomy Nexus integration — private execution for Smart Session agents

**On-chain proof:**
- Private cross-chain swap: 1 USDC (Base) → 8.61 ARB (Arbitrum), 34 seconds, unlinkable
- Private Morpho deposit via Kohaku adapter
- Shield/unshield round-trips across 3 chains

## The ZK ownership primitive

The Railgun merkle tree is already a ZK-proven ownership ledger. Every shielded note is:
- Cryptographically owned by a specific 0zk identity
- Provable on-chain without revealing which note or how much
- Spendable only by the holder via nullifier + ZK proof
- Programmable — notes can represent anything: revenue claims, stake, future tokens

This is the foundation for ownership without cap tables. A shared merkle tree where contributors hold encrypted claims. Revenue distribution happens proportionally to note holders — without anyone knowing who holds what.

**What exists today:** the merkle tree, the ZK proofs, the shielding/unshielding, the gasless execution, the cross-chain routing, the agent MCP interface.

**What we'd build next:** the application layer — programmable claims, revenue distribution to anonymous note holders, ZK-proven contribution records. Turn the privacy pool into a coordination instrument.

## Links

- SDK: [npmjs.com/package/@b402ai/sdk](https://npmjs.com/package/@b402ai/sdk)
- MCP: [npmjs.com/package/b402-mcp](https://npmjs.com/package/b402-mcp)
- Kohaku adapter: [github.com/b402-ai/b402-kohaku](https://github.com/b402-ai/b402-kohaku)
- Demo: [x.com/_mayurc](https://x.com/_mayurc)

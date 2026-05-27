🌙 Midnight Bulletin Board — Cardano Granny's Journey

👩‍💻 Who Am I?
I'm Cardano Granny. I've been online since the Prodigy days, wrote a little BASIC back in the mid-80s, and have been following crypto since early 2017. My professional background has always been in the beauty industry — not computers — but I've never been afraid of technology or intimidated by learning something new.
When Midnight Network came along with its promise of privacy-preserving blockchain technology, I decided to dive in headfirst through the Midnight Academy. I had never written a real line of code before starting these lessons. I used AI assistance along the way and I'm not embarrassed to say so — knowing how to learn with the tools available to you is a skill in itself.
If you're reading this and think you're too old or too far outside the tech world to understand any of this — I hope this repository changes your mind.

📖 What Is This Repository?
This is my working copy of the Midnight Bulletin Board (bboard) example — a complete, privacy-preserving decentralized application built on the Midnight Network.
I worked through this project as part of the Midnight Academy Lessons 3.1 through 3.4, learning about:

🔐 Zero Knowledge (ZK) proofs and what they actually mean in practice
📝 The Compact smart contract language
🏗️ How a real DApp is structured in layers (contract, API, CLI)
🌙 How Midnight protects your identity while keeping messages public


🧱 What The Bulletin Board Does
The bulletin board lets anyone post a public message — but only the original poster can take it down, and they prove ownership without ever revealing who they are.
This is selective disclosure in action:
What Everyone SeesWhat Only You KnowThe message itselfYour secret keyA hash of your public keyThat the hash came from YOUThe board state (occupied/vacant)Your identity
The magic is that the network can verify you are the owner without learning anything about you. That's a Zero Knowledge proof.

🗺️ The Three Layers I Studied
Layer 1 — The Contract (Lesson 3.1)
Written in Compact, Midnight's privacy-focused smart contract language. It defines:

The board's state (VACANT or OCCUPIED)
Two circuits: post and takeDown
A witness-based identity system using secret keys and public key hashes
Replay protection using a sequence number

Layer 2 — The API (Lesson 3.2)
A TypeScript layer built with RxJS that:

Connects all the infrastructure pieces together
Observes on-chain state changes in real time
Exposes deploy(), join(), post(), and takeDown() methods

Layer 3 — The CLI (Lesson 3.3)
An interactive command-line application that:

Creates and manages wallets
Generates DUST (the shielded fee token)
Provides a menu for interacting with the bulletin board


🚀 What I Actually Did (Lesson 3.4)
I ran the complete end-to-end lifecycle of the DApp:

✅ Compiled the Compact contract into ZK circuits
✅ Built the CLI infrastructure
✅ Started all four services (node, indexer, proof server, faucet)
✅ Created a wallet with the genesis seed
✅ Deployed a bulletin board contract to the local network
✅ Posted a message: "Hello from Cardano Granny on Midnight!"
✅ Viewed the three different state perspectives (ledger, private, derived)
✅ Took down the message and watched the sequence number increment

The Three State Views In Action
When I posted my message, here is what each view showed:
Option 3 — Ledger State (what everyone sees):
Current state is: 'occupied'
Current message is: 'Hello from Cardano Granny on Midnight!'
Current sequence is: 1
Current owner is: '8e9c65e788747e29ca36da48f5add2b2bef0d1488601a5199314c4091dcc619d'
Option 4 — Private State (what only I know):
Current secret key is: [private — never shared publicly]
Option 5 — Derived State (the combined view):
Current state is: 'occupied'
Current message is: 'Hello from Cardano Granny on Midnight!'
Current sequence is: 1
Current owner is: 'you'
The public sees a hash. I see 'you'. Nobody can reverse the hash to find me. That's privacy-preserving technology working in real life.

💡 What I Learned About Zero Knowledge Proofs
Before this course, ZK proofs sounded like science fiction. Now I understand them in plain English:

A Zero Knowledge proof lets you prove you know something without revealing what it is.

In the bulletin board:

My secret key never touches the blockchain
The network only sees a mathematical hash derived from my key
A ZK proof confirms I ran the circuit correctly, without revealing my key
Even if someone sees my public key hash, they cannot work backwards to find me

It's like proving you know the combination to a safe without opening the safe or saying the numbers out loud.

🐛 My Contribution to the Midnight Community
While working through this lesson, I discovered that both the preprod-remote and standalone modes were failing with Wallet.Sync errors due to outdated Docker image versions.
I reported this issue in the Midnight Discord #dev-chat, where moderator norm [MDNT] confirmed he could reproduce it and escalated it to the development team.
This led directly to Pull Request #1441 being created, reviewed, and merged:
👉 fix: bump versions #1441
The fix updated two Docker images:

indexer-standalone: 3.0.0 → 4.0.1
midnight-node: 0.20.1 → 0.22.3

I may be new to coding, but I was able to contribute to the Midnight developer community by simply doing the work and reporting what I found. 😊

🔮 Where I'm Going Next
This is just the beginning. My long-term goal is to build VaultBeauty — a privacy-preserving application on the Midnight Network for the beauty industry. Through projects like this bulletin board, I am learning the patterns and building the understanding I need to make that vision real.
One lesson at a time. One block at a time. 🌙

🛠️ How To Run This Yourself
Prerequisites

Node.js LTS (v24.11.1 or higher)
Docker Desktop
WSL2 (if on Windows)

Steps
Clone the repository and navigate into it, then install dependencies with npm install. Compile the contract by running npm install, npm run compact, and npm run build inside the contract folder. Then build and run the CLI from the bboard-cli folder with npm install, npm run build, and npm run standalone. When the menu appears, choose option 1 to deploy a fresh bulletin board!

🙏 Acknowledgements

The Midnight Network team for building this technology and maintaining excellent documentation
norm [MDNT] and JAlbertCode for their quick response to my bug report
Claude (Anthropic) for patient, step-by-step guidance through every lesson
The Midnight Discord community for being welcoming to someone coming at this from a completely different background


Cardano Granny — Rimrock, Arizona — May 2026 🌵🌙

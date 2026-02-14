# Stellance 🚀

> Decentralized freelance payment platform powered by Stellar (XLM)

Stellance eliminates payment barriers for freelancers worldwide — no banks, no middlemen, no excessive fees. Get paid instantly, anywhere in the world, using the Stellar blockchain.

---

## 🌍 The Problem

- Freelancers lose up to **20% of earnings** to platform fees and payment processors
- Millions of freelancers in Africa, Asia, and Latin America **can't receive international payments** due to banking restrictions
- Traditional payouts take **3–7 business days** and involve multiple intermediaries
- No transparent, on-chain record of work agreements or payment history

## ✅ The Solution

Stellance uses Stellar's payment network to:
- Send payments **instantly** across borders for fractions of a cent
- Support **USDC and XLM** as payment currencies with easy local conversion
- Give freelancers and clients a **trustless, transparent** escrow system
- Work for **anyone with a smartphone** — no bank account required

---

## ✨ Key Features

- **Instant Cross-Border Payments** — Powered by Stellar, settlements in 3–5 seconds
- **Escrow Smart Contracts** — Funds are locked until work is delivered and approved
- **Multi-Currency Support** — Pay in USDC, XLM, or other Stellar assets
- **On-Chain Job Agreements** — Immutable records of contracts and milestones
- **Low Fees** — Platform fee under 2%, vs. 20% on traditional platforms
- **No Bank Required** — Just a Stellar wallet address to get started
- **Freelancer Profiles** — Reputation system backed by on-chain payment history

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js 14 (App Router) |
| Backend | NestJS |
| Blockchain | Stellar Network (XLM / USDC) |
| Stellar SDK | `@stellar/stellar-sdk` |
| Database | PostgreSQL |
| ORM | Prisma |
| Auth | JWT + Stellar wallet signature |
| File Storage | IPFS / AWS S3 |
| Deployment | Vercel (frontend) + Railway (backend) |

---

## 📁 Project Structure

```
stellance/
├── apps/
│   ├── web/                        # Next.js frontend
│   │   ├── app/
│   │   │   ├── (auth)/
│   │   │   │   ├── login/
│   │   │   │   └── register/
│   │   │   ├── (dashboard)/
│   │   │   │   ├── jobs/
│   │   │   │   ├── contracts/
│   │   │   │   ├── payments/
│   │   │   │   └── profile/
│   │   │   ├── layout.tsx
│   │   │   └── page.tsx
│   │   ├── components/
│   │   │   ├── ui/
│   │   │   ├── wallet/
│   │   │   ├── jobs/
│   │   │   └── payments/
│   │   ├── hooks/
│   │   │   ├── useStellarWallet.ts
│   │   │   ├── useEscrow.ts
│   │   │   └── usePayments.ts
│   │   ├── lib/
│   │   │   ├── stellar.ts
│   │   │   └── api.ts
│   │   └── public/
│   │
│   └── api/                        # NestJS backend
│       ├── src/
│       │   ├── auth/
│       │   │   ├── auth.module.ts
│       │   │   ├── auth.service.ts
│       │   │   └── auth.controller.ts
│       │   ├── users/
│       │   │   ├── users.module.ts
│       │   │   ├── users.service.ts
│       │   │   └── users.controller.ts
│       │   ├── jobs/
│       │   │   ├── jobs.module.ts
│       │   │   ├── jobs.service.ts
│       │   │   └── jobs.controller.ts
│       │   ├── contracts/
│       │   │   ├── contracts.module.ts
│       │   │   ├── contracts.service.ts
│       │   │   └── contracts.controller.ts
│       │   ├── payments/
│       │   │   ├── payments.module.ts
│       │   │   ├── payments.service.ts
│       │   │   └── payments.controller.ts
│       │   ├── stellar/
│       │   │   ├── stellar.module.ts
│       │   │   ├── stellar.service.ts  # Core Stellar integration
│       │   │   └── escrow.service.ts   # Escrow logic
│       │   ├── prisma/
│       │   │   └── prisma.service.ts
│       │   └── main.ts
│       ├── prisma/
│       │   └── schema.prisma
│       └── test/
│
├── packages/
│   ├── shared/                     # Shared types & utilities
│   │   ├── types/
│   │   └── utils/
│   └── stellar-utils/             # Reusable Stellar helpers
│       ├── escrow.ts
│       ├── wallet.ts
│       └── transactions.ts
│
├── docs/
│   ├── architecture.md
│   ├── stellar-integration.md
│   └── api.md
│
├── .github/
│   └── workflows/
│       ├── ci.yml
│       └── deploy.yml
│
├── docker-compose.yml
├── turbo.json                      # Turborepo config (monorepo)
├── package.json
└── README.md
```

---

## 🔄 How It Works

```
1. Client posts a job
         ↓
2. Freelancer applies & gets hired
         ↓
3. Client funds escrow (XLM/USDC locked on Stellar)
         ↓
4. Freelancer completes work & submits
         ↓
5. Client approves → funds released instantly to freelancer
         ↓
6. Dispute? → Platform mediates & releases funds accordingly
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL
- Stellar testnet account ([Create one here](https://laboratory.stellar.org/#account-creator?network=test))

### Installation

```bash
# Clone the repo
git clone https://github.com/yourusername/stellance.git
cd stellance

# Install dependencies
npm install

# Set up environment variables
cp apps/api/.env.example apps/api/.env
cp apps/web/.env.example apps/web/.env

# Run database migrations
cd apps/api && npx prisma migrate dev

# Start development servers
npm run dev
```

### Environment Variables

**Backend (`apps/api/.env`)**
```env
DATABASE_URL=postgresql://user:password@localhost:5432/stellance
JWT_SECRET=your_jwt_secret
STELLAR_NETWORK=testnet           # or 'mainnet'
STELLAR_HORIZON_URL=https://horizon-testnet.stellar.org
ESCROW_SECRET_KEY=your_stellar_secret_key
```

**Frontend (`apps/web/.env.local`)**
```env
NEXT_PUBLIC_API_URL=http://localhost:3001
NEXT_PUBLIC_STELLAR_NETWORK=testnet
```

---

## 🗺 Roadmap

### Phase 1 — MVP (Month 1–2)
- [ ] User registration & Stellar wallet connection
- [ ] Job posting and browsing
- [ ] Basic escrow (fund → approve → release)
- [ ] Payment history dashboard

### Phase 2 — Core Features (Month 3–4)
- [ ] Milestone-based payments
- [ ] Dispute resolution system
- [ ] Freelancer reputation & reviews
- [ ] Multi-currency support (USDC, XLM, EURC)

### Phase 3 — Growth (Month 5–6)
- [ ] Mobile app (React Native)
- [ ] Team/agency accounts
- [ ] API for third-party integrations
- [ ] Fiat on/off ramp integration

---

## 🤝 Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](./docs/CONTRIBUTING.md) first.

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](./LICENSE) file for details.

---

## 🌐 Connect

Built with ❤️ to empower freelancers worldwide.

> *"Your work, your money, your terms."*

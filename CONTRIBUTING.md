# Contributing to Stell-Optics

Thank you for your interest in contributing to Stell-Optics.

This project is a proposed Stellar-powered Web3 platform that connects blockchain payments with everyday mobile connectivity. Our goal is to make crypto practical for real-world use by enabling XLM-based purchases of mobile data bundles, while keeping the system secure, transparent, and easy to extend.

Please read [README.md](README.md) first so you understand the product vision, the intended architecture, and the roadmap before proposing changes.

## Project vision

Stell-Optics is designed around a simple core idea:

- users connect a Stellar wallet;
- choose a mobile data bundle;
- approve an XLM payment;
- the backend verifies the payment;
- the provider fulfills the mobile data order;
- the user receives confirmation and purchase history.

This is an evolving project. Not every capability described in the README is fully implemented yet, and work should be scoped accordingly.

## Where to contribute

The repository is organized around the main parts of the system:

| Area | Purpose | Notes |
| --- | --- | --- |
| [`apps/frontend`](apps/frontend/) | Web experience and dashboard | Planned as the primary user interface |
| [`apps/backend`](apps/backend/) | FastAPI backend, payment verification, and provider integration | Core business logic lives here |
| [`contracts`](contracts/) | Soroban / Rust smart contracts | Intended for selected on-chain functionality |
| [`docs`](docs/) | Architecture, process, and project guidance | Use these for design and workflow context |
| [`scripts`](scripts/) | Utility scripts and repository automation | Helpful for validation and maintenance |

Before starting work, identify which layer your change belongs to and keep your patch focused on that part of the system.

## Contribution principles

We value practical, secure, and well-documented contributions.

- Keep changes focused and easy to review.
- Prefer server-side verification over trusting client-provided transaction data.
- Never request a user’s private keys or seed phrase.
- Use testnet settings first; do not mix development and production credentials.
- Document new APIs, flow changes, or assumptions in the relevant docs.
- If a change is substantial, open or reference an issue first.

## Getting started

### Prerequisites

Before contributing, make sure you have the tools needed for the feature area you are working on:

- Git
- Node.js and npm
- Python 3.11 or a compatible version
- PostgreSQL
- Rust and Soroban tooling if you are working on contracts

### Clone and set up

```bash
git clone https://github.com/Dev-Zully/Stell-Optics.git
cd Stell-Optics
```

Then follow the setup instructions for the relevant component:

- frontend: see the app-specific setup in [`apps/frontend`](apps/frontend/)
- backend: see the backend setup in [`apps/backend`](apps/backend/)
- contracts: use the contract workspace in [`contracts`](contracts/)

The project should be developed with a clear separation between:

- wallet interaction,
- payment verification,
- provider fulfillment,
- and user-facing order tracking.

## Development workflow

1. Fork the repository and create a branch for your work.
2. Keep your branch aligned with the project goal and scope.
3. Make small, atomic commits with clear messages.
4. Validate the relevant app or component before opening a pull request.
5. Open a pull request describing the problem, the solution, and any risks.

Suggested branch naming patterns:

- `feat/...` for new features
- `fix/...` for bug fixes
- `docs/...` for documentation updates
- `chore/...` for maintenance work

## Coding and design expectations

### Web and mobile work

- Keep the user flow consistent with the README purchase journey.
- Make sure data bundle selection, quote generation, and transaction state are clearly understandable.
- Keep wallet actions explicit and user-controlled.

### Backend work

- Verify payment details independently on the Stellar network.
- Treat incoming transaction data as untrusted until confirmed server-side.
- Handle duplicate orders and retries carefully.
- Preserve transparent order status and error reporting.

### Contract work

- Keep Soroban contracts focused on real on-chain needs.
- Avoid adding smart contract logic where a secure backend process would be clearer and simpler.
- Add tests and review the safety assumptions before proposing a production deployment.

## Testing and verification

Before submitting a pull request, run the checks that apply to the code you touched.

Examples include:

```bash
# frontend
npm test

# backend
pytest

# contract workspace
cargo test
```

Use the app-level or workspace-specific scripts defined in each project folder when available. The goal is not just to pass a broad suite, but to confirm the behavior relevant to your change.

## Security and responsible development

Stell-Optics works with blockchain payments and telecom integrations, so security is a first-class concern.

Please:

- never commit secrets, private keys, or provider credentials;
- keep environment variables in local configuration or a secure secrets manager;
- separate Testnet and Mainnet configuration;
- verify payment status on the server before fulfilling orders;
- handle idempotency and duplicate processing carefully;
- document any assumptions around provider failures or delayed delivery.

If you are fixing a security issue, do not open a public issue. Use the private reporting process described in the project documentation.

## Documentation expectations

When changing a workflow, API, or system architecture:

- update the relevant docs,
- keep examples aligned with the README,
- describe any implementation status clearly,
- note whether the behavior is proposed, in progress, or implemented.

This project is an early-stage product vision, so clarity matters as much as correctness.

## Pull requests

When opening a pull request:

- explain the problem and the reason for the change;
- describe the impact on the user flow or backend behavior;
- include screenshots or examples when relevant;
- explain how the change was verified;
- reference any related issue or discussion.

Keep pull requests focused and reviewable. Large, mixed-purpose changes are harder to validate and maintain.

## Code of conduct

This project follows the Contributor Covenant Code of Conduct. Participation in the project implies respect for the community and the goal of building useful, secure, and accessible blockchain tools.

Thank you for helping make Stell-Optics more useful, more secure, and more practical for everyday people.

### Hi, I'm Andrew

Stanford CS

Currently building [Jane](https://jane-dusky.vercel.app), an AI financial controller that runs your money on autopilot.

## Jane

**The goal.** Jane looks through your bank accounts securely through Plaid and builds a picture
of who you are: a college student, a dog owner, a mother of three. Then it goes through every
area of your money:
- subscriptions and bills
- bank fees and idle cash
- cards, loans and debt
- insurance
- taxes
- investing and retirement
- your goals

In each area it finds the best plan for you, and it prefills the steps through connectors.
All you do is tap yes or no.

**Where it is now.** The MVP is a read-only closed beta ([live](https://jane-dusky.vercel.app),
[overview](https://github.com/cubic1M/jane-overview)). Jane reads accounts through Plaid or uploaded
statements and builds the profile. It finds what each area is costing you and shows the best
plan with the exact steps, which the user carries out. Connectors that take those steps for the
user come next, in stages.

My work focuses on:

- **The AI agent.** Agents uses tools over the user's own data. All money math is done in
  deterministic code, never by the model, and every reply passes a guardrail check before
  it's shown.
- **Security and privacy.** Every query is scoped to the signed-in user, and a test proves
  every route refuses another person's IDs. Plaid tokens are encrypted with AES-256-GCM, and
  spending caps stay atomic even when many requests arrive at once.
- **Engineering with AI agents.** Jane is built with a team of agents working in parallel.
  I designed the specs and rules they follow, the CI and merge gates, and a deploy
  loop that ships only green commits and rolls back on a failed live check.

## Selected work

- **Access proof:** a test proves every route refuses another person's data.
- **Deny by default:** all database access is denied unless scoped to the signed-in user, with
  a no-bypass test login.
- **Concurrency-safe limits:** requests sent at once can't exceed AI spending caps or run an
  action twice.
- **Tax suggestions:** what isn't withheld yet, with the calculation shown and user corrections.
- **Instant pages:** pages are cached and preloaded in the background.
- **The first connector:** a read-only Robinhood connection over MCP, switched off until
  approved.

**Stack:** Next.js, TypeScript, Postgres/Prisma, Plaid, Anthropic Claude, Vercel, Vitest and
Playwright (about 9,300 test cases).

[Jane](https://jane-dusky.vercel.app) · [Jane overview](https://github.com/cubic1M/jane-overview)

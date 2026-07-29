<div align="center">

# 🤖 SendsBot

### AI-Powered Business Messaging & E-Commerce Automation

[![Live](https://img.shields.io/badge/Live-sendsbot.com-00D1FF?style=for-the-badge&logo=googlechrome&logoColor=white)](https://www.sendsbot.com)
[![Status](https://img.shields.io/badge/Status-Active%20Development-FFD93D?style=for-the-badge)](https://www.sendsbot.com)

**Founder & Lead Developer**

</div>

---

## What it is

A SaaS platform that lets businesses run AI-assisted WhatsApp and Instagram
conversations, marketing campaigns and e-commerce automation from a single dashboard.

**→ [sendsbot.com](https://www.sendsbot.com)**

## What it does

- **AI-assisted replies** grounded in the business's own product catalogue and knowledge
  base, so answers come from real inventory rather than invention
- **Campaign tools** for scheduled and segmented outbound messaging
- **E-commerce automation** — abandoned-cart recovery and order-status lookups
- **Unified inbox** across channels, with hand-off to a human when one is needed
- **Business back office** — subscription billing, team roles and permissions, a
  referral programme, and analytics with an audit trail

## Compliance & reliability

Opt-out handling is enforced on every outbound path, with per-account send limits,
encrypted third-party credentials, and error monitoring throughout.

Getting opt-out right matters more than it sounds: it has to sit on the send path
itself, not in the campaign builder, or the one code path someone adds later bypasses it.
The general shape:

```ts
async function send(recipient: string, message: string) {
  // Checked here, at the single point every outbound message passes through -
  // not at the call sites, which multiply over time.
  if (await hasOptedOut(recipient)) {
    return { skipped: 'opted-out' };
  }
  if (await overDailyLimit(recipient)) {
    return { skipped: 'rate-limited' };
  }
  return deliver(recipient, message);
}
```

> Illustrative only. It is not taken from the SendsBot codebase, and it is not how the
> system is put together.

## Built with

![Next.js](https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=flat-square&logo=supabase&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)

## Source

This repository is a showcase. **The application source is private, and the
implementation is deliberately not documented publicly.**

SendsBot is a commercial product in active development. What it does is described
above; how it is built is not, and that is on purpose.

I'm glad to go into depth in an interview.

---

<div align="center">

**[Enes Elhovete](https://www.enes-elhovete.com)** · [enes.elhovete@hotmail.com](mailto:enes.elhovete@hotmail.com) · [LinkedIn](https://www.linkedin.com/in/enes-elhovete/)

</div>

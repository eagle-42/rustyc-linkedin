# LinkedIn Posts — Axel Beaugrand

---

## Post 01 — Hook #1 ✅
> "I spent 10 years making Python work in production. Then I used Rust. I can't go back."

---

I spent 10 years making Python work in production.
Then I used Rust. I can't go back.

Python got me everywhere. A decade of data pipelines, health records, infrastructure at Korian, Groupama, GE. It ships fast. I was good at it.

The problem showed up quietly.

A bare `except` swallowed an error without a trace.
A type mismatch passed every test and only surfaced under real load.
A service degraded so slowly nobody noticed until it was too late.

Each time, I spent hours finding what the language could have caught for free.

Then at GE I joined an HPC platform. Simulation jobs running for up to 14 days.

One silent failure meant 336 hours of compute gone. No replay. No partial results. Just a Monday conversation I watched happen once and never wanted to be part of.

I wrote my first Rust microservice that week.

The compiler rejected my code 31 times before it ran. I had the error messages on one screen and the Rust Book on the other. I read the same chapter three times and couldn't tell you what it said.

Shit, this is hard.

But every rejection came with the exact line number, the memory location, the ownership chain. The compiler knew what was wrong before I shipped it.

When it finally ran, it ran correctly. I didn't lie awake wondering what might break. I knew.

I still write Python. Some problems don't need Rust.

But the services I care most about are in Rust now. They don't wake me up at night.

10 years of Python taught me to move fast.
Rust taught me to sleep.

If you're a platform engineer curious about where Rust actually fits, follow me. I write about this every week.

---

#Rust #PlatformEngineering #SRE #HPC #Python #SystemsProgramming #OpenTelemetry #SoftwareEngineering

---

## Post 02 — Hook #2 ✅
> "10 years of platform engineering. The one thing I wish I'd learned sooner: Rust."

---

10 years of platform engineering.
The one thing I wish I'd learned sooner: Rust.

A decade of keeping systems alive. Korian, Groupama, GE, Renault. Health records. Finance pipelines. HPC simulations. Infra that people depended on.

Python carried me most of the way. I was good at it.

But there was always a tax.

A type mismatch passed every test and surfaced under real load at 3am.
A pipeline drifted for 6 weeks before anyone noticed.
The health record system ran on "probably fine." Nobody said it out loud. Nobody had to.

Each time, I added more monitoring. More tests. More alerts. The surface area of uncertainty never went to zero.

At GE I worked on a simulation platform. Jobs ran up to 14 days. One silent failure meant 336 hours of compute, gone. No replay. No partial results.

I watched it happen in a Monday standup. Someone explained what failed. The room went quiet. I sat there thinking: we built all this observability infrastructure. We still didn't catch it.

That week I started learning Rust. The cost of being wrong had become too high.

The compiler was brutal. Week 3. Sunday evening. I had the error message open on one screen and the Rust Book on the other, just to feel like I was making progress. I'd read the same chapter three times and couldn't tell you what it said.

I almost closed the laptop.

"Maybe this is for computer science people. I started with Python data pipelines. Maybe that's as far as I go."

Then something shifted.

The compiler wasn't blocking me. It was showing me exactly what I hadn't thought through. Memory safety. Thread safety. Every edge case I would have found at 2am in production.

When it finally compiled, it ran correctly. Not "probably correctly." Correctly.

10 years taught me to ship fast and monitor hard. Rust gave me a third option: make wrong states unrepresentable before you ship.

I wish I'd had it at Korian. I wish I'd had it at Groupama.

Your Python years aren't wasted. They're your foundation. You just need to go one layer deeper.

If you're a platform engineer wondering where Rust actually fits, follow me. I write about this every week.

---

#Rust #PlatformEngineering #SRE #Observability #Python #SystemsProgramming #OpenTelemetry #HPC

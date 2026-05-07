---
title: "AgentCon Raleigh"
date: 2026-05-07
draft: false
summary: "Lessons learned from attending AgentCon-Raleigh"
tags: ["AI", "Learning"]
---

# I Spent a Day at AgentCon Raleigh and My Brain Hasn't Stopped Since

**May 6, 2026 · Durham, NC · AgentCon World Tour**

---

I drove out to the NC Biotech Center in Durham yesterday for AgentCon Raleigh — part of the Global AI Community's worldwide AI Agents World Tour — and I'm still processing everything I heard. Seven sessions, one full day, and somewhere around four pages of notes scrawled in the margins of my notebook. Here's what stood out.

---

## What Made the Day Worth the Drive

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin: 1.5rem 0;">

  <div style="border: 1px solid rgba(255,255,255,0.15); border-radius: 10px; padding: 1.25rem 1.5rem;">
    <div style="font-size: 1.4rem; margin-bottom: 0.6rem;">🎙</div>
    <h4 style="font-size: 0.9rem; font-weight: 600; margin: 0 0 0.4rem;">Deep-dive talks</h4>
    <p style="font-size: 0.85rem; line-height: 1.6; margin: 0;">Speakers sharing battle-tested patterns — not polished marketing, but real architectural decisions and tradeoffs from people actively shipping agents.</p>
  </div>

  <div style="border: 1px solid rgba(255,255,255,0.15); border-radius: 10px; padding: 1.25rem 1.5rem;">
    <div style="font-size: 1.4rem; margin-bottom: 0.6rem;">🛠</div>
    <h4 style="font-size: 0.9rem; font-weight: 600; margin: 0 0 0.4rem;">Technical workshops</h4>
    <p style="font-size: 0.85rem; line-height: 1.6; margin: 0;">Hands-on sessions covering building, deploying, and scaling agents — with time to actually get your hands dirty in the tooling.</p>
  </div>

  <div style="border: 1px solid rgba(255,255,255,0.15); border-radius: 10px; padding: 1.25rem 1.5rem;">
    <div style="font-size: 1.4rem; margin-bottom: 0.6rem;">⚡</div>
    <h4 style="font-size: 0.9rem; font-weight: 600; margin: 0 0 0.4rem;">Live demos</h4>
    <p style="font-size: 0.85rem; line-height: 1.6; margin: 0;">Open-source frameworks demoed live, with presenters walking through code in real time. The kind of thing that actually sticks.</p>
  </div>

  <div style="border: 1px solid rgba(255,255,255,0.15); border-radius: 10px; padding: 1.25rem 1.5rem;">
    <div style="font-size: 1.4rem; margin-bottom: 0.6rem;">🌐</div>
    <h4 style="font-size: 0.9rem; font-weight: 600; margin: 0 0 0.4rem;">Global community</h4>
    <p style="font-size: 0.85rem; line-height: 1.6; margin: 0;">Builders from across the Triangle and beyond — a reminder that the Raleigh-Durham area punches well above its weight in AI development talent.</p>
  </div>

</div>

## Keynote: So You're An Agent Boss Now — April Dunnam

April kicked off the day with a keynote that I suspect was specifically designed to make everyone feel a little behind and a lot excited at the same time. Her framing was sharp: generative AI was the warmup act. Agents are the main event.

The distinction she drew is one I keep coming back to. Generative AI waits for your prompt. Agents _perceive, plan, and act_ — sometimes across dozens of steps, across multiple systems, without you touching a thing. That's not an upgrade. That's a different relationship between humans and software entirely.

She walked through where the agentic stack actually lives today — Azure AI Foundry, Semantic Kernel, AutoGen, MCP, low-code tooling — and made the case that what we need now isn't just builders, it's people who can _lead_ agents. Give them direction. Supply the judgment. Recognize when something's going sideways before it's gone too far sideways to fix.

The "AgentBoss" framing stuck with me. It's a little cheeky but it's also accurate. The tools exist. The question is whether the humans running them are ready to lead.

---

## Agentic Coding Harnesses from Nothing — James Nugent

This was the session I was most excited about coming in and it did not disappoint. James took the "let's demystify this" approach and actually built an agentic coding harness from scratch in Go — running against a model on his laptop, live, in the room.

Tools like Claude Code, Codex, and Copilot can feel like black boxes. James pulled back the curtain and showed what's actually happening underneath. Turns out it's not magic — it's a loop you can understand, reason about, and build yourself.

What I took away: even if you never ship your own harness, building one (or at least watching someone build one) fundamentally changes how you use the big-name tools. You stop guessing and start reasoning. That's worth a 45-minute session any day.

---

## Stop Fighting Your Framework: Ship Agents with Open Source — Jonathan Vogel

Jonathan opened with something I've definitely experienced: "Most AI agent demos work once." Then requirements change, you need to swap a model, add a tool, debug a decision path — and suddenly you're wrestling with the framework instead of building your product.

His answer is Strands Agents, the open-source SDK Amazon teams used internally to compress their agent shipping timelines from months to weeks. The core idea is a model-driven agentic loop — reason, act, reflect — that's simple enough to get started quickly but extensible enough to survive real traffic, real edge cases, and real users.

He live-coded an agent from scratch during the session, added tools, and narrated every step of what was happening. By the end I had a much cleaner mental model for how production agents should be structured. The "stop fighting your framework" message is something I want to paste above my desk.

---

## Brownfield vs. Greenfield AI: Same Tools, Different Playbooks — Chris Perrin

Chris might have delivered the most _immediately applicable_ session of the day. His setup: he builds solo greenfield products at night and leads enterprise brownfield engineering teams by day. That dual perspective made this talk genuinely different.

The big insight is one most teams discover the hard way — the wrong playbook can cost you a sprint. Prompting an AI to generate code for a legacy codebase the same way you'd prompt it for a greenfield project is a recipe for "local correctness, global incompatibility." The code looks fine. The system breaks.

He walked us through side-by-side prompting, the concept of "context debt" (surfacing the implicit decisions baked into an old codebase before the AI unknowingly overwrites them), and a review checklist for catching brownfield failure modes before they ship.

I work in both contexts regularly and I'm already thinking about how to adapt my prompting discipline based on what Chris laid out.

---

## From Monolith to Microservices: AI to Accelerate Decomposition & Team Learning — Sunil Mishra

Sunil tackled one of the most daunting things in enterprise engineering: getting out of the monolith. The organizational reality he described felt very familiar — large, complex legacy applications that are hard to scale, teams that lack the time and documentation to do a migration safely, and a transformation process that traditionally eats months of expert attention.

His session showed how AI-powered tools can change the calculus: analyzing legacy codebases, identifying hidden dependencies, surfacing natural service boundaries, and essentially acting as an interactive guide that explains code paths and summarizes business logic on demand.

The part that resonated most was the "team learning" angle. It's not just about moving faster. It's about reducing the grip of tribal knowledge — the one senior engineer who holds the mental map of why things are the way they are. AI as a tool for democratizing that understanding is a use case I hadn't fully appreciated before this session.

---

## Building a Controlled Agentic SDLC — Chris Condron

Chris shared something rare: a real war story. His talk covered PowerModels' journey from cautiously adopting AI in their development pipeline all the way to running a fully controlled agentic SDLC — for an application with _strict correctness requirements_. That last part is the key detail that made this session so interesting.

It's easy to use agents in low-stakes contexts. Using them where the output genuinely cannot be wrong is a different problem. Chris walked through how they started, how the system grew, the challenges they ran into, and — critically — the mind-shifts the team had to make to succeed.

He also demoed the actual agentic flow they run in production today: the approach, the steps, the tools they built. It's one of the best examples I've seen of agentic development taken seriously as an engineering discipline, not just a productivity shortcut.

---

## Copilot Studio to Azure AI Foundry: A Framework for Knowing When — and How — to Scale — Abhijeet Jadhav

Abhijeet closed out the day with something that felt almost like a palate cleanser: clarity. His session tackled a question a lot of enterprise teams are quietly grappling with — when do you outgrow Copilot Studio and move to Azure AI Foundry?

He built a practical, demo-driven framework around five platform graduation signals, a scoring matrix you can apply to your current project right now, three architecture transition patterns that protect existing investments, and a cost crossover analysis between Copilot Credits and Azure consumption.

I don't always love sessions that feel like vendor guidance, but this one earned its runtime by being genuinely tool-agnostic about the decision framework itself. The question of when to scale isn't a Microsoft question — it's an engineering judgment question, and Abhijeet gave us a principled way to answer it.

---

## The Day in a Sentence

If I had to distill everything down: agents aren't coming — they're here, the tooling is maturing fast, and the competitive advantage is now going to the people who have _judgment_ about when and how to deploy them, not just the ability to get them working once.

AgentCon Raleigh was exactly the kind of day I needed. Dense, technical, practical, and full of people who are actually shipping this stuff. If the World Tour comes anywhere near you, go.

---

_AgentCon Raleigh was organized by Global AI Raleigh and made possible by Microsoft, KCDC, and All Things AI. The AgentCon World Tour runs globally — find the next stop at [agentcon.dev](https://agentcon.dev)._

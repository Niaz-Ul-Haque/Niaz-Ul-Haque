<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,55:1B3A5C,100:2F81F7&height=190&section=header&text=Niaz%20Ul%20Haque&fontSize=54&fontColor=E6EDF3&fontAlignY=36&animation=fadeIn&desc=software%20engineer%20%C2%B7%20toronto%2C%20canada&descSize=17&descAlignY=57" width="100%" alt="Niaz Ul Haque, software engineer, Toronto, Canada" />

<a href="https://niazsite.vercel.app"><img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=18&pause=1400&color=2F81F7&center=true&vCenter=true&width=760&height=44&lines=Document+pipelines%2C+gateways%2C+and+no+frontend+framework;I+write+the+rules+the+coding+agents+have+to+follow;Most+of+my+best+work+is+behind+a+private+toggle" alt="Document pipelines, gateways, and no frontend framework" /></a>

<samp><a href="https://niazsite.vercel.app"><b>portfolio</b></a> &nbsp;·&nbsp; <a href="https://www.linkedin.com/in/mohammed-niaz-ul/"><b>linkedin</b></a> &nbsp;·&nbsp; <a href="https://x.com/AsahiKibo1"><b>x</b></a> &nbsp;·&nbsp; <a href="https://github.com/Niaz-Ul-Haque?tab=repositories"><b>repositories</b></a></samp>

</div>

<br>

I build systems that take messy input and turn it into something a database will accept. Long scanned PDFs, files that were faxed at some point in their life, the same name spelled four different ways.

Python where the ML libraries live, TypeScript nearly everywhere else, Postgres underneath. Most of my attention goes to the seams between services, because that is where things break. I would rather build something I can still run in two years than something that wins an argument about frameworks.

> [!NOTE]
> Twenty-four of my thirty most recent repositories are private. What follows is the trailer, not the film.

<br>

## What I'm actually building

These are personal projects. I build them to find out how something works, so the engineering is the point rather than the product.

**A document intelligence pipeline.** Messy financial paperwork goes in, structured and redacted profiles come out. A Python engine does conversion, OCR, LLM extraction and the profile merge. A Node gateway owns the public surface, sessions and CRUD. Postgres and a filesystem data lake hold the results. Every hop is HTTP. I skipped the message bus because nothing in there needed one.

**A strangler migration nobody noticed.** I moved four Python services onto Node one frozen contract at a time. The new process answered the old loopback ports, so the document pipeline kept calling them and never found out. The blockers I have not solved yet are written down in the repo, including the three places where two processes still share state through a filesystem instead of an API. Unwritten blockers become somebody's Tuesday.

**A frontend with no framework.** Native web components on an actor runtime: FIFO mailboxes, onion middleware, and a supervisor that health-checks its children and restarts the ones that stop answering. `fetch` lives in exactly one file and the model layer never touches the DOM. It was either principle or spite. The bundle is smaller either way.

**A component library for my own projects.** Custom elements, no runtime dependency, two stylesheets: the components and the theme values. It never goes to npm. Every project pulls it in as a local package, so changing the look lands everywhere at once instead of in four pull requests.

**The rules repo.** One repository holding the code-design practices, git workflow, PR checklist and review tooling that every other repository points at instead of copying. I work with coding agents daily, and the code is the easy file. The hard one explains what "good" means here, precisely enough that something with no taste can follow it.

<details>
<summary><b>&nbsp;the shape of it, roughly</b></summary>

<br>

```mermaid
flowchart LR
FE["web components<br/>actor runtime"] --> GW["gateway<br/>sessions · auth"]
GW --> APP["application layer<br/>reads · CRUD"]
GW --> ING["integration<br/>pipeline jobs"]
ING --> CV["convert + OCR"]
CV --> EX["LLM extraction"]
EX --> MG["merge + redact"]
APP --> PG[("postgres")]
MG --> PG
MG --> DL[["data lake"]]
```

One public port. Everything else on loopback. The data lake is disposable on purpose: every profile in Postgres can be rebuilt from its artifacts, so a bad extraction is a reprocess and never a re-ingest.

</details>

<br>

## On the public shelf

**[Revert Guide](https://github.com/Niaz-Ul-Haque/revert-guide)**. An offline-first, multilingual companion for new Muslims. English and French, structured content, automatic language fallback, and a translation layer that can take a third language without a rewrite.

**[ScrollMate](https://github.com/Niaz-Ul-Haque/Scrollmate)**. Hands-free auto-scroll for vertical comics on Android. Kotlin, accessibility gesture dispatch, and a floating bubble that remembers where you put it. It requests no `INTERNET` permission, so it cannot phone home. There is no phone and there is no home.

**[Pocket Pilot](https://github.com/Niaz-Ul-Haque/pocket-pilot)**. Privacy-first personal finance for Canadians. Budgets, savings goals, cash-flow forecasting, anomaly detection, row-level security, and an assistant that reads your spending so you don't have to relive it.

**[AWS Backend Playground](https://github.com/Niaz-Ul-Haque/aws-backend-playground)**. Lambda, DynamoDB, SAM, Parameter Store, and a deploy pipeline that authenticates through OIDC instead of a long-lived access key sitting in a secret somebody forgot to rotate.

**[SN Pest Control](https://github.com/Niaz-Ul-Haque/sn-pest-nextjs)**. A bilingual site, rebuilt. Statically generated, accessible, structured data throughout, and fast on the phone of someone who is currently looking at a wasp.

<br>

## Tools

<div align="center"><img src="https://skillicons.dev/icons?i=ts,python,kotlin,nodejs,react,nextjs,tailwind,postgres,supabase,aws,docker,githubactions&theme=dark&perline=12" alt="TypeScript, Python, Kotlin, Node.js, React, Next.js, Tailwind, PostgreSQL, Supabase, AWS, Docker, GitHub Actions" /></div>

And the unglamorous half that does the actual work: Vitest, Playwright, pgTAP, ruff, mypy, Docling, OCR, hermetic test suites that need no network, and a `commit-msg` hook that rejects my own commit messages more often than I would like to put in writing.

<br>

## Changelog

```console
## [2026.09] - unreleased

### Added
- a pipeline that reads eighty-page PDFs so that no human has to
- pre-push hooks running typecheck and tests, because I could not be trusted
- an architecture document, before the architecture

### Changed
- the frontend framework (removed it)
- "microservice" to "module", after counting the actual hops

### Deprecated
- "we'll clean this up later"

### Known issues
- still explains system architecture at dinner parties
- open tabs: 47 (wontfix)
```

<details>
<summary><b>&nbsp;numbers, for the people who like numbers</b></summary>

<br>

<div align="center"><img src="https://streak-stats.demolab.com?user=Niaz-Ul-Haque&theme=transparent&hide_border=true&border_radius=10&mode=weekly&exclude_days=Sat%2CSun&date_format=M%20j%5B%2C%20Y%5D&ring=2F81F7&fire=2F81F7&currStreakLabel=2F81F7" alt="contribution streak" /></div>

Weekends excluded on purpose. Any metric that charges me rent for taking a Saturday off can go be a landlord somewhere else.

</details>

<details>
<summary><b>&nbsp;off-duty</b></summary>

<br>

K-dramas, anime and K-pop, in roughly that order and occasionally all at once. I have opinions about the pacing of the back half of a sixteen-episode run and I will share them without being asked.

Otherwise: taking things apart to find out how they work, rebuilding them slightly worse, and learning more from the worse version than the original ever taught me.

</details>

<br>

<div align="center">

<picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Niaz-Ul-Haque/Niaz-Ul-Haque/output/github-contribution-grid-snake-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Niaz-Ul-Haque/Niaz-Ul-Haque/output/github-contribution-grid-snake.svg"><img alt="a snake eating a year of my commits" src="https://raw.githubusercontent.com/Niaz-Ul-Haque/Niaz-Ul-Haque/output/github-contribution-grid-snake.svg"></picture>

<br><br>

<samp><b>If you got this far, the private repos are genuinely the good ones.</b></samp>

</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2F81F7,45:1B3A5C,100:0D1117&height=130&section=footer&reversal=true" width="100%" alt="" />

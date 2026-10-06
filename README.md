# AI Studio Examples: Keep Your Project Moving

AI Studio is being developed as a web-based orchestration environment for general project development and for integrating AI workflows into client projects. Its purpose is to make it easier to move between work on a local computer and work on the web, while keeping the project's history, instructions and decisions connected.

A project often outlives the computer, chat session or model used to work on it. Reconstructing that context every time interrupts development: which files mattered, what the agent tried, why a decision was made, and what should happen next. AI Studio puts that continuity at the center of the workspace.

## One project, across environments and providers

- **Work locally, continue on the web.** Use local files, editors and development tools, then use the web workspace to inspect project state, coordinate AI work and pick up from retained history. The same project context should support both environments.
- **Retain history without carrying it all on your laptop.** The hosted architecture uses S3 for durable agent history and retained artifacts. The aim is to retrieve what a task needs while keeping accumulated history and large historical data in cloud storage, rather than requiring a complete local copy.
- **Develop projects and bring AI into client work.** Organize source files, project instructions, model runs, outputs and review decisions around the project. Adapt workflows for implementation, research, analysis and client deliverables, with client-specific access and operating policies.
- **Try different models and companies without starting over.** Keep project notes, instructions, source references and agent history independently of a single provider's chat interface. That retained context becomes the starting point when a different model or provider adapter is selected.

Context continuity means retaining the project record and deliberately supplying relevant context to the next run. Models still differ in context windows, tools and behavior; continuity does not promise identical answers or transfer a provider's hidden internal state.

## What these examples show today

The orchestration environment and its local/web integration are in development. This public repository provides Apache-2.0 building blocks and a synthetic, browser-only workspace tour. The tour illustrates project navigation, files, assistant roles and source-linked review records; its replies are deterministic mocks. Live S3 history retrieval, local/web synchronization and real provider switching belong to the operating application rather than this static demo.

The evidence-review workflows below demonstrate one use of the broader environment: keeping sources, bounded AI assistance, evaluation, accountable expert judgment and an exact release or handoff connected. The same project foundation can support general development and client AI workflows. The sector-specific brief, evidence types, rubric and qualified roles remain configurable.

The included detailed portfolio is a **synthetic public-service planning scenario**. The browser demo also includes engineering-assurance and research-synthesis examples. Everything is fictional: it does not assess a real project, client, standard or professional outcome.

## The demonstrated workflow

The browser demo and portable portfolio make every stage inspectable:

1. **Brief** — record the review question, audience, and expected deliverable.
2. **Sources** — declare the exact evidence set rather than relying on an unrecorded chat context.
3. **Findings** — link each bounded finding to source identifiers and leave missing support visible.
4. **Agent policy** — constrain tools, sources, claims, and behavior for AI-assisted work.
5. **Evaluation** — apply a versioned rubric without treating an automated score as approval.
6. **Expert decision** — preserve the accountable domain specialist's decision as a separate gate.
7. **Exact release** — identify the commit, artifact digest, workflow, actor, time, and outcome.
8. **Handoff** — state who receives the reviewed evidence pack and under what scope.

These examples focus on evidence-to-decision-to-release continuity. They give developers and expert teams a concrete workflow to adapt within AI Studio’s broader project orchestration environment, with project context and review records that remain useful across tools.

## Demo status

[Explore the live AI Studio workspace tour](https://categori-se.github.io/ai-studio-examples/). The site is deployed from an exact released tag and commit; its source link identifies the version being served.

This tree contains the `v0.5.1` documentation update. [`demo-provenance.json`](./demo-provenance.json) binds all six browser assets to that source version, and repository checks reject asset or source-link drift. The quick start uses Examples `v0.5.1` with the exact Contracts/Core `v0.5.0` dependencies. Those tags become available through their protected source releases.

- [Browse the public example repository](https://github.com/categori-se/ai-studio-examples)
- [Inspect the v0.5.1 example source](https://github.com/categori-se/ai-studio-examples/tree/v0.5.1)
- Browse [`portfolio/`](./portfolio/) for the synthetic service-access example and its digest-linked evidence chain

The hosted tour runs entirely in the browser using synthetic files and mock assistants. The operating application's sign-in, model execution, S3 history access, client connections and deployment controls are outside this static example.

## Reference scenario: synthetic service-access portfolio

`portfolio/workspace.yaml` indexes one fictional public-service planning review. This scenario was selected because its source limits, unresolved accessibility evidence, and expert gate are easy to see; a technical assurance note, research synthesis, policy recommendation, or due-diligence handoff can use the same contracts with a domain-owned rubric and roles. Follow the files in this order:

| File | What it demonstrates | What it does not claim |
| --- | --- | --- |
| `workspace.yaml` | A portable index that references project manifests by safe relative path | It is not a tenant or cloud account |
| `projects/evidence-review/project.yaml` | One service-access review question, owner role, bounded finding, declared source, agent policy, rubric, expert approval role, risk, cost center, and logical target | Declaring policy does not enforce identity, prove a finding, or make the contracts sector-specific |
| `fixtures/public-guidance.md` | A fictional planning record linked by a stable evidence identifier | It is not customer data, authoritative guidance, or a real service recommendation |
| `instructions/reviewer.md` | A narrow service-access evidence-review role with one allowed tool and explicit limits | It is not a private prompt, autonomous decision-maker, or release agent |
| `rubrics/evidence-quality.yaml` | Weighted, versioned criteria with human review required | A passing score is evidence, not approval |
| `records/document-set.json` | Exact source identity, version, storage identity, media type, and content digest | A manifest does not establish what the document proves |
| `records/evaluation-result.json` | A contract-valid machine result with rubric identity, bounded scores, confidence, and citations to the exact document set | Its `human_review` state remains `pending` |
| `records/review-decision.json` | A separate, attributable expert decision bound to the exact evaluation bytes | It explicitly does not authorize deployment, trading, source mutation, or any other operating effect |
| `records/release-artifact.json` | The approved finding, limitations, exact commit, and review-decision digest carried into the release artifact | This small fixture is not a production artifact format or storage service |
| `records/release-record.json` | A v2 release contract bound to the reviewed artifact digest, exact commit, synthetic workflow, and verification result | The reserved `example.invalid` URLs are deliberately non-operational |
| `records/handoff.json` | A read-only recipient scope bound to both the decision and release-record digests | No public handoff contract exists yet; repository tests enforce this deliberately small example shape |
| `no-content-telemetry.mjs` | OpenTelemetry GenAI operation details with content-bearing attributes omitted | It does not configure or select a telemetry vendor |

The tests recompute every file digest and reject a broken transition. In particular, a successful workflow string is insufficient: the browser marks a project released only when the exact document set, evaluation, human decision, artifact, release record, and read-only handoff agree.

## What is public, and what a managed service adds

The public code is useful by itself. Individuals and teams can copy, adapt, validate, run, and self-host the contracts, local workflow, synthetic portfolio, and static demo without a hosted account.

| Apache-2.0 components in these public repositories | Optional private managed operations |
| --- | --- |
| Provider-neutral project, evaluation, release, and telemetry contracts | Authenticated, owner-scoped records across projects and teams |
| Local-first shell, CLI, plugin SDK, and deterministic mock provider | Encrypted connector custody and bounded server-side agent execution |
| Inspectable briefs, source links, findings, reviewer policy, rubrics, and release fixtures, including the synthetic service-access reference | Shared candidate review, append-only expert decisions, and audit context |
| Low-idle-cost private-S3/CloudFront hosting template with no account-specific settings | Reviewed exact-SHA deployment requests and broader operational oversight |

The hosted AI Studio adds web orchestration, durable S3-backed project and agent history, and app-owned identity and execution controls over the portable foundation. Credentials, customer material, private infrastructure, proprietary execution policy, billing and account-specific settings retain their private boundaries. The public code remains usable locally or in self-managed workflows.

## Source quick start

Node.js 24 or later is required. The packages are not yet published to npm, so clone the three repositories as siblings and install the two local packages explicitly:

```bash
git clone --branch v0.5.0 --depth 1 https://github.com/categori-se/ai-studio-contracts.git studio-contracts
git clone --branch v0.5.0 --depth 1 https://github.com/categori-se/ai-studio-core.git studio-core
git clone --branch v0.5.1 --depth 1 https://github.com/categori-se/ai-studio-examples.git studio-examples

cd studio-core
npm install --no-save --package-lock=false ../studio-contracts
npm test

cd ../studio-examples
npm install --no-save --package-lock=false ../studio-contracts ../studio-core
npm test
node local-demo/demo.mjs
node ../studio-core/bin/studio.js inspect portfolio/workspace.yaml
node portfolio/no-content-telemetry.mjs
python3 -m http.server 8000 --directory docs
```

These commands deliberately use immutable release tags rather than mutable `main` branches. Each public repository also runs `npm run check:public-tree` before dependency installation; the check rejects unexpected files, generated directories, symlinks, non-text payloads, known credentials, private imports, and account-specific infrastructure material.

Expected local-demo output:

```text
Mock plan completed for local-demo.
```

The manifest inspection prints normalized JSON. The telemetry example prints attributes such as operation name, provider, model, run, and token counts; it must not print the synthetic private input, output, instructions, tool definition, or prompt variable used by the example.

## Low-idle-cost static deployment template

[`deployment/static-site.template.yaml`](./deployment/static-site.template.yaml) is a usable baseline for the public demo: a private, encrypted S3 origin; CloudFront Origin Access Control restricted to the exact distribution; HTTPS redirection; a narrow security-header policy; no logs, functions, database, NAT gateway, EC2 instance, or always-on application runtime; and one-day cleanup of incomplete multipart uploads. It uses CloudFront's default hostname and certificate so the public template needs no domain or account-specific identifier.

Deploy and upload the six reviewed files with your own AWS identity:

```bash
aws cloudformation deploy \
  --stack-name studio-examples-static \
  --template-file deployment/static-site.template.yaml

SITE_BUCKET=$(aws cloudformation describe-stacks \
  --stack-name studio-examples-static \
  --query 'Stacks[0].Outputs[?OutputKey==`SiteBucketName`].OutputValue' \
  --output text)
SITE_DISTRIBUTION=$(aws cloudformation describe-stacks \
  --stack-name studio-examples-static \
  --query 'Stacks[0].Outputs[?OutputKey==`SiteDistributionId`].OutputValue' \
  --output text)

aws s3 sync docs/ "s3://${SITE_BUCKET}/" --delete
aws cloudfront create-invalidation --distribution-id "${SITE_DISTRIBUTION}" --paths '/*'
```

S3 storage and requests plus CloudFront requests and transfer remain usage-billed; the template does not promise a fixed visitor cost. Its idle posture has no provisioned compute, public IPv4 address, NAT gateway, database, or log-ingestion stream. The bucket is intentionally unversioned so cleanup is explicit and does not leave hidden noncurrent versions. Empty it before deleting the stack:

```bash
aws s3 rm "s3://${SITE_BUCKET}/" --recursive
aws cloudformation delete-stack --stack-name studio-examples-static
aws cloudformation wait stack-delete-complete --stack-name studio-examples-static
```

The bucket uses `DeletionPolicy: Delete`, but CloudFormation cannot delete a non-empty bucket. `UpdateReplacePolicy: Retain` protects content during an unexpected replacement, so remove any replaced bucket manually after confirming it is obsolete. Treat this as a baseline: review identity, domain, certificate, monitoring, abuse controls, budgets, and deployment permissions for a real public service. Never place credentials, customer material, or private service configuration in this repository.

## Who benefits

- Developers who want to carry project context between local tools and a web workspace.
- Consultants and teams integrating AI workflows into client projects.
- Individuals comparing models and providers while retaining their own project history.
- Domain experts who need source-linked findings and an explicit human gate beside AI-assisted work.
- Research, engineering, policy, assurance, due-diligence, and advisory teams that need a reproducible handoff without adopting a large governance platform.
- Service planners and technical reviewers who want to adapt a complete synthetic reference rather than start from an empty schema.
- Maintainers implementing Studio Contracts in another language or tool.
- Developers evaluating a local, provider-neutral project manifest before adopting any service.

## Contributing

Good contributions are small enough to understand in one review and answer a real integration question. [Open an issue](https://github.com/categori-se/ai-studio-examples/issues) with the workflow you want to demonstrate and why an existing example is insufficient. Examples must be synthetic, deterministic, safe to copy, covered by tests, and consistent with [`CONTRIBUTING.md`](./CONTRIBUTING.md).

The examples are licensed under the Apache License, Version 2.0. No hosted subscription is required to copy, run, or adapt them.

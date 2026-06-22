# RakerOne user documentation — project instructions

## About this project

- Operator (end-user) documentation for **RakerOne**, built on [Mintlify](https://mintlify.com).
- Pages are MDX files with YAML frontmatter; navigation lives in `docs.json`.
- Run `mint dev` to preview, `mint broken-links` to check links.
- **Audience:** non-technical business/operations users ("operators"). Every page answers **"what you need to do to make it work,"** never "how it works" internally. No architecture, no code, no engineering names.

## Terminology (use the customer-facing UI term, never the engineering name)

| Use this (exact casing) | Never write |
|---|---|
| **Record type** / **record** | data object, object definition, row entity |
| **AI task** | agentic task, agent task |
| **Florent** | the bot, the agent |
| **Building Blocks** | Builder, Library, Definitions |
| **Project templates** vs **Document templates** | "Templates" alone (always disambiguate) |
| **Playbook** (blueprint) vs **Run** (one execution) | workflow, process, instance, job |
| **Project** | workspace, case, matter |
| **Organization** | tenant, account |
| **Identity provider** | IdP, WorkOS, SSO provider |

- Use exact in-app status names verbatim and bold them: runs are **Done** (not "Completed"); a sequence-blocked task is **Blocked** (shown as **Waiting** in a run); published building blocks show **Published** (document templates show **Active**); projects are **Open** / **Closed**.
- The four roles: **Admin**, **Manager**, **Builder**, **Member**. Roles and accounts are managed in the identity provider, not in RakerOne.

## Style preferences

- Second person, present tense, active voice ("You claim the task, then submit it").
- Sentence case for headings. One idea per sentence.
- Bold for UI elements: tabs, buttons, menu items, field labels, statuses (**New project**, the **Files** tab, **Pending approval**). Don't bold ordinary nouns.
- Task-oriented: lead with the goal, say what happens after the action.
- Be precise about Florent: "Florent drafted / suggested / is waiting for approval." Never imply Florent approved, finished, or decided. **Florent drafts; you decide.**
- Errors and limits: cause first, fix second, no jargon or raw error codes.

## Anti-repetition rule (most important)

Each concept is owned by exactly one page. If a page touches a concept another page owns, give a one-line mention and **link** — never re-explain it. Definitions live only in `get-started/concepts`; the permission matrix only in `admin/roles-and-permissions`; field review + citations only in `work/reviewing-ai-work`; the approval *model* in `playbooks/assignments-and-approvals` while the *act* of approving is in `work/reviewing-ai-work`.

## Screenshots

Mark every screenshot spot with an MDX comment in exactly this format:

```mdx
{/* TODO: Screenshot — <specific thing to show> */}
```

Never use HTML comments (`<!-- ... -->`) — they break the MDX build. A human fills these in with real images later (wrap finished images in `<Frame>`).

## Components

`<Steps>`/`<Step>` for procedures · `<Note>`/`<Tip>`/`<Warning>`/`<Info>` for asides · `<AccordionGroup>`/`<Accordion>` for reference detail and FAQs · `<Tabs>`/`<Tab>` for parallel variants · `<CardGroup>`/`<Card>` for "where to go next" grids. Keep nesting shallow; don't invent components.

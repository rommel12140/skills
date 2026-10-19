# Interface code structure and component reuse

Interface code is part of the design.
A page that renders well from one 1,500-line file cannot be refined, reviewed or reused without breaking something nearby.
These rules apply whenever a Build or Refine adds, extracts or moves interface code.
They are framework-neutral and hold for a Vite and React app, a Next.js app and a plain HTML and CSS site.

## Follow the project's structure first

When the project already has a clear, consistent folder structure, follow it and use its names.
Apply the default layout below only to a new project, or to a part of a project that has no structure yet.
Do not reorganize an existing codebase as a side effect of a design task.
If the existing structure is causing a real problem, name it as a finding and propose the move separately.

## Reuse before you write

1. Before writing a new component, search the project's shared `ui/` and `features/` folders, or their local equivalents, for one that does the same job.
2. Open the project's component showcase page, if it has one, and compare what is there with what you need.
3. Search the page's own folder for a part that already renders the same thing.
4. When an existing component is close, extend it with a variant, a prop or a modifier class instead of making a near-duplicate.
5. Make a new component only when no existing one does the job, and say in the notes which ones you checked.

Two components that differ only in a colour, a size or one optional slot are one component with two variants.
A copied component with a small edit is a defect even when it renders correctly, because the next change lands in one copy and not the other.
For storage and schema decisions, the same rule applies to database tables and shared stores: see the sibling `data-model` skill.

## When to extract a component

- Extract a visual unit when it has one clear responsibility, or when it repeats in another view.
- Keep new or extracted files under about 300 lines.
  Split by responsibility before that limit, not by cutting a file in half.
- Keep each component's styles beside the component they describe.
- Preserve cascade order when moving styles, so a rule that used to win still wins.
- Do not extract a one-line wrapper that has no responsibility of its own.

## Default folder layout

One folder per screen, and every shared part filed by who uses it.

| Folder | Holds |
| :--- | :--- |
| `app/` | Entry points and the app shell |
| `pages/<page>/` | The screen, the parts only it uses, its CSS, its data requests and its preview |
| `features/<subject>/` | Product-aware parts used by two or more screens |
| `ui/` | Plain building blocks with no product data, each with its CSS beside it, plus the showcase page |
| `lib/` | Helpers that belong to no screen |
| `styles/` | Design tokens and the global base only |
| `assets/` | Images and icons that code imports |
| `public/` | Files served at their own web address |

A part moves up only when a second screen uses it: from its page folder to `features/`, and from `features/` to `ui/` once it carries no product data.
Do not file a part in `features/` or `ui/` in advance because it might be shared one day.
Never leave page parts loose in one flat folder.
A flat folder of 160 files hides which screen owns each part and makes reuse a guess.

Map the names to the stack instead of fighting it.
In Next.js the routing folder is `app/` or `pages/`, so keep each route's private parts in a folder beside its route file and keep `features/`, `ui/` and `lib/` outside the routing folder.
On a plain site, each page's HTML sits in its own folder with its CSS and scripts, and shared partials and styles follow the same `ui/` and `styles/` split.

## Prove that nothing moved

- Add every new shared component to the showcase page, with each variant and state it supports.
- When extracting existing UI, capture the page before and after at the widths and themes in [measure before and after](../SKILL.md#measure-before-and-after) and compare the rendered output.
  A refactor that changes pixels is a design change and needs the same review as one.
- Check every other screen that uses a component you edited, not only the one you were working on.

## Review findings

In Audit, report these as descriptive craft findings with a location and a fix:

- `STRUCT` for a file far over the size limit, page parts loose in a flat folder, or a shared part filed under one page.
- `REUSE` for a near-duplicate of an existing component, or a new component that an existing one with a variant would cover.

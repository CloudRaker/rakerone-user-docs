# Screenshot production plan — RakerOne operator docs

## Progress (live)

- **48 screenshots captured + wired** into 23 MDX files (real PNGs in `/images`, wrapped in `<Frame>`).
- **5 marked `[Non Automatable]`** in code (two conceptual diagrams; the docs-site landing card grid; two live-AI streaming states — "Florent is reading documents" / "Florent is working").
- **60 remaining** — most need more seeded data or are live-AI states (see "Remaining" below).

**Automation harness** (reusable, persists between runs): `…/scratchpad/cap.js` drives a local headless Chromium authenticated by the reused `dev.raker.one` Chrome session cookie (`cookies.json`), saving real PNGs straight into `/images`. The `rakerone-demo` MCP builds the mock data.

**Use-case seeded so far** — *Vendor Contract Review*:
- Record types **Contract** + **Vendor** (library + project-scoped).
- Project **ACME-1** with 5 CUAD legal PDFs + 8 records.
- Actions: **Extract contract terms** (published), **Summarize agreement** (draft).
- Playbooks: **Onboard a vendor** (5 task types — Form / File upload / AI task / Action / Form — with dependencies + approvals, active) and **Review a contract** (draft).
- A live run **VEND-001** (running; intake task claimed/in-progress).
- 1 API key.

**Remaining ~60, by what they still need:**
- **Live-AI states** (mostly `[Non Automatable]`): `reviewing-ai-work` (confidence/citations/drafts), `florent` chat, `task-types` drafts/reading, `run-a-playbook` #178 completed-run summary, `batch-runs` review grid.
- **Document templates** (.docx upload) → `document-templates` + a generate action.
- **Project template built** → `project-templates` cards/editor.
- **Threads/comments + Inbox** → `collaboration`.
- **Custom editable view** → `data` #3 (filter builder).
- **French toggle** → `language`.
- **Smaller staged states**: approval panel (`assignments` #70), task setup sheet (`build-a-playbook` #119), validation banner (#177), run-actions menu (`run-a-playbook` #162), caught-up empty state (`my-work` #75), record-type options editor.

---

Generated from a parallel pass over all 31 MDX files. **116 screenshot TODOs** — auto: **77**, partial (stage a state): **31**, non-automatable: **8**.

Legend — `auto` = reachable by navigation + seeded data · `partial` = needs a specific staged state · `non` = `[Non Automatable]`, left in code for a human.

Use case seeded: **Vendor Contract Review** (record types Contract + Vendor; project ACME-1 with CUAD legal PDFs + records; playbooks/actions/templates/runs to follow).


## `index.mdx`

1. **🟢 auto** — The full RakerOne app shell: left sidebar (Work/Projects/Building Blocks/Admin groups visible) with a project open in the main content area, showing the product's overall layout as a first-look hero shot. Capture the whole viewport including sidebar and an open project's detail view (files, records, runs, people).
   - area: App shell with sidebar and an open project detail page
   - route: /projects then click into a seeded project (e.g. Vendor onboarding or Contract review); best-guess project detail URL /projects/{id}
   - needs: At least one project must exist with content — seed the 'Vendor Contract Review' use case: a project holding CUAD legal PDF files and seeded Contract/Vendor records, plus at least one run so the project detail view is populated, not empty.

2. **🔴 non** — The landing page section showing the explore-by-area cards. Note: the doc prose lists four cards in the comment but the CardGroup actually renders five (Projects, Playbooks, Record types, Actions & documents, Administration). This is a docs-site screenshot of the rendered Mintlify/landing page card grid, not the RakerOne app UI itself.
   - area: Documentation landing page (index.mdx 'Explore by area' card grid), not the RakerOne app
   - route: The published docs site landing page root /, 'Explore by area' section; best-guess docs URL
   - needs: No app mock data needed — this renders from the MDX CardGroup on the docs site. Requires the docs site itself to be built/served so the cards render.
   - note: This targets the docs landing page card grid, not the live RakerOne app (dev.raker.one). The capture pipeline is for live-app screenshots, so this is out of scope for the app-driven capture method; mark non-automatable for the app browser flow.


## `get-started/introduction.mdx`

1. **🔴 non** — A simple labeled hierarchy/flow diagram illustrating the core data model: Organization at the top, branching into Building Blocks (project templates, playbooks, actions, record types, document templates) and Projects, with Projects leading to Runs, then Tasks, then Records. This is a conceptual diagram, not a literal app screen — no such diagram view exists in the product.
   - area: Conceptual diagram (no corresponding app screen)
   - route: N/A — illustrative diagram, must be authored/drawn rather than captured from the app
   - needs: None from the app. Requires a hand-authored diagram asset since the relationships (Org → Building Blocks + Projects → Runs → Tasks → Records) are not rendered anywhere in the UI.
   - note: This is a conceptual relationship diagram that does not correspond to any live screen in the app, so it cannot be captured via DOM screenshot of the running product. It must be designed as an illustration. [Non Automatable]

2. **🟢 auto** — The full left sidebar expanded, showing all groups at once: the organization switcher header (org name + logo for 'Demo Environment'), the Work group (Home, Inbox, Chat), the Projects group with a few listed projects and the + create button, the Building Blocks group (Project templates, Playbooks, Actions, Record types, Document templates), the Admin group (Settings, Users, Roles, API keys), and the profile/footer at the bottom showing the user's name.
   - area: Left sidebar (global navigation), captured from any main page e.g. Home
   - route: /
   - needs: Logged in as an org admin (Baptiste Laget) with create-project permission so the + button and all groups (Building Blocks, Admin) are visible. A few seeded projects under the Projects group (e.g. vendor onboarding, contract review) so the project list is populated rather than empty.


## `get-started/concepts.mdx`

1. **🟢 auto** — A high-level structural view of the RakerOne app that visually conveys the hierarchy Organization → Building Blocks + Projects → Runs → Tasks → Records. Best real-app surrogate: the full left sidebar expanded showing all groups (Work: Home, Inbox, Chat; Projects; Building Blocks: Project templates, Playbooks, Actions, Record types, Document templates; Admin: Settings, Users, Roles, API keys; profile at bottom) with the organization/tenant name 'Demo Environment' visible in the sidebar header. This maps the conceptual diagram onto the actual navigation the doc describes.
   - area: Left sidebar (full height), Home page background; sidebar header shows tenant name
   - route: https://dev.raker.one/ (Home)
   - needs: None beyond default tenant 'Demo Environment'. The Building Blocks group should contain the planned record types (Contract, Vendor), playbooks, and actions so the groups look populated, but the sidebar group labels themselves render regardless.

2. **🟡 partial** — An open playbook run inside a project, focused on the task rail / task list, showing several tasks of differing types (Form, File upload, Document, Action, AI task) each with its task-type chip/icon and a colored status badge (e.g. Available, Running, Completed). The spread of task types and statuses is the point — the prose lists five task types and notes each kind of work has its own status badge.
   - area: Project run workspace — task rail (left/side list of tasks) within an active run; run number like PT-001 visible in header
   - route: https://dev.raker.one/projects → open a project (e.g. Contract Review) → open a run (best-guess: /projects/{id}/runs/{runId})
   - needs: A project with a started playbook run whose tasks cover multiple task types (Form, File upload, Document, Action, AI task) and are in a mix of statuses (at least one Available/Running and one Completed) so both the type chips and the status-badge spread are visible. Seed the playbook with these task types and advance the run partway.
   - note: The run workspace and task rail are static UI, but capturing a meaningful 'spread' of task-type chips AND multiple distinct status badges requires staging a run advanced to a mid-execution state with varied task types and statuses — a specific seeded state rather than a fresh empty run.


## `get-started/quickstart.mdx`

1. **🟢 auto** — The New project creation dialog/form on step 2 showing the Blank project type selected, the Name input field, the auto-generated project number hint beneath it, and the icon picker control. Frame the full form including the Create project button.
   - area: New project dialog (opened from the + button next to the Projects group in the sidebar)
   - route: Sidebar > Projects group > click the + (New project) button, choose Blank project, advance to step 2 (best-guess; modal overlay, no dedicated URL)
   - needs: None beyond a logged-in tenant; the Blank project flow is built in. Reach step 2 by selecting Blank project in step 1.

2. **🟢 auto** — A project's Playbooks tab showing the Playbooks table with at least one Published-status row exposing a Run button, plus the Ask Florent card below/beside it with its text input and the Create plan button.
   - area: Project detail > Playbooks tab
   - route: /projects > open a project (e.g. Contract Review) > Playbooks tab (best-guess project sub-route)
   - needs: A project with at least one Published playbook so a Run button renders; the Ask Florent card is part of the page. Seed a vendor/contract-review project with a published playbook.

3. **🟡 partial** — The full run workspace three-column layout: left task rail with Open, Blocked (labeled Waiting), and Done groups populated; the Timeline stream in the center; and one task opened in the right column.
   - area: Run workspace (after starting a playbook run)
   - route: Project > Playbooks > Run a published playbook > lands in run workspace (best-guess run URL)
   - needs: An active run that has tasks distributed across Open, Blocked/Waiting, and Done states, with one task selected/open on the right. Seed a run partway through so all three rail groups are non-empty.
   - note: Needs a run staged with tasks across Open/Waiting/Done and one task open. The state is stageable but must be deliberately seeded to show all three groups.

4. **🟡 partial** — The Pending approval / drafts-to-review panel showing a drafted record with its fields, a citation chip on a value, the fields-need-verification note, and the Approve values (or Approve documents) and Reject buttons.
   - area: Run workspace right column, on a task in Pending approval state
   - route: Run workspace > open the task marked Pending approval (best-guess run URL)
   - needs: A task that has reached Pending approval with Florent-produced drafts containing fields, at least one citation chip, and the verification note. Must seed a run where a Document/AI task has completed extraction and is awaiting approval.
   - note: Requires a specific staged state (task in Pending approval with drafts and citations) that can be seeded, but the drafts must already exist — not just navigation.

5. **🟡 partial** — The Run summary panel in the right column of a finished run, showing the Everything's done. message and the Records created count.
   - area: Run workspace right column, after the run is complete
   - route: Run workspace of a completed run (best-guess run URL)
   - needs: A run that has been fully completed (all tasks Done, records approved) so the Run summary renders with a non-zero records-created count. Seed a finished run.
   - note: Needs a fully completed run staged so the summary panel appears with the records count. Stageable but requires the run to be driven to completion first.


## `projects/overview.mdx`

1. **🟢 auto** — The full project detail header at the top of an open project: the project icon, the breadcrumb reading Projects > the project number (e.g. PRJ-1), the project name, the green Open status badge, and the "..." menu on the right. Open the "..." menu so the Close project item is visible. Include the row of tabs directly below the header (Files, Overview, Record types, Playbooks, Playbook runs, Project actions, Settings), with Files selected as the default tab.
   - area: Project detail page header + tab bar (Projects group in sidebar)
   - route: From the sidebar Projects group, open a seeded project such as the vendor onboarding or contract review project; best-guess /projects/{id}
   - needs: An Open project with a name, icon, and auto-assigned number (e.g. a Vendor Contract Review project). Project must be in Open status to show the green badge and the Close project menu item.

2. **🟢 auto** — The project Overview tab showing its four summary cards populated with data: Happening now (active/in-flight runs), My tasks (the viewer's assigned tasks), Project actions (recent ad hoc actions run over the project), and History (finished work). Each card should contain real seeded entries rather than empty states.
   - area: Project detail page, Overview tab
   - route: Open a seeded project, then click the Overview tab; best-guess /projects/{id} then select Overview tab
   - needs: A project seeded with: at least one in-progress playbook run (for Happening now), at least one task assigned to Baptiste Laget (for My tasks), at least one completed project action (for Project actions), and some completed runs/tasks (for History). Without this data the cards render empty states.


## `projects/create-a-project.mdx`

1. **🟢 auto** — The first step of the New project flow: the starting-point card grid. Show the "Blank project" card (with its subtitle "Just a name, an icon, and the people who can see it.") next to one or more project-template cards. Each template card should display its icon, name, optional description, and the numbering hint like "Projects get numbers like IMM-1."
   - area: New project page, step 1 (choose a starting point) card grid
   - route: Sidebar > Projects group > New project entry, or /projects then click New project button. Likely /projects/new (best-guess)
   - needs: At least one project template must exist (with icon, name, description, and a number prefix like IMM) so a template card renders alongside the Blank project card. Current user must have project-create permission so the grid shows instead of the no-access banner.

2. **🟢 auto** — The second step of the New project flow: the Details form plus Access section. Show the header label ("Blank project" or "From \"{template name}\""), the Project name field, the read-only Project number with its PRJ-1/IMM-1 hint, the Icon picker field, the Description field (placeholder "Optional notes for anyone working on this project."), and the Access section with Roles with access and People with access pickers. The Create project button (disabled until name + icon set) should be visible.
   - area: New project page, step 2 (fill in the details + access)
   - route: From the step-1 card grid, click "Blank project" (or a template card) to advance to the details form. /projects/new (best-guess)
   - needs: Reachable after choosing a starting point in step 1. To show the template header label and pre-filled access, a project template should exist; otherwise pick Blank project. Roles and people should exist in the org so the Access pickers have selectable options.

3. **🟢 auto** — An existing open project's Settings tab. Show the subtitle "Update this project's details and control who can access it.", the Project details section (Name, Icon, Description), the Access section (Roles with access / People with access pickers), the Close this project card (visible because the project is Open and user can close it), and the Summary reference panel listing Status, Number, Created from (A template / Started blank), Created date, and Updated date. The Save button should be visible.
   - area: Project detail page > Settings tab
   - route: Open an existing project from /projects, then click the Settings tab. /projects/{projectId}/settings (best-guess)
   - needs: At least one Open project must exist (ideally one created from a template so the Summary shows "A template" under Created from). Current user must have the manage permission so the editable fields and Close-this-project card render rather than the read-only view.


## `projects/data.mdx`

1. **🟢 auto** — The records table for a record type (e.g. Contract or Vendor), showing several seeded rows. Capture the table header with the record-type icon and name, the Edit fields button, and the New record button, then the view toolbar, then the table grid. The Title column must be pinned first; at least one column should render a colored Select/Multi-select badge, plus formatted date/currency cells and Yes/No booleans if present.
   - area: Project detail > Record types tab > a record type's records table
   - route: Home > open a project (e.g. Contract Review) > Record types tab > click the Contract record type (best-guess; project record-type table route to be discovered live)
   - needs: A project containing the Contract (or Vendor) record type with several seeded records, including a Select/Multi-select field populated with colored option values and at least one date or currency field.

2. **🟢 auto** — The view toolbar across the top of the records table: the View switcher on the left showing the active view name (All records), the Filter button, the Sort button, and the "…" options menu opened to reveal Default View, Fields, Create custom view, Copy link to view, and Delete view entries.
   - area: Project detail > Record types tab > records table view toolbar with options menu open
   - route: Open a project > Record types tab > a record type's records table > click the "…" options button to open the menu
   - needs: A record type's records table with the default All records view present (default seeded data is enough; a custom view optional to show Delete view enabled).

3. **🟢 auto** — The Filter builder popover opened from the Filter button, showing at least one condition row with a field picker, a condition picker (Is, Contains, etc.), and a value input, plus the Match dropdown (All conditions (AND) / Any condition (OR)) that appears when more than one condition is present. Add two conditions so the Match dropdown is visible.
   - area: Project detail > records table > Filter button popover
   - route: Open a record type's records table > click Filter > Add filter twice (configure two conditions to reveal the Match dropdown)
   - needs: A record type with filterable fields (Select/text/number/date — not currency/email/phone/URL/address). Two filter conditions added so the Match (All/Any) dropdown renders.

4. **🟢 auto** — The New record dialog opened from the New record button, showing field controls matched to types (text box, number, currency, Yes/No switch, date picker, Select dropdown, Multi-select tags) and required fields marked with a red asterisk (*). Include the Create record button.
   - area: Project detail > records table > New record dialog
   - route: Open a record type's records table > click New record (or Add the first record on an empty state)
   - needs: A record type (e.g. Contract) whose schema includes a mix of field types and at least one required field so the red asterisk renders. Dialog can be left empty/unsubmitted.

5. **🟢 auto** — A record opened in its full panel in view mode: header showing the record's Title value, fields grouped into sections in the Fields pane on the right, and the Source document pane on the left. For a hand-entered record the left pane reads "Select a field's cited source to preview it here."
   - area: Project detail > records table > record detail panel (view mode)
   - route: Open a record type's records table > click any row to open the record panel
   - needs: A seeded record (Contract or Vendor) with multiple populated fields grouped into sections. To show the empty left-pane prompt, open a record entered by hand (no AI citations); alternatively an AI-extracted record to show a source preview.


## `projects/files.mdx`

1. **🟢 auto** — The full Files workspace for a project: the left folder rail (All files / Inbox / folder tree), the file list on the right showing several seeded files with Name, Tags, and Updated columns, and the top toolbar containing the Search box and the Upload files button. This is the default landing view when opening a project.
   - area: Project detail > Files tab (default tab) for the Contract Review / Vendor onboarding project
   - route: /projects then open the Vendor Contract Review project; the Files tab is the default. Best-guess URL: /projects/{projectId} (discover live)
   - needs: A project with several uploaded CUAD legal PDF files, at least one folder in the folder tree, and a few tags applied so the rail and list are populated rather than empty.

2. **🔴 non** — The full-page 'Drop files to upload' drag-and-drop overlay shown while dragging files over the page, plus the upload progress panel showing per-file states (Waiting, a transfer percentage, Saving, Uploaded, and a Failed example).
   - area: Project Files tab during an active drag-and-drop / upload
   - route: /projects > open project > Files tab, then drag files onto the page. Best-guess URL: /projects/{projectId}
   - needs: Files staged for upload to trigger the overlay and a mid-flight progress panel with mixed per-file states (in-progress percentage plus at least one Failed). The overlay only appears during an active drag, and the progress states are transient.
   - note: The drag overlay and mid-upload progress states are transient timing-dependent UI that cannot be reliably frozen for a screenshot.

3. **🟢 auto** — The organization controls: the left folder rail showing All files, Inbox, and a nested folder tree, together with the 'Filter by tag' control above the list and the 'Show archived' switch in the toolbar.
   - area: Project Files tab, focused on the folder rail and filter toolbar
   - route: /projects > open project > Files tab. Best-guess URL: /projects/{projectId}
   - needs: A project with a nested folder tree (e.g. a folder with 'Add folder inside' subfolders), multiple tags applied across files so the Filter by tag control has options, and at least one archived file so the Show archived switch is meaningful.

4. **🟢 auto** — A single file row's '...' menu open showing Run action with this file, Download, Move, and Archive; and the bulk-action toolbar that appears when several files are selected via checkboxes showing 'N items selected' with Run action, Download, Move, Archive, Tag, and Clear selection.
   - area: Project Files tab, file list row menu and multi-select toolbar
   - route: /projects > open project > Files tab. Best-guess URL: /projects/{projectId}
   - needs: Several files in the list so multiple can be selected. Open one row's '...' menu and separately select 2+ files via checkboxes to surface the bulk toolbar (may need two captures or a state where both are visible).

5. **🟢 auto** — The File details panel for a generated file: the preview area, Properties (Type, Size, Added, Status), Tags, Location, and the 'Where this file came from' provenance line reading something like 'Generated by {action} from {records}' with the 'Open the run that created this file' link.
   - area: Project Files tab > File details side panel
   - route: /projects > open project > Files tab > click a generated file. Best-guess URL: /projects/{projectId}
   - needs: A generated file (produced by a run or action) that has provenance, so the 'Where this file came from' line and run link appear; ideally a previewable type (PDF or Word) and some Produced records / Action history populated.


## `projects/run-a-playbook.mdx`

1. **🟢 auto** — The full project Playbooks tab: the top Playbooks table listing the project's playbooks with Name/Status/Tasks columns and a Run play-icon button next to Published rows; the "From the library" section with "Use in this project" buttons; the "Ask Florent" card with its text box and Create plan button; and the "Recent work" table below listing past/current runs (run number, Playbook, Status, task progress, Started).
   - area: Project detail > Playbooks tab
   - route: Open a project from /projects, then click the Playbooks tab (best-guess /projects/{id}/playbooks)
   - needs: A project (e.g. Vendor Contract Review) containing at least one Published playbook, at least one library playbook available to add, Florent enabled, and at least one prior run so the Recent work table is non-empty.

2. **🟢 auto** — The complete run workspace three-column layout: left column with the task rail (Open/Waiting/Done sections, task-type icons, avatars, status badges) and the Files panel below it; middle column showing the Timeline stream with the comment composer pinned at the bottom; right column showing an opened task's detail. Run header with run number, playbook name, status badge visible at top.
   - area: Run workspace (active run)
   - route: From the project Playbooks tab, click Run on a Published playbook or click a run number in Recent work (best-guess /runs/{runNumber})
   - needs: An active (In progress) run with a mix of task statuses so the rail shows Open, Waiting, and Done groups; at least one timeline event/comment; at least one attached file so the Files panel is non-empty; one task selected/open on the right.

3. **🟡 partial** — The middle Timeline column showing a chronological stream: a human-posted comment, a Florent reply under the name "Florent" with the F avatar, and a run event such as "completed {task}" that includes an Open task button; the comment composer pinned at the bottom.
   - area: Run workspace > Timeline (middle column)
   - route: Open an active or completed run, focus the Timeline middle column (best-guess /runs/{runNumber})
   - needs: A run (Florent-enabled playbook) whose timeline contains a human comment, a Florent reply, and at least one task-completion event tied to a task (so the Open task button renders).
   - note: Requires a staged timeline containing a Florent reply and a completed-task event; these can be seeded as historical run data, but the specific event mix must be arranged.

4. **🟡 partial** — The run header with the Run actions three-dots overflow menu open, displaying "Pause run" and "Cancel run…" options; and the header state of a paused run showing the "Resume" button.
   - area: Run workspace > run header lifecycle controls
   - route: Open an active run, click the three-dots Run actions overflow in the header (best-guess /runs/{runNumber})
   - needs: An active run owned/managed by the current user (so lifecycle controls appear). The Resume button portion additionally needs a run in Paused state. May require two captures: one with the overflow menu open on an active run, one of a paused run's header.
   - note: The overflow menu is auto-reachable, but showing the Resume button requires staging a run in the Paused state; needs the user to have manage-run permission.

5. **🟡 partial** — The right column Run summary panel for a completed (Done) run: the "Everything's done." headline with "{N} tasks completed {date}", the All tasks list (each task clickable), and the Records created count.
   - area: Run workspace > Run summary (right column, completed run)
   - route: Open a run that has reached the Done state (best-guess /runs/{runNumber})
   - needs: A run in the Done final state, all tasks completed, that produced at least one record so the Records created count is non-zero.
   - note: Structural panel but requires a run staged in the Done state with completed tasks and created records; achievable by seeding a finished run.


## `projects/project-templates.mdx`

1. **🟢 auto** — The left sidebar with the Building Blocks group expanded, showing its five entries: Project templates, Playbooks, Actions, Record types, Document templates. Highlight/hover the Project templates entry so it reads as the focus.
   - area: Left sidebar, Building Blocks group
   - route: / (any page; sidebar is global — Building Blocks group is always present)
   - needs: None beyond a Builder/Admin role so the Building Blocks group and Project templates entry render. Logged-in session as Baptiste Laget already qualifies.

2. **🟢 auto** — The Project templates index page showing the grid of template cards — each card with icon, name, optional description, and the hint "Projects get numbers like {PREFIX}-1." At least one card must display the Archived badge.
   - area: Project templates index (Building Blocks > Project templates)
   - route: /project-templates (best-guess; click Project templates in the Building Blocks sidebar group)
   - needs: At least two project templates created (e.g. a Vendor onboarding template and a Contract review template), with one of them archived so the Archived badge appears.

3. **🟢 auto** — The New project template form/dialog with the Name and Icon fields, the Project number prefix field, a description field, the "Who can use this template" role/people picker, and the "Default access for new projects" role/people picker, plus the Create project template button.
   - area: New project template form (opened via New project template button on the index)
   - route: /project-templates/new (best-guess; from the Project templates index click New project template / Create your first project template)
   - needs: None required to open the empty form; optionally pre-fill Name (e.g. Vendor onboarding) and prefix (e.g. VEN) to make the prefix and access sections read clearly. Roles must exist to populate the access pickers.

4. **🟢 auto** — The template editor for an existing template showing the three tabs — Details, Playbooks, Record types — and the Archive button in the top-right. Details tab active with the locked prefix and Save changes button; ideally show the tab strip clearly.
   - area: Project template editor (opened by clicking a template on the index)
   - route: /project-templates/{id} (best-guess; click an existing template card on the index)
   - needs: An existing, non-archived project template (e.g. Vendor onboarding) so the editor opens with all three tabs and the Archive button visible; ideally with a playbook and a record type added so those tabs aren't empty.


## `record-types/overview.mdx`

1. **🟢 auto** — A live project's Record types tab showing the list of record types tracked by that project (e.g. Contract, Vendor), each row showing a field/Fields count. This is the live-project scope that actually holds records.
   - area: Inside a project > Record types tab
   - route: Sidebar > Projects > open a seeded project (e.g. vendor onboarding or contract review) > Record types tab. Best-guess URL like /projects/{id}/record-types
   - needs: A project (e.g. 'Vendor Contract Review') containing at least two record types added to it (Contract, Vendor), each with several fields so a non-zero Fields count shows.

2. **🟢 auto** — The left sidebar with the Building Blocks group expanded, showing its five items: Project templates, Playbooks, Actions, Record types, Document templates.
   - area: Left sidebar > Building Blocks group
   - route: Any page (e.g. Home /); ensure the Building Blocks sidebar group is expanded.
   - needs: None — the sidebar groups exist by default for a Builder/Admin user.

3. **🟢 auto** — The org-library Record types table under Building Blocks, listing several record types with Name, field/Fields count, and description columns. Doc says builders/admins create and edit them here.
   - area: Building Blocks > Record types (org library)
   - route: Sidebar > Building Blocks > Record types. Best-guess URL like /record-types
   - needs: At least two record types created in the org library (Contract and Vendor already exist per app facts; ideally each with several fields and a description so Fields counts and description column are populated).


## `record-types/build-a-record-type.mdx`

1. **🟢 auto** — The New record type dialog open, showing the subtitle 'Name your record type and pick an icon. You'll define its fields next.', the Icon picker, a filled Singular name field (e.g. 'Invoice'), and the optional Plural name field. Show the Create record type button.
   - area: New record type dialog, opened from the Record types library (Building Blocks > Record types) or a project's Record types tab
   - route: Best-guess: navigate to Building Blocks > Record types, then click 'New record type' (route likely /record-types)
   - needs: None beyond being a Builder/Admin. Type a sample Singular name like 'Invoice' into the field before capturing. No record type needs to pre-exist.

2. **🟢 auto** — The schema editor's Fields tab listing several field rows in order, each showing the field label, a type badge (e.g. Text, Currency), with at least one row showing the Title badge and another showing the Required badge. Show the Fields/Settings tabs, the '…' actions menu in the header, and the Add field button.
   - area: Schema editor, Fields tab, for an existing record type (e.g. Contract)
   - route: Best-guess: Building Blocks > Record types > open the Contract record type to land in the schema editor (Fields tab)
   - needs: A record type (e.g. Contract) with a few fields, one designated as Title and at least one marked Required, plus a Currency field to show a non-Text type badge. The seeded Contract record type should be configured this way.

3. **🟢 auto** — The schema editor's Settings tab showing Icon, Singular name and Plural name, the Identifier field, a filled Description, and the Title field dropdown for picking which field is the record title. Show the Save settings button.
   - area: Schema editor, Settings tab, for an existing record type (e.g. Contract)
   - route: Best-guess: Building Blocks > Record types > open Contract > Settings tab
   - needs: A record type (e.g. Contract) with names, a description filled in, and multiple fields so the Title field dropdown has options. Seed the description text.

4. **🟢 auto** — The Add field form with the Type dropdown expanded, revealing the list of field types (Text, Long text, Number, Currency, Boolean, Date, Date & time, Select, Multi-select, Email, Phone, URL, Address) with their descriptions. Also show the Label, Key, Help text, Required, Unique, and Default value controls behind/around it.
   - area: Add field form (modal/panel) opened from the schema editor Fields tab, with the Type dropdown open
   - route: Best-guess: Building Blocks > Record types > open a record type > Fields tab > click 'Add field' > click the Type dropdown
   - needs: An existing record type to open the Fields tab on. No data required beyond opening the form and the dropdown.

5. **🟢 auto** — The Options editor that appears when the field Type is Select or Multi-select, showing two or three options each with a label and a color badge (e.g. Gray/Green/Blue), reorder arrows, trash buttons, and the Add option button.
   - area: Add/Edit field form in the schema editor, with Type set to Select or Multi-select so the Options editor is visible
   - route: Best-guess: Building Blocks > Record types > open a record type > Fields tab > Add field > set Type to Select > Options editor appears
   - needs: Set the field Type to Select, then add two or three options with distinct labels and colors before capturing.

6. **🟢 auto** — Not applicable
   - area: Not applicable
   - route: Not applicable
   - needs: Not applicable


## `playbooks/overview.mdx`

1. **🟡 partial** — Two captures intended to sit side by side illustrating the definition-vs-run contrast. (1) The Playbooks library list view showing the table with Name, Status, Tasks, Uses, and Version columns and several published playbook definitions. (2) A live run workspace showing the three-column run layout (task list / center work area / context panel) for an in-progress run such as a contract review run. Capture each separately; the doc composes them side by side.
   - area: Building Blocks > Playbooks library (table) AND a project's run workspace (three-column run view)
   - route: /playbooks for the library list; for the run, open a project then a specific run, e.g. /projects/<id>/runs/<run-id> (best-guess; discover live)
   - needs: Several published playbook definitions seeded so the library table has multiple rows with non-zero Tasks/Uses/Version values (e.g. Vendor Contract Review, Vendor Onboarding). At least one started run in an in-progress state so the three-column run workspace renders with active tasks.
   - note: Library list is straightforwardly auto-capturable, but the run workspace requires staging a run in an in-progress state with active tasks, and it is a composite two-part shot.

2. **🟢 auto** — The left sidebar with the Building Blocks group expanded (Project templates, Playbooks, Actions, Record types, Document templates) and the Playbooks item in the active/highlighted state.
   - area: Left sidebar, Building Blocks navigation group
   - route: /playbooks (so Playbooks is the active highlighted item)
   - needs: None beyond default navigation; ensure the Building Blocks group is expanded.

3. **🟡 partial** — The playbook editor header bar showing the playbook name, a version chip reading v2, a Published status badge, and the Validate and Activate buttons.
   - area: Playbook editor (no-code authoring screen), top header bar
   - route: Open a playbook definition from /playbooks into its editor, e.g. /playbooks/<id>/edit (best-guess; discover live)
   - needs: A playbook definition that has been published at least twice so its version chip reads v2 and its status badge reads Published (e.g. the Vendor Contract Review playbook published, edited, and republished).
   - note: Requires staging a playbook in a specific Published, v2 state; the v2 chip and Published badge depend on prior publish history that must be seeded.

4. **🟡 partial** — (Note: this is the same single editor-header TODO as above; only one capture is needed.)
   - area: Playbook editor header bar
   - route: /playbooks/<id>/edit (best-guess)
   - needs: Same as above; do not double-capture.
   - note: Duplicate marker reference for the single v2/Published editor-header TODO.


## `playbooks/build-a-playbook.mdx`

1. **🟢 auto** — The 'New playbook' modal dialog with all fields filled: Name (e.g. 'Approval process'), Identifier auto-filled (e.g. 'approvalProcess'), Run number prefix (e.g. 'OPS'), and a short Description. Show the Create playbook button at the bottom.
   - area: Playbooks library (Building Blocks > Playbooks) — New playbook creation dialog overlay
   - route: /playbooks then click 'New playbook' (or 'Create your first playbook' on empty library) in top-right
   - needs: Builder or Admin role on the session. The dialog can be opened on an empty or populated Playbooks library; fields are typed in manually to show the filled state. No persisted data required.

2. **🟢 auto** — The playbook editor on the Tasks tab: the visual Task flow map at the top (showing steps with 'Starts with'/'After stage N' and 'Waits for' labels) and the Task details list below with one row per task — each showing position, colored type badge, task name, group label, assignment summary, an Approval chip, and 'Waits for' dependency chips.
   - area: Playbook editor — Tasks tab (Task flow + Task details areas)
   - route: /playbooks then open a published/draft playbook to enter the editor; ensure the Tasks tab is selected (best-guess editor route)
   - needs: A playbook with several tasks of differing types (Form, File upload, Document, Action, AI), at least one task with Requires approval on (to render the Approval chip), and dependencies wired between tasks (to render 'Waits for' chips and the flow map). Seed via the planned Vendor Contract Review playbooks.

3. **🟢 auto** — The Task setup slide-out sheet opened on the People section: the assignment strategy controls (specific person / role / run starter / project member / Florent) and the 'Requires approval' toggle switched ON, with the explanatory text 'When enabled, this task parks for review before its output is committed'. Show the Save task / Delete task buttons.
   - area: Playbook editor — Tasks tab — Task setup sheet (People accordion/section)
   - route: /playbooks > open a playbook editor > Tasks tab > click a task row (or its edit pencil) to open the sheet, then scroll to/expand the People section
   - needs: A playbook containing at least one task. Open that task's setup sheet and turn Requires approval on. Using a Document/Action/AI task that writes records would show approval forced on naturally.

4. **🟢 auto** — The playbook editor Settings tab showing the Numbering card (Prefix e.g. 'PT', Pattern, Date format, Separator, and the live preview text 'Runs will be numbered PT-001, PT-002, …') alongside the Florent card with its switches (Enable Florent, Enable Florent chat, and the three auto-run switches: Run actions automatically, Run document tasks automatically, Run AI tasks automatically).
   - area: Playbook editor — Settings tab (Numbering card + Florent card)
   - route: /playbooks > open a playbook editor > Settings tab (best-guess editor route)
   - needs: An existing playbook. Set a Prefix on the Numbering card so the live preview renders, and enable Florent so the three auto-run switches appear. No persisted runs needed.

5. **🟡 partial** — The validation alert banner titled 'N things to fix before this playbook can run', listing each issue attributed to its task by name (e.g. 'Collect documents: …'), shown after clicking Validate (or attempting Activate) on a playbook with problems.
   - area: Playbook editor — header Validate/Activate action, validation result banner
   - route: /playbooks > open a draft playbook editor > click Validate in the top-right header
   - needs: A draft playbook deliberately left with validation problems (e.g. a record-writing task without Requires approval, or a task missing required configuration) so clicking Validate surfaces the 'N things to fix' banner with named issues. Stage this incomplete state.
   - note: Needs a specific staged state: a draft playbook with deliberate validation errors so the failure banner renders. Once staged, clicking Validate reliably shows the banner.


## `playbooks/task-types.mdx`

1. **🟢 auto** — The 'Add task' dropdown menu expanded in the no-code playbook builder, showing the full list of six selectable task types in order: Form, File upload, Document, Action, AI task, and Form fill. Capture the open menu with all six entries visible so readers can match the prose table to the actual builder UI.
   - area: Playbook builder (no-code editor) — the task list / canvas area with the 'Add task' menu open
   - route: Navigate to /playbooks, open (or create) a playbook to enter the builder, then click the 'Add task' button to open the type dropdown. Best-guess builder route: /playbooks/{id}/edit or /playbooks/{id}/build.
   - needs: At least one playbook must exist (e.g. a 'Vendor Contract Review' playbook) so the builder/editor can be opened. No tasks need to pre-exist; the menu itself is the subject.

2. **🔴 non** — A Document task in a run while it is actively executing, showing the in-progress state 'Reading document' along with the message 'Florent is reading documents and preparing results for review.' Capture the task panel mid-run with the progress/loading indicator.
   - area: Run workspace — a Document task panel in its in-progress/running state
   - route: Open a project (/projects), open a run of a playbook that contains a Document task, and view the Document task while it is reading files. Best-guess run route discovered live, e.g. /projects/{id}/runs/{runId}.
   - needs: A project with seeded files (CUAD legal PDFs) and a playbook containing a Document task; a run must be started and the Document task must be actively reading documents at capture time.
   - note: Depends on live Florent AI streaming and transient in-progress timing ('Florent is reading documents…') that cannot be frozen reliably for a clean screenshot. [Non Automatable]

3. **🟡 partial** — The 'Drafts to review' panel for a record-writing Document task at Pending approval: a drafted record showing its extracted field values, a needs-verification note, source citations linking back to the document, and the 'Approve values' and 'Reject' action buttons.
   - area: Run workspace — the drafts/approval review panel for a Document task at 'Pending approval'
   - route: Open a project run containing a record-writing Document task that has finished and parked at Pending approval, then open the drafts review panel. Best-guess route discovered live, e.g. /projects/{id}/runs/{runId} with the Document task selected.
   - needs: A completed Document task that extracted records (e.g. Contract records from CUAD PDFs) and is staged at Pending approval with approval turned on, so drafts with citations and the Approve/Reject buttons are present. This state must be seeded/staged.
   - note: Needs a specific stage-able state: a Document task whose extraction has finished and is parked at Pending approval with drafts and citations. Once seeded to that state, the panel is static and capturable.

4. **🔴 non** — An AI task in a run while it is actively executing, showing the running state with the message 'Florent is working on this task' (the open-ended Florent progress indicator).
   - area: Run workspace — an AI task panel in its in-progress/running state
   - route: Open a project run containing an AI task and view the AI task panel while Florent is working on it. Best-guess run route discovered live, e.g. /projects/{id}/runs/{runId} with the AI task selected.
   - needs: A project and playbook containing an AI task; a run started so the AI task is actively executing ('Florent is working on this task') at capture time.
   - note: Depends on live Florent AI streaming and transient timing ('Florent is working on this task') that cannot be frozen reliably. [Non Automatable]


## `playbooks/triggers.mdx`

1. **🟢 auto** — The "Starting runs" card inside the playbook editor's Settings tab, showing the two on/off switches: "People can start this playbook" (on by default) and "Start from a webhook" (off by default, with its description text "lets other systems start this playbook — for example when an email arrives"). Frame the card so both toggles and their descriptions are legible.
   - area: Playbook editor > Settings tab > Starting runs card
   - route: /playbooks then open a playbook to enter the editor, then click the Settings tab (best-guess: /playbooks/{id} or an editor route with a Settings tab)
   - needs: A saved playbook (e.g. a Vendor Contract Review playbook) that can be opened in the editor. No special run state needed — toggles can be shown at their defaults (People on, Webhook off).

2. **🟢 auto** — The "Recent work" table/list on a project's Playbooks page, with at least one run row visible at the top representing a recently (auto-)started run. Show the run row(s) including columns/status so a viewer can see where automatic runs surface.
   - area: Project > Playbooks page > Recent work section
   - route: /projects then open a project (e.g. the Vendor Contract Review / vendor onboarding project), then its Playbooks tab/page (best-guess: /projects/{id} with a Playbooks tab showing Recent work)
   - needs: A project with a playbook that has at least one run in the Recent work list. Seed one or more runs so the table is non-empty; a top run can represent the auto-started run. No live webhook needed — any seeded run row demonstrates the surface.


## `playbooks/assignments-and-approvals.mdx`

1. **🟡 partial** — The task rail / list inside an open run, showing several tasks at once with distinct status badges (e.g. Waiting, Available, In progress, Pending approval) and the avatars of the person who claimed each task plus its approver. Should make the assignment + approval model concrete: who owns each task and who signs it off.
   - area: Run detail view — the task rail/sidebar listing the run's tasks, opened from a project's run
   - route: Open a project from /projects, then open a run with multiple tasks in mixed states (best-guess: /projects/{id}/runs/{runId})
   - needs: A playbook run with several seeded tasks across mixed statuses and assignments: at least one claimed/in-progress task (with claimer avatar), one Pending approval task (with a distinct approver), and one Waiting/Available task. Tasks must have assigned doers and approvers so avatars render.
   - note: Reachable by navigating into a run, but requires a run staged with multiple tasks in specific mixed statuses and with both claimer and approver avatars populated — a stageable but specific state.

2. **🟡 partial** — The Approval panel shown when an approver opens a task that is in Pending approval, including the panel heading, the reviewer instructions describing what to check, and the Approve and Reject action buttons.
   - area: Task detail panel — the Approval section on a task that is Pending approval, viewed as the resolved approver
   - route: Open a Pending approval task from a run or from /work/my-work, viewed as the approver (best-guess: task detail within a run)
   - needs: A task submitted by a doer or Florent that is now in Pending approval, with the current user (Baptiste Laget) resolved as its approver so the Approve/Reject buttons and approval instructions render. The task should have approval-required configuration (e.g. an AI/Florent task) and approver instructions text.
   - note: The Approve/Reject panel only renders when a task is staged in Pending approval with the current user as the resolved approver — a specific but seedable state.


## `actions/overview.mdx`

1. **🟢 auto** — The left sidebar with the Building Blocks group expanded showing its items (Project templates, Playbooks, Actions, Record types, Document templates), with the Actions item visually highlighted/active. Crop to the sidebar column only.
   - area: Left sidebar, Building Blocks group
   - route: /actions
   - needs: None beyond default app state. Navigate to /actions so the Actions item shows as the active/highlighted sidebar entry.

2. **🟡 partial** — The full Actions library page: top section 'Your actions' table with rows showing Name, Status badge, Output, and Used by columns — including at least one Published row and one Draft row — and below it the read-only 'Building blocks' list (Add a record, Update a record, Find records, Florent comment, Send notification, Wait) each with an info button.
   - area: Actions library main content area
   - route: /actions
   - needs: Seed at least two custom actions: one in Published status and one in Draft status, ideally with distinct Output values (e.g. a record type name, Inline fields, Generated documents, or Filled forms) and varying Used by counts (e.g. 'Not in use' and '1 playbook'). For the Vendor Contract Review use case: a Published 'Extract contract terms' action and a Draft 'Generate document' action.
   - note: Requires staged mock data — both a Published and a Draft custom action must exist to show the status badge variety described. Once seeded, the page is static and captures cleanly.

3. **🟢 auto** — The New action creation dialog/modal opened, showing the 'What should it do?' section with the three radio cards: Read documents ('AI reads files and fills in fields your team review.'), Generate documents ('Fill a Word template with record data to create PDF or Word files.'), and Fill forms ('Fill a blank PDF or image form with record data to create finished documents.'), plus the Name field below.
   - area: New action dialog (modal over Actions library)
   - route: /actions then click New action (top-right)
   - needs: Logged-in user must have builder or admin role so the New action button is visible. No other mock data needed — just open the dialog.


## `actions/extract-data.mdx`

1. **🟢 auto** — The 'New action' dialog open over the Actions library, showing the 'What should it do?' section with its radio/choice cards (one being 'Read documents' described as 'AI reads files and fills in fields your team review'), with the 'Read documents' card selected/highlighted. Name and Description fields and the 'Create action' button should be visible.
   - area: Actions library (Building Blocks > Actions) with the 'New action' creation dialog overlay open
   - route: /actions then click 'New action' button
   - needs: At least the Actions library reachable; no pre-existing action needed. Just open the New action dialog and click the 'Read documents' choice card to select it.

2. **🟢 auto** — The top header bar of the extract action editor: action name on the left, a 'Draft' badge, the list of activation blockers (e.g. 'Add extraction instructions before activating.', 'Pick a record type for the output.', 'Add at least one output field.'), and the Save (disabled when no unsaved changes) and Activate buttons on the right.
   - area: Extract action editor (Read documents action), header region
   - route: /actions then open a newly created draft Read documents action (best-guess /actions/{actionId})
   - needs: A freshly created Draft 'Read documents' action with no instructions, no record type, and no output fields yet — so the activation blockers are all listed and Activate is disabled.

3. **🟢 auto** — The 'Output' setup panel showing the Record type / Inline fields toggle (with 'Record type' selected) and the 'Pick a record type' dropdown with a record type chosen — each option showing name, field count, and description. The extracted fields (the record type's fields) should be visible below.
   - area: Extract action editor, left 'Output' panel
   - route: /actions then open the draft Read documents action and focus the Output panel
   - needs: A Draft Read documents action plus at least one existing record type (Contract or Vendor already exist). Set the Output toggle to 'Record type' and pick one (e.g. Contract) so its fields render.

4. **🟢 auto** — The 'How it runs' panel with the Instructions textarea (with sample text like 'Extract the title, date, and key details from each document.'), the Mode dropdown opened to reveal its three options ('Extract from each file', 'Extract one combined result', 'Extract table rows from documents'), and the Model preset selector (with Provider/Model fields below).
   - area: Extract action editor, 'How it runs' panel
   - route: /actions then open the draft Read documents action and open the Mode dropdown in the How it runs panel
   - needs: A Draft Read documents action with some instruction text typed in. Open the Mode dropdown so all three options are visible at capture time.

5. **🟡 partial** — The right-side 'Test bench' after a completed 'Run test': a results table with one row per field showing the Field column, the extracted Value, and a Score (confidence) per value. Sample files shown as added; ideally an amber warnings banner is not required but the populated results table is the focus.
   - area: Extract action editor, right 'Test bench' panel, post-run results state
   - route: /actions then open the draft Read documents action, add sample files, and click Run test
   - needs: A configured draft action (instructions + record type/inline fields) plus 1-3 sample PDF/DOCX files (CUAD legal PDFs). A test run must have completed so the Field/Value/Score table is populated — requires actual AI extraction to finish.
   - note: Requires staging sample files and running a real extraction; the populated results table is a stable post-run state but depends on a completed AI run, so it needs setup and waiting rather than just navigation.


## `actions/document-templates.mdx`

1. **🟢 auto** — The Document templates library table view with its column headers Name, Status, Kind, Binding, Version, Used by, Updated. Rows should include at least one template with a Draft status badge and one with an Active status badge, with the Used by column showing values like 'Not in use' and '2 actions'.
   - area: Building Blocks > Document templates library (table list)
   - route: /document-templates (best-guess; reach via sidebar Building Blocks > Document templates)
   - needs: At least two document templates seeded: one in Draft status and one in Active status. The Active one should be referenced by 1-2 generate actions so 'Used by' shows a count (e.g. '2 actions') while another shows 'Not in use'. Each needs a Kind (Word), a Binding (e.g. Contract record type), and a Version.

2. **🟢 auto** — The New template dialog open, showing the 'What kind of template?' choice with 'Word document' selected (description 'A .docx with placeholders, filled with record data to make PDF or Word files'), the file drop zone with a chosen .docx file (e.g. 'Engagement letter.docx'), and the prefilled Name field plus optional Description. The Create template button should be visible.
   - area: Building Blocks > Document templates > New template dialog
   - route: /document-templates then click 'New document template' (best-guess)
   - needs: A sample .docx file to upload (e.g. an engagement-letter / contract template). The dialog itself needs no seeded data, but a .docx must be selected to show the chosen-file and prefilled-Name state.

3. **🟢 auto** — The document template editor for a Word template: header with template name, Status badge (Draft), Version badge, and Save + Activate buttons; the Record type binding select bound to a record type (e.g. Contract); the 'What it expects' panel listing placeholders with their type (Value, Loop, Loop item), usage count, and field mapping; and the 'Checks' panel showing validation results (ideally 'Template looks good.' or a flagged Unknown variable).
   - area: Building Blocks > Document templates > template editor (bind/check section)
   - route: /document-templates/{id} (best-guess; open a template to enter the editor)
   - needs: A seeded Word document template (Draft) with a .docx containing recognizable placeholders (e.g. {{ clientName }}, {{ contract.value }}), bound to the Contract record type so 'What it expects' lists real variables and Checks shows results. To show 'Unknown variable', include one placeholder that does not map to a field.

4. **🟡 partial** — The 'Try it' panel of the template editor after clicking Render preview, showing an inline PDF preview rendered from sample data or a picked record. Visible controls: Sample data (JSON) input or 'Pick a record', the Render preview button, the inline PDF, and the 'Save as sample data' action. Optionally a 'Some placeholders were left blank.' notice if any are blank.
   - area: Building Blocks > Document templates > template editor (Try it / render preview)
   - route: /document-templates/{id} then scroll/open the 'Try it' panel and click 'Render preview' (best-guess)
   - needs: A bound template with valid placeholders, plus either saved Sample data (JSON) or a seeded Contract record to pick. Format must be PDF (not Word) so the preview renders inline rather than showing the Word 'Preview isn't available' message. A render must be triggered to produce the inline PDF.
   - note: Reachable by seeding a template + record and clicking Render preview, but it requires staging a successful PDF render (valid placeholders, PDF format, and triggering the render) to show the inline preview state.

5. **🟡 partial** — A run's Generated documents task panel in the Pending approval state, showing 'Documents to review (N)' with at least one document previewed inline (PDF), a render warnings banner such as 'Some placeholders were left blank.', the prompt 'Open each document to confirm it reads correctly, then approve...', and the 'Approve documents' button.
   - area: Project run > generate task panel (Generated documents, Pending approval)
   - route: Open a project run that includes a generate action task in Pending approval, e.g. /projects/{id}/runs/{runId} (best-guess)
   - needs: A playbook run that includes a generate action task requiring approval, executed so it produced one or more generated documents and parked at Pending approval (not yet approved). At least one generated PDF, and ideally a render that left a placeholder blank to surface the warnings banner. The task must be in the pre-approval state.
   - note: Reachable but needs a specific staged run state: a generate task that has produced documents and is sitting at Pending approval before anyone approves. Requires seeding the run and stopping at that gate.


## `actions/batch-runs.mdx`

1. **🟢 auto** — The batch-run launcher in its extract configuration: the Action dropdown showing a chosen published extract action (e.g. 'Extract contract terms'), the Files picker rendered as a checkbox table of the project's CUAD legal PDFs with several rows ticked, and the Run action button in its enabled state. Capture the full two-step launcher panel.
   - area: Batch run launcher (project action run), extract input mode with Files picker
   - route: Open a project (e.g. Contract Review) > Project actions tab > Run project action; OR from /actions open a published extract action > Run > pick project. Best-guess path under /projects/<id> (discover live).
   - needs: A project with several CUAD legal PDF files uploaded; a published extract action bound to the Contract record type (e.g. 'Extract contract terms'). Select that action in the dropdown and tick a few files so Run action becomes enabled.

2. **🟡 partial** — The header region of the batch review grid: the action name as heading with its run-status badge (e.g. 'Needs review'), the live summary line (e.g. '12 approved · 3 to review · 1 failed · 16 files'), the Export CSV link, and the Approve all clean button with its count. Frame just the header and the top of the grid.
   - area: Batch review grid, header bar
   - route: From the Project actions run-history table, click a completed/needs-review run to open its review grid. Best-guess path under /projects/<id> project actions (discover live).
   - needs: A finished or partially-finished extract run with a mix of approved / to-review / failed rows so the summary counts and a 'Needs review' badge render, and at least one clean row so Approve all clean shows a count.
   - note: Needs a specific run state (mixed approved/to-review/failed rows) to make the badge, summary counts and Approve all clean count meaningful; that state must be seeded but is stageable.

3. **🟡 partial** — The review grid with several rows selected via their row checkboxes, revealing the bulk action bar containing Approve selected, Retry failed, and Clear. Show the checked rows and the bulk bar together.
   - area: Batch review grid with row selection / bulk action bar
   - route: Open a run's review grid (Project actions > click a run), then tick a few row checkboxes. Best-guess path under /projects/<id>.
   - needs: A run whose grid has rows in selectable states — include at least one 'Needs review' row and one 'Failed' row so Approve selected and Retry failed are both relevant. Tick 2-3 row checkboxes to reveal the bulk bar.
   - note: The bulk bar only appears once rows are selected and is most meaningful with a needs-review + failed mix; that run state must be staged but selecting rows is deterministic.

4. **🟡 partial** — The full-screen per-row review dialog for an extract row: left column showing the source PDF scrolled to a cited region with the citation highlighted, right column listing one card per output field (label, value, confidence score, cited-sources count) with a field selected, and the Approve / Reject / Save changes action buttons.
   - area: Per-row review dialog (extract row)
   - route: In a run's review grid, click Review on a needs-review extract row (or click a field's citation chip). Best-guess path under /projects/<id>.
   - needs: An extract run with at least one row in 'Needs review' whose fields carry citations into a source CUAD PDF (so the left viewer can highlight a cited region and field cards show confidence + cited-sources counts).
   - note: Reachable by opening a needs-review row, but depends on a seeded row that still needs review with real citations into the source PDF; that reviewable state must be staged (not approved/rejected yet).

5. **🟡 partial** — The Project actions tab run-history table showing multiple past/live runs as rows, each with Action, Status, Progress (approved out of total), To review count, and Started columns — with statuses spanning at least Processing, Needs review, and Completed.
   - area: Project actions tab — run history table
   - route: Open a project > Project actions tab. Best-guess path under /projects/<id> (discover the tab live).
   - needs: Several seeded runs in the same project across different statuses (one Completed, one Needs review, and ideally one Processing) so the table shows the status variety described.
   - note: The table itself is static and reachable, but showing the described status variety — especially a live Processing run — requires staging multiple runs in distinct states; a Processing row is transient and may be hard to freeze.


## `work/my-work.mdx`

1. **🟢 auto** — The full My work / Home page at a wide viewport: the personal greeting header with the attention-summary line and current date on the right, the colored Work summary badge row (overdue / needs approval / in progress / available / done today), the My tasks card with its grouped sections and open count, and the Up next card pinned on the right side.
   - area: Home / My work page (sidebar > Work > Home)
   - route: /
   - needs: Logged-in user (Baptiste Laget) with several tasks assigned across the seeded Vendor Contract Review projects, spread so multiple buckets are non-zero (at least one overdue, one needs-approval, one in-progress, one available). Use a wide browser window so the Up next side card renders.

2. **🟢 auto** — Close/cropped view of the My tasks card showing the grouped headers (Overdue, Needs approval, In progress, Available) in urgency order, the card header total open count (e.g. '7 open'), and rows each with a status dot, task name, a type chip (Form, File upload, Document, Action, AI task, Form fill) and the quiet playbook / project / Due {date} line, with at least one overdue due date shown in red.
   - area: Home / My work page — My tasks card
   - route: /
   - needs: Tasks assigned to the user covering all six type chips (Form, File upload, Document, Action, AI task, Form fill) and at least one task in each of the Overdue, Needs approval, In progress, and Available buckets, with one overdue due date so the red date shows. Tasks belong to seeded playbooks/projects so the quiet metadata line is populated.

3. **🟢 auto** — The Up next card (wide-screen side panel) lifting the single most pressing task — ideally an overdue task — with its task name, type chip, metadata, and the 'Open task →' link.
   - area: Home / My work page — Up next side card
   - route: /
   - needs: At least one overdue task assigned to the user (so the card picks it as most pressing) and a wide browser window so the Up next card renders alongside the list.

4. **🟡 partial** — The calm caught-up empty state of My work: the briefcase icon with the heading 'You're all caught up' and the subtext 'Nothing needs your attention right now. New tasks land here as they're assigned to you.'
   - area: Home / My work page — empty state
   - route: /
   - needs: A user account with zero open tasks and nothing completed today (use a freshly seeded user with no assignments, or impersonate one), so the page renders the empty state rather than the task list.
   - note: Needs a specific empty state — a user with no open tasks and nothing done today — which must be staged rather than captured from the active demo user who has tasks.

5. **🟡 partial** — Two states of the same task inside the run: (1) Available state — the Claim task button with the greyed-out work surface (form fields or file dropzone) below it reading 'Claim this task to fill it out'; and (2) after claiming — status changed to In progress, the user's avatar on the task, and the work surface unlocked for editing.
   - area: Task detail inside a run (opened from My tasks / Up next)
   - route: / then click an Available task row (opens the run with the task; best-guess run route discovered live)
   - needs: An unclaimed group-offered (Available) task on a seeded playbook run — e.g. a Form or File upload task in the Vendor Contract Review flow — that the demo user is eligible to claim. Capture the Available state first, then perform the claim action to capture the In progress / avatar / unlocked state.
   - note: Two-state capture requiring an Available task then performing the claim action to reach the In progress state; both are seedable/stageable but the second frame depends on staging the claim.


## `work/completing-tasks.mdx`

1. **🟢 auto** — A Form task open inside its run, in the In progress state after being claimed. Show the Fields panel with editable inputs (some marked required), the helper line 'Complete the fields below to submit this task.', and the 'Submit task' button at the bottom. If feasible, include one field marked 'Suggested by AI' to match the surrounding prose.
   - area: Task detail panel within a run (Form task work surface), opened from My work or from a run's task list
   - route: Open a run containing a Form task and click the task to open it; best-guess via /projects > a project > a run, or from /work/my-work. Exact run URL must be discovered live.
   - needs: A playbook with a Form task, a run started from it, the Form task claimed by Baptiste Laget so status is In progress and fields are editable. Ideally one field pre-filled by Florent and marked 'Suggested by AI'.

2. **🟢 auto** — A File upload task open inside its run, In progress, showing one or more upload fields (e.g. labelled like 'Insurance card (front)') each with an 'Upload' button, at least one field showing 'Uploaded {date}' state, and the 'Complete task' button at the bottom.
   - area: Task detail panel within a run (File upload task work surface)
   - route: Open a run containing a File upload task and click the task; best-guess via /projects > a project > a run, or /work/my-work. Exact run URL discovered live.
   - needs: A playbook with a File upload task, a run started from it, the task claimed so it is In progress with per-field Upload buttons visible. Ideally one CUAD legal PDF already uploaded to a field so the 'Uploaded {date}' state shows.

3. **🟡 partial** — A task that has already been submitted, in read-only state. Show the 'Submitted by {name}' banner at the top (name = Baptiste Laget) and the fields locked/greyed and non-editable below it.
   - area: Task detail panel within a run (post-submit read-only view)
   - route: Open a run whose task has been submitted and click the task; best-guess via /projects > a project > a run, or /work/my-work. Exact run URL discovered live.
   - needs: A run with a Form (or File upload) task that has been claimed and submitted by Baptiste Laget, so the task is in a submitted/locked state showing the 'Submitted by' banner. The task should NOT yet be approved/completed if the read-only submitted banner differs from completed.
   - note: Requires a specific staged state: a task already submitted by the user so it is locked with the 'Submitted by {name}' banner. Achievable by seeding and submitting the task, but depends on staging that exact post-submit state.


## `work/reviewing-ai-work.mdx`

1. **🟡 partial** — A single AI-written field value on an open record, with the two chips beside it: the confidence chip (icon rated out of 5, colored green/amber/red) and the quote-mark source-count chip showing a citation count. The confidence chip's hover tooltip is open, revealing the numeric confidence score and the AI's reasoning text.
   - area: Record panel (slide-out) opened from a project's records table / Data tab — a field row on a Contract or Vendor record that Florent extracted.
   - route: /projects -> open the Vendor Contract Review project -> Data tab -> open a Contract record to slide out the record panel (best-guess; record panel route discovered live)
   - needs: A Contract record with at least one AI-extracted, grounded field value carrying a citation and a computed confidence score (4-5 / 3 / 1-2 range to show chip color). Citation must reference a seeded CUAD legal PDF.
   - note: The field/chip layout is static and reachable by seeding an AI-extracted value, but the confidence-score-and-reasoning tooltip is hover-only and must be held open over the chip while capturing — stage by triggering and holding hover on the confidence chip.

2. **🟢 auto** — The source viewer open on a cited PDF: the original file rendered inline scrolled to the cited page (Page N badge visible), the cited region highlighted on the page, the confidence chip repeated, and the 'Cited text' banner showing the exact quote beneath. A Download button should be visible.
   - area: Source viewer — fills the document pane in the record panel, or appears as a modal titled 'Source for {field}' when opened from a standalone chip.
   - route: /projects -> Vendor Contract Review -> Data tab -> open a Contract record -> click the confidence or source-count chip on an AI field to open the source viewer (best-guess)
   - needs: An AI field whose citation points to a seeded CUAD legal PDF with a recorded page number, highlighted region coordinates, and cited-text quote. Single-citation value opens the source directly.

3. **🟡 partial** — The source viewer in transcript mode: a Transcript pane showing speaker and timestamp lines instead of a PDF, scrolled to and highlighting the cited passage, with the header reading 'Transcript' plus the recording's duration.
   - area: Source viewer (Transcript variant), opened from a citation chip — inside the 'Audio and video sources' accordion context.
   - route: /projects -> Vendor Contract Review -> Data tab -> open a record whose AI field cites a transcribed recording -> click the citation chip (best-guess)
   - needs: An AI-extracted field whose citation references a transcribed audio/video recording (transcript with speaker + timestamp lines, a known duration, and a cited line). The procurement use case ships mostly PDFs, so a seeded transcript source must be added.
   - note: Viewer is static, but it requires staging a transcript-backed source (audio/video with transcript) which is not part of the default CUAD PDF mock data — that specific source state must be seeded first.

4. **🟢 auto** — A single field row in the record panel: field label, citation chip, and the 'Pending review' status badge next to the label, with the badge's menu open showing Approve / Reject / Dismiss. The item matching the current state (Dismiss, since value is Pending) may be greyed; if showing an Approved value instead, Approve would be greyed.
   - area: Record panel field row — status badge dropdown menu expanded.
   - route: /projects -> Vendor Contract Review -> Data tab -> open a Contract record -> click the 'Pending review' status badge on an AI field to open its menu (best-guess)
   - needs: A Contract/Vendor record with an AI-written field in 'Pending review' state (freshly landed, not yet approved/rejected) and the viewer logged in with review permission (Admin/Manager/Builder — Baptiste qualifies).

5. **🟢 auto** — The records table for an AI-written field, with the column header's down-arrow dropdown open showing the three bulk options: Approve this column, Reject this column, Dismiss this column.
   - area: Records table (project Data tab) — column header dropdown for an AI-written field column.
   - route: /projects -> Vendor Contract Review -> Data tab -> click the down-arrow on an AI-written column header to open its menu (best-guess)
   - needs: A records table with at least one AI-written field column populated across multiple records (so the column has AI values to bulk-review), viewed with review permission.


## `work/florent.mdx`

1. **🟢 auto** — The left sidebar Work section with the Chat group expanded into a collapsible group: a New chat item plus several recent conversation titles listed newest-first, with the current conversation highlighted. Crop to the sidebar Work group.
   - area: Left sidebar > Work section (Home, Inbox, Chat). Chat expanded as a group.
   - route: /chat (best-guess; reach via sidebar Chat item) — open Chat after at least one conversation exists
   - needs: At least 2-3 seeded Florent conversations must exist so Chat renders as a collapsible group (not a single item) and shows recent titles. One conversation open/highlighted.

2. **🟢 auto** — The Chat welcome screen showing the 'Ask Florent' eyebrow, a time-of-day greeting with the user's first name (Baptiste), the promise line 'Tell Florent what you need. Florent drafts. You decide what to approve.', the large composer with placeholder 'Describe a process, a project, or a question…', and the four suggestion chips (What needs my attention?, Draft a playbook, Set up a project, What data do we track?).
   - area: Chat welcome / new-chat landing screen (main content area).
   - route: /chat or /chat/new (best-guess); click Chat then New chat to reach the empty welcome state
   - needs: None beyond being signed in. Welcome screen renders on a fresh New chat. Greeting varies by time of day — acceptable.

3. **🔴 non** — An active conversation thread: a user message bubble on the right, a Florent text reply, an inline tool-call card, and the 'Florent is working…' spinner/indicator showing while Florent is mid-step.
   - area: Inside a Chat conversation (main thread area + composer).
   - route: /chat/{conversationId} (best-guess); send a message and capture while Florent streams
   - needs: A live in-flight reply: the 'Florent is working…' spinner only shows while Florent is actively working, which is transient AI streaming. The static parts (user bubble, reply, tool-call card) can be staged from a completed conversation, but the working indicator cannot be frozen reliably.
   - note: The 'Florent is working…' spinner depends on live AI streaming/transient timing that cannot be frozen reliably; [Non Automatable].

4. **🟢 auto** — The conversation header with its ⋯ (overflow) menu open, showing the Rename and Delete menu items.
   - area: Conversation header (top of an open Chat conversation), ⋯ menu dropdown.
   - route: /chat/{conversationId} (best-guess); open a conversation, click the ⋯ menu in the header
   - needs: At least one existing Florent conversation to open so the header and its ⋯ menu are available.

5. **🔴 non** — A Florent reply bubble that conversationally explains a permission limit, e.g. 'I can't create that — you'd need the … permission (or a teammate who has it).', shown after asking Florent to draft something the current role can't create.
   - area: Inside a Chat conversation (Florent reply text).
   - route: /chat/{conversationId} (best-guess); ask Florent to draft something the signed-in role lacks permission for
   - needs: Requires a user/role without the relevant create permission and a prompt that triggers the refusal; the exact conversational refusal wording is AI-generated and not deterministic.
   - note: Depends on live AI generating a permission-refusal reply and on a specific restricted-role state; wording is non-deterministic and cannot be reliably staged; [Non Automatable].


## `work/collaboration.mdx`

1. **🟢 auto** — A task detail panel (or record panel) showing the Comments thread: heading reading 'Comments' or "Comments on '[subject]'", at least one posted comment displayed above, and the reply composer at the bottom with the 'Reply to thread…' placeholder and the text-formatting toolbar / Post comment button.
   - area: Run workspace task detail panel (or record panel) — Comments thread section
   - route: /projects → open a project → open a run → click a task to open its detail panel → locate the Comments thread (best-guess; run/task URL discovered live)
   - needs: A playbook run with at least one task, and at least one comment already posted on that task's thread so the thread is not in the empty 'No comments yet.' state.

2. **🟢 auto** — The comment composer with the 'Mention teammate' picker open, triggered by typing @, listing matching teammate name suggestions for selection.
   - area: Comments thread composer — Mention teammate picker popover
   - route: /projects → open a run → open a task's Comments thread → click into the composer → type @ to open the Mention teammate picker
   - needs: Multiple users in the tenant so the picker shows teammate suggestions after typing @. A task with an open comment thread to type in.

3. **🟢 auto** — An open per-comment 'Comment actions' menu showing the Edit and Delete options, with a nearby comment displaying the '(edited)' marker.
   - area: Comments thread — individual comment row, Comment actions overflow menu
   - route: /projects → open a run → open a task's Comments thread → click the Comment actions (overflow) menu on one of your own comments
   - needs: At least two comments authored by the current user (Baptiste Laget), with one already edited so it shows the '(edited)' marker; the actions menu only appears on the user's own comments.

4. **🟢 auto** — The left sidebar Work group showing the Inbox item with an unread-count badge (a number; reads 99+ above 99).
   - area: Left sidebar — Work group, Inbox item
   - route: Any page (e.g. /) — sidebar is always visible; focus on the Inbox item
   - needs: At least one unread notification for the current user (e.g. an @mention or task assignment) so the count badge renders on the Inbox item.

5. **🟢 auto** — The Inbox overlay open from the sidebar showing the 'Search inbox…' box at top, notifications grouped under Unread and Read headings, a 'New' badge on an unread item, and the bottom All / Unread toggle with 'Mark all read'.
   - area: Inbox overlay (opened from sidebar Inbox item)
   - route: Sidebar → click Inbox to open the overlay
   - needs: Both unread and read notifications for the current user so both the Unread and Read groups render (with a New badge on an unread item) and Mark all read is enabled.


## `admin/organization-settings.mdx`

1. **🟢 auto** — The full Organization settings page in its default (unmodified) state: page heading "Organization settings" with subtext "Set the logo people see when they switch between organizations.", the square "Preview" avatar, the "Logo" section, the dashed "Choose logo" upload box reading "No file selected", and the disabled "Save logo" button.
   - area: Admin group > Settings (Organization settings page)
   - route: Click Settings under the Admin group in the sidebar; best-guess URL /settings
   - needs: None beyond being logged in as an admin (Baptiste Laget). The page is admin-only; non-admins see an access banner instead.

2. **🟡 partial** — The Organization settings page after a successful logo upload: the Preview avatar updated to show the newly chosen image, and the green "Logo saved." confirmation text displayed next to the now-enabled "Save logo" button.
   - area: Admin group > Settings (Organization settings page), post-save success state
   - route: Settings under Admin in sidebar; best-guess URL /settings
   - needs: A square logo image file (PNG/JPG/WebP/GIF/SVG under 2 MB) must be selected via the Choose logo dropzone, then Save logo clicked to trigger the green "Logo saved." confirmation.
   - note: Requires staging the success state: upload a valid logo file and click Save to surface the transient green "Logo saved." confirmation, which must be captured after the save completes.

3. **🟡 partial** — The organization switcher dropdown opened from the top of the sidebar: the dropdown labelled "Organizations" listing two or more organizations, each with its name and logo, including the current organization (Demo Environment).
   - area: Sidebar header > organization switcher dropdown (expanded)
   - route: Click the organization name and logo at the top of the sidebar to open the Organizations dropdown; no specific URL
   - needs: The signed-in account must belong to at least two organizations for the switcher to list multiple entries; otherwise the dropdown only shows the single current organization.
   - note: Opening the dropdown is a simple menu interaction (auto), but showing "two or more organizations" requires the account to belong to multiple orgs, which must be staged.


## `admin/members-and-invites.mdx`

1. **🟢 auto** — The Users directory page: heading "Users" with subtext "Everyone in your organization", the two-column table (Name | Email) populated with at least a couple of organization members (e.g. Baptiste Laget and one other), and the "Roles are managed in your identity provider." reminder line directly below the table.
   - area: Admin > Users page (read-only members directory)
   - route: /users (best-guess; click "Users" under the Admin group in the left sidebar)
   - needs: At least 2 users present in the org directory so the table renders rows (the demo tenant should already have the logged-in user; add one more seeded member if the table looks too sparse).

2. **🟡 partial** — Two states of the Users page: (1) the empty state showing "No users found" with the message "Invite and manage members in your identity provider."; and (2) the error state showing "We couldn't load your organization's members right now" with a Retry button.
   - area: Admin > Users page (empty state and load-error state)
   - route: /users (best-guess; click "Users" under the Admin group in the left sidebar)
   - needs: Empty state: a directory with zero members returned (hard to stage in the demo tenant which has the logged-in user — may need an org with no members or a mocked empty response). Error state: force the members fetch to fail (e.g. block/intercept the network request) so the error + Retry button render.
   - note: Both are specific non-default states: the empty state requires a zero-member directory and the error state requires forcing the members request to fail; neither appears under normal conditions but each can be staged via seeded/mocked data or a blocked network request.


## `admin/roles-and-permissions.mdx`

1. **🟢 auto** — The Roles page main content: the read-only table listing all four roles (Admin, Manager, Builder, Member) in the Role column with their capability sentences/descriptions in the Capabilities column. Capture the full table so all four rows are visible.
   - area: Admin group > Roles page (read-only roles reference table)
   - route: /roles (best-guess; reach via sidebar Admin > Roles)
   - needs: None beyond the default four built-in roles. Must be signed in as an admin (Baptiste Laget / Demo Environment) since the page is admin-only; a non-admin sees the 'You don't have access to this page' message instead.

2. **🟢 auto** — A single project's Access list panel/section, showing the two groupings: 'Roles with access' (roles granted access to the project) and 'People with access' (individuals added to the project). Illustrates scoped per-project access.
   - area: Projects > a specific project > Access / settings (project access list with Roles and People sections)
   - route: /projects > open a project > Access tab or settings (best-guess; exact path discovered live)
   - needs: A seeded project (e.g. a Vendor Contract Review / vendor onboarding project) that has at least one role granted access and at least one individual person added, so both the 'Roles with access' and 'People with access' lists show entries.


## `admin/api-keys.mdx`

1. **🟢 auto** — The Admin > API keys list page showing the full table with column headers Name, Permissions, Last used, and Created; at least one populated row with a permission badge (e.g. Can impersonate or No permissions) and a Revoke button at the end of the row; the Create API key button in the top-right of the page header.
   - area: Admin group > API keys page
   - route: Sidebar: Admin > API keys (best-guess URL /api-keys or /admin/api-keys; discover live)
   - needs: At least 2 seeded API keys with descriptive names (e.g. "Data import service", "Webhook trigger"), varied permissions so badges differ (one with Can impersonate, one with No permissions), and one with a Last used timestamp and another showing Never.

2. **🟢 auto** — The Create API key dialog (first screen) open over the page, showing the Name text field, the Permissions checkbox grid of capabilities, and the Can impersonate users toggle switch (left off), plus the Create key button.
   - area: Admin > API keys page > Create API key dialog (step 1)
   - route: Sidebar: Admin > API keys, then click Create API key (top-right)
   - needs: None beyond reaching the API keys page; the dialog opens empty. Optionally type a sample name like "Data import service" to show the filled field.

3. **🟢 auto** — The second screen of the create flow titled Copy your API key, showing the generated full key value, the Copy button (pre-click state, not yet Copied), the warning banner that the key won't be viewable again, and the Done button.
   - area: Admin > API keys page > Create API key dialog (step 2, post-creation)
   - route: Sidebar: Admin > API keys > Create API key > fill Name + permissions > click Create key to reach the second screen
   - needs: Complete the create flow with a sample name (e.g. "Data import service") and submit to generate a real one-time key value. Note: this consumes a real key creation; the screen only appears once per key.

4. **🟢 auto** — The Revoke this API key? confirmation dialog showing the warning that any system using the key will immediately lose access, with the Revoke key (destructive) and Cancel buttons.
   - area: Admin > API keys page > Revoke confirmation dialog
   - route: Sidebar: Admin > API keys, then click Revoke on a key's row
   - needs: At least one existing API key in the table to click Revoke on. Capture the dialog before confirming so the key is not actually revoked (or revoke a throwaway key).


## `admin/language.mdx`

1. **🟢 auto** — The profile menu opened from the sidebar footer. The menu should display the user's name (Baptiste Laget) and email at the top, then a Language section marked with a globe icon containing two selectable options — English and Français (Canada) — with one selected, and a Log out item below.
   - area: Profile menu overlay anchored to the Profile button in the sidebar footer (bottom of the left sidebar)
   - route: Home (/), then click the Profile button (showing the user name) at the bottom of the left sidebar to open the menu
   - needs: None beyond the logged-in user (Baptiste Laget, Demo Environment). The language options are built-in.

2. **🟡 partial** — The app with language set to Français (Canada): a translated signed-in page (e.g. My work / Home or a project) showing French interface text (sidebar, navigation, labels in French), contrasted with an Admin page (e.g. Organization settings, Users, Roles, or API keys) that remains in English despite the French setting.
   - area: Two views — a translated product page (Home/My work or a project) and an Admin settings page — both with the French language toggle active
   - route: Open the Profile menu, select Français (Canada); then capture a translated page at / (or My work), then navigate to /admin/organization-settings (Settings) to show the still-English Admin page
   - needs: Language preference toggled to Français (Canada) for the session. A project may need to exist if capturing a project page as the translated example, but Home/My work suffices with no extra data.
   - note: Requires staging a specific state — switching the UI language to Français (Canada) via the profile menu before capturing — and ideally a side-by-side/sequential capture of a translated page and an English Admin page.

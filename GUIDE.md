# Maker Hub guide

What every screen, colour and tag means. Look up the word you see on the screen.

## Colours

Used everywhere in Maker Hub.

| Colour | Means |
|---|---|
| Red | Broken now. Something does not work, fix it first. |
| Amber | Worth a look. Not broken, but worth checking, for example a missing description or a flow that is switched off. |
| Green | All good. |
| Red dashed line | The path of a broken part. Fix the start of the path. |

## Top bar

Same on every page.

- Back: returns to the screen before. Esc closes pop-ups.
- Print: Save as PDF. Opens the print window with everything expanded.
- Star: Export for AI. See [Export for AI](#export-for-ai).
- Pencil: My notes. See [My notes](#my-notes).
- Refresh: reads the latest data again.
- `?`: How it works for the page you are on.
- Environment name: the environment you are looking at.

## Home

A summary of everything that happened in the environment.

- Timeline: one bubble per event.
  - Blue: Deployments. A solution was imported or changed.
  - Red: Failed. Cloud flows that failed that day. The number is the failed runs.
  - Orange: Switched off. A flow was turned off.
  - Purple: Access. Someone got a role or group. Needs auditing.
- Today, Yesterday, Week, 4 weeks: the time range.
- Only our work: hides Microsoft's own solutions.
- Type buttons under the timeline: click one to show only that type. Show all resets.
- Our work, Busiest projects, Check-up: summary cards. Click to open the detail.

## Check-up

Your environment checked against 21 guidelines, live, every time you open the page.

- The ring: how many guidelines are met.
- Fix now: red guidelines.
- Worth a look: amber guidelines.
- Passed: green guidelines.
- Details: why it matters, how to fix it and the items behind it.
- Include default publisher: also checks items made with the default publisher.
- To-do status on each row: On our list, Planned, Done, Not for us. You can add people, a date and a comment. Saved in your browser.
- To-do as PDF, Copy as tasks, Email: share the list.

The guidelines:

| Area | Guideline |
|---|---|
| Solutions | All our tables are in a solution |
| Solutions | Each project uses one prefix |
| Solutions | Test and Live hold managed solutions only |
| Flows | No flows failing in the last 7 days |
| Flows | No flows owned by people who have left |
| Flows | Flows owned by a service account |
| Flows | Flows use connection references |
| Flows | Environment variables have a value |
| Flows | Connection references are connected |
| Security | Only a few System Administrators (limit 5) |
| Security | Broad roles kept small (limit 10) |
| Security | Access to our apps given through groups |
| Documentation | Our tables have a description |
| Documentation | Our flows have a description |
| Clean-up | No flows switched off for a long time (90 days) |
| Clean-up | Nothing untouched for 12 months or more |
| Connectors | Only approved connectors used |
| Connectors | No direct HTTP calls |
| Connectors | Custom connectors are described |
| Environment | Auditing is switched on |
| Environment | Environment type is set for the Hub |

Limits can be changed with the `lt_HubLimits` setting, see the README.

## Workbench

Your solutions while you build them.

### All solutions

| Column or tag | Means |
|---|---|
| Dot | Red, amber or green health of the solution. |
| Failing flows | Flows that failed in the last 28 days, with the number of failed runs. |
| 1 off | One flow in the solution is switched off. |
| env var | An environment variable has no value. |
| leaver-owned | A flow or process is owned by someone who has left. It stops when their account is switched off. |
| connection | A connection reference has no connection. Flows that use it can't run. |
| Documented | The share of tables, columns, flows, apps and other items that have a description. Green 80% or more, amber 40 to 79%, red under 40%. |
| 8 need attention | Click to show only solutions with red or amber. |
| Owned by leavers | Flows whose owner has left the company. |

### One solution

Tabs inside a solution:

- Overview: what it is, a description you can copy, what to do next, health today and what it depends on.
- Map: who can use it, the app, tables, automation and connections. Same as Big picture.
- Tables and columns: names to copy, lookups and what happens when the other row is deleted.
  - Deleted too: the rows are deleted as well. Check before deleting.
  - Link cleared: the lookup is emptied.
  - Delete blocked: the other row can't be deleted.
  - Only risks: shows only the cascades.
  - No description: the item has no description yet.
- Shortcuts: logical names, filters for Power Automate, expand queries, Web API URLs and FetchXML, ready to copy.
- Flows and runs: one strip per flow for the last 3 weeks. Green ran fine (darker is more runs), red failed, grey no runs. Click a red day to see the failed run.
- Security: what each role can do on each table. User, BU, Parent, Org show how far the right reaches. Delete is in red.
- Depends on: what the solution needs from other solutions or Microsoft tables.
- Settings: environment variables and connection references.
- History: when it was imported, exported or upgraded, and if it worked.

## Big picture

How a solution is built. Four tabs, one for each team:

- Power Platform: a map of roles, apps, tables, automation and connections, with a colour for each part. Click a box to open it. Click a flow to see its steps.
- Power BI: tables with their meaning, how they join, choice codes and how to connect.
- Data engineering: data connections, dataflows, virtual tables, change tracking and keys.
- Master data: lookup lists, who uses them and possible duplicates.

Files this visit: drop a `.pbit`, `.pbix`, `.sql` or `.xlsx`, or paste SQL or Power Query. It joins the map as a dotted line. Click it to see the query steps and code. Column not in Dataverse any more means the query asks for a column that no longer exists.

Support mode: shows what is broken and what changed recently first.

### Flow view

- Read-only. Nothing can be changed.
- Each step is drawn like the Power Automate designer.
- Search steps by name, table or connector. Switch between Diagram and Outline.
- Flags on a step:
  - Outside call: data leaves your tenant through HTTP.
  - Key in the URL: a key or password is typed into the flow.
  - Runs after failed: the next step also runs when this one fails.
  - No connection: the connection reference has no connection, the flow stops here.

## Launch pad

Check a solution file before it is imported.

- Drop a solution `.zip`. It is read in your browser only. Nothing is uploaded, imported or saved.
- Score: passed counts 1, worth a look counts a half, fix counts 0. Score is the total divided by the number of checks, times 100.
- 5 to fix, 8 worth a look, 7 passed: the checks by colour.
- Compare with this environment:
  - New: not in this environment yet.
  - Changed: different from what is here now.
  - Will be removed: here now, but not in the file.
  - Same: no change.
- Dashed outlines on the map show New and Changed parts.
- Show me: opens the part behind the problem.

## Keys

Who has the keys to which app.

- Browse apps: who can open an app.
- Browse people: what a person can open.
- Compare two people: what a colleague can open and the other person can't, and which group gives it.
- Give access to an app: every group that opens an app, and what else each group gives.
- Needs access: the person you are helping.
- Compare with: the colleague who already has access.
- Open group: copies the group name so you can find it.
- Email to confirm: writes the access request for you.
- Managers come from Microsoft Entra.

## My notes

- Click the pencil, then click anything on the screen to leave a note.
- Tags: Like, Concern, Question.
- All notes are in one list, saved in this browser only.
- Save as PDF or Export for AI from the notes panel.

## Export for AI

Downloads one Markdown file that explains the solution, so tools like Copilot or ChatGPT understand it.

- Project, Power BI, Data engineer: what the file focuses on.
- Before each export you choose:
  - Partly hidden (recommended): environment and server names are hidden (for example `•••.crm.dynamics.com`), IDs keep only their first 4 characters, emails are numbered.
  - Placeholders: names and IDs are replaced with placeholders.
  - Full detail: nothing is hidden. Only for an AI approved inside your company.
- Always removed: passwords, keys and tokens.
- Always kept: tables, columns, descriptions, Power Query, DAX, SQL and flow logic.
- Never exported: data rows.

## Words you may see

| Word | Means |
|---|---|
| Ours | Only things we built. Microsoft's own items are left out. |
| All | Everything, including Microsoft's own items. |
| Broken now | Parts that don't work right now. |
| Worth a look | Not broken, but worth checking. |
| Prefix check | Tables or columns whose prefix doesn't match the solution. Usually made with the wrong publisher. |
| Service owned | Owned by the service account set in `lt_HubServiceAccount`. |
| Connection reference | A link from a flow to a connection. Lets the flow move between environments cleanly. |
| Environment variable | A setting a solution needs, filled in per environment. |
| Managed | A locked solution, the right choice for Test and Live. |
| Unmanaged | An open solution you can change, the right choice for Dev. |

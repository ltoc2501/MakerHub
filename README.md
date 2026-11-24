# Maker Hub

One place to see how your Power Platform solutions are built and how healthy they are.

Maker Hub is a Power Platform solution with read-only web pages. You import it once, open it in your browser and it reads your Dataverse live as you click around. It has no tables of its own, no flows and no extra database.

This is version 1.

## Contents

- [What is in the solution](#what-is-in-the-solution)
- [Before you start](#before-you-start)
- [Import](#import)
- [Open Maker Hub](#open-maker-hub)
- [Security](#security)
- [What needs to be switched on](#what-needs-to-be-switched-on)
- [Optional settings](#optional-settings)
- [Change or remove sections](#change-or-remove-sections)
- [Help inside the app](#help-inside-the-app)
- [Update and remove](#update-and-remove)
- [Questions](#questions)

## What is in the solution

- Name: Maker Hub (`MakerHub`), unmanaged
- Publisher prefix: `lt`
- 11 web resources under `lt_/makerhub/`
- 1 model-driven app: Maker Hub
- No tables, no security roles, no flows, no plug-ins

| Page | File |
|---|---|
| Home | `home.html` |
| Check-up | `healthcheck.html` |
| Workbench | `solutionexplorer.html` |
| Tables | `schemalens.html` |
| Keys | `appaccess.html` |
| Big picture | `developer.html` |
| Launch pad | `citizen.html` |
| Shared code and styles, used by every page | `shared.js`, `shared.css`, `model.js`, `guide.js` |

## Before you start

- A Power Platform environment with Dataverse.
- To import: the System Customizer or System Administrator role in that environment.
- To use it: any user with access to the environment can open it.
- A modern browser (Edge or Chrome).

## Import

1. Download the latest `MakerHub_x_x_x_x.zip` from this repository.
2. Go to [make.powerapps.com](https://make.powerapps.com) and pick your environment.
3. Open Solutions, then Import solution, then Browse and choose the zip file.
4. Click Next, then Import. It takes about a minute.

You may see this message: "This solution was exported from a [Full] environment, which has more components than the current [Standard] environment." You can ignore it. Maker Hub only contains web pages, and they work in every environment with Dataverse.

## Open Maker Hub

After import click Publish all customizations at the top of Solutions. Then open Solutions, then Maker Hub, then Apps. Click the three dots next to Maker Hub and choose Play.

Step by step with screenshots: [Maker-Hub-Installation.pdf](Maker-Hub-Installation.pdf)

Maker Hub hides the app bar by itself, so you only see Maker Hub with its own menu.

### Who is it for

This version is kept simple on purpose. It is made for makers who look after their own environment.

- The solution has no security roles of its own.
- Everyone sees only what their own security role already allows. Maker Hub is read-only and changes nothing.
- Want to share it with others? You can. Select Maker Hub in Apps and click Share. Think first about which security groups or roles should see this information about your environment.

You can also open it with a link, for example as a bookmark. Use your own environment address instead of `YOUR-ORG`:

```
https://YOUR-ORG.crm.dynamics.com/main.aspx?pagetype=webresource&webresourceName=lt_/makerhub/home.html&navbar=off&cmdbar=false
```

## Security

- Maker Hub is read-only. It does not create, change or delete anything in your environment.
- It uses your own sign-in. Dataverse decides what you can see, so every user sees only what their security role allows.
- With System Administrator or System Customizer you see everything. With a smaller role some pages show less. If something is hidden, the page tells you that you don't have permission.
- Nothing is sent outside your tenant. The pages only talk to your own Dataverse.
- Notes you write and files you drop on Launch pad stay in your own browser. They are not uploaded and not shared with anyone.
- Export for AI removes passwords, keys and tokens, hides environment and server names, shortens IDs and never exports data rows. You choose the level before each export.

## What needs to be switched on

Some screens need features that are part of Power Platform but not always switched on:

- Auditing: needed to show who got which role or group (the Access bubbles on Home). If auditing is off, Home tells you.
- Flow run history in Dataverse: needed for failed runs and the run strips. Only solution-aware cloud flows are shown.

## Optional settings

Maker Hub works without any settings. If you want, you can create these environment variables in the Maker Hub solution. Use exactly these names:

| Name | What to put in | Example |
|---|---|---|
| `lt_HubEnvironmentType` | Dev, Test or Live. If empty, it is guessed from the environment name. | `Dev` |
| `lt_HubAreas` | Which business area each publisher prefix belongs to. | `{"abc":"Sales"}` |
| `lt_HubApprovedConnectors` | Extra connectors your company approves. | `sql,azureblob` |
| `lt_HubLimits` | Limits for the Check-up. | `{"admins":5,"broad":10,"untouchedDays":365,"offDays":90}` |
| `lt_HubServiceAccount` | Email of your service account. Flows it owns count as service owned. | `power.platform@contoso.com` |

## Change or remove sections

Maker Hub could be a single file. I split it into one page per section on purpose, so it is easier for you to change it.

- Don't need a section? Remove or edit its page (see the table above). The rest keeps working.
- Keep `shared.js`, `shared.css`, `model.js` and `guide.js`. Every page needs them.
- All files must keep the `lt_/makerhub/` name, because the pages load each other by that path.

## Help inside the app

- Every page has a `?` button with How it works, with pictures.
- Small `i` buttons next to headings explain what a section shows and how numbers are calculated.
- [GUIDE.md](GUIDE.md) explains every screen, colour, tag and button.

## Update and remove

- Update: import the newer zip over the old one. Your notes stay in your browser.
- Remove: open Solutions, then MakerHub. Select all items (the app, its site map and the 11 web resources) and click Delete, then delete the solution itself. Deleting only the solution leaves the items behind, because it is unmanaged. Nothing else in your environment changes.

## Questions

Something doesn't work or you have an idea? Open an issue in this repository.

## Versions

- 1.0.0.1: Maker Hub app included, opens without the model-driven top bar (`navbar=off`), Export for AI hides environment names fully.
- 1.0.0.0: first version.

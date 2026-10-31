# housemaint

A local-first home maintenance tracker. Point it at an appliance manual, and it pulls out the maintenance schedule and reminds you when things are due.

> Status: pre-development. Language and stack not yet chosen.

## Problem

Every home has dozens of maintenance tasks: furnace filters, water heater flushes, fridge water filters, dryer vent cleaning, smoke detector batteries, HVAC service, gutter cleaning. The intervals are buried in manual PDFs that nobody reads, so tasks get forgotten until something breaks or a warranty is voided.

Existing tools make you type every task and interval in by hand. Few people keep that up.

## Core idea

1. Add an asset (for example, "Rheem water heater, model XG50T06EC36U1") and attach its manual PDF.
2. housemaint extracts the maintenance tasks and intervals from the manual (for example, "Flush tank: every 6 months", "Inspect anode rod: every 2 years").
3. You review and confirm the extracted tasks.
4. housemaint tracks when each task was last done and what's due next.

## Principles

- **Local-first:** all data lives on the user's machine. No account and no required cloud service. It works offline.
- **Your data, plain formats:** data is stored in an inspectable, portable format, such as SQLite or plain files, and can be exported.
- **A human confirms extraction:** extracted schedules are suggestions until the user accepts them, and nothing is added silently.
- **Plays well with others:** it should integrate with existing tools rather than replace them.

## MVP scope

- [ ] Add, edit and remove assets (name, category, location, make, model, install date, notes)
- [ ] Attach documents to an asset (manual PDF, receipt, warranty)
- [ ] Extract maintenance tasks and intervals from a manual PDF
- [ ] Review screen for accepting, editing or rejecting extracted tasks
- [ ] Add recurring tasks by hand (interval based, such as every N days, months or years)
- [ ] Mark a task done, with a date and optional note and cost, and keep a history log
- [ ] Overview of overdue tasks, tasks due soon and upcoming tasks
- [ ] Export all data (JSON)

## Later / nice to have

- Warranty expiry tracking
- Seasonal tasks ("every fall") and usage-based tasks ("every 500 hours")
- Calendar export (iCal feed) for reminders
- Notifications (desktop, email, ntfy and so on)
- Integrations: [Homebox](https://github.com/sysadminsmedia/homebox) (inventory), Home Assistant
- Shared library of known schedules by appliance model
- Mobile-friendly UI and photo capture of model plates

## Non-goals (for now)

- A full home inventory system (Homebox already does this well)
- Multi-user or multi-household SaaS hosting
- Chore and grocery management (Grocy covers this)

## Prior art

| Project | What it does | Gap housemaint fills |
|---|---|---|
| [grocy](https://github.com/grocy/grocy) | Household management with chores | No extraction from manuals; general purpose |
| [homebox](https://github.com/sysadminsmedia/homebox) | Home inventory with warranty fields | Not focused on recurring maintenance |
| [Warracker](https://github.com/sassanix/Warracker) | Warranty tracker | Warranties only |
| [LubeLogger](https://github.com/hargata/lubelog) | Vehicle maintenance tracker | Vehicles only, but a good model to follow |
| [homelogger](https://github.com/FrancisLaboratories/homelogger) | Self-hosted home maintenance tracker | Tasks entered by hand |
| HA plugins (home-keeper, home_maintenance) | Recurring tasks in Home Assistant | Requires Home Assistant; tasks entered by hand |

## Open questions

- **Form factor:** desktop app, self-hosted web app, CLI, or several of these?
- **Language and stack:** not yet decided.
- **Storage:** SQLite or plain files (Markdown/YAML) that users can edit and put under version control?
- **Extraction approach:** text extraction plus rules, a local LLM (to stay fully local), an optional cloud LLM, or a mix of these? How should scanned or image-only manuals be handled?
- **Reminders:** how are users notified when the app isn't running?

## License

TBD

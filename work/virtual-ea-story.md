Skip to deck01 / 09A AgentRunner Story
# MyVirtual EA
— the real story.
A personal access layer on Microsoft Graph.
**Zero code. 12 tools. A lot of lessons.**
What shipped, what got blocked, what the Graph API taught me the hard way,
          and where the agent is heading next.**Sauravi**Senior Director, Product Management (Walmart International)
Walmart Global Tech · Bengaluru, Bangalore · May 2026📅One sentence frame: "This is the honest story of what it took to build an AI layer on top of Outlook — what works, what the API actively fights you on, and where it's going next." Don't oversell it. The friction is part of the story.02 / 09Why this exists
## A Senior Director's calendar is a political artifact.
The friction that made a Virtual EA worth building.🔁
#### Recurring series traps
Graph returns_occurrence_IDs. Patching the wrong one means your room change disappears next week.🏢
#### Room booking is broken by default
`findRooms`and`/places`return 403/404 in most tenants. You can't discover rooms the official way.🔔
#### Notification spam is unavoidable
Graph ignores`Prefer: outlook.send-notifications=false`on calendar PATCHes. Every bulk edit pings every attendee.📅
#### The 180-day silent cliff
Exchange auto-declines room invites beyond ~180 days. Book a 12-month series and half your rooms silently vanish.🌏
#### Timezone landmines
Raw UTC offsets break across DST. Every wrong booking is a missed call with someone in Chicago or California.📝
#### Body overwrite risk
One careless PATCH and the agenda, dial-in links, and attachments disappear. Graph replaces, it doesn't merge.
> "I'm the layer between Sauravi and Outlook's sharp edges — I know which room is too small for a 1:1, that her Friday 'weekly sync' room change has to hit the series master not the occurrence, and that booking a room 9 months out will silently get auto-declined at day 181 — so she doesn't have to."— meeting-room-agent, in its own wordsName the pain before the solution. Each of these problems is real, discovered in production — not anticipated. The agent exists because the Graph API is powerful but unforgiving, and a Senior Director shouldn't need to know its internals to run a clean calendar.03 / 09The surface area
## 12 tools. One conversational surface.
Everything a calendar-heavy Senior Director needs — without touching Outlook directly.
### 🏢Room & space management
- Catalog-driven room discovery (building/floor YAML — no hardcoding)
- Tier-based sizing: 1:1s never in solo rooms; 7+ go straight to large
- Known-blocker cross-check before any recommendation
- 180-day window awareness — proactive offer to cap or split long series
### 🔁Recurring series intelligence
- Series-master resolution before any PATCH (Graph returns occurrence IDs)
- Modified-occurrence awareness — exceptions flagged, not overwritten
- Never-no-end rule enforced if preference is set; renewal flagged
- Proactive 6-month room booking with explicit flag for the remainder
### ⚙️Preference-driven behaviour
- All user context loaded at session start from`get_user_preferences`
- Deep-merge writes — never a whole-record overwrite
- Schema-versioned profiles with migration awareness
- Zero user-specific values in the system prompt
### 🛡️Safe editing guardrails
- Body preservation: read → append assistant note → write (never replace)
- Notification threshold warning before bulk patches; heads-up email offered
- Always IANA timezone names for DST safety; display in user's local label
- Mandatory OneDrive sync reminder after every preference writeFrame these as pairs: room smarts + series smarts on the left (the "why it's hard" pair), preference-driven + safe-editing on the right (the "how we stay safe" pair). The key sentence: "12 tools, but only one thing changes how they behave — your preference profile."04 / 09The orchestration asset
## Zero hardcoded values. Everything is profile-driven.
One JSON describes you. Every agent reads it. Same agent, any user, any timezone, any building.
### What the schema coversdisplay name & signatureIANA timezone + labelhome building / floor / quadrantworking hourshard blocks + exceptionsroom tier rankingsknown room blockersmeeting link defaultscolor category mappingsmodification-note templatenotification thresholdsrecurrence capsnever-use-no-end flagschema: user-preferences-schema.v1.yaml
### How it loads
`get_user_preferences(user_email)`runs at session start.
              If no profile exists → onboarding flow triggers automatically.
              Updates via`update_user_preferences`with**deep merge**— never a whole-record overwrite.
### Why this matters at scale
The same agent handles a**Bangalore IC**and a**US-based EA**without a re-prompt.
              Timezone, building, room tier, notification threshold — all profile-driven.
              Add a new user: create a profile. No prompt edit. No redeploy.
### The orchestration unlock
Preference profiles are Composition Pattern #1 from the stack's ORCHESTRATION.md.
              The Copilot Studio variant reads from the_same_preference store (via OneDrive).
              Change a preference once → both surfaces honour it.
              This is what "compound into platform leverage" looks like in practice.
#### Schema evolution ahead
v1.yaml is live. Migration-aware (handles missing fields gracefully). Future versions will add team-level shared preferences — not yet shipped.The headline is the principle: nothing about a user lives in the prompt. Show the tag cloud as evidence of coverage. Then land on the orchestration unlock — the same preference file powers two different surfaces. That's the platform-level behaviour.05 / 09First-time experience
## One minute. Then you're in.
Structured onboarding triggers automatically when no profile exists. Seamlessly hands off into the session.1
#### Greet & frame
Explain it's a one-time setup, ~1 minute. Sets expectations so users don't abandon mid-flow.2
#### Identity & link
Name + signature → default meeting link. The two things that go in every event invite.3
#### Location & hours
Office + building/floor → preferred meeting window + hard blocks. Grounds every room and time suggestion.4
#### Room tiers + colours
Room preferences only if the building is in the org catalog. Colour-category opt-in. Both skippable.5
#### Save → handoff
`update_user_preferences`→ profile summary echoed back → straight into "here are today's events."
### Design choices that matter
- Questions asked in dependency order — each answer informs the next
- Room tier question skipped if building not in catalog (no dead-ends)
- Profile echoed back before session continues — user confirms accuracy
- Subsequent sessions: zero onboarding friction, profile already loaded
### What this enables downstream
- Every room recommendation is grounded in the user's actual building
- Every time suggestion respects their declared hard blocks
- Notification threshold set upfront — no surprise spam warnings mid-session
- Profile schema is designed to support a second surface (Copilot Studio, when stable) via the same OneDrive storeThe key framing: onboarding is the moment the agent stops being generic and starts being yours. Five questions, dependency-ordered, and then you're in the session. The "straight into today's events" handoff matters — zero ceremony once done.06 / 09Where it earns its keep
## The recurring series & room booking smarts.
Six behaviours that are invisible when they work — and catastrophic when they don't.🔍
#### Series-master resolution before every PATCH
Graph returns occurrence IDs, not series master IDs. The agent fetches the event first, extracts`seriesMasterId`, then patches — so "update the room on my weekly 1:1" propagates to all future occurrences, not just next week's.⚡
#### Modified-occurrence awareness
Occurrences with`type: exception`(e.g. a rescheduled instance) are flagged for separate handling. A master-series patch won't silently overwrite a deliberate exception.📅
#### The 180-day room window trap — proactively handled
Exchange auto-declines room invites beyond ~180 days. For 12-month recurring asks, the agent proactively offers three options: cap at 6 months, book room for first 6 + flag the rest, or skip the room. No silent failures.♾️
#### Never-no-end rule
If`never_use_no_end_recurrence`is set in the profile, the agent refuses open-ended series, always tells the user when a series ends, and flags for renewal. Prevents phantom recurring events that nobody owns.🚫
#### Known-blocker cross-referencing
Free/busy lookups can miss recurring conflicts. The agent cross-references each user's`known_blockers`list before recommending any room or time — a second layer of conflict detection that Graph doesn't provide natively.📐
#### Tier-based room sizing
1:1s never go into a 2-person solo room (too intimate for a Director-level). 7+ attendees skip straight to large rooms. Tier rankings come from the user's preference profile — no hard rules in the prompt.Each of these was discovered through a real failure. Walk through two or three rather than all six. The point: every one of these "smart bits" exists because the naive approach breaks in production.07 / 09What's new
## Three additions that changed the shape of the agent.
Not just new features — structural changes to how it works and who it serves.🗂️
#### Org-level room catalog —`get_org_room_catalog`
Rooms are now loaded per building/floor from a shared YAML catalog, not hardcoded per user. Adding a new building means adding a new YAML file — not editing the agent prompt. This is the fix for the broken`findRooms`API: rooms discovered organically from calendar history get added to the catalog and are available to everyone from that point on.🌱 New🧪
#### Copilot Studio variant — in-progress experiment(not yet functional)
We're exploring a Teams/Outlook surface via Copilot Studio — a parallel agent that would let EAs like the EA run the same assistant without touching a terminal. Same preference schema, same room catalog, same logic —**but the integration is currently buggy and not in real use.**The direction is right; the plumbing isn't stable yet. Consider this architectural groundwork, not a shipped capability.🚧 In progress🔄
#### Dual-system sync infrastructure(forward-looking)
After every preference write, the agent appends a sync reminder: mirror the change to OneDrive (`Documents/meeting-room-agent-prefs/preferences.json`). The preference schema is designed so a second surface can read from a shared store — but since the Copilot Studio variant isn't functional yet, this reminder is**anticipatory infrastructure**, not live drift-prevention. When the second surface is stable, the plumbing will be ready.🌱 NewBe honest about the Copilot Studio experiment: the intent is right (Teams/Outlook surface for non-technical EAs), but the integration is currently buggy and not in real use. Lead with the org catalog as the concrete shipped improvement. Frame the Copilot Studio work as 'we proved the architecture supports it — now we need to make it stable.' The sync reminder is future infrastructure, not live behaviour.08 / 09What the Graph API taught me
## The honest lessons. What we got wrong first.
Every one of these was discovered in production, not in documentation.
#### 🔔Notification spam is unavoidable
Graph ignores`Prefer: outlook.send-notifications=false`for calendar PATCHes. Design response: warn before bulk patches above the user's threshold, offer a heads-up email first, offer a summary email after. Inform — don't surprise.
#### 🏢Room discovery is broken
`findRooms`and`/places`return 403/404 in most tenants. Workaround: discover rooms organically from existing calendar history, then persist them in the org catalog YAML. It works — just not the official way.
#### 🌏Timezone: always IANA, never raw offset
Raw UTC offsets break across DST boundaries. Always convert via IANA name (e.g.`Asia/Kolkata`). Display in the user's local label; send all Graph API calls in UTC. One wrong booking at 9am = missed call with Chicago.
#### 📝Body preservation: read first, always
Never overwrite an event body directly. Always: read the full event → append the assistant note using the user's modification template → write back. Graph replaces bodies on PATCH — one shortcut and the agenda disappears.
#### 🔄Two-system drift is a real risk — when the second surface ships
The Copilot Studio variant isn't functional yet, so there's no active drift to resolve today. But the architecture anticipates it: AgentRunner reads from a local store; a second surface would read from SharePoint. The sync reminder baked into the tool response is forward-looking infrastructure — designed to prevent drift once both surfaces are live, not to fix it now.
#### 📅The 180-day room booking cliff
Exchange auto-declines room invites beyond ~180 days — silently. The fix is proactive detection: when a user books a room for a long series, the agent surfaces the cliff and offers options before Exchange acts. Warn early, offer choices.Be honest and specific. These aren't theoretical warnings — each one has a production story behind it. The "red" ones (notification spam, room discovery) are still unresolved at the API level; we've designed around them, not through them. Frame that honesty as a feature, not a weakness.09 / 09Take it further
## What's next — and how to get involved.
Three open tracks. The pattern is forkable right now.
### 🔧 The sync bridge
Replace the manual OneDrive sync reminder with a real bidirectional sync between the local preference store and SharePoint. One write, both surfaces updated. The architecture is designed for it — needs the plumbing.
### 📊 Instrumentation
Add lightweight cross-session telemetry: bookings made, series patched, edge cases triggered, rooms added to catalog. Gives us the numbers we can't honestly report yet.
### 🤝 EA rollout at scale
The Copilot Studio experiment is exploring a Teams/Outlook surface for non-technical users. Once the integration is stable, document the deployment playbook, run it for a second EA, and we have a replicable programme.[🔗**Fork the stack**internal.example.com/user-id/Sauravi-agent-stack](https://github.example.com aria-label=)[📋**EA rollout guide**internal.example.com/sharing/user-id/deploy-plan](https://agent-platform.example.com aria-label=)[📊**Live tracker**internal.example.com/sharing/user-id/sauravi-agent-stack-tracker](https://agent-platform.example.com aria-label=)✉️**Talk to me**sauravi.rai@example.com
The agent is the pattern. The pattern is_forkable_. Take it and make it yours.End with energy and a concrete ask: which of the three tracks will you lean into? The sync bridge is engineering-heavy; instrumentation is a good afternoon; the EA rollout is a people programme. Pick the one that matches what you have available right now.
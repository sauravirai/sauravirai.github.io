Walmart Global Technology · Bangalore · 2026
# My First Agent
What I Built & What I Learned
A real scheduling problem. A working agent. Zero code written.SR🤖SauraviSenior Director, Product ManagementWalmart Global Technology · BangaloreWalmart Global Technology · BangaloreApril 2026[**Prerequisite:**New to AI agent CLI? Get started atinternal.example.com/doghousefirst →](https://agent-platform.example.com target=)🎬 THE STORY IN 30 SECONDS
# Watchhow it started
Before we dive into the architecture, hear it directly from Sauravi — built with an AI avatar to match the AI story being told.🎬 Generated with HeyGenAI avatar reading Sauravi's script — same tools we're talking about☁️ Hosted on GitHub PagesPersonal portfolio demo⏱️ ~30 secondsThe 30-second pitch — full story unfolds in the slides ahead[↗ Open in OneDrive](https://internal.example.com
       target=)The Problem —and What Got BuiltScheduling a global team with no EA and a calendar that fights back. The perfect test case for AI agent CLI.BeforeRoom RouletteMultiple rooms, all heavily booked in office hours. Open calendars one by one and hope.Zoom or Teams?Add the link manually, every time — and hope everyone joins the right platform.IST ↔ UTC in your headEvery external meeting. Mental math, every time. A silent tax on focus.Opaque updatesChanged the time? Type a manual note. No guarantee anyone reads it.Hard blocks ignoredLunch, family time — people book right over them because the calendar doesn't know.No EA, global teamLeading across India, US, international markets — every booking and reschedule is manual, all you.Her agent solved itAgent books the right roomChecks availability across all rooms, picks by size and preference. One command.Meeting link auto-addedZoom URL inserted into every invite, automatically. Never forgotten again.Timezone handled silentlySay "2pm" in IST. Agent converts to UTC for the API, confirms back in IST. Zero mental math.Timestamped change notesAny update appends a clear note to the invite description. Transparent, automatic.Hard blocks always respectedAgent knows your protected time and never suggests anything inside those windows.EA orchestration — on the roadmapThe team-ready Meeting Room Agent adds shared config; EA–EA coordination and schedule defrag are next.
Scheduling was the test case — concrete, repeatable, and obviously broken. Solve it, and you have a template for the next workflow too.Spotting the Gap:First TinkeringBefore the breakthrough, there was just curiosity — and a list of things that wasted time.Why scheduling was the right test case
- **Repetitive**— done multiple times a day, every day. Small gain × high frequency = real time back.
- **Clear success criteria**— either the room is booked correctly or it isn't. Easy to verify.
- **Self-contained**— calendar + room data + one API. No complex dependencies to untangle first.
- **Zero EA**— leading a global team with no executive assistant means every booking is manual, every time.
- **Transferable pattern**— solve one repetitive workflow with an agent, and you have the blueprint for the next.How the conversations with AI agent CLI evolvedV0
### "Can you book a room for me?"
First prompt. Sauravi just asked plainly. AI agent CLI explained it needed calendar access. She gave it. It worked — once.V0.5
### "What if I tell you my preferences?"
She described her room order, her Zoom link, her timezone — in plain English, inside the chat. The agent followed them. But she had to re-explain them every session.V1
### "Let's write all this into the system prompt."
AI agent CLI helped her move the rules and preferences into a persistent system prompt. Now it remembered everything. One prompt, no re-explaining.
### "Wait — can my teammate use this too?"
And that's when it hit her. The agent was hers — it had her Zoom link, her timezone, her room list. It couldn't be anyone else's._Yet._
The real breakthrough wasn't the first booking — it was a teammate asking_"Can I use this too?"_That one question exposed the hard-coded limits and unlocked the whole team design.Making It Workfor the Whole TeamSauravi’s personalized Meeting Room Agent worked for one person. The goal: make it usable by the whole team without rebuilding from scratch.The Scaling Insight
- What if you could describe**any user**in a YAML file — their timezone, their Zoom link, their room preferences?
- The agent reads that file at session start and**just knows**who it's talking to. One agent brain, infinite identities.
- It goes from**Sauravi's agent**to**the team's agent**— just by adding a YAML file per person.
- When preferences change, update**one file**. The agent adapts instantly. Zero redeployment. Zero friction.What the agent "knows" about Sauraviprefs/sauravi.rai@example.com.yaml
```
# Sauravi's personal agent preferences

identity:
  name:     "Sauravi"
  email:    "sauravi.rai@example.com"
  timezone: "Asia/Kolkata"  # IST UTC+5:30

conferencing:
  zoom_link: "https://internal.example.com
  always_add: true

office_hours:
  work_start:      "09:30"
  work_end:        "17:30"
  preferred_start: "10:00"
  preferred_end:   "15:00"
  hard_blocks:
    - label: "Lunch"
      start: "13:00"  end: "14:00"
    - label: "Family time"
      start: "16:30"  end: "19:30"

room_priority:
  # Tier 1 — preferred (airy, window view)
  - Alderaan
  - Solaris
  # Tier 2 — standard
  - Skywalker
  - Arrakis
  - Babylon
  # Tier 3 — last resort
  - Skynet
  - Mandalore

booking_rules:
  confirm_before_change: true
  append_update_note:   true
  note_prefix: "[Updated"
```
Personal → Team:How the Agent Got BetterStart simple. Ship it. Hit a real wall. Then make it better. This is the story of every good tool ever built.Sauravi’s agent — one person, hard-coded
- All preferences baked directly into the system prompt markdown file
- Sauravi's Zoom link was a literal string in the prompt
- Timezone, room list, working hours — all hard-coded
- Only worked for one person — Sauravi
- Changing preferences meant editing the prompt and re-reading it
- No shared room data — rooms described in plain English inside the promptMeeting Room Agent — shared, configurable
- Structured YAML preferences file per user — clean separation of concerns
- `prefs/_template.yaml`— new user onboarding in minutes
- Shared org-catalog YAML — rooms discoverable by any team member
- Python tools to load/save preferences and room catalogs cleanly
- Agent bootstraps from data — one prompt serves the whole team
- Update a preference → agent adapts instantly, zero re-deployment1Start MessyOne big system prompt. Hard-coded values. It works!2Feel the FrictionThe config is hard-coded for one person. Changing preferences means editing the whole prompt.3Extract the DataPull preferences into YAML. Build the shared room catalog.4Team ReadyCopy the template YAML. Fill in your details. Done.Timeline: key milestones from the journeyMar 23, 2026 ✅🚀First sessionAI agent CLI opened, calendar connected, first tinkering beginsMar 25, 2026 ✅📅First real bookingAlderaan booked live. Zoom link auto-added. "It actually worked!"Late Mar 2026👥Teammate asks to joinExposed the single-user hard-coding problem instantlyApr 17, 2026 ✅📄V2: Config splitPreferences → YAML. 82M tokens, 16K lines in a single sprintApr 17, 2026 ✅🗺️Room catalog liveFloor plan → shared YAML config. Team-ready, same sprint
Dates confirmed from MS Graph calendar watermarks + InternalLLMGateway AI usage logs.How It's Built:The Two FilesAll custom agent behavior comes from just two files. That's it.File 1System Prompt —_agent's brain & rules_system-prompt.md
```
## Identity
You are the Meeting Room Agent for [Company] Bengaluru
PTPP2 2nd floor. You manage calendars via
MS Graph API on behalf of {user}.

## Session Start
1. Load prefs from prefs/{user_email}.yaml
2. Load room catalog from
   org-catalog/PTPP2-2F.yaml
3. List today's calendar events for user
4. Greet user with a summary

## Room Booking Rules
- Always check availability first
- Match room capacity to meeting size
- Respect user's room_priority order
- ALWAYS add zoom_link if always_add=true
- NEVER modify without explicit confirmation

## On Any Change
- Append timestamped note to description
- Handle recurring series via seriesMasterId
- Confirm scope: "this event" vs "all events"

## Time Handling
- User speaks in IST, API uses UTC
- Convert silently; confirm in IST to user
- Respect hard_blocks — never suggest times
   that fall within them
```
Bonus FileRoom Catalog —_PTPP2 Floor 2 room layout_org-catalog/PTPP2-2F.yaml
```
floor:    "PTPP2 2nd Floor"
location: "[Company] Office, Bangalore"

rooms:
  - name:     Alderaan
    capacity: 6
    email:    alderaan@example.com
    features: [window_view, whiteboard, airy]

  - name:     Solaris
    capacity: 8
    email:    solaris@example.com
    features: [av_system, whiteboard]

  - name:     Skywalker
    capacity: 12
    email:    skywalker@example.com
    features: [av_system, projector]

  - name:     Mandalore
    capacity: 20
    email:    mandalore@example.com
    features: [large_screen, av_system]
    notes:    "Last resort — far from team pods"

# Add more rooms as your org grows
# This file is shared across all users
```

### One floor layout, one file
The PTPP2 Floor 2 room config is shared across the whole team. Update capacity or a room name once, everyone benefits.How the catalog was created
Sauravi annotated a photo of the**PTPP2 floor plan**in another GenAI tool, which extracted room names, capacities, and positions into structured YAML.

**Next step:**bring this into the agent itself — AI agent CLI can read image files directly, so the floor plan annotation workflow can live entirely inside the agent going forward.Under the Hood:How It Actually WorksOne conversation → three file reads → four API calls → calendar patched. No code. Just config.New to AI agents? The 6 concepts you need to follow this slide:🧠LLMLarge Language Model. The AI brain — reads your words and decides what to do. GPT, Claude, Gemini are all LLMs.🐶AgentAn LLM given a_goal_, a_set of tools_, and permission to_take action_. It thinks in steps until the job is done.📋System PromptThe agent's written job description. Tells it_who it is_, what rules to follow, and what tools it has. This is the main config file.🔧Tool / SubagentA specific capability the agent can call: "check my calendar," "book a room," "send a Teams message." This agent's key tool is_msgraph_.🔌MCP**Model Context Protocol.**The universal standard for connecting agents to tools — like USB, but for AI. Means any agent can talk to any compatible service.💭Context WindowThe agent's working memory — everything it can "see" at once: your conversation, its instructions, and loaded data. Finite in size.👤You"Book me a quiet
room for 2pm"→🐶AI agent CLILLM core
(InternalLLMGateway AI / Claude)system_prompt.mdprefs/you.yamlrooms.yaml→⚡msgraphAI agent CLI
subagenthandles auth
token refresh→MS Graph APIGET/me/calendar/eventsPOSTfindMeetingTimesPATCH/events/{id}PATCHdescription + note→✅Booked!~8 seconds
start to finishAuth & Security
The msgraph subagent handles your corporate M365 token — no credentials are ever stored in the YAML files. Token refresh is automatic. Read/write scopes are Calendars.ReadWrite only.State & Storage
The agent is**stateless per conversation**— it re-reads both YAML files at the start of each session. Conversation history lives in AI agent CLI's context window only. No database, no backend.Technical Optimizations:What V3 Could Look LikeThe agent works great today. Here's what a more production-hardened version would add.HIGH IMPACTBatch Room Availability
Currently checks room availability room-by-room (N sequential API calls).**Replace with`findMeetingTimes`**— one call, all rooms ranked by preference simultaneously.~70% fewer API calls  ·  ~2-3s fasterMEDIUMPrompt Compression
The system prompt is verbose (~1,800 tokens). Rewrite in structured shorthand — same instructions, ~30% fewer tokens per conversation turn.~$0.001 saved per conversation  ·  faster latencyMEDIUMSession-Level Calendar Cache
Today, each booking request re-fetches your calendar. In a multi-booking session, cache the day view once at conversation start and reuse it.Eliminates redundant GET calls in multi-turn sessionsFUTUREProactive Room Notifications
Subscribe to MS Graph**webhook notifications**on room calendars. When your preferred room gets freed mid-day, the agent pings you via Teams — without you asking.Reactive → Proactive. Game changer for packed days.Graceful Auth Expiry HandlingIf the MS Graph token expires mid-conversation, the agent currently errors. Add a retry-with-reauth flow.Timezone Auto-DetectionCurrently reads timezone from YAML. Could auto-detect from your most recent calendar event instead — one less thing to configure.The Real Numbers:Cost to Build & RunReal data from MS Graph + InternalLLMGateway AI usage. V1 live**Mar 25, 2026**. V2 launched in a single-day sprint on**Apr 17, 2026**. Every ✅ number is sourced.V1 Live ✅Mar 25, 2026Earliest agent watermark in MS Graph calendarV2 Live ✅Apr 17, 2026One-day sprint · 82M tokens · 16,623 linesBuild total ✅7 active days117.6M tokens · 1,778 requests · 23,533 linesYour weekly meetings ✅~55 / week703 events in 90 days — exact from MS GraphBuild Cost ✅7 active daysV1 in late-March · V2 as a one-day sprintV1 build (Mar 23–25)3 days · 3.8M tok ✅V2 sprint (Apr 17)1 day · 82M tok · 16K lines ✅Code written by Sauravi0 linesAI agent CLI + infra cost$0Token Cost ✅98% cachedOnly 1.81M of 117.6M tokens were new completionsTotal tokens (build + run)117.6M ✅Completion tokens (billable)1.81M (1.5%) ✅$ cost → check InternalLLMGateway portal[look it up →](https://github.example.com style=)MS Graph + infra$0ROI — real data4+ hrs savedconfirmed minimum (50 bookings × 5 min)Confirmed bookings since Apr 1750+ ✅5 active recurring series→ Apr 2027 ✅Projected annual savings~21 hrs/yrYour meeting load (55/wk)high — room friction is realData sources (✅ = live from MS Graph)✅ 703 events / 90 days = 55 meetings/week  |  ✅ V1 watermark: Mar 25, 2026 (meeting-room-agent-a02a88)  |  ✅ V2: Apr 17, 2026 (user confirmed)  |  ✅ 7 active AI agent CLI days · 117.6M tokens · 1.81M completion  |  ✅ 5 recurring room holds through Apr 2027**One gap left:**Token cost in $ — check your usage on the[InternalLLMGateway GenAI portal](https://github.example.com style=)(Looker password reset → IT helpdesk). Everything else on this slide is sourced from live data. ✅Try It Yourself:The Agent is LiveSauravi's personalized Meeting Room Agent is published. Download it and try it out — right now, if you have AI agent CLI installed.Example conversationBook me a room for my 2pm 1:1 with [colleague] today. Just us two.**Checking availability 2:00–3:00 PM IST...**

**Alderaan**is free
Solaris booked until 3pm

Shall I book Alderaan & add your Zoom link?Yes, do it.**Done!**Room booked, Zoom link added, note appended.

~8 sec vs ~5–7 min manually.Get the Agent[Sauravi's Meeting Room Agentinternal.example.com/marketplace](https://agent-platform.example.com target=)[YAML Templates & Agent FilesCopy prefs/_template.yaml to get started](https://agent-platform.example.com target=)What to try first
- Fill in`prefs/your.name@example.com.yaml`with your timezone, Zoom link, and room order.
- Ask it:_"Book me a quiet room for a 30-min sync tomorrow at 11am."_
- Watch it check availability, pick from your priority list, add your Zoom link, and patch the invite — all in one shot.
### VPN or Corporate WiFi required
internal.example.com is a corporate intranet link. Make sure you’re on VPN before clicking.🐾 Start Today!Pick any workflow that costs you 10 minutes a day. That's your first use case — just like Sauravi did.Sauravi's journeyYour turnStartDay 1first booking ·**Mar 25 ✅**Habit~1 weekV1 in daily useTeam~3 weeksV1 → V2, team-ready ✅You~30 minyour first agentSR🤖"If I can build a working AI agent in a morning,so can you.Start with one annoying workflow."— Sauravi · Senior Director, Product Management1
### Install AI agent CLI
Connect to**VPN or Corporate WiFi**, then[internal.example.com](https://agent-platform.example.com style=)→ install guide. About 2 minutes.2
### Open terminal and run agent-creator
Type`/agent agent-creator`. It walks you through building your first agent config interactively.3
### Describe what you want
_"Help me design an agent that handles my X every day."_AI agent CLI asks the right questions and drafts your system prompt.4
### Fill in your preferences file
Copy`prefs/_template.yaml`from the shared workspace. Fill in timezone, email, preferences. That's your identity file.5
### Iterate — you're doing agile AI
Run it. Notice what's off. Update one line. Run again. This is exactly how the first version was built.First agent: ~30 minNo app deploymentQuick linksVPN requiredAI agent CLI[internal.example.com](https://agent-platform.example.com style=)Dog House[internal.example.com/doghouse](https://agent-platform.example.com style=)Agent Marketplace[internal.example.com/marketplace](https://agent-platform.example.com style=)Slack[#code-puppy](https://example.slack.com style=)Shared files[internal.example.com/sharing/user-id](https://agent-platform.example.com style=)Already on the team? Try the Room Agent right nowType`/book`in Slack → your room is booked, Zoom added, timezone handled. No forms. No waiting./book →🎯InternalAgentPlatform Skill or AI agent CLI Agent?Repeatable prompt pattern →**InternalAgentPlatform Skill**|  Think & act across steps →**Agent**[Skill Marketplace](https://agent-platform.example.com style=)`/skill-market`[InternalAgentPlatform on GitHub](https://github.example.com style=)What's next for this agent**Schedule defrag**— cluster meetings, protect focus windows**EA–EA coordination**— two agents scheduling across leaders**Voice interface**— "Book me a room" without typing1 / 8Speaker Notes👋Let Sauravi know you're watching — it helps her track who found this useful.✓ Send×0
### Quick Feedback×How useful was this session?😐🙂😊🤩🤯What excited you most?Golden HoursSchedule DefragGUI for EAsCopilot IntegrationEA–EA CollabVoice InterfaceTravel PlannerTry the AgentAny thoughts or suggestions?CancelSubmit🎉
### Sent to Slack!
Sauravi will see your feedback in real time. Thank you!
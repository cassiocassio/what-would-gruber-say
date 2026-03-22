# What Would Gruber Say?

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) agent that reviews your macOS app the way a thoughtful Mac user would — checking for HIG compliance, native feel, and the kind of details that separate a Mac app from an app that happens to run on a Mac.

Drop it into your project. Ask it to review your SwiftUI views, your toolbar, your menu bar, your keyboard shortcuts. It'll tell you what John Gruber would notice, what John Siracusa would file a Radar about, and what would make the indie Mac dev community wince.

## What it checks

- **HIG compliance** — toolbar zones, menu bar completeness, reserved shortcuts, SF Symbols, context menu conventions
- **Native feel** — vibrancy, system accent colour, row height, disclosure triangles, spring animations with reduce-motion guards
- **Keyboard shortcuts** — modifier key hierarchy, reserved system shortcuts, native vs web layer split for hybrid apps
- **Accessibility** — VoiceOver, Dynamic Type, high contrast, reduced motion, keyboard-only navigation, focus transitions at native/web boundaries
- **App Store readiness** — security-scoped bookmarks vs path strings, sandbox file access, codesigning, entitlement hygiene, data migration planning
- **Usability** — learnability, efficiency, error prevention, feedback, information hierarchy, cognitive load (Hick's law, Miller's 7+/-2, progressive disclosure)
- **Hybrid app guidance** — WKWebView bridge security, navigation restriction, ephemeral storage, native/web coordination

## Usage

Copy the agent file into your project:

```bash
mkdir -p .claude/agents
cp path/to/mac-ux-review.md .claude/agents/
```

Or clone this repo and copy it:

```bash
git clone https://github.com/cassiocassio/what-would-gruber-say.git
cp what-would-gruber-say/.claude/agents/mac-ux-review.md your-project/.claude/agents/
```

Then in Claude Code, ask it to review your code:

```
@mac-ux-review ContentView.swift
@mac-ux-review desktop/Views/
```

The agent reads your Swift files, checks them against the rules, and produces a structured review with specific findings, file paths, line numbers, and concrete suggestions.

## What it doesn't do

This is a **macOS native** reviewer. It doesn't cover:

- iOS, iPadOS, visionOS, or watchOS (different HIG, different patterns)
- Web-only apps (no native shell to review)
- Cross-platform frameworks like Flutter or React Native (different trade-offs)
- Your app's specific design system tokens or component library — that's your concern, not ours

## Philosophy

The Mac has always been opinionated software for opinionated people. The best Mac apps don't just follow the HIG — they understand *why* the HIG says what it says, and they extend that sensibility into their own design decisions.

This agent tries to encode that sensibility. Not as rigid rules, but as the questions a thoughtful Mac user would ask: *Does the sidebar use vibrancy? Does Cmd+, open Settings? Does the toolbar title show the document name, not the app name? Does the context menu append "..." when an item needs additional input?*

These details are individually small. Collectively, they're the difference between "this feels like a Mac app" and "this feels like an Electron app with a custom title bar."

## Credits and sources

This agent encodes opinions and conventions from across the Mac development community. Credit where it's due:

### Apple

- **[macOS Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/)** — the canonical reference for sidebars, toolbars, menus, keyboards, windows, and accessibility. Every check in this agent traces back to a specific HIG section
- **[SF Symbols](https://developer.apple.com/sf-symbols/)** — Apple's icon system that auto-adapts to weight, size, accessibility settings, and accent colour

### The commentariat

- **[John Gruber](https://daringfireball.net/)** (Daring Fireball) — two decades of writing on what makes Mac software feel right. His instinct for when something is "not quite Mac-like" is the north star for this agent. If Gruber would notice it, we flag it
- **[John Siracusa](https://hypercritical.co/)** — the legendary macOS reviewer whose Ars Technica reviews (10,000+ words each, for over a decade) set the standard for platform-level attention to detail. Co-host of ATP. The person who would file a Radar about your disclosure triangle animation timing
- **[Marco Arment](https://marco.org/)** — Overcast, Tumblr co-founder, ATP co-host. Practitioner who writes publicly about the trade-offs of indie Mac/iOS development, App Store review, and what it means to ship quality software on Apple platforms
- **[Craig Hockenberry](https://furbo.org/)** — Iconfactory co-founder (Twitterrific, xScope). Decades of Mac development wisdom, particularly on icon design, colour management, and making things feel right at the pixel level

### Toolbar and layout

- **[Mario Guzman](https://www.marioguzmancortes.com/)** — toolbar layout guidelines: leading (navigation), centre (principal), trailing (content-descriptive title). The three-zone toolbar model referenced throughout this agent

### The apps that set the bar

These are the Mac apps we reference as exemplars of native feel. When this agent says "follow the Tower model" or "use the Bear pattern," this is what it means:

- **[Things 3](https://culturedcode.com/things/)** (Cultured Code) — spring animations, relaxed spacing, the gold standard for "feels like it was made for this platform"
- **[Bear](https://bear.app/)** (Shiny Frog) — tag-based sidebar, mixed-case section headers, TagCons. Proof that a note app can feel like a first-party Apple app
- **[Tower](https://www.git-tower.com/)** (fournova) — grey pill badges for status ("Fully Merged", "Stale"), red circle only for "needs attention." The badge model we recommend
- **[Reeder](https://reederapp.com/)** (Silvio Rizzi) — restraint as a design principle. No unread counts, no badge noise. Proof that removing UI is a feature
- **[1Password](https://1password.com/)** (AgileBits) — search-first, vault sidebar. Native feel despite complex functionality
- **[Arc](https://arc.net/)** (The Browser Company) — spaces, pinned tabs, creative sidebar use. Pushing what "native feel" means while staying Mac-like
- **[Transmit](https://panic.com/transmit/)** / **[Nova](https://nova.app/)** (Panic) — the Panic aesthetic: playful but precise, always native, never gratuitous
- **[Fork](https://git-fork.com/)** — branch badges, clean Git UI. Proof that developer tools can be beautiful Mac apps
- **Finder, Apple Mail, Apple Notes, Safari** — the first-party references for sidebar patterns, context menus, multi-window, and keyboard shortcuts

### App Store veterans

The sandbox readiness, codesigning, and entitlement guidance in this agent comes from the collective wisdom of indie developers who shipped non-sandboxed apps first and learned the hard way:

- Security-scoped bookmarks instead of path strings (the #1 source of rework)
- Inside-out codesigning (never `codesign --deep`)
- The one-shot sandbox migration (`com.apple.security.app-sandbox.migration`)
- Temporary exception entitlements that pass 15 times then get rejected on update 16
- `CFBundleVersion` that must strictly increment (both Sparkle and App Store Connect)
- The quarantine xattr that silently breaks App Store Connect uploads

This wisdom is spread across blog posts, conference talks, and Twitter/Mastodon threads from developers like **Daniel Jalkut** (Red Sweater, MarsEdit), **Brent Simmons** (NetNewsWire), **Jeff Johnson** (Underpass), **Drew McCormack** (Ensembles), and countless others who've navigated App Review.

## Contributing

Found something we missed? A HIG rule that should be checked? An indie Mac dev convention we overlooked? A credit we should add?

Open an issue or PR. This agent gets better when more Mac developers contribute their hard-won opinions.

## License

MIT. Use it, fork it, adapt it for your team's conventions.

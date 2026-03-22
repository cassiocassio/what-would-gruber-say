# What Would Gruber Say?

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) agent that reviews your macOS app for HIG compliance, native feel, and the small details that matter.

## What "Mac-assed" means

John Gruber [coined the term](https://daringfireball.net/linked/2020/03/20/mac-assed-mac-apps) in 2020, borrowing from Brent Simmons: apps that are "unapologetically Mac apps — platform-specific and not trying to wow us with all their custom not-Mac-like UI." Some examples from Daring Fireball:

- **SoundSource** (Rogue Amoeba) — Gruber called it "[a hall-of-fame caliber example of a Mac-assed Mac app](https://daringfireball.net/linked/2020/08/09/soundsource-5)" and "the system-wide audio menu item that ought to be built into macOS"
- **Nova** (Panic) — "[an extremely Mac-app Mac app](https://daringfireball.net/2020/11/sketch_mac_app_mac_apps)." Gruber preferred Panic's phrasing to his own
- **Fantastical** — "[truly a Mac-assed Mac app](https://daringfireball.net/linked/2020/12/03/fantastical-mac)." Later noted it's one of the rare Mac-first apps that [successfully ported to Windows](https://daringfireball.net/linked/2024/11/01/fantastical-for-windows)
- **Sonar** — "[my favorite new Mac app of the year](https://daringfireball.net/linked/2024/02/25/sonar)." A brand-new app for GitHub/GitLab issues that's "totally Mac-assed"
- **Sketch** — worth "[embracing and celebrating](https://daringfireball.net/2020/11/sketch_mac_app_mac_apps)" — you can start using it instantly because it follows Mac conventions

And the counterexample: Gruber called Electron "[without question a scourge](https://daringfireball.net/2018/12/electron_and_the_decline_of_native_apps)" and noted that Slack is "[emphatically not a Mac-assed Mac app](https://daringfireball.net/linked/2020/03/20/mac-assed-mac-apps)." On what makes an app feel right on the Mac: "[ultimately, you know it when you see it](https://daringfireball.net/linked/2025/04/02/apps-feel-right-mac-watts-martin)."

Apple itself isn't exempt. Gruber called macOS Tahoe's utility app icons "[a folder full of dead canaries](https://daringfireball.net/2025/08/macos_26_tahoes_dead_canary_utility_app_icons)," wrote that the trend of [icons in every menu item](https://daringfireball.net/linked/2026/01/06/nielsen-icons-in-menus) is the reason he won't upgrade to Tahoe, and flagged the disappearance of [toolbar text labels](https://daringfireball.net/linked/2019/05/23/mac-toolbar-labels) as an accessibility problem. Being Mac-assed means following the platform's best instincts, not necessarily its latest ones.

This agent tries to make that instinct checkable.

## What it checks

- **HIG compliance** — toolbar zones, menu bar completeness, reserved shortcuts, SF Symbols, context menus
- **Native feel** — vibrancy, system accent colour, disclosure triangles, animations with reduce-motion guards
- **Keyboard shortcuts** — modifier hierarchy, reserved system shortcuts, native vs web layer split
- **Accessibility** — VoiceOver, Dynamic Type, high contrast, reduced motion, keyboard-only navigation
- **App Store readiness** — security-scoped bookmarks, sandbox file access, codesigning, entitlements
- **Usability** — learnability, efficiency, error prevention, cognitive load
- **Hybrid apps** — WKWebView bridge security, native/web coordination

## Usage

Copy the agent into your project:

```bash
mkdir -p .claude/agents
curl -o .claude/agents/mac-ux-review.md \
  https://raw.githubusercontent.com/cassiocassio/what-would-gruber-say/main/.claude/agents/mac-ux-review.md
```

Then ask it to review your code:

```
@mac-ux-review ContentView.swift
```

## What it doesn't do

This is a macOS reviewer. It doesn't cover iOS, visionOS, web-only apps, or cross-platform frameworks. It doesn't know your design system — that's yours.

## Credits

This agent draws on the [macOS Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/), [SF Symbols](https://developer.apple.com/sf-symbols/), and Mario Guzman's toolbar layout guidelines.

### Writers

- **[John Gruber](https://daringfireball.net/)** — coined "[Mac-assed Mac apps](https://daringfireball.net/linked/2020/03/20/mac-assed-mac-apps)," has written about what makes Mac software feel right for twenty years. Called Electron "[without question a scourge](https://daringfireball.net/2018/12/electron_and_the_decline_of_native_apps)." On what makes an app feel right on the Mac: "[ultimately, you know it when you see it](https://daringfireball.net/linked/2025/04/02/apps-feel-right-mac-watts-martin)"
- **[John Siracusa](https://hypercritical.co/)** — ATP co-host, wrote the long-form macOS reviews at Ars Technica
- **[Marco Arment](https://marco.org/)** — Overcast, ATP co-host, writes about indie Mac/iOS development trade-offs
- **[Craig Hockenberry](https://furbo.org/)** — Iconfactory (Twitterrific, xScope)
- **[Brent Simmons](https://inessential.com/)** — NetNewsWire, which Gruber called a [Mac-assed Mac app](https://daringfireball.net/linked/2020/03/20/mac-assed-mac-apps)

### Apps Gruber has praised as "Mac-assed Mac apps"

These are apps Gruber has specifically cited on Daring Fireball:

- **[Fantastical](https://flexibits.com/fantastical)** — "[truly a Mac-assed Mac app](https://daringfireball.net/linked/2020/12/03/fantastical-mac)"
- **[Nova](https://nova.app/)** (Panic) — "[an extremely Mac-app Mac app](https://daringfireball.net/2020/11/sketch_mac_app_mac_apps)"
- **[Sketch](https://www.sketch.com/)** — worth "[embracing and celebrating](https://daringfireball.net/2020/11/sketch_mac_app_mac_apps)" as a native Mac app
- **[NetNewsWire](https://netnewswire.com/)** (Brent Simmons) — "[a Mac-assed Mac app, and it's a point of pride](https://daringfireball.net/linked/2020/03/20/mac-assed-mac-apps)"
- **[Sonar](https://www.sonarsoftware.dev/)** — "[my favorite new Mac app of the year](https://daringfireball.net/linked/2024/02/25/sonar)"
- **[SoundSource](https://rogueamoeba.com/soundsource/)** (Rogue Amoeba) — "[a hall-of-fame caliber example of a Mac-assed Mac app](https://daringfireball.net/linked/2020/08/09/soundsource-5)"
- **[MarsEdit](https://redsweater.com/marsedit/)** (Daniel Jalkut) — cited as a canonical example
- **[BBEdit](https://www.barebones.com/products/bbedit/)** (Bare Bones Software) — "It doesn't suck." Gruber: "[I haven't made a single dollar in my adult life that didn't involve BBEdit](https://www.barebones.com/products/bbedit/testimonials20.php)"
- **[Proxyman](https://proxyman.io/)** — a Mac-native alternative to Charles/Wireshark
- **[Nisus Writer](https://nisus.com/)** — Mac-only word processor since 1989

### Other apps referenced for specific patterns

Good Mac apps we reference for specific conventions, though not necessarily cited by Gruber:

- **[Things 3](https://culturedcode.com/things/)** — spring animations, spacing
- **[Bear](https://bear.app/)** — sidebar conventions, section headers
- **[Tower](https://www.git-tower.com/)** — badge restraint (grey pill for status, red only for "needs attention")
- **[Reeder](https://reederapp.com/)** — restraint (no unread counts)
- **[Transmit](https://panic.com/transmit/)** (Panic) — native feel
- **[Rogue Amoeba](https://rogueamoeba.com/)** apps (Audio Hijack, Loopback, Piezo, Airfoil) — audio utilities done right
- **Finder, Mail, Notes, Safari** — first-party references for sidebar, context menus, multi-window, shortcuts

### The cautionary tale

Gruber on **1Password 8** moving from native to Electron: the decisions "[make perfect sense for the enterprise SaaS world](https://daringfireball.net/2022/01/1password_follow-up)" but "[it might not be feasible to move to the new model without spoiling what many 1Password users liked best](https://daringfireball.net/2022/01/1password_follow-up)."

### App Store wisdom

Sandbox, codesigning, and entitlement guidance from indie developers who shipped non-sandboxed first — including [Daniel Jalkut](https://red-sweater.com/) (MarsEdit), [Brent Simmons](https://inessential.com/) (NetNewsWire), and others who've written about navigating App Review.

## Contributing

Found a HIG rule we missed, or a convention we got wrong? Open an issue or PR.

## License

MIT

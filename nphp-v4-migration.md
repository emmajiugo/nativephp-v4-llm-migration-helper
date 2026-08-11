# NativePHP v4 / EDGE Components — LLM Pointer

> Index of NativePHP Mobile v4 EDGE component documentation, in the style of
> `llms.txt`. Fetch only the component you need instead of crawling the docs site.
> Every link below points at **raw markdown** — directly readable by an LLM or
> `WebFetch`, no HTML scraping.

## How to use this file

Look up the `<native:*>` tag in the index, fetch that one raw URL, read it, done.

URL patterns, if you need to construct one yourself:

- Raw markdown (prefer this): `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/<slug>.md`
- Human-readable docs: `https://nativephp.com/docs/mobile/4/edge-components/<slug>`

Read [`introduction.md`](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/introduction.md)
first if you have no context on EDGE at all, then
[`layout.md`](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/layout.md)
for the Tailwind-style styling and layout rules that apply across every component.

## Required packages

Components are split across **two** packages. A doc page alone is not proof a
component is available — confirm which package provides it, and that the package
is installed.

| Package | Provides |
|---|---|
| `nativephp/mobile` | Core EDGE elements: layout, navigation & chrome, text, icons, drawing |
| `nativephp/mobile-ui` | Richer UI: lists, modals, form controls, badges, chips, tabs, webview |

`mobile-ui` is under active development and tags ship frequently — **always check
the latest tag rather than trusting a version pinned in this document**:

```bash
# mobile-ui — public repo, tags newest first
curl -s https://api.github.com/repos/NativePHP/mobile-ui/tags \
  | grep '"name"' | head -5

# core mobile — NOT a public GitHub repo; ask composer instead
composer show nativephp/mobile --all | grep versions

# core mobile release source (public mirror used by super-native)
curl -s https://api.github.com/repos/NativePHP/mobile-air/tags \
  | grep '"name"' | head -5
```

Install it if it isn't already present:

```bash
composer show nativephp/mobile-ui >/dev/null 2>&1 \
  && echo "installed" \
  || composer require nativephp/mobile-ui
```

Every `0.x` tag so far requires only `nativephp/mobile` `^4.0`, so `mobile-ui`
does not drag in a bleeding-edge core. Confirm for the tag you pick:

```bash
curl -s https://raw.githubusercontent.com/NativePHP/mobile-ui/<tag>/composer.json \
  | grep -A4 '"require"'
```

**Install trap:** the `plugins.nativephp.com` composer repository lags behind the
GitHub tags — it has been observed indexing `0.3.0` while `0.4.0` was already
tagged. Compare the two, and add a VCS repository only if the version you need is
missing from composer:

```bash
composer clear-cache && composer show nativephp/mobile-ui --all | grep versions
```

```json
{ "type": "vcs", "url": "https://github.com/NativePHP/mobile-ui" }
```

### Which package provides which component

> **Snapshot, not a contract.** The lists below were taken from
> `nativephp/mobile` 4.1.0 and `nativephp/mobile-ui` 0.4.0. Both packages gain
> elements with each tag, so treat these as "at least these exist" and re-derive
> from your own install (commands at the end of this section).

With both packages installed, **58** element tags resolve. Which package actually
wins for each tag is determined by `mobile-ui`'s manifest, not by which package
happens to ship a class file — so read this by tag, not by filename.

Served by **core** `nativephp/mobile` (27):
`bottom_nav`, `bottom_nav_item`, `canvas`, `circle`, `column`, `divider`, `fab`,
`gesture_area`, `icon`, `image`, `lazy_grid`, `line`, `pressable`, `rect`,
`refreshable`, `row`, `scroll_view`, `side_nav`, `side_nav_group`,
`side_nav_header`, `side_nav_item`, `spacer`, `stack`, `text`, `top_bar`,
`top_bar_action`, `top_bar_title`.

Served by **`nativephp/mobile-ui`** (31):
`accordion`, `accordion_content`, `accordion_header`, `activity_indicator`,
`badge`, `bare_text_input`, `bottom_sheet`, `button`, `button_group`, `carousel`,
`checkbox`, `chip`, `date_picker`, `filled_text_input`, `floating_overlay`,
`list`, `list_item`, `list_section`, `modal`, `native_drawer`,
`outlined_text_input`, `progress_bar`, `radio`, `radio_group`, `select`,
`slider`, `tab`, `tab_row`, `toggle`, `virtual_list`, `webview`.

So these documented components need `mobile-ui` and will not render on a
core-only install: `accordion`, `badge`, `button-group`, `carousel`, `checkbox`,
`chip`, `list`, `modal`, `progress-bar`, `radio-group`, `select`, `slider`,
`tab-row`, `text-input` (all three variants), `toggle`, `virtual-list`,
`webview`. Shipped but undocumented at the time of writing: `date-picker`,
`native-drawer`, `floating-overlay`.

**Installing `mobile-ui` silently replaces four core tags.** `button`, `toggle`,
`activity_indicator` and `bottom_sheet` stop resolving to
`Native\Mobile\Edge\Elements\*` and start resolving to
`Native\Mobile\UI\Elements\*`. Behaviour and supported attributes can differ, so
re-check those four against the docs after installing.

Watch out for two traps in this area:

- **Shipping a class file does not mean serving the tag.** `mobile-ui` ships
  `src/Elements/Icon.php`, but its manifest registers `icon` to the *core*
  `Native\Mobile\Edge\Elements\Icon`. Only the registry is authoritative.
- **Class name ≠ tag name.** `NativeList` serves `list`, `NativeVirtualList`
  serves `virtual_list`. Tags are snake_case in the registry and kebab-case in
  Blade (`<native:virtual-list>`).

**Ground truth for an install** — dump the registry, which resolves overrides and
tag names correctly where a directory listing does not:

```bash
php -r '
require "vendor/autoload.php";
$app = require "bootstrap/app.php";
$app->make(Illuminate\Contracts\Console\Kernel::class)->bootstrap();
$all = Native\Mobile\Edge\ElementRegistry::all();
ksort($all);
foreach ($all as $tag => $cls) printf("%-22s %s\n", $tag, $cls);
echo count($all), " tags registered\n";
'
```

To check what a tag ships *before* installing it:

```bash
curl -s "https://api.github.com/repos/NativePHP/mobile-ui/git/trees/<tag>?recursive=1" \
  | grep -oE 'src/Elements/[A-Za-z]+\.php'
```

The authoritative tag→component mapping is each package's manifest, which lists
every registered component including overrides:

```bash
curl -s "https://raw.githubusercontent.com/NativePHP/mobile-ui/<tag>/nativephp.json"
```

The docs site tracks `nativephp/mobile` **dev-main**, so a page may describe a
component or attribute that no tagged release has yet. The reference app
`super-native` pins `dev-main` from the `NativePHP/mobile-air` VCS repo for the
same reason — check its `composer.json` for what it currently expects.

## Component index

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/`

### Concepts

| Doc | Covers |
|---|---|
| [introduction.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/introduction.md) | What EDGE is, how native tags are compiled |
| [layout.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/layout.md) | Layout & styling — Tailwind-style classes, sizing, spacing |

### Structure & layout

| Tags | Doc |
|---|---|
| `column` | [column.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/column.md) |
| `row` | [row.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/row.md) |
| `stack` | [stack.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/stack.md) |
| `spacer` | [spacer.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/spacer.md) |
| `divider`, `horizontal-divider` | [divider.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/divider.md) |
| `scroll-view` | [scroll-view.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/scroll-view.md) |
| `lazy-grid` | [lazy-grid.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/lazy-grid.md) |
| `refreshable` | [refreshable.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/refreshable.md) |

### Navigation & chrome

| Tags | Doc |
|---|---|
| `bottom-nav`, `bottom-nav-item` | [bottom-nav.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/bottom-nav.md) |
| `top-bar`, `top-bar-action` | [top-bar.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/top-bar.md) |
| `side-nav`, `side-nav-group`, `side-nav-header`, `side-nav-item` | [side-nav.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/side-nav.md) |
| `tab-row`, `tab` | [tab-row.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/tab-row.md) |
| (context menus — uses `list-item`, `top-bar`, `pressable`) | [menus.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/menus.md) |

### Content & typography

| Tags | Doc |
|---|---|
| `text` | [text.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/text.md) |
| `icon` | [icon.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/icon.md) |
| `image` | [image.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/image.md) |
| `badge` | [badge.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/badge.md) |
| `chip` | [chip.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/chip.md) |
| `list`, `list-item`, `list-section` | [list.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/list.md) |
| `virtual-list` | [virtual-list.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/virtual-list.md) |
| `carousel` | [carousel.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/carousel.md) |
| `accordion`, `accordion-header`, `accordion-content` | [accordion.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/accordion.md) |
| `webview` | [web-view.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/web-view.md) |

### Input & controls

| Tags | Doc |
|---|---|
| `button` | [button.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/button.md) |
| `button-group` | [button-group.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/button-group.md) |
| `fab` | [fab.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/fab.md) |
| `pressable` | [pressable.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/pressable.md) |
| `gesture-area` | [gesture-area.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/gesture-area.md) |
| `filled-text-input`, `outlined-text-input`, `bare-text-input`, `bottom-bar` | [text-input.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/text-input.md) |
| `checkbox` | [checkbox.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/checkbox.md) |
| `radio-group`, `radio` | [radio-group.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/radio-group.md) |
| `toggle` | [toggle.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/toggle.md) |
| `select` | [select.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/select.md) |
| `slider` | [slider.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/slider.md) |

### Overlays & feedback

| Tags | Doc |
|---|---|
| `modal` | [modal.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/modal.md) |
| `bottom-sheet` | [bottom-sheet.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/bottom-sheet.md) |
| `activity-indicator` | [activity-indicator.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/activity-indicator.md) |
| `progress-bar` | [progress-bar.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/progress-bar.md) |

### Drawing

| Tags | Doc |
|---|---|
| `canvas` | [canvas.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/canvas.md) |
| `circle`, `line`, `rect` | [shapes.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/shapes.md) |

## Testing native screens

v4 ships a testing API for native screens — `vendor/nativephp/mobile/src/Testing/`
(`Native.php`, `TestableComponent.php`, `FakeBridge.php`, `PestExpectations.php`,
`TreeSpy.php`, `TestDumpHandler.php`). Confirmed present in **4.1.0**, so this is
usable today, not dev-main only.

This matters because ordinary Pest feature tests do **not** exercise native
screens at all: `Route::native` returns a 200 stub under `runningUnitTests()`
(`NativeServiceProvider.php:327-333`), so a broken layout or a missing builder
method passes lint and the suite and fails only on device. Use these helpers to
close that gap.

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/`

| Doc | Covers |
|---|---|
| [introduction.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/introduction.md) | `Native::test()`, `Native::visit()`, `Native::fakeBridge()`, `assertSee`, `assertSet` |
| [interactions.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/interactions.md) | Pressing elements, `assertNativeCalled`, `assertWentBack` |
| [navigation.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/navigation.md) | Flows and chrome — `assertScreen`, `assertNavigatedTo`, `assertHasTabBar`, `assertHasTab`, `assertNavTitle`, `assertMissingElement` |
| [native-events.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/native-events.md) | Bridge events — `assertNativeCalledTimes`, `assertNativeCallOrder`, `assertAwaitingNativeEvent` |
| [accessibility.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/accessibility.md) | `assertAccessible`, `NativeRouter::registeredRoutes()`, `PestExpectations::register()` |
| [advanced.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/advanced.md) | `assertElement`, `assertMatchesSnapshot`, render counts (`assertRenderCount`, `assertNotRerendered`), `assertCopied` |

Verified to exist on `Native` in 4.1.0: `test()`, `visit()`, `fakeBridge()`. On
`TestableComponent`: `assertHasTabBar`, `assertHasTab`, `assertScreen`,
`assertNavigatedTo`, `assertNavTitle`, `assertSee`, `assertSet`, `assertElement`,
`assertMissingElement`, `assertNativeCalled`, `assertAccessible`,
`assertMatchesSnapshot`, `assertWentBack`.

Check any assertion before relying on it, since the docs track dev-main:

```bash
php -r 'require "vendor/autoload.php";
  var_dump(method_exists("Native\Mobile\Testing\TestableComponent", "assertHasTab"));'
```

Highest-value coverage for a shell migration: `assertHasTabBar` / `assertHasTab`
to pin the tab config, and `assertNavigatedTo` to prove a tab tap replaces to the
right native route rather than exiting to the web view.

## Reference app — `NativePHP/super-native`

Kitchen-sink app. Best source for *how components compose* in real screens,
which the per-component docs don't show. Raw file base:
`https://raw.githubusercontent.com/NativePHP/super-native/main/`

Native screens live in `app/NativeComponents/`. The topic-organised demos:

| File | Topic |
|---|---|
| `app/NativeComponents/ExploreLayout.php` | layout & styling |
| `app/NativeComponents/ExploreTypography.php` | text |
| `app/NativeComponents/ExploreButtons.php` | buttons, pressables |
| `app/NativeComponents/ExploreForms.php` | inputs, checkboxes, toggles |
| `app/NativeComponents/ExplorePickers.php` | select, slider, radio |
| `app/NativeComponents/ExploreSheets.php` | modals, bottom sheets |
| `app/NativeComponents/ExploreMenus.php` | menus |
| `app/NativeComponents/ExploreIcons.php` | icons |
| `app/NativeComponents/ExploreCards.php` | composed card layouts |

Browse the full tree:

```bash
curl -s "https://api.github.com/repos/NativePHP/super-native/git/trees/main?recursive=1" \
  | grep -o '"path": *"[^"]*"'
```

Caveat: super-native runs dev-main, so it may use components or APIs absent from
4.1.0. Cross-check against the installed `Elements/` directory.

## Breaking change: EDGE chrome no longer works from a webview Blade layout

The v4 upgrade guide states that no application code changes are required. **That
is not true for any app that rendered EDGE chrome — top bar, bottom nav or side
nav — from its webview Blade layout.**

v4 **removed webview-mode native chrome entirely.** Verified three ways:

1. v3's response-time flush middleware `RenderEdgeComponents` (which called
   `Edge::set()`) no longer exists — v4 ships only `HonorsRequestedNativeScreen`.
2. `Edge.Set` is registered in neither platform bridge — zero matches in
   `BridgeFunctionRegistration.kt` and `.swift`.
3. `<native:*>` tags do not compile outside a native-screen render.
   `NativeTagPrecompiler` no-ops unless `setActive(true)`, which only
   `NativeComponent::renderBladeBoundToSelf()` sets. Confirmed by compiling
   `<native:bottom-nav>` via `Blade::compileString()` — it came back as literal
   markup.

Both platform sources state it plainly: *"WebView-mode chrome (the Edge-bridge
top bar / bottom nav / side nav) is gone — native chrome now comes exclusively
from the element-collector path (NativeRootStack / NativeRootTabs)."*

### What breaks in a webview-only app

An app whose `start_url` points at a normal web route, with no `Route::native`
screens, will hit all three of these:

| Symptom | Cause |
|---|---|
| `Class "Native\Mobile\Edge\Edge" not found` on render | `Edge::clear()` / `Edge::set()` were deleted in v4. Any Blade calling them throws. |
| Native chrome silently disappears | `<native:*>` tags in a webview layout are no longer compiled — they emit as raw unknown HTML. |
| Blocking XHR that 404s on every page | JS `Edge.clearSync()` / `Edge.setSync()` still ship in `native.d.ts`, but the `Edge.Set` bridge method is unregistered, so `/_native/api/call` returns `METHOD_NOT_FOUND`. A `try/catch` usually swallows it. |

Find every affected site:

```bash
grep -rn 'Native\\Mobile\\Edge\|Edge::' resources/ app/ routes/ config/
grep -rn '<native:' resources/views/
grep -rn 'clearSync\|setSync\|Edge' resources/js/
```

Note the third symptom is the easiest to miss: it is not a crash, just a
synchronous main-thread request failing on every navigation.

### Migration path

Restoring chrome means moving to native screens (`Route::native` +
`NativeComponent`) — not editing the Blade layout. There is no v4 API to set
chrome from a webview render.

A staged migration is possible because `mobile-ui` ships `Webview`
(`src/Elements/Webview.php`): a native shell screen owns the chrome and hosts the
existing web app inside `<native:webview>`, so views move to native one at a time
rather than in a big bang.

Rough shape — verify against
[`web-view.md`](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/web-view.md)
and `super-native` before building:

1. Install `nativephp/mobile-ui` (see **Required packages**).
2. Add a `NativeComponent` shell screen holding the chrome (e.g.
   `<native:bottom-nav>`) plus `<native:webview>` pointed at the web app.
3. Register it with `Route::native(...)` and point `NATIVEPHP_START_URL` at it —
   `config/nativephp.php` `start_url` defaults to `'/'`.
4. Remove the dead EDGE calls found by the greps above. With chrome living in the
   shell, there is nothing to clear per-page.
5. Migrate views to native screens incrementally.

Steps 2-3 are reconstructed from the docs and `super-native`, not from a verified
build — treat them as a starting point and confirm on device.

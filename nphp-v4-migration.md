# NativePHP v4 / EDGE Components — LLM Pointer

> Index of NativePHP Mobile v4 EDGE component documentation, in the style of
> `llms.txt`. Fetch only the component you need instead of crawling the docs site.
> Documentation and individual source-file links use **raw content** whenever
> possible, so an LLM or `WebFetch` can read them without HTML scraping.

## How to use this file

Use the smallest relevant reference set, then follow it to the implementation:

1. Fetch only the doc page for the API, screen behavior, or architecture concern.
2. If the index offers a SuperNative example, fetch its `NativeComponent` PHP
   file **and** its paired `resources/views/native/*.blade.php` view.
3. Follow imports, layouts, child components, and Blade includes only when the
   fetched file calls them and they apply to the migration at hand.
4. Stop once the required behavior is understood. Do not crawl all docs or copy
   an entire SuperNative design for an unrelated feature.

The PHP component contains state, actions, routing, and data setup. Its native
Blade view contains the EDGE tree, styling, and composition. Read both before
using an example as a design or implementation reference.

For a migration concern that is not an EDGE element, use the indexes below the
component index. They link to the source documentation and, where available,
the matching SuperNative `NativeComponent` implementation.

URL patterns, if you need to construct one yourself:

- Raw markdown (prefer this): `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/<slug>.md`
- Human-readable docs: `https://nativephp.com/docs/mobile/4/edge-components/<slug>`

Read [`introduction.md`](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/introduction.md)
first if you have no context on EDGE at all, then
[`layout.md`](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/layout.md)
for the Tailwind-style styling and layout rules that apply across every component.

## Native screen fundamentals

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/`

| Doc | Covers | SuperNative implementation |
|---|---|---|
| [overview.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/overview.md) | NativePHP Mobile overview | [Home.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Home.php) |
| [native-ui.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/native-ui.md) | Creating native screens | [DemoLauncher.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/DemoLauncher.php) |
| [routing.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/routing.md) | `Route::native`, navigation, route parameters | [Browse.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Browse.php) |
| [layouts.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/layouts.md) | Native layouts, stacks, tabs and shared chrome | [Home.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Home.php) |
| [nested-components.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/nested-components.md) | Composing native components | [EdgeChildTest.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/EdgeChildTest.php) |
| [events.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/events.md) | Native event channels | [EventChannelTest.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/EventChannelTest.php) |
| [native-functions.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/native-functions.md) | Calling device functions from PHP | [Demo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Demo.php) |
| [positioning.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/positioning.md) | Absolute and overlay positioning | [ExploreLayout.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreLayout.php) |
| [safe-area.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/safe-area.md) | System-safe insets | [ExploreLayout.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreLayout.php) |
| [device.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/device.md) | Device information and platform checks | -- |
| [dialogs.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/dialogs.md) | Native alerts, confirms and prompts | -- |
| [file.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/file.md) | File-system access | -- |
| [jump.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/jump.md) | Opening URLs and external apps | -- |
| [assets.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/assets.md) | Bundled assets | -- |
| [app-icon.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/app-icon.md) | Application icon | -- |
| [splash-screens.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/splash-screens.md) | Splash screen configuration | -- |
| [system.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/system.md) | System UI and device integration | -- |

## Native screen behavior and app services

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/`

| Doc | Covers | SuperNative implementation |
|---|---|---|
| [data-binding.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/data-binding.md) | Binding form controls to component state | [Counter.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Counter.php) |
| [reactivity.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/reactivity.md) | Updating native trees from state changes | [ReactivityDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ReactivityDemo.php) |
| [gestures.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/gestures.md) | Gesture recognition | [GestureDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/GestureDemo.php) |
| [search.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/search.md) | Native search | [InstagramSearch.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/InstagramSearch.php) |
| [accessibility.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/accessibility.md) | Accessibility semantics and testing | -- |
| [authentication.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/authentication.md) | Authentication on-device | -- |
| [databases.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/databases.md) | Local database configuration and sync | -- |
| [deep-links.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/deep-links.md) | Deep-link routing | -- |
| [lifecycle-hooks.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/lifecycle-hooks.md) | Application and screen lifecycle | -- |
| [push-notifications.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/push-notifications.md) | Push permission, tokens and handlers | -- |
| [queues.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/queues.md) | On-device queue workers | -- |
| [security.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/security.md) | Secure storage and application hardening | -- |
| [theming.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/theming.md) | App and native-element themes | [Demo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Demo.php) |
| [websockets.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/websockets.md) | WebSocket connections and events | -- |

## Rendering architecture

Read these before changing rendering, performance, or app-lifecycle behavior.
They explain why a NativeComponent is not a webview Blade response, and why
native UI updates must remain small and deterministic.

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/`

| Doc | Covers | SuperNative implementation |
|---|---|---|
| [about-the-new-architecture.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/about-the-new-architecture.md) | v4 architecture and terminology | [DemoLauncher.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/DemoLauncher.php) |
| [render-publish-mount.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/render-publish-mount.md) | Render, publish and mount lifecycle | [Counter.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Counter.php) |
| [renderer.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/renderer.md) | PHP-to-native rendering pipeline | [Demo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Demo.php) |
| [subtree-reuse.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/subtree-reuse.md) | Stable identity and efficient subtree updates | [ReactivityDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ReactivityDemo.php) |
| [threading-model.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/threading-model.md) | PHP and native-thread execution model | [EventChannelTest.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/EventChannelTest.php) |
| [embedded-php.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/embedded-php.md) | Embedded Laravel/PHP runtime | -- |
| [cross-platform-implementation.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/cross-platform-implementation.md) | Android and iOS implementation differences | -- |
| [glossary.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/glossary.md) | Architecture vocabulary | -- |
| [super-native.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/architecture/super-native.md) | Reference-app architecture | [SuperNative source](https://github.com/NativePHP/super-native/tree/main/app/NativeComponents) |

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

SuperNative is the primary source for real native-screen composition. When using
it as a reference, fetch the matched pair in the tables below: the PHP component
and its native Blade view. Do not use a PHP class alone to recreate a screen.

Source bases:

- Components: `https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/`
- Native views: `https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/`

### Component demos

| Topic | NativeComponent | Native Blade view |
|---|---|---|
| Animation | [Animate.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Animate.php) | [animate.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/animate.blade.php) |
| Routing and navigation | [Browse.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Browse.php) | [browse.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/browse.blade.php) |
| Buttons and form actions | [ButtonsForm.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ButtonsForm.php) | [buttons-form.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/buttons-form.blade.php) |
| Checkbox | [Checkbox.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Checkbox.php) | [checkbox.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/checkbox.blade.php) |
| State and data binding | [Counter.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Counter.php) | [counter.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/counter.blade.php) |
| General element demo | [Demo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Demo.php) | [demo.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/demo.blade.php) |
| Demo navigation | [DemoLauncher.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/DemoLauncher.php) | [demo-launcher.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/demo-launcher.blade.php) |
| Native event channels | [EventChannelTest.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/EventChannelTest.php) | [event-channel-test.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/event-channel-test.blade.php) |
| Component catalogue | [Explore.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Explore.php) | [explore.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore.blade.php) |
| Buttons and pressables | [ExploreButtons.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreButtons.php) | [explore/buttons.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore/buttons.blade.php) |
| Composed cards | [ExploreCards.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreCards.php) | [explore/cards.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore/cards.blade.php) |
| Text inputs, checkboxes and toggles | [ExploreForms.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreForms.php) | [explore/forms.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore/forms.blade.php) |
| Icons | [ExploreIcons.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreIcons.php) | [explore-icons.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore-icons.blade.php) |
| Layout and styling | [ExploreLayout.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreLayout.php) | [explore/layout.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore/layout.blade.php) |
| Context menus | [ExploreMenus.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreMenus.php) | [explore/menus.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore/menus.blade.php) |
| Select, slider and radio | [ExplorePickers.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExplorePickers.php) | [explore/pickers.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore/pickers.blade.php) |
| Modal and bottom sheet | [ExploreSheets.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreSheets.php) | [explore/sheets.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore/sheets.blade.php) |
| Typography | [ExploreTypography.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ExploreTypography.php) | [explore/typography.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/explore/typography.blade.php) |
| Game controls | [GamePad.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/GamePad.php) | [game-pad.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/game-pad.blade.php) |
| Gestures | [GestureDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/GestureDemo.php) | [gesture-demo.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/gesture-demo.blade.php) |
| Glass effect | [Glass.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Glass.php) | [glass.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/glass.blade.php) |
| App home | [Home.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Home.php) | [home.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/home.blade.php) |
| List detail | [ItemDetail.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ItemDetail.php) | [item-detail.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/item-detail.blade.php) |
| Listing detail | [ListingDetail.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ListingDetail.php) | [listing-detail.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/listing-detail.blade.php) |
| Mail-style UI | [MailDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/MailDemo.php) | [mail-demo.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/mail-demo.blade.php) |
| Animated state | [NumberSwitcherDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/NumberSwitcherDemo.php) | [number-switcher.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/number-switcher.blade.php) |
| Profile | [Profile.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Profile.php) | [profile.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/profile.blade.php) |
| Reactivity | [ReactivityDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ReactivityDemo.php) | [reactivity-demo.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/reactivity-demo.blade.php), [placeholder](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/reactivity-demo-placeholder.blade.php) |
| Pull to refresh | [RefreshableDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/RefreshableDemo.php) | [refreshable-demo.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/refreshable-demo.blade.php) |
| Stack positioning | [StackPositioningDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/StackPositioningDemo.php) | [stack-positioning-demo.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/stack-positioning-demo.blade.php) |
| Theming | [ThemeLab.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ThemeLab.php) | [theme-lab.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/theme-lab.blade.php) |
| Transitions | [TransitionsDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/TransitionsDemo.php) | [transitions/index.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/transitions/index.blade.php) |
| Transition detail | [TransitionDetail.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/TransitionDetail.php) | [transitions/detail.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/transitions/detail.blade.php) |
| Embedded webview | [WebviewDemo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/WebviewDemo.php) | [webview-demo.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/webview-demo.blade.php) |

### Complete design references

These are complete multi-screen designs. Fetch the matching PHP class and Blade
view for each screen needed by the design; then follow the shared data trait only
if the migrated feature needs its fixture or interaction data.

| Design | NativeComponent | Native Blade view |
|---|---|---|
| Twitter | [TwitterFeed.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/TwitterFeed.php) | [twitter-feed.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/twitter-feed.blade.php) |
| Twitter | [TwitterProfile.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/TwitterProfile.php) | [twitter-profile.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/twitter-profile.blade.php) |
| Twitter | [TweetDetail.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/TweetDetail.php) | [tweet-detail.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/tweet-detail.blade.php) |
| Twitter | [ComposeTweet.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/ComposeTweet.php) | [compose-tweet.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/compose-tweet.blade.php) |
| Facebook | [FacebookFeed.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/FacebookFeed.php) | [facebook-feed.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/facebook-feed.blade.php) |
| Facebook | [FacebookPost.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/FacebookPost.php) | [facebook-post.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/facebook-post.blade.php) |
| Facebook | [FacebookProfile.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/FacebookProfile.php) | [facebook-profile.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/facebook-profile.blade.php) |
| Facebook | [FacebookCreate.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/FacebookCreate.php) | [facebook-create.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/facebook-create.blade.php) |
| Instagram | [InstagramFeed.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/InstagramFeed.php) | [instagram-feed.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/instagram-feed.blade.php) |
| Instagram | [InstagramPost.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/InstagramPost.php) | [instagram-post.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/instagram-post.blade.php) |
| Instagram | [InstagramProfile.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/InstagramProfile.php) | [instagram-profile.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/instagram-profile.blade.php) |
| Instagram | [InstagramSearch.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/InstagramSearch.php) | [instagram-search.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/instagram-search.blade.php) |
| Spotify | [SpotifyHome.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SpotifyHome.php) | [spotify-home.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/spotify-home.blade.php) |
| Spotify | [SpotifyPlaylist.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SpotifyPlaylist.php) | [spotify-playlist.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/spotify-playlist.blade.php) |
| Spotify | [SpotifyArtist.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SpotifyArtist.php) | [spotify-artist.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/spotify-artist.blade.php) |
| Spotify | [SpotifySearch.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SpotifySearch.php) | [spotify-search.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/spotify-search.blade.php) |
| YouTube | [YouTubeHome.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/YouTubeHome.php) | [youtube-home.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/youtube-home.blade.php) |
| YouTube | [YouTubeVideo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/YouTubeVideo.php) | [youtube-video.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/youtube-video.blade.php) |
| YouTube | [YouTubeChannel.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/YouTubeChannel.php) | [youtube-channel.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/youtube-channel.blade.php) |
| YouTube | [YouTubeSearch.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/YouTubeSearch.php) | [youtube-search.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/youtube-search.blade.php) |
| SyncUp | [SyncUpNativeChats.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SyncUpNative/SyncUpNativeChats.php) | [syncup/chats.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/syncup/chats.blade.php) |
| SyncUp | [SyncUpNativeFriends.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SyncUpNative/SyncUpNativeFriends.php) | [syncup/friends.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/syncup/friends.blade.php) |
| SyncUp | [SyncUpNativeProfile.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SyncUpNative/SyncUpNativeProfile.php) | [syncup/profile.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/syncup/profile.blade.php) |
| SyncUp | [SyncUpNativeLogin.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SyncUpNative/SyncUpNativeLogin.php) | [syncup/login.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/syncup/login.blade.php) |
| SyncUp | [SyncUpNativeChat.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SyncUpNative/SyncUpNativeChat.php) | [syncup-native/chat.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/syncup-native/chat.blade.php) |
| iHerb | [IHerbStore.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/IHerbStore.php) | No matching native Blade view on upstream `main` |
| iHerb | [IHerbCategory.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/IHerbCategory.php) | No matching native Blade view on upstream `main` |
| iHerb | [IHerbProduct.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/IHerbProduct.php) | No matching native Blade view on upstream `main` |
| iHerb | [IHerbCart.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/IHerbCart.php) | No matching native Blade view on upstream `main` |

### Layouts, partials, and upstream gaps

These layout classes build navigation or tab chrome directly and therefore do
not have Blade views: [NativeStackLayout.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Layouts/NativeStackLayout.php), [StackLayout.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Layouts/StackLayout.php), [TabsLayout.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Layouts/TabsLayout.php), and [SyncUpTabsLayout.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Layouts/SyncUpTabsLayout.php). SyncUp also uses [SyncUpNativeTabsLayout.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SyncUpNative/Layouts/SyncUpNativeTabsLayout.php).

The general demo composes [demo-nav.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/partials/demo-nav.blade.php), [card-header.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/partials/card-header.blade.php), and [status-dot.blade.php](https://raw.githubusercontent.com/NativePHP/super-native/main/resources/views/native/partials/status-dot.blade.php). Fetch those only after `demo.blade.php` shows they are relevant.

The following upstream components name views that are not present under
`resources/views/native/` on `main`: `DoomGame`, `EdgeChildTest`, `IHerbCart`,
`IHerbCategory`, `IHerbProduct`, `IHerbStore`, `JustifyRepro`, `TestLayout`, and
`Testing`. Do not infer or fabricate their Blade implementations. `EdgeChildTestCard`
returns an element directly and has no Blade view.

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

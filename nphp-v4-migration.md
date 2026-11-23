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

The `native:` tag prefix is optional: `<native:column>` and `<column>` compile to
the same element. The docs use the prefix; SuperNative views mostly drop it. Treat
both spellings as equivalent when you read examples or grep a codebase.

If your agent supports MCP, NativePHP hosts a docs server at
`https://nativephp.com/api/mcp/message` (no key needed). It exposes `search_docs`,
`get_page`, `list_edge_components`, `get_edge_component`, `search_plugins` and
`get_plugin`, so you can query the current docs instead of fetching raw files. See
[`mcp.md`](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/getting-started/mcp.md).

## Getting started and upgrading

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/getting-started/`

| Doc | Covers |
|---|---|
| [upgrade-guide.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/getting-started/upgrade-guide.md) | 3.x → 4.0 (PHP 8.4, core-merged plugins, opt-in Vite), plus 4.5 and 4.6 notes |
| [installation.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/getting-started/installation.md) | Installing core and registering `nativephp/mobile-ui` |
| [configuration.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/getting-started/configuration.md) | `config/nativephp.php` keys |
| [commands.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/getting-started/commands.md) | `native:*` Artisan commands |
| [environment-setup.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/getting-started/environment-setup.md) | Toolchain requirements |
| [development.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/getting-started/development.md) | `native:run`, `native:watch`, Jump |
| [versioning.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/getting-started/versioning.md) | Release and support policy |

The changelog page is rendered from `NativePHP/mobile-air` GitHub releases, so read
release notes from the API instead of the raw page:

```bash
curl -s https://api.github.com/repos/NativePHP/mobile-air/releases \
  | grep -E '"(tag_name|body)"' | head -20
```

Upgrade steps that do require changes, in addition to the EDGE chrome break
described at the end of this file:

- **4.0:** PHP 8.4 minimum. Remove `nativephp/mobile-device`, `-dialog`, `-file`
  and `-system` (`php artisan native:plugin:uninstall --core-v4`), because core
  now declares a Composer conflict with them. Vite no longer starts with
  `native:run`/`native:watch` unless you pass `--vite`. Run
  `php artisan native:install --force` after `composer update`.
- **4.5:** only a build packaged with `APP_ENV=production` can ship to the public
  store tracks. Any other value produces a testing-only build.
- **4.6:** translated iOS permission strings are written only for locales in the
  new `supported_locales` config key plus `app.locale`.
- **4.8:** `NativeLayout::usesNativeChrome()` now defaults to `true` (it was
  `false` through 4.7). A layout that never overrode it switches from the
  custom-drawn Column chrome to system `NavigationStack`/`TabView` on iOS and
  `NavHost`/`Scaffold` on Android. Return `false` to keep the old look, but the
  source marks that fallback as temporary. The upgrade guide does not mention
  this yet.
- **4.8:** after `native:install --force`, the native shell signs every event it
  posts to `/_native/api/events`. PHP then rejects unsigned posts, so your own
  JS that posts to that endpoint stops working. An app that updates only the
  Composer package keeps accepting unsigned events until it rebuilds.

## Native screen fundamentals

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/`

| Doc | Covers | SuperNative implementation |
|---|---|---|
| [overview.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/overview.md) | NativePHP Mobile overview | [Home.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Home.php) |
| [native-ui.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/native-ui.md) | Creating native screens | [DemoLauncher.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/DemoLauncher.php) |
| [routing.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/routing.md) | `Route::native`, navigation, route parameters | [Browse.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Browse.php) |
| [layouts.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/layouts.md) | Native layouts, stacks, tabs and shared chrome | [Home.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Home.php) |
| [middleware.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/middleware.md) | Route middleware (e.g. `auth`) on `Route::native` screens | -- |
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
| [async-tasks.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/async-tasks.md) | Running slow work off the UI thread | -- |
| [validation.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/validation.md) | `ValidatesInput` trait for screen state (since 4.7) | -- |
| [localization.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/digging-deeper/localization.md) | `supported_locales` and per-app language (since 4.6) | -- |
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

## Plugins

Device APIs other than Device, Dialog, File and System are plugins. Check that
each plugin the v3 app used has a v4-compatible release, and that it is
registered in `app/Providers/NativeServiceProvider.php`.

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/`

| Doc | Covers | SuperNative implementation |
|---|---|---|
| [using-plugins.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/using-plugins.md) | Installing and registering plugins | -- |
| [ui-components.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/ui-components.md) | Adding your own native element types | -- |
| [creating-plugins.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/creating-plugins.md), [bridge-functions.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/bridge-functions.md), [events.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/events.md), [lifecycle-hooks.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/lifecycle-hooks.md), [permissions-dependencies.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/permissions-dependencies.md), [advanced-configuration.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/advanced-configuration.md), [validation-testing.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/validation-testing.md), [best-practices.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/best-practices.md) | Writing or porting a plugin | -- |
| [core/biometrics.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/biometrics.md) | Biometric prompt | [Demo.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Demo.php) |
| [core/camera.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/camera.md) | Photo and video capture | [SyncUpNativeChat.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/SyncUpNative/SyncUpNativeChat.php) |
| [core/secure-storage.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/secure-storage.md) | Keychain/Keystore storage | [AuthenticatesWithVibe.php](https://raw.githubusercontent.com/NativePHP/super-native/main/app/NativeComponents/Concerns/AuthenticatesWithVibe.php) |
| `core/`: [browser](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/browser.md), [firebase](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/firebase.md), [geolocation](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/geolocation.md), [media-player](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/media-player.md), [microphone](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/microphone.md), [network](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/network.md), [scanner](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/scanner.md), [share](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/share.md), [vibe](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/plugins/core/vibe.md) | Other first-party plugins | -- |

## Publishing

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/publishing/`

[introduction.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/publishing/introduction.md)
(production vs. testing builds),
[android.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/publishing/android.md),
[ios.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/publishing/ios.md),
[bifrost.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/publishing/bifrost.md)
(cloud builds).

## Required packages

EDGE needs **both** packages. Core `nativephp/mobile` owns the rendering pipeline
and some PHP element classes. All SwiftUI and Compose **renderers**, including the
renderers for `text` and `column`, ship in `nativephp/mobile-ui`.

| Package | Provides |
|---|---|
| `nativephp/mobile` | Rendering pipeline, element registry, PHP classes for layout, text, icons, chrome and drawing |
| `nativephp/mobile-ui` | Native renderers for every element, plus the PHP classes for lists, modals, form controls, buttons, pager, webview and more |

`mobile-ui` is a plugin, so installing it is not enough. You must also register it:

```bash
composer require nativephp/mobile-ui
php artisan vendor:publish --tag=nativephp-plugins-provider
php artisan native:plugin:register nativephp/mobile-ui
php artisan native:plugin:list   # confirm NativeUIServiceProvider is listed
```

If it is missing or unregistered, `<native:button>`, `<native:list-item>` and
the other plugin-only tags throw `Unknown native element type`. Core-class tags
such as `<native:column>` and `<native:text>` still compile, but they **draw
nothing on the device**. A blank screen usually means the plugin is not
registered.

`mobile-ui` is under active development and tags ship frequently. **Always check
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

Newer `mobile-ui` tags raise the minimum core version. Pick a `mobile-ui` tag that
matches the core you can run, or upgrade core first:

| `mobile-ui` | Requires `nativephp/mobile` |
|---|---|
| 0.4.0 | `^4.0` |
| 0.5.0 – 0.7.0 | `^4.5` |
| 0.8.0 | `^4.6` |
| 0.9.0 | `^4.7` |
| 0.10.0 | `^4.8` |

Confirm for the tag you pick:

```bash
curl -s https://raw.githubusercontent.com/NativePHP/mobile-ui/<tag>/composer.json \
  | grep -A4 '"require"'
```

**Install trap:** the `plugins.nativephp.com` composer repository can lag behind
the GitHub tags. It has been seen indexing `0.3.0` while `0.4.0` was already
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
> `nativephp/mobile` 4.8.0 and `nativephp/mobile-ui` 0.10.0. Both packages gain
> elements with each tag, so treat these as "at least these exist" and re-derive
> from your own install (commands at the end of this section).

With both packages installed, **67** element tags resolve in the PHP registry.
Every one of them renders through `mobile-ui`. The split below only shows where
the PHP element class comes from, which decides whether a tag compiles at all
without the plugin.

Registered by **core** `NativeServiceProvider::registerCoreElements()` (26). These
compile without `mobile-ui` but draw nothing on device without it:
`bottom_nav`, `bottom_nav_item`, `canvas`, `circle`, `column`, `divider`, `fab`,
`gesture_area`, `icon`, `image`, `line`, `pressable`, `rect`, `refreshable`,
`row`, `scroll_view`, `side_nav`, `side_nav_group`, `side_nav_header`,
`side_nav_item`, `spacer`, `stack`, `text`, `top_bar`, `top_bar_action`,
`top_bar_title`.

Registered only by **`nativephp/mobile-ui`**'s manifest (41). These throw
`Unknown native element type` without the plugin:
`accordion`, `accordion_content`, `accordion_header`, `activity_indicator`,
`background_layer`, `badge`, `bare_text_input`, `bottom_sheet`, `button`,
`button_group`, `carousel`, `checkbox`, `chip`, `date_picker`, `emoji_picker`,
`filled_text_input`, `floating_overlay`, `lazy_grid`, `list`, `list_item`,
`list_placeholder`, `list_section`, `modal`, `native_drawer`,
`outlined_text_input`, `pager`, `pager_header`, `pager_overlay`, `popover`,
`progress_bar`, `radio`, `radio_group`, `select`, `sheet_pane`, `slider`,
`sticky_header`, `tab`, `tab_row`, `toggle`, `virtual_list`, `webview`.

Core still ships `Native\Mobile\Edge\Elements\{Button, Toggle, ActivityIndicator,
BottomSheet, TextInput}`, but it no longer registers them. The `button`,
`toggle`, `activity_indicator` and `bottom_sheet` tags resolve only to
`Native\Mobile\UI\Elements\*`. Do not write code against the core classes for
these tags.

`lazy_grid` uses a core class (`Native\Mobile\Edge\Elements\LazyGrid`), but only
the `mobile-ui` manifest registers it.

Shipped but undocumented at the time of writing: `background_layer`,
`date_picker`, `emoji_picker`, `floating_overlay`, `list_placeholder`,
`native_drawer`, `pager_header`, `pager_overlay`, `popover`, `sheet_pane`,
`sticky_header`, `top_bar_title`. Read the element class in
`vendor/nativephp/mobile-ui/src/Elements/` before you use one of these.

`divider.md` documents `horizontal-divider`, and the 0.10.0 manifest lists
`horizontal_divider`. But the manifest points it at
`Native\Mobile\Edge\Elements\HorizontalDivider`, and core 4.8.0 does not ship that
class. The registry therefore skips the tag. Confirm `horizontal_divider` is in
your registry dump before you use it; otherwise use `divider`.

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
component or attribute that no tagged release has yet. Pages mark newer features
with a `since` version (for example `pager` is `mobile-ui` 0.5+, validation is
core 4.7+). The reference app `super-native` pins `nativephp/mobile`
`dev-main as 4.9.9` from the `NativePHP/mobile-air` VCS repo. At the time of
writing its lockfile resolved `nativephp/mobile-ui` **0.3.0**, which is older
than the docs. A SuperNative view can therefore lack attributes the docs
describe, and the docs can describe elements SuperNative never uses. Check its
`composer.lock` for what it currently resolves:

```bash
curl -s https://raw.githubusercontent.com/NativePHP/super-native/main/composer.lock \
  | grep -A1 '"name": "nativephp/'
```

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
| `pager` (full-screen snap paging, `mobile-ui` 0.5+) | [pager.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/pager.md) |
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
| `filled-text-input`, `outlined-text-input`, `bare-text-input` | [text-input.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/edge-components/text-input.md) |
| `bottom-bar` (keyboard-aware bottom content) | [layouts.md#keyboard-aware-bottom-content](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/the-basics/layouts.md) |
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

v4 ships a testing API for native screens in `vendor/nativephp/mobile/src/Testing/`
(`Native.php`, `TestableComponent.php`, `FakeBridge.php`, `FakeAsyncTask.php`,
`PestExpectations.php`, `TreeSpy.php`, `TestDumpHandler.php`). It is present in
tagged releases (checked on 4.1.0, 4.7.0 and 4.8.0), not only on dev-main.

This matters because ordinary Pest feature tests do **not** exercise native
screens at all. Under `runningUnitTests()`, `Route::native` returns a 200 stub
whose body says "test it with Native::test() / Native::visit()"
(`NativeServiceProvider.php:403-408` in 4.7.0 and 4.8.0). So a broken layout or a missing
builder method passes lint and the suite, and fails only on device. Use these
helpers to close that gap.

Docs base: `https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/`

| Doc | Covers |
|---|---|
| [introduction.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/introduction.md) | `Native::test()`, `Native::visit()`, `Native::fakeBridge()`, `assertSee`, `assertSet` |
| [interactions.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/interactions.md) | Pressing elements, `assertNativeCalled`, `assertWentBack` |
| [navigation.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/navigation.md) | Flows and chrome — `assertScreen`, `assertNavigatedTo`, `assertReplacedWith`, `assertExitedToWeb`, `assertTransition`, `assertNoNavigation`, `assertHasTabBar`, `assertHasTab`, `assertTabActive`, `assertNavTitle`, `assertMissingElement` |
| [native-events.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/native-events.md) | Bridge events — `assertNativeCalledTimes`, `assertNativeCallOrder`, `assertAwaitingNativeEvent` |
| [accessibility.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/accessibility.md) | `assertAccessible`, `NativeRouter::registeredRoutes()`, `PestExpectations::register()` |
| [advanced.md](https://raw.githubusercontent.com/NativePHP/nativephp.com/main/resources/views/docs/mobile/4/testing/advanced.md) | `assertElement`, `assertMatchesSnapshot`, render counts (`assertRenderCount`, `assertNotRerendered`) |

Verified to exist on `Native` in 4.8.0: `test()`, `visit()`, `fakeBridge()`. On
`TestableComponent`, every assertion named in the table above exists, plus
`assertNavAction`/`assertMissingNavAction` (new in 4.8.0, not yet in the docs),
`assertDontSee`, `assertNotSet`, `assertNativeNotCalled`,
`assertNotAwaitingNativeEvent`, `assertRerendered`, `assertDispatched`,
`assertNotDispatched`, `assertDispatchedTo`, `assertTabBarHidden`/`Visible`,
`assertNavBarHidden`/`Visible`, and the `follow()`/`followNavigation()` helpers
for walking multi-screen flows.

`assertCopied()` is not a core assertion. It appears only in
`plugins/validation-testing.md` as an example `FakeBridge::macro` that a plugin
registers for itself.

Check any assertion before relying on it, since the docs track dev-main:

```bash
php -r 'require "vendor/autoload.php";
  var_dump(method_exists("Native\Mobile\Testing\TestableComponent", "assertHasTab"));'
```

Highest-value coverage for a shell migration: `assertHasTabBar` / `assertHasTab`
to pin the tab config, `assertNavigatedTo` / `assertReplacedWith` to prove a tab
tap lands on the right native route, and `assertExitedToWeb` to pin the places
where leaving the native stack for the web view is intended.

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

Caveat: super-native runs core dev-main, so it may use core APIs absent from
your tagged release. Cross-check against your registry dump (see **Required
packages**).

## Breaking change: EDGE chrome no longer works from a webview Blade layout

The v4 upgrade guide states that no application code changes are required. **That
is not true for any app that rendered EDGE chrome — top bar, bottom nav or side
nav — from its webview Blade layout.**

The v4 EDGE introduction page still recommends putting components in a layout
such as `layouts/app.blade.php`. Do not follow that for a webview layout: in v4,
`<native:*>` tags compile only inside a native-screen render (see point 3
below).

v4 **removed webview-mode native chrome entirely.** Verified three ways (still
true in 4.8.0):

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
| Blocking XHR that 404s on every page | JS `Edge.clearSync()` / `Edge.setSync()` (and `SetEdge`/`ClearEdge`) still ship in `resources/dist/native.d.ts`, but the `Edge.Set` bridge method is unregistered, so `/_native/api/call` returns `METHOD_NOT_FOUND`. A `try/catch` usually swallows it. |

Find every affected site:

```bash
grep -rn 'Native\\Mobile\\Edge\|Edge::' resources/ app/ routes/ config/
grep -rn '<native:' resources/views/
grep -rn 'clearSync\|setSync\|SetEdge\|ClearEdge\|Edge' resources/js/
```

The `<native:` grep misses unprefixed tags. Grep for the chrome tags as well:

```bash
grep -rnE '<(bottom-nav|top-bar|side-nav)[ >/-]' resources/views/
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

1. Install **and register** `nativephp/mobile-ui` (see **Required packages**).
2. Add a `NativeComponent` shell screen holding the chrome (e.g.
   `<native:bottom-nav>`) plus `<native:webview php src="/your-route">`. The
   `php` attribute is required. Without it the web view is a sandboxed foreign
   page with JavaScript and DOM storage off, no `window.Native` bridge, and no
   access to the app's session. In `php` mode, `src` is an app route path, not a
   URL. A path that does not start with `/` falls back to `start_url`. Each
   `php`-mode web view boots its own PHP context, so expect a slower first load.
3. Register it with `Route::native(...)` and point `NATIVEPHP_START_URL` at it —
   `config/nativephp.php` `start_url` defaults to `'/'`.
4. Remove the dead EDGE calls found by the greps above. With chrome living in the
   shell, there is nothing to clear per-page.
5. Migrate views to native screens incrementally.

Steps 2-3 are reconstructed from the docs and `super-native`, not from a verified
build — treat them as a starting point and confirm on device.

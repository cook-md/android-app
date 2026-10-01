# Changelog

What changed in each release of the app, newest first. Internal engineering
notes stay in the private repository; this file is generated from it.

## [0.12.1] - 2026-09-30

### Added

- Signed-out users now see a "Sign in / See plans" prompt at feature gates
  (photo and social-link imports, meal plans, the paywall) instead of a paywall
  they cannot buy from, matching iOS.

### Fixed

- Shopping list: removing a recipe no longer fails when another recipe on the
  list has been deleted, and deleted recipes no longer appear on the aisle tab.
- Sharing: protocol-relative image URLs now resolve, and images missing from
  disk are skipped instead of breaking the share.
- Timers: the background timer service now stops reliably.
- Clipping: cancelling the sign-in alert closes the import instead of leaving an
  empty screen, and a signed-out link import asks about social imports rather
  than photo imports.
- A device without a cook.md account counts as signed out even when an anonymous
  purchase session exists.
- Sign-in alert buttons use the accent label colour.

## [0.12.0] - 2026-09-29

### Added

- Menus (meal plans): a menu screen opened from the recipe browser or a
  `cook://` link, with day cards, scaling, and "add the whole menu to the
  shopping list".
- Menu files opened from other apps are previewed and saved to Plans.
- The Basic plan card in the paywall now lists meal plans.
- Shopping list redesign: the recipe tab shows linked recipes and menu dishes as
  badged sub-sections; restyled aisle tab, tabs, empty state, clear dialog and
  options sheet.

### Fixed

- Shopping list: linked recipes that cannot be found are skipped with a warning
  instead of dropping the entry; repeated linked recipes are grouped as on iOS;
  amounts are right-aligned; long scale factors fit at large font sizes.
- Importing: only the file's actual extension is dropped, file names are trimmed
  before detecting menus, and draft and menu titles are sanitised before
  numbering.
- Local folders: saving a copy never overwrites an existing file, and the mirror
  writes over a name the folder picker already claimed.
- Menus: deep links open in the menu screen, recipe references stay inside the
  recipe root, double taps are ignored while a preview save runs, and the scale
  button and controls are labelled for TalkBack.

## [0.11.0] - 2026-09-23

### Added

- Open `.cook` files from anywhere (file managers, mail, messaging apps) into
  the shared-recipe preview.
- Deep links: `cook://my/<path>` and `https://cook.md/my/<path>` open the recipe
  or folder; long-press a recipe or folder to copy its link.
- The onboarding paywall is offered on a later day's launch instead of right
  away.

### Fixed

- Shopping list warns about recipe reference cycles, and unportioned
  sub-recipes scale correctly.
- Import review: fixed misleading details and blank refusal screens.
- Cook is offered for `.cook` files whose URI carries no file name.

## [0.10.2] - 2026-09-16

### Added

- Cook Cloud paywalls: new copy, Cook Pro purchasable in the app, import
  meters and account states; a plan badge that says where the plan is managed;
  "Manage subscription" for buyers who never signed in; a warning when an
  account merge left two subscriptions billed.

### Fixed

- The real sync error is shown, and sync starts right after buying a plan.
- Transient Play Billing failures are retried instead of reported.
- Lost access to a custom recipe folder is recovered.
- Just-saved recipes are kept, and the first folder sync is faster.
- The expired-session flag is cleared when the user signs back in.

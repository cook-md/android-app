# Changelog

What changed in each release of the app, newest first. Internal engineering
notes stay in the private repository; this file is generated from it.

## [0.13.0] - 2026-10-08

### Added

- Getting started now asks about allergies, how much time you have on weeknights
  and what you want help with, so your first recipes fit better — and ends on a
  "Your cookbook is ready" page showing what was added for you.
- Clip a recipe from plain text: the clip screen has a new Text tab where you paste a
  recipe copied from a note, a message or an email, and the app turns it into a recipe
  you can cook from.

### Changed

- Recipes in a folder are listed in file-name order. A recipe whose `title:` differs
  from its file name shows the title but sits where the file name sorts.
- In meal plans, notes are `-- note` lines, as in the Cook Editor and CookCLI; a `> note`
  line now shows as plain text.
- Meal plans are now free for everyone, signed in or not: every day of a plan is
  open, and you can add a whole plan to your shopping list without a plan or an
  account.

### Fixed

- Adding a meal plan to the shopping list now buys what the plan says: a dish ordered
  by servings (`{4%servings}` of a recipe that serves two) is added twice, not four
  times, matching the portion shown on the plan.
- Opening your recipes, or a folder of them, is fast however many recipes you
  have: the app now reads only the folder on screen, and only the recipes you
  can see, instead of every recipe in the library. Rows show their file name
  first and fill in the title and photo as they come into view.
- Meal plans are read the same way as in the Cook Editor, CookCLI and the iPhone
  app: a dish ordered by servings (`{4%servings}`) shows how many times the
  recipe is cooked, meal times (`Dinner (19:00):`) are shown, and `-- notes`
  appear as notes.
- The "preparing your recipes" screen at the end of onboarding no longer closes
  after a second or two with the bar half full: it stays up long enough to read
  the cooking facts and fills the bar before your recipes open.
- Turning sync on when your sign-in has lapsed now asks you to sign in again
  instead of showing an error screen that came back every time you closed it.
- Your starter recipes are no longer lost to a slow connection: the download at
  the end of getting started now waits as long as a recipe import does, instead
  of giving up after ten quiet seconds and handing you the demo recipes.
- If the folder you picked for your recipes stops answering — its storage app
  was removed, or the folder itself was deleted — the app now notices on the
  first save and shows the "pick your folder again" banner, instead of failing
  the save with a generic error.

## [0.12.2] - 2026-10-02

### Added

- "What's new" in Settings → About opens this changelog.
- Hit the import limit without an account? You can now sign in for free
  to keep importing, and the import picks up where it stopped.
- Meal plans for today and tomorrow now appear at the top of My recipes, so
  tonight's dinner is one tap away.

### Changed

- Onboarding and sign-in prompts no longer suggest that an account alone
  brings sync, photo imports or meal plans: sync comes with Cook Basic, photo
  and social-link imports with a Cook Cloud plan.

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


# Release Notes

## Version 3.4.0

* Add a new configuration option for whether building highlighters (e.g.,
  Junimo Huts) run when the mouse is over the building.

## Version 3.3.1

* Fix order of checking "IsScarecrow" and using the game's get scarecrow radius
  function vs. checking by item name.

## Version 3.3.0

* Fix bug where holding the Blue Armchair would show the mega-bomb range

* Update for SMAPI 3.14

## Version 3.2.0

### User-visible Changes

* Show beehouse range from Better Beehouses (if installed)

## Version 3.1.0

### User-visible Changes

* Add configuration in-game (title screen only) via Generic Mod Config Menu.
  If GMCM Options is also installed then tint colors can be configured as well.


### API Changes

* All highlighters are now cleared when returning to the title screen.  The
  `SaveLoaded` event is a good place to put any calls to `Add...Highlighter`.

## Version 3.0.0

### User-visible Changes

* Built for SDV 1.5.5 / SMAPI 3.13
* Adjust "outer" range for bombs to be centered, reflecting bug fix in the game
* Check the "IsScarecrow" function exposed in 1.5.5 when looking at items.
  This should have no effect in the base game, but will automatically reflect
  scarecrow ranges for items added or modified by other mods using this feature.

## Version 2.8.0

### User-visible Changes

* Show sprinkler range for the Radioactive Sprinkler from the
  Radioactive Tools mod (if installed)

## Version 2.7.0

### User-visible Changes

* Added `showHeldBombRange` config option.  Note that the `ShowBombRange`
  option must be on for either `showHeldBombRange` or `showPlacedBombRange`
  to have effect.

* Key configurations now use the features introduced in SMAPI 3.9 to support
  multi-key bindings.  See [the wiki](https://stardewvalleywiki.com/Modding:Player_Guide/Key_Bindings#Multi-key_bindings)
  for details on the syntax.

### API Changes

* All API functions that take an `SButton` argument are now deprecated in favor
  of new versions that take a `KeybindList` argument.

## Version 2.6.0

### User-visible Changes

* Added bomb highlighting to things that explode but aren't bombs

## Version 2.5.0

### User-visible Changes

* Improved performance of integrations with other sprinkler mods
  on farms with lots of items (e.g., debris).

### API Changes

* Add a new signature of `AddItemRangeHighlighter` with
  callbacks for the beginning and end of each "batch" of
  highlight range calculation.

## Version 2.4.0

### User-visible Changes

* Integration with Line Sprinklers mod (if installed)
  to support line sprinkler ranges.

* Update Better Sprinklers and Simple Sprinklers integrations
  to not show sprinkler highlights if ShowSprinklerRange is
  turned off in the configuration.

## Version 2.3.0

### User-visible Changes

* Integration with Simple Sprinklers mod (if installed)
  to use its defined sprinkler ranges.

## Version 2.2.1

### User-visible Changes

* Fix split-screen issues (I hope).

## Version 2.2.0

### User-visible Changes

* Show correct range for sprinklers with Pressure Nozzle.

## Version 2.1.0

### User-visible Changes

* Integration with the Better Sprinklers mod (if installed)
  to use its defined sprinkler ranges.  Note that Better
  Sprinklers will still do its own highlighting in addition
  to the Range Highlighter highlighting.

## Version 2.0.0

* Update rendering to handle separate UI scaling vs zoom in
  Stardew Valley 1.5 / SMAPI 3.8.  No longer compatible
  with older versions (thus the major version number bump).

## Version 1.5.1

### User-visible Changes

* The Bomber Jacket item no longer shows a bomb range highlight.

## Version 1.5.0

### User-visible Changes

* Added configuration options to control whether holding a
  sprinkler, scarecrow, or beehouse automatically highlights
  the range of other (already placed) items of that type.

### API Changes

* Add a new signature of `AddItemRangeHighlighter` to allow
  specifing whether to highlight other (already placed) items
  if the highlighter matches the currently held item.  Deprecate
  the old signature.

## Version 1.4.0

### User-visible Changes

* Add Show*THING*Range configuration options to allow disabling
  highlighting of *THING* completely.
* Integration with the Prismatic Tools mod so that the range of
  the prismatic sprinkler matches the configured value in
  Prismatic Tools.
* Integration with the Better Junimos mod (if installed) to use
  its configured Junimo Hut range.
* Highlights now work during building placement.

### API Changes

* Change the function argument to `AddItemRangeHighlighter` to
  take the `Item` object and its ID as arguments in addition to
  the lower-cased item name.  (And by change I mean added a new
  signature and deprecated the old one.)
* Add a signature of `AddBuildingRangeHighlighter` that allows
  matching on a `BluePrint` during building placement.

-----

## Version 1.3.0

* Add the `hotkeysToggle` configuration property (off by default).
  If this property is changed to `true` then the hotkeys will act
  as a toggle switch rather than needing to be held down.
* Fix a NullReferenceException that was sometimes
  being printed to the console when moving between locations
  (only observed as a farm hand in multiplayer).

-----

## Version 1.2.0

* Bombs now show multiple areas of effect
  * The innermost area is where the bomb can cause dirt to turn
    into hoed ground.  The default configuration is to not show
    this area.
  * The "normal" range is the area where rocks and many items are
    destroyed.  This is the range shown in previous versions.
  * The outermost area is where crops are destroyed, flooring is
    disrupted, and the player takes damage.  (Note that this area
    is not centered on the bomb.)  The default configuration does
    show this range, but it can be disabled.
* Bombs that have been placed on the ground now show their ranges.
  This can be disabled in configuration.

_A note on the API:_

Unlike all of the other highlights, the bomb highlighting does not
use the public API.  Bombs are weird, and I didn't want to make
a messy API to support them without some other use case for it.

-----

## Version 1.1.1

* Change the default key bindings so that they do not conflict
  with the default movement keys.  (Keep in mind that if the
  `config.json` has already been generated with the old defaults
  then they won't be overwritten with the new defaults.)

-----

## Version 1.1.0

### User-visible Changes

* Bomb ranges are now highlighted when a bomb is equipped.
  (Ranges of bombs already on the ground are not shown.)

### API Changes

* Two new functions have been added to the API:
  * `GetCartesianCircleWithTruncate` truncates a tile's distance from
    the origin to an integer before comparing it against the radius.
    This is the same as the existing `GetCartesianCircle`.
  * `GetCartesianCircleWithRound` rounds a tile's distance from
    the origin to the nearest integer before comparing it against the radius.
    (This is the shape of a bomb's blast.)
* The `GetCartesianCircle` function is now deprecated.

-----

## Version 1.0.0

Initial release

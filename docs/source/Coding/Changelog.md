# Changelog

## Evennia 3.0.0

Dec 20, 2023

- Dependency: Twisted 23.10 (<24) to address upstream CVE alert.
- Dependency (potentially Backwards incompatible): Django 4.2 (<4.3). Increases
  minimum supported versions of MariaDB, MySQL and PostgreSQL,
  see [django release nodes][django-release-notes]
- [Feature][pull3313] (Backwards incompatible): `OptionHandler.set` now returns
  `BaseOption` rather than its `.value`. Instead access `.value` or `.display()`
  on this return for more control. (Volund)
- [Feature][pull3278]: (Backwards incompatible): Refactor home page into multiple sub-parts for easier
  overriding and composition (johnnyvoruz)
- [Feature][pull3180]: (Potentially Backwards incompatible): Make build commands
  easier to override, with new utility hooks (Volund)
- [Feature][issue3273]: Allow passing `text_kwargs` kwarg to `EvMore.msg` in order to expand
  the outputfunc used for every evmore page.
- [Feature][pull3286]: Allow Discord bot to change user's nickname and assign
  roles for a user on a given server (holl0wstar).
- [Feature][pull3301]: Make EvenniaAdminSite include custom models better; adds
  `DJANGO_ADMIN_APP_ORDER` and `DJANGO_ADMIN_APP_EXCLUDE` as modifable
  settings.(Volund)
- [Feature][pull3179]: Handling of the `.db._playable_characters` helper
  methods. Also adds events hooks to modify effects when this list changes (Volund)
  avoiding race conditions until server starts (Volund)
- [Feature][pull3281]: Add `$your()` and `$Your()` for actor stance emoting (Volund)
- [Feature][pull3177]: Add `Account.get_character_slots()`,
  `.get_available_character_slots()`, `.check_available_slots` and
  `at_post_create_character` methods to allow better customization of character creation (Volund)
- [Feature][pull3319]: Refactor/cleanup of Evennia server/portal startup files
  into services for easier overriding (Volund)
- [Feature][issue3307]: Add support for Attribute-categories when using the monitorhandler
  with input funcs to monitor Attribute changes.
- [Feature][pull3342]: Add `Command.cmdset_source`, referring to the cmdset each
  command was originally pulled from (Volund)
- [Feature][pull3343]: Add `access_type` as optional kwarg to lockfuncs (Volund)
- [Feature][pull3344]: New middleware for checking IP/subnets from requests. New
  tools `evennia.utils.match_ip` and `utils.ip_from_request` to help. (Volund)
- [Feature][pull3349]: Refactored almost all default commands to use
  `Command.msg` over the `command.caller.msg` direct call (more flexible) (Volund)
- [Feature][pull3346]: Refactor cmdhandler to be more extensible; make cmd merge
  a bit more deterministic (Volund)
- [Feature][pull3348]: Make Fallback AJAX web client more customizable (same as
  the websocket client) (Volund)
- [Feature][pull3353]: Add unique id to each webclient instance, separates play
  sessions run from the same browser. (InpsectorCaracal)
- [Feature][pull3365]: Make the rpsystem contrib's prefix (`/` by default)
  configurable with a setting (used to be hard-coded) (InspectorCaracal)
- Fix (Backwards incompatible): Change `settings._TEST_ENVIRONMENT` to
  `settings.TEST_ENVIRONMENT` to address issues during refactored startup sequence.
- [Fix][pull3347]: New `generate_default_locks()` method on typeclasses;
  `.create` and `lockhandler.add()` will now properly handle emptry strings
(Volund)
- [Fix][pull3197]: Make sure Global scripts only start in one place,
- [Fix][pull3324]: Make account-post-login-fail signal fire properly. Add
  `CUSTOM_SIGNAL` for adding one's own signals (Volund)
- [Fix][pull3267]: Missing recache step in ObjectSessionHandler (InspectorCaracal)
- [Fix][pull3270]: Evennia is its own MSSP family now, so we should return that
  instead of 'Custom' (InspectorCaracal)
- [Fix][pull3274]: Traceback when creating objects with initial nattributes
  (InspectorCaracal)
- [Fix][issue3272]: Make sure `ScriptHandler.add` does not fail if passed an
  instantiated script. (Volund)
- [Fix][pull3350]: `CmdHelp` was using the wrong protocol-key identifier when
  routing to the ajax web client.
- [Fix][pull3338]: Resolve if/elif bug in XYZGrid contrib launch command
  (jaborsh)
- [fix][issue3331]: Made XYZGrid query zcoords in a case-insensitive manner.
- [Fix][pull3322]: Fix `BaseOption.display` to always return a string.
- [Fix][pull3358]: Fix so Portal resets `server_restart_mode` flag when having
  successfully reconnected to the Server after a restart. (InspectorCaracal)
- [Fix][pull3359]: Fix gendersub contrib to use proper pronoun when referencing
  other objects than oneself (InspectorCaracal)
- [Fix][pull3361]: Fix of monitoring Attributes with categories (scyfris)
- Docs & docstrings: Lots of Typo and other fixes (iLPdev, InspectorCaracal, jaborsh,
  HouseOfPoe etc)
- Beginner tutorial: Cleanup and starting earlier with explaining how to add to
  the default cmdsets.

[pull3267]: https://github.com/evennia/evennia/pull/3267
[pull3270]: https://github.com/evennia/evennia/pull/3270
[pull3274]: https://github.com/evennia/evennia/pull/3274
[pull3278]: https://github.com/evennia/evennia/pull/3278
[pull3286]: https://github.com/evennia/evennia/pull/3286
[pull3301]: https://github.com/evennia/evennia/pull/3301
[pull3179]: https://github.com/evennia/evennia/pull/3179
[pull3197]: https://github.com/evennia/evennia/pull/3197
[pull3313]: https://github.com/evennia/evennia/pull/3313
[pull3281]: https://github.com/evennia/evennia/pull/3281
[pull3322]: https://github.com/evennia/evennia/pull/3322
[pull3177]: https://github.com/evennia/evennia/pull/3177
[pull3180]: https://github.com/evennia/evennia/pull/3180
[pull3319]: https://github.com/evennia/evennia/pull/3319
[pull3324]: https://github.com/evennia/evennia/pull/3324
[pull3338]: https://github.com/evennia/evennia/pull/3338
[pull3342]: https://github.com/evennia/evennia/pull/3342
[pull3343]: https://github.com/evennia/evennia/pull/3343
[pull3344]: https://github.com/evennia/evennia/pull/3344
[pull3349]: https://github.com/evennia/evennia/pull/3349
[pull3350]: https://github.com/evennia/evennia/pull/3350
[pull3346]: https://github.com/evennia/evennia/pull/3346
[pull3348]: https://github.com/evennia/evennia/pull/3348
[pull3358]: https://github.com/evennia/evennia/pull/3358
[pull3359]: https://github.com/evennia/evennia/pull/3359
[pull3361]: https://github.com/evennia/evennia/pull/3361
[pull3347]: https://github.com/evennia/evennia/pull/3347
[pull3353]: https://github.com/evennia/evennia/pull/3353
[pull3365]: https://github.com/evennia/evennia/pull/3365
[issue3272]: https://github.com/evennia/evennia/issues/3272
[issue3273]: https://github.com/evennia/evennia/issues/3273
[issue3307]: https://github.com/evennia/evennia/issues/3307
[issue3331]: https://github.com/evennia/evennia/issues/3331

[django-release-notes]: https://docs.djangoproject.com/en/4.2/releases/4.2/#backwards-incompatible-changes-in-4-2

## Evennia 2.3.0

Sept 3, 2023

- Feat: EvMenu tooltips for multiple help categories in a node (Seannio).
- Feat: Default `examine` command now also shows an account's `last_login`
  (michaelfaith84)
- Fix: Portal would accidentally start global scripts. (blongden)
- Fix: Traceback when printing CounterTrait contrib objects. (InspectorCaracal)
- Fix: Typo in evadventure twitch combat's call of `create_combathandler`.
- Docs: Fix bug in evadventure equipmenthandler blocking creation of npcs.
  in-game.
- Docs: Plenty of typo fixes (iLPDev, moldikins, others)

## Evennia 2.2.0

Aug 6, 2023

- Contrib: Large-language-model (LLM) AI integration; allows NPCs to talk using
  responses from an LLM server.
- Fix: Make sure `at_server_reload` is called also on non-repeating Scripts.
- Fix: Webclient was not giving a proper error when sending an unknown outputfunc to it.
- Fix: Make `py` command always send strings unless `client_raw` flag is set.
- Fix: `Script.start` with an integer `start_delay` caused a traceback.
- Fix: Removing "Guest" from the permission-hierarchy setting messed up access.
- Docs: Remove doc pages for Travis/TeamCity CI tools, they were both very much
  out of date, and Travis is not free for OSS anymore.
- Docs: A lot fixes of typos and bugs in tutorials.

## Evennia 2.1.0

July 14, 2023

- Fix: The new `ExtendedRoom` contrib has a bug when dug with no descriptions.
- Fix: Clean up `get_sides` function in evadventure tutorial to return also
  the calling combatant with its `allies` return, to make it easier to reason around.
- Feature: Add `SSL_CERTIFICATE_ISSUERS` setting for customizing Telnet+SSL.
- Contrib: Refactored `dice.roll` contrib function to use `safe_eval`. Can now
  optionally be used as `dice.roll("2d10 + 4 > 10")`. Old way works too.
- Lots of doc updates.

## Evennia 2.0.1

June 17, 2023

- Fix: A look-bug in the `ExtendedRoom` contrib (InspectorCaracal)

## Evennia 2.0.0

June 10, 2023

- **Possible backwards incompatibility**: Updated contrib `ExtendedRoom` now
  supports arbitrary room-states, state-based descriptions, embedded funcparser
  tags, details and random messages.  While this feature is made to be as
  backwards-compatible as possible, so many people depend on this contrib class
  that we are updating the major Evennia version to indicate the big changes.
- New Contrib: `Container` typeclass with new commands for storing and retrieving
  things inside them (InspectorCaracal)
- Feature: Add `TagCategoryProperty` for setting categories with multiple tags
  as properties directly on objects. Complements `TagProperty`.
- Feature: Attribute-support for saving/loading `deques` with `maxlen=` set.
- Feature: Refactor to provide `evennia.SESSION_HANDLER` for easier overloading
  and less risks of circular import problems (Volund)
- Fix: Allow webclient's goldenlayout UI (default) to understand `msg`
  `cls` kwarg for customizing the CSS class for every resulting `div` (friarzen)
- Fix: The `AttributeHandler.all()` now actually accepts `category=` as
  keyword arg, like our docs already claimed it should (Volund)
- Fix: `TickerHandler` store key updating was refactored, fixing an issue with
  updating intervals (InspectorCaracal)
- Docs: Removed warning about Python3.11 on Windows; upstream Twistd now
  supports 3.11 on Windows.
- Docs: New Beginner-Tutorial lessons for NPCs, Base-Combat Twitch-Combat and
  Turnbased-combat (note that the Beginner tutorial is still WIP).
- Stabilize how to make the major update in the docs.
- Fix: A lot of other minor bug fixes.


## Evennia 1.3.0

Apr 29, 2023

- Feature: Better ANSI color fallbacks (InspectorCaracal).
- Feature: Add support for saving `deque` with `maxlen` to Attributes (before
  `maxlen` was ignored).
- Fix: The username validator did not display errors correctly in web
  registration form.
- Fix: Components contrib had issues with inherited typeclasses (ChrisLR)
- Fix: f-string fix in clothing contrib (aMiss-aWry)
- Fix: Have `EvenniaTestCase` properly flush idmapper cache (bradleymarques)
- Tools: More unit tests for scripts (Storsorken)
- Docs: Made separate doc pages for Exits, Characters and Rooms. Expanded on how
  to change the description of an in-game object with templating.
- Docs: A multitude of doc issues and typos fixed.

## Evennia 1.2.1

Feb 26, 2023

- Bug fix: Make sure command parser gives precedence to longer cmd-aliases. So
  if sending `smile at` and the cmd `smile` has alias `smile at`, the match is
  ordered so the result is never interpreted as `smile` with an argument `at`.
- Bug fix: || (escaped color tags) were parsed too early in help entries,
  leading to colors when wanting a | separator
- Bug fix: Make sure spawned objects get `typeclass_path` pointing to the true
  location rather than alias (in line with `create_object`).
- Bug fix: Building Menu contrib menu no using Replace over Union mergetype to
  avoid clashing with in-game commands while building
- Feature: RPSystem contrib `sdesc` command can now view/delete your sdesc.
- Bug fix: Change so `script obj = [scriptname|id]` is required to manipulate
  scripts on objects; `script scriptname|id` only works on global scripts.
- Doc: Add warning about `Django-wiki` (in wiki tutorial) only supporting
  Django <4.0.
- Doc: Expanded `XYZGrid` docstring to clarify `MapLink` class will not itself
  spawn anything, children must define their prototypes explicitly.
- Doc: Explained why `AttributeProperty.at_get/set` will not be called if
  accessing the Attribute from the `AttributeHandler` (bypassing the property)
- Bug fix: Evtable options showed spurious empty lines if set without desc
- Usage fix: The `teleport:` and `teleport_here:` locks where checked in
  `CmdTeleport`, but not actually set on any entities. These locks are now
  set with defaults on all objects,characters,rooms and exits.

## Evennia 1.2.0

Feb 25, 2023

- Bug fix: `TagHandler.get` did not consistently cast to string (aMiss-aWry)
- Bug fix: Channels hard to manage if given in different case (aMiss-aWry)
- Feature: `logger.delete_log` function for deleting custom logs from inside the
  server (aMiss-aWry)
- Doc: Nginx setup (InspectorCaracal)
- Feature: Add `fly/dive` commands to `XYZGrid` contrib to showcase treating its
  Z-axis as a full 3D grid. Also fixed minor bug in `XYZGrid` contrib when using
  a Z axis named using an integer rather than a string.
- Bug fix: `$an()` inlinefunc didn't understand to use 'an' words starting with a
  capital vowel
- Bug fix: Another case of the 'duplicate Discord bot connections' bug
  (InspectorCaracal)
- Fix: Make XYZGrid contrib's MapParserErrors more succinct

## Evennia 1.1.1

Jan 15, 2023

- Bug fix: Better handler malformed alias-regex given to nickhandler. A
  regex-relevant character in a channel alias could cause server to not restart.
- Feature: Add `attr` keyword to `create_channel`. This allows setting
  attributes on channels at creation, also from `DEFAULT_CHANNELS` definitions.

## Evennia 1.1.0
Jan 7, 2023

- Stop new registrations with `settings.NEW_ACCOUNT_REGISTRATION_ENABLED`
  (inspectorcaracal)
- Bug fixes.

## Evennia 1.0.2
Dec 21, 2022

- Bug fix release. Fix more issues with discord bot reconnecting. Some doc
updates.

## Evennia 1.0.1
Dec 7, 2022

- Bug fix release. Main issue was reconnect bug for discord bot.

## Evennia 1.0.0

2019-2022

_Changed to using `main` branch to follow github standard. Old `master` branch remains
for now but will not be used anymore, so as to not break installs during transition._

Also changing to using semantic versioning with this version.

Increase requirements: Django 4.1+, Twisted 22.10+ Python 3.10, 3.11.  PostgreSQL 11+.

- New `drop:holds()` lock default to limit dropping nonsensical things. Access check
  defaults to True for backwards-compatibility in 0.9, will be False in 1.0
- REST API allows you external access to db objects through HTTP requests (Tehom)
- `Object.normalize_name` and `.validate_name` added to (by default) enforce latinify
  on character name and avoid potential exploits using clever Unicode chars (trhr)
- New `utils.format_grid` for easily displaying long lists of items in a block.
- Using `lunr` search indexing for better `help` matching and suggestions. Also improve
  the main help command's default listing output.
- Added `content_types` indexing to DefaultObject's ContentsHandler. (volund)
- Made most of the networking classes such as Protocols and the SessionHandlers
  replaceable via `settings.py` for modding enthusiasts. (volund)
- The `initial_setup.py` file can now be substituted in `settings.py` to customize
  initial game database state. (volund)
- Added new Traits contrib, converted and expanded from Ainneve project.
- Added new `requirements_extra.txt` file for easily getting all optional dependencies.
- Change default multi-match syntax from 1-obj, 2-obj to obj-1, obj-2.
- Make `object.search` support 'stacks=0' keyword - if ``>0``, the method will return
  N identical matches instead of triggering a multi-match error.
- Add `tags.has()` method for checking if an object has a tag or tags (PR by ChrisLR)
- Make IP throttle use Django-based cache system for optional persistence (PR by strikaco)
- Renamed Tutorial classes "Weapon" and "WeaponRack" to "TutorialWeapon" and
  "TutorialWeaponRack" to prevent collisions with classes in mygame
- New `crafting` contrib, adding a full crafting subsystem (Griatch 2020)
- The `rplanguage` contrib now auto-capitalizes sentences and retains ellipsis (...). This
  change means that proper nouns at the start of sentences will not be treated as nouns.
- Make MuxCommand `lhs/rhslist` always be lists, also if empty (used to be the empty string)
- Fix typo in UnixCommand contrib, where `help` was given as `--hel`.
- Latin (la) i18n translation (jamalainm)
- Made the `evennia` dir possible to use without gamedir for purpose of doc generation.
- Make Scripts' timer component independent from script object deletion; can now start/stop
  timer without deleting Script. The `.persistent` flag now only controls if timer survives
  reload - Script has to be removed with `.delete()` like other typeclassed entities.
- Add `utils.repeat` and `utils.unrepeat` as shortcuts to TickerHandler add/remove, similar
  to how `utils.delay` is a shortcut for TaskHandler add.
- Refactor the classic `red_button` example to use `utils.delay/repeat` and modern recommended
  code style and paradigms instead of relying on `Scripts` for everything.
- Expand `CommandTest` with ability to check multiple message-receivers; inspired by PR by
  user davewiththenicehat. Also add new doc string.
- Add central `FuncParser` as a much more powerful replacement for the old `parse_inlinefunc`
  function.
- Attribute/NAttribute got a homogenous representation, using intefaces, both
  `AttributeHandler` and `NAttributeHandler` has same api now.
- Add `evennia/utils/verb_conjugation` for automatic verb conjugation (English only). This
  is useful for implementing actor-stance emoting for sending a string to different targets.
- New version of Italian translation (rpolve)
- `utils.evmenu.ask_yes_no` is a helper function that makes it easy to ask a yes/no question
  to the user and respond to their input. This complements the existing `get_input` helper.
- Allow sending messages with `page/tell` without a `=` if target name contains no spaces.
- New FileHelpStorage system allows adding help entries via external files.
- `sethelp` command now warns if shadowing other help-types when creating a new
  entry.
- Help command now uses `view` lock to determine if cmd/entry shows in index and
  `read` lock to determine if it can be read. It used to be `view` in the role
  of the latter. Migration swaps these around.
- In modules given by `settings.PROTOTYPE_MODULES`, spawner will now first look for a global
  list `PROTOTYPE_LIST` of dicts before loading all dicts in the module as prototypes.
- New Channel-System using the `channel` command and nicks. Removed the `ChannelHandler` and the
  concept of a dynamically created `ChannelCmdSet`.
- Add `Msg.db_receiver_external` field to allowe external, string-id message-receivers.
- Renamed `app.css` to `website.css` for consistency. Removed old prosimii-css files.
- Remove `mygame/web/static_overrides` and -`template_overrides`, reorganize website/admin/client/api
  into a more consistent structure for overriding. Expanded webpage documentation considerably.
- REST API list-view was shortened (#2401). New CSS/HTML. Add ReDoc for API autodoc page.
- Update and fix dummyrunner with cleaner code and setup.
- Made `iter_to_str` format prettier strings, using Oxford comma.
- Added an MXP anchor tag to also support clickable web links.
- New `tasks` command for managing tasks started with `utils.delay` (PR by davewiththenicehat)
- Make `help` index output clickable for webclient/clients with MXP (PR by davewiththenicehat)
- Custom `evennia` launcher commands (e.g. `evennia mycmd foo bar`). Add new commands as callables
  accepting `*args`, as `settings.EXTRA_LAUNCHER_COMMANDS = {'mycmd': 'path.to.callable', ...}`.
- New `XYZGrid` contrib, adding x,y,z grid coordinates with in-game map and
  pathfinding. Controlled outside of the game via custom evennia launcher command.
- `Script.delete` has new kwarg `stop_task=True`, that can be used to avoid
  infinite recursion when wanting to set up Script to delete-on-stop.
- Command executions now done on copies to make sure `yield` don't cause crossovers. Add
  `Command.retain_instance` flag for reusing the same command instance.
- The `typeclass` command will now correctly search the correct database-table for the target
  obj (avoids mistakenly assigning an AccountDB-typeclass to a Character etc).
- Merged `script` and `scripts` commands into one, for both managing global- and
  on-object Scripts. Moved `CmdScripts` and `CmdObjects` to `commands/default/building.py`.
- Keep GMCP function case if outputfunc starts with capital letter (so `cmd_name` -> `Cmd.Name`
  but `Cmd_nAmE` -> `Cmd.nAmE`). This helps e.g Mudlet's legacy `Client_GUI` implementation)
- Prototypes now allow setting `prototype_parent` directly to a prototype-dict.
  This makes it easier when dynamically building in-module prototypes.
- `RPSystem contrib` was expanded to support case, so /tall becomes 'tall man'
  while /Tall becomes 'Tall man'. One can turn this off if wanting the old style.
- Change `EvTable` fixed-height rebalance algorithm to fill with empty lines at end of
  column instead of inserting rows based on cell-size (could be mistaken for a bug).
- Split `return_appearance` hook with helper methods and have it use a template
  string in order to make it easier to override.
- Add validation question to default account creation.
- Add `LOCALECHO` client option to add server-side echo for clients that does
  not support this (useful for getting a complete log).
- Make `@lazy_property` decorator create read/delete-protected properties. This is
  because it's used for handlers, and e.g. self.locks=[] is a common beginner mistake.
- Add `$pron()` inlinefunc for pronoun parsing in actor-stance strings using
  `msg_contents`.
- Update defauklt website to show Telnet/SSL/SSH connect info. Added new
  `SERVER_HOSTNAME` setting for use in the server:port stanza.
- Changed all `at_before/after_*` hooks to `at_pre/post_*` for consistency
  across Evennia (the old names still work but are deprecated)
- Change `settings.COMMAND_DEFAULT_ARG_REGEX` default from `None` to a regex meaning that
  a space or `/` must separate the cmdname and args. This better fits common expectations.
- Add confirmation question to `ban`/`unban` commands.
- Check new `teleport` and `teleport_here` lock-types in `teleport` command to optionally
  allow to limit teleportation of an object or to a specific destination.
- Add `settings.MXP_ENABLED=True` and `settings.MXP_OUTGOING_ONLY=True` as sane defaults,
  to avoid known security issues with players entering MXP links.
- Add browser name to webclient `CLIENT_NAME` in `session.protocol_flags`, e.g.
  `"Evennia webclient (websocket:firefox)"` or `"evennia webclient (ajax:chrome)"`.
- `TagHandler.add/has(tag=...)` kwarg changed to `add/has(key=...)` for consistency
  with other handlers.
- Make `DefaultScript.delete`, `DefaultChannel.delete` and `DefaultAccount.delete` return
  bool True/False if deletion was successful (like `DefaultObject.delete` before them)
- `contrib.custom_gametime` days/weeks/months now always starts from 1 (to match
  the standard calendar form ... there is no month 0 every year after all).
- `AttributeProperty`/`NAttributeProperty` to allow managing Attributes/NAttributes
  on typeclasses in the same way as Django fields.
- Give build/system commands a `@name` to fall back to if the non-@ name is used
  by another command (like `open` and `@open`. If no duplicate, @ is optional.
- Move legacy channel-management commands (`ccreate`, `addcom` etc) to a contrib
  since their work is now fully handled by the single `channel` command.
- Expand `examine` command's code to much more extensible and modular. Show
  attribute categories and value types (when not strings).
- `AttributeHandler.remove(key, return_exception=False, category=None, ...)` changed
  to `.remove(key, category=None, return_exception=False, ...)` for consistency.
- New `command cooldown` contrib for making it easier to manage commands using
  dynamic cooldowns between uses (owllex)
- Restructured `contrib/` folder, placing all contribs as separate packages under
  subfolders. All imports will need to be updated.
- Made `MonitorHandler.add/remove` support `category` for monitoring Attributes
  with a category (before only key was used, ignoring category entirely).
- Move `create_*` functions into db managers, leaving `utils.create` only being
  wrapper functions (consistent with `utils.search`). No change of api otherwise.
- Add support for `$dbref()` and `$search` when assigning an Attribute value
  with the `set` command. This allows assigning real objects from in-game.
- Add ability to examine `/script` and `/channel` entities  with `examine` command.
- Homogenize manager search methods to return querysets and not lists.
- Restructure unit tests to always honor default settings; make new parents in
  on location for easy use in game dir.
- The `Lunr` search engine used by help excludes common words; the settings-list
  `LUNR_STOP_WORD_FILTER_EXCEPTIONS` can be extended to make sure common names are included.
- Add `.deserialize()` method to `_Saver*` structures to help completely
  decouple structures from database without needing separate import.
- Add `run_in_main_thread` as a helper for those wanting to code server code
  from a web view.
- Update `evennia.utils.logger` to use Twisted's new logging API. No change in Evennia API
  except more standard aliases logger.error/info/exception/debug etc can now be used.
- Have `type/force` default to `update`-mode rather than `reset`mode and add more verbose
  warning when using reset mode.
- Attribute storage support defaultdics (Hendher)
- Add ObjectParent mixin to default game folder template as an easy, ready-made
  way to override features on all ObjectDB-inheriting objects easily.
  source location, mimicking behavior of `at_pre_move` hook - returning False will abort move.
- Add `TagProperty`, `AliasProperty` and `PermissionProperty` to assign these
  data in a similar way to django fields.
- New `at_pre_object_receive(obj, source_location)` method on Objects. Called on
  destination, mimicking behavior of `at_pre_move` hook - returning False will abort move.
- New `at_pre_object_leave(obj, destination)` method on Objects. Called on
- The db pickle-serializer now checks for methods `__serialize_dbobjs__` and `__deserialize_dbobjs__`
  to allow custom packing/unpacking of nested dbobjs, to allow storing in Attribute.
- Optimizations to rpsystem contrib performance. Breaking change: `.get_sdesc()` will
  now return `None` instead of `.db.desc` if no sdesc is set; fallback in hook (inspectorCaracal)
- Reworked text2html parser to avoid problems with stateful color tags (inspectorCaracal)
- Simplified `EvMenu.options_formatter` hook to use `EvColumn` and f-strings (inspectorcaracal)
- Allow `# CODE`, `# HEADER` etc as well as `#CODE`/`#HEADER` in batchcode
  files - this works better with black linting.
- Added `move_type` str kwarg to `move_to()` calls, optionally identifying the type of
  move being done ('teleport', 'disembark', 'give' etc). (volund)
- Made RPSystem contrib msg calls pass `pose` or `say` as msg-`type` for use in
  e.g. webclient pane filtering where desired. (volund)
- Added `Account.uses_screenreader(session=None)` as a quick shortcut for
  finding if a user uses a screenreader (and adjust display accordingly).
- Fixed bug in `cmdset.remove()` where a command could not be deleted by `key`,
  even though doc suggested one could (ChrisLR)
- New contrib `name_generator` for building random real-world based or fantasy-names
  based on phonetic rules.
- Enable proper serialization of dict subclasses in Attributes (aogier)
- `object.search` fuzzy-matching now uses `icontains` instead of `istartswith`
  to better match how search works elsewhere (volund)
- The `.at_traverse` hook now receives a `exit_obj` kwarg, linking back to the
  exit triggering the hook (volund)
- Contrib `buffs` for managing temporary and permanent RPG status buffs effects (tegiminis)
- New `at_server_init()` hook called before all other startup hooks for all
  startup modes. Used for more generic overriding (volund)
- New `search` lock type used to completely hide an object from being found by
  the `DefaultObject.search` (`caller.search`) method. (CloudKeeper)
- Change setting `MULTISESSION_MODE` to now only control sessions, not how many
  characters can be puppeted simultaneously. New settings now control that.
- Add new setting `AUTO_CREATE_CHARACTER_WITH_ACCOUNT`, a boolean deciding if
  the new account should also get a matching character (legacy MUD style).
- Add new setting `AUTO_PUPPET_ON_LOGIN`, boolean deciding if one should
  automatically puppet the last/available character on connection (legacy MUD style)
- Add new setting `MAX_NR_SIMULTANEUS_PUPPETS` - how many puppets the account
  can run at the same time. Used to limit multi-playing.
- Make setting `MAX_NR_CHARACTERS` interact better with the new settings above.
- Allow `$search` funcparser func to search tags and to accept kwargs for more
  powerful searches passed into the regular search functions.
- `spawner.spawn` and linked methods now has a kwarg `protfunc_raise_errors`
  (default True) to disable strict errors on malformed/not-found protfuncs
- Improve search performance when having many DB-based prototypes via caching.
- Remove the `return_parents` kwarg of `evennia.prototypes.spawner.spawn` since it
  was inefficient and unused.
- Made all id fields BigAutoField for all databases. (owllex)
- `EvForm` refactored. New `literals` mapping, for literal mappings into the
  main template (e.g. for single-character replacements).
- `EvForm` `cells` kwarg now accepts `EvCells` with custom formatting options
  (mainly for custom align/valign). `EvCells` now makes use of `utils.justify`.
- `utils.justify` now supports `align="a"` (absolute alignments. This keeps
  the given left indent but crops/fills to the width. Used in EvCells.
- `EvTable` now supports passing `EvColumn`s as a list directly, (`EvTable(table=[colA,colB])`)
- Add `tags=` search criterion to `DefaultObject.search`.
- Add `AT_EXIT_TRAVERSE` signal, firing when an exit is traversed.
- Add integration between Evennia and Discord channels (PR by Inspector Cararacal)
- Support for using a Godot-powered client with Evennia (PR by ChrisLR)
- Added German translation (patch by Zhuraj)

## Evennia 0.9.5

> 2019-2020
> Released 2020-11-14.
> Transitional release, including new doc system.

Backported from develop: Python 3.8, 3.9 support. Django 3.2+ support, Twisted 21+ support.

- `is_typeclass(obj (Object), exact (bool))` now defaults to exact=False
- `py` command now reroutes stdout to output results in-game client. `py`
without arguments starts a full interactive Python console.
- Webclient default to a single input pane instead of two. Now defaults to no help-popup.
- Webclient fix of prompt display
- Webclient multimedia support for relaying images, video and sounds via
  `.msg(image=URL)`, `.msg(video=URL)`
  and `.msg(audio=URL)`
- Add Spanish translation (fermuch)
- Expand `GLOBAL_SCRIPTS` container to always start scripts and to include all
  global scripts regardless of how they were created.
- Change settings to always use lists instead of tuples, to make mutable
  settings easier to add to. (#1912)
- Make new `CHANNEL_MUDINFO` setting for specifying the mudinfo channel
- Make `CHANNEL_CONNECTINFO` take full channel definition
- Make `DEFAULT_CHANNELS` list auto-create channels missing at reload
- Webclient `ANSI->HTML` parser updated. Webclient line width changed from 1.6em to 1.1em
  to better make ANSI graphics look the same as for third-party clients
- `AttributeHandler.get(return_list=True)` will return `[]` if there are no
  Attributes instead of `[None]`.
- Remove `pillow` requirement (install especially if using imagefield)
- Add Simplified Korean translation (aceamro)
- Show warning on `start -l` if settings contains values unsafe for production.
- Make code auto-formatted with Black.
- Make default `set` command able to edit nested structures (PR by Aaron McMillan)
- Allow running Evennia test suite from core repo with `make test`.
- Return `store_key` from `TickerHandler.add` and add `store_key` as a kwarg to
  the `TickerHandler.remove` method. This makes it easier to manage tickers.
- EvMore auto-justify now defaults to False since this works better with all types
  of texts (such as tables). New `justify` bool. Old `justify_kwargs` remains
  but is now only used to pass extra kwargs into the justify function.
- EvMore `text` argument can now also be a list or a queryset. Querysets will be
  sliced to only return the required data per page.
- Improve performance of `find` and `objects` commands on large data sets (strikaco)
- New `CHANNEL_HANDLER_CLASS` setting allows for replacing the ChannelHandler entirely.
- Made `py` interactive mode support regular quit() and more verbose.
- Made `Account.options.get` accept `default=None` kwarg to mimic other uses of get. Set
  the new `raise_exception` boolean if ranting to raise KeyError on a missing key.
- Moved behavior of unmodified `Command` and `MuxCommand` `.func()` to new
  `.get_command_info()` method for easier overloading and access. (Volund)
- Removed unused `CYCLE_LOGFILES` setting. Added `SERVER_LOG_DAY_ROTATION`
  and `SERVER_LOG_MAX_SIZE` (and equivalent for PORTAL) to control log rotation.
- Addded `inside_rec` lockfunc - if room is locked, the normal `inside()` lockfunc will
  fail e.g. for your inventory objs (since their loc is you), whereas this will pass.
- RPSystem contrib's CmdRecog will now list all recogs if no arg is given. Also multiple
  bugfixes.
- Remove `dummy@example.com` as a default account email when unset, a string is no longer
  required by Django.
- Fixes to `spawn`, make updating an existing prototype/object work better. Add `/raw` switch
  to `spawn` command to extract the raw prototype dict for manual editing.
- `list_to_string` is now `iter_to_string` (but old name still works as legacy alias). It will
  now accept any input, including generators and single values.
- EvTable should now correctly handle columns with wider asian-characters in them.
- Update Twisted requirement to >=2.3.0 to close security vulnerability
- Add `$random` inlinefunc, supports minval,maxval arguments that can be ints and floats.
- Add `evennia.utils.inlinefuncs.raw(<str>)` as a helper to escape inlinefuncs in a string.
- Make CmdGet/Drop/Give give proper error if `obj.move_to` returns `False`.
- Make `Object/Room/Exit.create`'s `account` argument optional. If not given, will set perms
  to that of the object itself (along with normal Admin/Dev permission).
- Make `INLINEFUNC_STACK_MAXSIZE` default visible in `settings_default.py`.
- Change how `ic` finds puppets; non-priveleged users will use `_playable_characters` list as
  candidates, Builders+ will use list, local search and only global search if no match found.
- Make `cmd.at_post_cmd()` always run after `cmd.func()`, even when the latter uses delays
  with yield.
- `EvMore` support for db queries and django paginators as well as easier to override for custom
  pagination (e.g. to create EvTables for every page instead of splittine one table)
- Using `EvMore pagination`, dramatically improves performance of `spawn/list` and `scripts` listings
  (100x speed increase for displaying 1000+ prototypes/scripts).
- `EvMenu` now uses the more logically named `.ndb._evmenu` instead of `.ndb._menutree` to store itself.
  Both still work for backward compatibility, but `_menutree` is deprecated.
- `EvMenu.msg(txt)` added as a central place to send text to the user, makes it easier to override.
  Default `EvMenu.msg` sends with OOB type="menu" for use with OOB and webclient pane-redirects.
- New EvMenu templating system for quickly building simpler EvMenus without as much code.
- Add `Command.client_height()` method to match existing `.client_width` (stricako)
- Include more Web-client info in `session.protocol_flags`.
- Fixes in multi-match situations - don't allow finding/listing multimatches for 3-box when
  only two boxes in location.
- Fix for TaskHandler with proper deferred returns/ability to cancel etc (PR by davewiththenicehat)
- Add `PermissionHandler.check` method for straight string perm-checks without needing lockstrings.
- Add `evennia.utils.utils.strip_unsafe_input` for removing html/newlines/tags from user input. The
  `INPUT_CLEANUP_BYPASS_PERMISSIONS` is a list of perms that bypass this safety stripping.
- Make default `set` and `examine` commands aware of Attribute categories.

## Evennia 0.9

> 2018-2019
> Released Oct 2019

### Distribution

- New requirement: Python 3.7 (py2.7 support removed)
- Django 2.1
- Twisted 19.2.1
- Autobahn websockets (removed old tmwx)
- Docker image updated

### Commands

- Remove `@`-prefix from all default commands (prefixes still work, optional)
- Removed default `@delaccount` command, incorporating as `@account/delete` instead. Added confirmation
  question.
- Add new `@force` command to have another object perform a command.
- Add the Portal uptime to the `@time` command.
- Make the `@link` command first make a local search before a global search.
- Have the default Unloggedin-look command look for optional `connection_screen()` callable in
  `mygame/server/conf/connection_screen.py`. This allows for more flexible welcome screens
  that are calculated on the fly.
- `@py` command now defaults to escaping html tags in its output when viewing in the webclient.
  Use new `/clientraw` switch to get old behavior (issue #1369).
- Shorter and more informative, dynamic, listing of on-command vars if not
  setting func() in child command class.
- New Command helper methods
  - `.client_width()` returns client width of the session running the command.
  - `.styled_table(*args, **kwargs)` returns a formatted evtable styled by user's options
  - `.style_header(*args, **kwargs)` creates styled header entry
  - `.style_separator(*args, **kwargs)`      "             separator
  - `.style_footer(*args, **kwargs)`         "             footer

### Web

- Change webclient from old txws version to use more supported/feature-rich Autobahn websocket library

#### Evennia game index

- Made Evennia game index client a part of core - now configured from settings file (old configs
  need to be moved)
- The `evennia connections` command starts a wizard that helps you connect your game to the game index.
- The game index now accepts games with no public telnet/webclient info (for early prototypes).

#### New golden-layout based Webclient UI (@friarzen)
- Features
  - Much slicker behavior and more professional look
  - Allows tabbing as well as click and drag of panes in any grid position
  - Renaming tabs, assignments of data tags and output types are simple per-pane menus now
  - Any number of input panes, with separate histories
  - Button UI (disabled in JS by default)

#### Web/Django standard initiative (@strikaco)
- Features
  - Adds a series of web-based forms and generic class-based views
    - Accounts
      - Register - Enhances registration; allows optional collection of email address
      - Form - Adds a generic Django form for creating Accounts from the web
    - Characters
      - Create - Authenticated users can create new characters from the website (requires associated form)
      - Detail - Authenticated and authorized users can view select details about characters
      - List - Authenticated and authorized users can browse a list of all characters
      - Manage - Authenticated users can edit or delete owned characters from the web
      - Form - Adds a generic Django form for creating characters from the web
    - Channels
      - Detail - Authorized users can view channel logs from the web
      - List - Authorized users can browse a list of all channels
    - Help Entries
      - Detail - Authorized users can view help entries from the web
      - List - Authorized users can browse a list of all help entries from the web
  - Navbar changes
    - Characters - Link to character list
    - Channels - Link to channel list
    - Help - Link to help entry list
    - Puppeting
      - Users can puppet their own characters within the context of the website
    - Dropdown
      - Link to create characters
      - Link to manage characters
      - Link to quick-select puppets
      - Link to password change workflow
- Functions
  - Updates Bootstrap to v4 stable
  - Enables use of Django Messages framework to communicate with users in browser
  - Implements webclient/website `_shared_login` functionality as Django middleware
  - 'account' and 'puppet' are added to all request contexts for authenticated users
  - Adds unit tests for all web views
- Cosmetic
  - Prettifies Django 'forgot password' workflow (requires SMTP to actually function)
  - Prettifies Django 'change password' workflow
- Bugfixes
  - Fixes bug on login page where error messages were not being displayed
  - Remove strvalue field from admin; it made no sense to have here, being an optimization field
    for internal use.

### Prototypes

- `evennia.prototypes.save_prototype` now takes the prototype as a normal
  argument (`prototype`) instead of having to give it as `**prototype`.
- `evennia.prototypes.search_prototype` has a new kwarg `require_single=False` that
  raises a KeyError exception if query gave 0 or >1 results.
- `evennia.prototypes.spawner` can now spawn by passing a `prototype_key`

### Typeclasses

- Add new methods on all typeclasses, useful specifically for object handling from the website/admin:
  + `web_get_admin_url()`: Returns the path to the object detail page in the Admin backend.
  + `web_get_create_url()`: Returns the path to the typeclass' creation page on the website, if implemented.
  + `web_get_absolute_url()`: Returns the path to the object's detail page on the website, if implemented.
  + `web_get_update_url()`: Returns the path to the object's update page on the website, if implemented.
  + `web_get_delete_url()`: Returns the path to the object's delete page on the website, if implemented.
- All typeclasses have new helper class method `create`, which encompasses useful functionality
  that used to be embedded for example in the respective `@create` or `@connect` commands.
- DefaultAccount now has new class methods implementing many things that used to be in unloggedin
  commands (these can now be customized on the class instead):
  + `is_banned()`: Checks if a given username or IP is banned.
  + `get_username_validators`: Return list of validators for username validation (see
    `settings.AUTH_USERNAME_VALIDATORS`)
  + `authenticate`: Method to check given username/password.
  + `normalize_username`: Normalizes names so (for Unicode environments) users cannot mimic existing usernames by replacing select characters with visually-similar Unicode chars.
  + `validate_username`: Mechanism for validating a username based on predefined Django validators.
  + `validate_password`: Mechanism for validating a password based on predefined Django validators.
  + `set_password`: Apply password to account, using validation checks.
- `AttributeHandler.remove` and `TagHandler.remove` can now be used to delete by-category. If neither
     key nor category is given, they now work the same as .clear().

### Protocols

- Support for `Grapevine` MUD-chat network ("channels" supported)

### Server

- Convert ServerConf model to store its values as a Picklefield (same as
    Attributes) instead of using a custom solution.
- OOB: Add support for MSDP LIST, REPORT, UNREPORT commands (re-mapped to `msdp_list`,
  `msdp_report`, `msdp_unreport`, inlinefuncs)
- Added `evennia.ANSIString` to flat API.
- Server/Portal log files now cycle to names on the form `server_.log_19_03_08_` instead of `server.log___19.3.8`, retaining
  unix file sorting order.
- Django signals fire for important events: Puppet/Unpuppet, Object create/rename, Login,
  Logout, Login fail Disconnect, Account create/rename

### Settings

- `GLOBAL_SCRIPTS` - dict defining typeclasses of global scripts to store on the new
  `evennia.GLOBAL_SCRIPTS` container. These will auto-start when Evennia start and will always
  exist.
- `OPTIONS_ACCOUNTS_DEFAULT` - option dict with option defaults and Option classes
- `OPTION_CLASS_MODULES` - classes representing an on-Account Option, on special form
- `VALIDATOR_FUNC_MODULES` - (general) text validator functions, for verifying an input
  is on a specific form.

### Utils

- `evennia` launcher now fully handles all django-admin commands, like running tests in parallel.
- `evennia.utils.create.account` now also takes `tags` and `attrs` keywords.
- `evennia.utils.interactive` decorator can now allow you to use yield(secs) to pause operation
  in any function, not just in Command.func. Likewise, response = yield(question) will work
  if the decorated function has an argument or kwarg `caller`.
- Added many more unit tests.
- Swap argument order of `evennia.set_trace` to `set_trace(term_size=(140, 40), debugger='auto')`
  since the size is more likely to be changed on the command line.
- `utils.to_str(text, session=None)` now acts as the old `utils.to_unicode` (which was removed).
  This converts to the str() type (not to a byte-string as in Evennia 0.8), trying different
  encodings. This function will also force-convert any object passed to it into a string (so
  `force_string` flag was removed and assumed always set).
- `utils.to_bytes(text, session=None)` replaces the old `utils.to_str()` functionality and converts
  str to bytes.
- `evennia.MONITOR_HANDLER.all` now takes keyword argument `obj` to only retrieve monitors from that specific
  Object (rather than all monitors in the entire handler).
- Support adding `\f` in command doc strings to force where EvMore puts page breaks.
- Validation Functions now added with standard API to homogenize user input validation.
- Option Classes added to make storing user-options easier and smoother.
- `evennia.VALIDATOR_CONTAINER` and `evennia.OPTION_CONTAINER` added to load these.

### Contribs

- Evscaperoom - a full puzzle engine for making multiplayer escape rooms in Evennia. Used to make
  the entry for the MUD-Coder's Guild's 2019 Game Jam with the theme "One Room", where it ranked #1.
- Evennia game-index client no longer a contrib - moved into server core and configured with new
  setting `GAME_INDEX_ENABLED`.
- The `extended_room` contrib saw some backwards-incompatible refactoring:
  + All commands now begin with `CmdExtendedRoom`. So before it was `CmdExtendedLook`, now
     it's `CmdExtendedRoomLook` etc.
  + The `detail` command was broken out of the `desc` command and is now a new, stand-alone command
     `CmdExtendedRoomDetail`.  This was done to make things easier to extend and to mimic how the detail
     command works in the tutorial-world.
  + The `detail` command now also supports deleting details (like the tutorial-world version).
  + The new `ExtendedRoomCmdSet` includes all the extended-room commands and is now the recommended way
     to install the extended-room contrib.
- Reworked `menu_login` contrib to use latest EvMenu standards. Now also supports guest logins.
- Mail contrib was refactored to have optional Command classes `CmdMail` for OOC+IC mail (added
    to the CharacterCmdSet and `CmdMailCharacter` for IC-only mailing between chars (added to CharacterCmdSet)

### Translations

- Simplified chinese, courtesy of user MaxAlex.


## Evennia 0.8

> 2017-2018
> Released Nov 2018

### Requirements

- Up requirements to Django 1.11.x, Twisted 18 and pillow 5.2.0
- Add `inflect` dependency for automatic pluralization of object names.

### Server/Portal

- Removed `evennia_runner`, completely refactor `evennia_launcher.py` (the 'evennia' program)
  with different functionality).
- Both Portal/Server are now stand-alone processes (easy to run as daemon)
- Made Portal the AMP Server for starting/restarting the Server (the AMP client)
- Dynamic logging now happens using `evennia -l` rather than by interactive mode.
- Made AMP secure against erroneous HTTP requests on the wrong port (return error messages).
- The `evennia istart` option will start/switch the Server in foreground (interactive) mode, where it logs
  to terminal and can be stopped with Ctrl-C. Using `evennia reload`, or reloading in-game, will
  return Server to normal daemon operation.
- For validating passwords, use safe Django password-validation backend instead of custom Evennia one.
- Alias `evennia restart` to mean the same as `evennia reload`.

### Prototype changes

- New OLC started from `olc` command for loading/saving/manipulating prototypes in a menu.
- Moved evennia/utils/spawner.py into the new evennia/prototypes/ along with all new
  functionality around prototypes.
- A new form of prototype - database-stored prototypes, editable from in-game, was added. The old,
  module-created prototypes remain as read-only prototypes.
- All prototypes must have a key `prototype_key` identifying the prototype in listings. This is
  checked to be server-unique. Prototypes created in a module will use the global variable name they
  are assigned to if no `prototype_key` is given.
- Prototype field `prototype` was renamed to `prototype_parent` to avoid mixing terms.
- All prototypes must either have `typeclass` or `prototype_parent` defined. If using
  `prototype_parent`, `typeclass` must be defined somewhere in the inheritance chain. This is a
  change from Evennia 0.7 which allowed 'mixin' prototypes without `typeclass`/`prototype_key`. To
  make a mixin now, give it a default typeclass, like `evennia.objects.objects.DefaultObject`  and just
  override in the child as needed.
- Spawning an object using a prototype will automatically assign a new tag to it, named the same as
  the `prototype_key` and with the category `from_prototype`.
- The spawn command was extended to accept a full prototype on one line.
- The spawn command got the /save switch to save the defined prototype and its key
- The command spawn/menu will now start an OLC (OnLine Creation) menu to load/save/edit/spawn prototypes.

### EvMenu

- Added `EvMenu.helptext_formatter(helptext)`  to allow custom formatting of per-node help.
- Added `evennia.utils.evmenu.list_node` decorator for turning an EvMenu node into a multi-page listing.
- A `goto` option callable returning None (rather than the name of the next node) will now rerun the
  current node instead of failing.
- Better error handling of in-node syntax errors.
- Improve dedent of default text/helptext formatter. Right-strip whitespace.
- Add `debug` option when creating menu - this turns off persistence and makes the `menudebug`
  command available for examining the current menu state.


### Webclient

- Webclient now uses a plugin system to inject new components from the html file.
- Split-windows - divide input field into any number of horizontal/vertical panes and
  assign different types of server messages to them.
- Lots of cleanup and bug fixes.
- Hot buttons plugin (friarzen) (disabled by default).

### Locks

- New function `evennia.locks.lockhandler.check_lockstring`. This allows for checking an object
  against an arbitrary lockstring without needing the lock to be stored on an object first.
- New function `evennia.locks.lockhandler.validate_lockstring` allows for stand-alone validation
  of a lockstring.
- New function `evennia.locks.lockhandler.get_all_lockfuncs` gives a dict {"name": lockfunc} for
  all available lock funcs. This is useful for dynamic listings.


### Utils

- Added new `columnize` function for easily splitting text into multiple columns. At this point it
  is not working too well with ansi-colored text however.
- Extend the `dedent` function with a new `baseline_index` kwarg. This allows to force all lines to
  the indentation given by the given line regardless of if other lines were already a 0 indentation.
  This removes a problem with the original `textwrap.dedent` which will only dedent to the least
  indented part of a text.
- Added `exit_cmd` to EvMore pager, to allow for calling a command (e.g. 'look') when leaving the pager.
- `get_all_typeclasses` will return  dict `{"path": typeclass, ...}` for all typeclasses available
  in the system. This is used by the new `@typeclass/list` subcommand (useful for builders etc).
- `evennia.utils.dbserialize.deserialize(obj)` is a new helper function to *completely* disconnect
  a mutable recovered from an Attribute from the database. This will convert all nested `_Saver*`
  classes to their plain-Python counterparts.

### General

- Start structuring the `CHANGELOG` to list features in more detail.
- Docker image `evennia/evennia:develop` is now auto-built, tracking the develop branch.
- Inflection and grouping of multiple objects in default room (an box, three boxes)
- `evennia.set_trace()` is now a shortcut for launching pdb/pudb on a line in the Evennia event loop.
- Removed the enforcing of `MAX_NR_CHARACTERS=1` for `MULTISESSION_MODE` `0` and `1` by default.
- Add `evennia.utils.logger.log_sec` for logging security-related messages (marked SS in log).

### Contribs

- `Auditing` (Johnny): Log and filter server input/output for security purposes
- `Build Menu` (vincent-lg): New @edit command to edit object properties in a menu.
- `Field Fill` (Tim Ashley Jenkins): Wraps EvMenu for creating submittable forms.
- `Health Bar` (Tim Ashley Jenkins): Easily create colorful bars/meters.
- `Tree select` (Fluttersprite): Wrap EvMenu to create a common type of menu from a string.
- `Turnbattle suite` (Tim Ashley Jenkins)- the old `turnbattle.py` was moved into its own
  `turnbattle/` package and reworked with many different flavors of combat systems:
 - `tb_basic` - The basic turnbattle system, with initiative/turn order attack/defense/damage.
 - `tb_equip` - Adds weapon and armor, wielding, accuracy modifiers.
 - `tb_items` - Extends `tb_equip` with item use with conditions/status effects.
 - `tb_magic` - Extends `tb_equip` with spellcasting.
 - `tb_range` - Adds system for abstract positioning and movement.
 - The `extended_room` contrib saw some backwards-incompatible refactoring:
   - All commands now begin with `CmdExtendedRoom`. So before it was `CmdExtendedLook`, now
     it's `CmdExtendedRoomLook` etc.
   - The `detail` command was broken out of the `desc` command and is now a new, stand-alone command
     `CmdExtendedRoomDetail`.  This was done to make things easier to extend and to mimic how the detail
     command works in the tutorial-world.
   - The `detail` command now also supports deleting details (like the tutorial-world version).
   - The new `ExtendedRoomCmdSet` includes all the extended-room commands and is now the recommended way
     to install the extended-room contrib.
- Updates and some cleanup of existing contribs.


### Internationalization

- Polish translation by user ogotai

# Overview-Changelogs

> These are changelogs from a time before we used formal version numbers.

## Sept 2017:
Release of Evennia 0.7; upgrade to Django 1.11, change 'Player' to
'Account', rework the website template and a slew of other updates.
Info on what changed and how to migrate is found here:
https://groups.google.com/forum/#!msg/evennia/0JYYNGY-NfE/cDFaIwmPBAAJ

## Feb 2017:
New devel branch created, to lead up to Evennia 0.7.

## Dec 2016:
Lots of bugfixes and considerable uptick in contributors. Unittest coverage
and PEP8 adoption and refactoring.

## May 2016:
Evennia 0.6 with completely reworked Out-of-band system, making
the message path completely flexible and built around input/outputfuncs.
A completely new webclient, split into the evennia.js library and a
gui library, making it easier to customize.

## Feb 2016:
Added the new EvMenu and EvMore utilities, updated EvEdit and cleaned up
a lot of the batchcommand functionality. Started work on new Devel branch.

## Sept 2015:
Evennia 0.5. Merged devel branch, full library format implemented.

## Feb 2015:
Development currently in devel/ branch. Moved typeclasses to use
django's proxy functionality. Changed the Evennia folder layout to a
library format with a stand-alone launcher, in preparation for making
an 'evennia' pypy package and using versioning. The version we will
merge with will likely be 0.5. There is also work with an expanded
testing structure and the use of threading for saves. We also now
use Travis for automatic build checking.

## Sept 2014:
Updated to Django 1.7+ which means South dependency was dropped and
minimum Python version upped to 2.7. MULTISESSION_MODE=3 was added
and the web customization system was overhauled using the latest
functionality of django. Otherwise, mostly bug-fixes and
implementation of various smaller feature requests as we got used
to github. Many new users have appeared.

## Jan 2014:
Moved Evennia project from Google Code to github.com/evennia/evennia.

## Nov 2013:
Moved the internal webserver into the Server and added support for
out-of-band protocols (MSDP initially). This large development push
also meant fixes and cleanups of the way attributes were handled.
Tags were added, along with proper handlers for permissions, nicks
and aliases.

## May 2013:
Made players able to control more than one Character at the same
time, through the MULTISESSION_MODE=2 addition. This lead to a lot
of internal changes for the server.

## Oct 2012:
Changed Evennia from the Modified Artistic 1.0 license to the more
standard and permissive BSD license. Lots of updates and bug fixes as
more people start to use it in new ways. Lots of new caching and
speed-ups.

## March 2012:
Evennia's API has changed and simplified slightly in that the
base-modules where removed from game/gamesrc. Instead admins are
encouraged to explicitly create new modules under game/gamesrc/ when
they want to implement their game - gamesrc/ is empty by default
except for the example folders that contain template files to use for
this purpose. We also added the ev.py file, implementing a new, flat
API.  Work is ongoing to add support for mud-specific telnet
extensions, notably the MSDP and GMCP out-of-band extensions.  On the
community side, evennia's dev blog was started and linked on planet
Mud-dev aggregator.

## Nov 2011:
After creating several different proof-of-concept game systems (in
contrib and privately) as well testing lots of things to make sure the
implementation is basically sound, we are declaring Evennia out of
Alpha. This can mean as much or as little as you want, admittedly -
development is still heavy but the issue list is at an all-time low
and the server is slowly stabilizing as people try different things
with it. So Beta it is!

## Aug 2011:
Split Evennia into two processes: Portal and Server. After a lot of
work trying to get in-memory code-reloading to work, it's clear this
is not Python's forte - it's impossible to catch all exceptions,
especially in asynchronous code like this.  Trying to do so results in
hackish, flakey and unstable code. With the Portal-Server split, the
Server can simply be rebooted while players connected to the Portal
remain connected. The two communicates over twisted's AMP protocol.

## May 2011:
The new version of Evennia, originally hitting trunk in Aug2010, is
maturing. All commands from the pre-Aug version, including IRC/IMC2
support works again. An ajax web-client was added earlier in the year,
including moving Evennia to be its own webserver (no more need for
Apache or django-testserver). Contrib-folder added.

## Aug 2010:
Evennia-griatch-branch is ready for merging with trunk. This marks a
rather big change in the inner workings of the server, such as the
introduction of TypeClasses and Scripts (as compared to the old
ScriptParents and Events) but should hopefully bring everything
together into one consistent package as code development continues.

## May 2010:
Evennia is currently being heavily revised and cleaned from
the years of gradual piecemeal development. It is thus in a very
'Alpha' stage at the moment. This means that old code snippets
will not be backwards compatabile. Changes touch almost all
parts of Evennia's innards, from the way Objects are handled
to Events, Commands and Permissions.

## April 2010:
Griatch takes over Maintainership of the Evennia project from
the original creator Greg Taylor.

# Older

Earlier revisions, with previous maintainer, used SVN on Google Code
and have no changelogs.

First commit (Evennia's birthday) was November 20, 2006.

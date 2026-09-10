# SchoolPop — How to Use This Addon

**by Mhortai**

SchoolPop is an addon for World of Warcraft 3.3.5a (Wrath of the Lich King). It replaces the game's floating damage numbers with better ones — coloured by the *type* of damage — and gives you your own private combat log and a per-fight damage/healing breakdown.

Every number is coloured by its **school** — the type of damage it is:

| Colour | School |
|---|---|
| Yellow | Physical (melee, Crusader Strike, etc.) |
| Pale gold | Holy |
| Orange | Fire |
| Green | Nature |
| Light blue | Frost |
| Purple-blue | Shadow |
| Pink | Arcane |
| Bright green | Healing |

So at a glance you know what kind of hit just landed. Crits are bigger and get `!!!` after the number. All colours can be changed.

---

## Installing it

1. Unzip the file you were given. You get a folder called `SchoolPop`.
2. Put that folder inside your game's `Interface\AddOns\` folder. If you already have an older `SchoolPop` there, delete it first.
3. Start the game (or type `/reload` if it's already running). A full restart is safest for a first install.
4. A small gem icon appears on your minimap — that's SchoolPop.

To check the version, open `SchoolPop\SchoolPop.toc` in a text editor and read the `## Version:` line.

---

## Three ways to open the options

- **Left-click the minimap gem** (right-click opens the Breakdown window).
- Type **`/sp`** in chat.
- Press **Escape → Interface → AddOns tab → SchoolPop**.

Everything on the panel applies immediately — no reload needed.

---

## The options panel

### Checkboxes

- **Floating text** — the numbers that float up from enemies. Turn off if you only want the log.
- **Pet damage** — include your pet's hits.
- **Show healing** — show your heals as green `+` numbers.
- **Short numbers** — abbreviate big numbers instead of every digit: `1.2K`, `56K`, `1.5M`, and past a million it rolls over to `B` (billion), `T` (trillion) and beyond — e.g. `2.5B`, not `2500M`. The combat-log window always keeps the full, exact numbers.
- **Spell icons** — put the ability's icon next to each number.
- **Over nameplates** — numbers appear above the enemy you hit and follow it. Needs nameplates on (press **V**).
- **Minimap button** — show or hide the gem.
- **Log window** — open the SchoolPop combat log.
- **ItemID** — annotate each combat-log line with where its proc came from and which of your items carries it.

### Dropdowns

- **Font** — twelve fonts (four are WoW's own; the rest are bundled).
- **Outline** — none, thin or thick black edge.
- **Direction** — how numbers move: up, down, sideways, diagonally, static, or **Arc** (a fountain-like throw; the default).

### Sliders

- **Font size**, **Duration**, **Distance** — size, how long a number stays, how far it travels.
- **Horizontal / Vertical** — the fixed screen position (used when a number isn't over a nameplate).
- **Spread** — how much a burst of hits scatters so they don't stack.
- **Merge** — hits of the same spell within this many seconds combine into one number with `x3` after it. Set to 0 to see every hit.
- **Icon size** and **Icon: Left / Right** — size and side of the spell icon.

### Colours

Click any coloured square to change that school's colour. **Reset colours** restores the defaults.

### Buttons (centered at the bottom)

- **Reset colours** — colours back to default.
- **Test** — fires a sample of every colour so you can check your settings without fighting.
- **Reset all** — everything back to defaults.
- **Open log** — opens the combat log window (row beneath).
- **Breakdown** — opens the DPS/HPS breakdown window (row beneath).

---

## The combat log window

Tick **Log window** in the options (or `/sp log`, or the keybinding). A black window lists only *your* combat, one line per hit:

```
Mhortai hits Sethekk Guard with Crusader Strike for 1,234,567!!!
Mhortai heals Priestname with Holy Light for 87,500
Mhortai is healed by Judgement of Light for 87,500 (12,000 overheal)
```

Each line is coloured by school; crits get `!!!`; healing lines show any overhealing.

**Title bar, left to right:** the **All / Damage / Healing** dropdown (what the log records), **Breakdown** (opens the breakdown window), **Export**, **?** (filter — see below), **Opt** (a pop-up with font size, opacity and a timestamps toggle), and **X**.

Along the very bottom is the **DPS / HPS meter line** — your damage and healing per second for the current fight, with the fight length. The **Clear** button at the bottom-right clears the log and resets the DPS/HPS meter in one click.

**Moving/resizing:** drag anywhere on the window to move it; drag the corner grip to resize. Use the scroll arrows on the right (or the mouse wheel) to scroll back.

**Export** opens a window with the whole log as plain text, already selected — press **Ctrl+C** and paste into Word or Notepad. (Addons can't write files directly. The same text is also saved to `WTF\Account\<your account>\SavedVariables\SchoolPopExport.lua` on logout.)

### The "?" filter — by ID or name

Click **?** to open the Filter box. Type either:

- **a spell ID** (a number) — the log shows only that proc's lines, and
- **a name** (text) — the log shows only lines whose ability name contains what you typed (proc, talent or skill), case-insensitive.

It filters live as you type, and keeps filtering new lines while the box has a value. Delete the text (or type something that matches nothing) to show everything again. Closing the box clears the filter.

### ItemID — where a proc came from

Some of your damage and healing comes from **procs** — effects that fire on their own from your gear, set bonuses or seals. With **ItemID** ticked, the log annotates each line with the proc's source and the item it's imprinted on, in white:

```
Mhortai is healed by Drain Life (Bryntroll, the Bone Arbiter; on Sanctified Lightsworn Shoulderplates) (71838)
```

This needs the **Uncapped** addon loaded, since that's what supplies your imprint data. If a proc isn't in the database and isn't imprinted on anything, the line just shows the proc name. (For a full standalone imprint viewer, use the separate **PicoID** addon.)

---

## The DPS / HPS breakdown window

Click **Breakdown** in the options (or `/sp breakdown`, or the Breakdown button in the log window). It breaks your damage and healing down by source for the current fight, in two tabs:

- **DPS** — every ability, spell and proc you dealt damage with this fight.
- **HPS** — the same for your healing.

Each row shows the source's **name with its spell ID in parentheses**, its **Total** for the fight (abbreviated), its **%** share, its **Hits**, and its **DPS/HPS** (per-second rate). Rows are sorted highest-total first and coloured by school. A footer shows the fight total and overall per-second.

**Each proc is its own row.** Procs are grouped by spell ID, so the several different "Drain Life" procs each get their own line — the ID in parentheses tells them apart: `Drain Life (71838)`, `Drain Life (34107)`. Melee swings are grouped into a single **Melee** row.

**Only your damage counts.** The breakdown includes only what *you* or *your pet* did — your attacks, spells, talents, procs and melee. Ground effects, boss debuffs and other things you didn't cause (e.g. Corrupted Ground) are not counted.

The meter and breakdown are cumulative: they keep counting across fights and only clear when you hit Reset (or the log's Clear button). The clock starts on your first action after a reset and keeps running. The window has a **Log** button (opens the log) and a **Reset** button (clears the current fight — breakdown, meter and log). Drag to move, corner grip to resize, and close it with its **X**, the minimap right-click, the Breakdown button, or `/sp breakdown`. (It deliberately does *not* close on Escape, so it stays put when you lose control of your character.)

---

## Keybinding

**Escape → Key Bindings → SchoolPop → Toggle log window** — assign a key to flip the log on and off mid-fight.

---

## Slash commands (everything is also in the panel)

| Command | What it does |
|---|---|
| `/sp` | Open the options panel |
| `/sp float` | Floating text on/off |
| `/sp heal` | Healing text on/off |
| `/sp pet` | Pet damage on/off |
| `/sp log` | Log window on/off |
| `/sp breakdown` | DPS/HPS breakdown window on/off |
| `/sp logfont 14` | Log window font size |
| `/sp test` | Show a sample of every colour |
| `/sp reset` | Everything back to defaults |

Any message the addon has for you appears in the log window, never in your normal chat.

---

## Common questions

**The numbers aren't over the enemy.** Nameplates must be on — press **V** (Shift-V for friendly plates, for healing).

**I see `x3` after a number.** That many hits of the same spell landed within the merge window and were combined. Set the **Merge** slider to 0 to see them separately.

**Numbers overlap.** Increase **Spread**, or turn on **Merge**.

**The breakdown shows something I didn't cast.** It shouldn't — the breakdown only counts your own and your pet's damage. If you still see a stray source, tell me its name and ID.

**The DPS/HPS column looks cut off.** Widen the window a little, or it may just be scrolled — the per-second value is the rightmost column.

**The addon doesn't load.** Check the folder is exactly `Interface\AddOns\SchoolPop\` and contains `SchoolPop.toc`, `SchoolPop.lua`, `SchoolPop_ProcDB.lua`, `SchoolPop_DropDB.lua`, `Bindings.xml` and a `Fonts` folder. At the character screen, click AddOns and make sure SchoolPop is ticked; if it says "out of date", tick **Load out of date AddOns**.

**I want to see Lua errors.** Type `/console scriptErrors 1` once — the game hides them by default.

**Where's my exported log?** Paste it from the Export window, or after logging out look in `WTF\Account\<your account>\SavedVariables\SchoolPopExport.lua`.

---

## Version history

See `CHANGELOG.txt` inside the SchoolPop folder for the full list of changes.

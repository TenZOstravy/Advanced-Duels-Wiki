# Messages & Languages

All player-facing text lives in `plugins/AdvancedDuels/langs/`. There is no `messages.yml`.

## Selecting a language

```yaml
lang: lang_EN
```

Available files: `lang_EN`, `lang_DE`, `lang_ES`, `lang_FR`, `lang_PL`, `lang_RU`, `lang_CZ`. Restart (or `/duels reload`) after changing.

If your selected file is outdated compared to the jar, the console warns you — and any keys you are missing are merged in automatically with a backup, so updating never deletes your edits.

## Editing messages

- Open `plugins/AdvancedDuels/langs/lang_<XX>.yml` and edit values. Keys must stay exactly as they are.
- Placeholders like `%player%`, `%kit%`, `%arena%`, `%bet_amount%` are replaced at runtime — never delete or rename them.
- `{PREFIX}` is defined once at the top under `STRINGS:` and reused everywhere. Change it in one place to rebrand every message.
- Colors use `&` codes by default. Set `use-minimessages: true` in `config.yml` to use MiniMessage formatting instead.

!!! warning "Never rename keys or placeholders"
    Renaming a key (e.g. `spectate:` → `watch:`) or a placeholder (e.g. `%kit%` → `%set%`) silently breaks that message — the plugin logs `Failed to load message` and sends nothing for it.

## Adding a new language

1. Copy `langs/lang_EN.yml` to `langs/lang_MY.yml`.
2. Translate the **values only**.
3. Set `lang: lang_MY` in `config.yml` and restart.

## MiniMessage

With `use-minimessages: true`, messages support MiniMessage tags (`<red>`, `<bold>`, gradients, ...). The `lang_minimessages.yml` file shipped in the jar shows the same messages in MiniMessage style as a reference.

## PlaceholderAPI fallback texts

These five small texts at the bottom of `config.yml` are used when data is unavailable:

| Key | Shown when |
|---|---|
| `user-not-found` | Placeholder requested for a player with no loaded data |
| `not-in-match` | Placeholder needs a match but the player has none (`none`) |
| `duration-format` | Match duration format (`mm:ss`) |
| `no-kit` | Duel uses own inventory instead of a kit (`none`) |
| `no-opponent` | Opponent placeholder with no opponent (`No opponent`) |

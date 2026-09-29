

[Back to README](readme.md)

# 📝 Character Policy for Memory Titles

We now follow SillyTavern’s behavior: titles/comments are broadly permissive. STMemoryBooks only removes control characters; all other printable Unicode is allowed. Memory content remains completely unrestricted.

## 🎯 Scope

Applies to:
- 🏷️ AI-extracted titles (`{{title}}`)
- 👤 Character names (`{{char}}`)
- 🧑‍💻 User names (`{{user}}`)
- 📋 Final lorebook entry titles/comments
- 🎨 Text used in title format templates

Does NOT apply to:
- 📝 Memory content (no restrictions)
- 💬 Original chat message content

## ✅ Allowed Characters

Everything that is printable Unicode is allowed in titles/comments, including (but not limited to):
- Latin letters, numbers, spaces, and punctuation
- International scripts (accents, Cyrillic, CJK, Arabic, etc.)
- Quotes and apostrophes (single and double)
- Symbols like `&`, `+`, `!`, `$`, `@`, `_`
- Emojis and pictographs

We do not impose a custom “allowed list” anymore.

## ❌ Removed Characters

Only control characters are removed during sanitization:
- C0 and C1 controls: `U+0000–U+001F`, `U+007F–U+009F`

If a title becomes empty after cleaning (e.g., it contained only control characters), we fall back to `"Auto Memory"` to ensure the lorebook entry is still created.

## 📊 Examples

| Input | Output | Status |
|-------|--------|--------|
| `Test Memory` | `Test Memory` | ✅ |
| `[001] - Scene` | `[001] - Scene` | ✅ |
| `René's Story` | `René's Story` | ✅ Quotes, accents preserved |
| `Сергей` | `Сергей` | ✅ Cyrillic preserved |
| `先生の話` | `先生の話` | ✅ CJK preserved |
| `O'Malley & Co.` | `O'Malley & Co.` | ✅ Symbols preserved |
| `Test_Name + Debug!` | `Test_Name + Debug!` | ✅ Underscore and symbols preserved |
| `😀🎯🧠` | `😀🎯🧠` | ✅ Emojis preserved |
| `<control>\u0007Beep</control>` | `<control>Beep</control>` | ⚠️ Control char removed |
| `\u0008\u0009` | `Auto Memory` | ⚠️ Only controls → fallback |

## 🔢 Template and Numbering Notes

- Title templates can include any printable characters. Only control characters will be stripped.
- Numbering tokens in formats are flexible. Common supported examples include:
  - `[000]`, `(000)`, `{000}`, `#000`
  - Wrapped forms like `#[000]`, `([000])`, `{[000]}`
- Extraction logic is resilient and can derive sequence numbers from many shapes, including `#7-8` (uses the last number).

## 🛡️ Why This Policy?

1. Aligns with SillyTavern’s permissive handling of text
2. Preserves user intent and formatting in titles
3. Keeps compatibility and reduces surprise removals
4. Still prevents problematic control characters

## 🧭 Migration Notes

- Previously, we aggressively filtered punctuation, symbols, underscores, quotes, and non-ASCII. That is no longer the case.
- Existing lorebook entries are unchanged. New titles will preserve more characters.
- If your workflow depended on strict filtering, consider adjusting templates instead of relying on sanitization.

## 💡 Pro Tips

1. Keep titles readable and consistent for easy browsing
2. Put long or complex details in the memory content
3. Use title templates to establish structure (e.g., numbering, date/time)
4. Preview titles to confirm they look the way you expect

[Back to README](readme.md)

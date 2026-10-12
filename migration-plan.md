# Example migration plan: schema 1 to 2

- Rename `messages.prefix` to `text.prefix` while retaining the configured value.
- Preserve all unrelated and unknown keys.
- If both old and new keys exist, prefer the new key and emit a warning.
- Validate the resulting types before writing.
- Create a timestamped backup and use an atomic replacement.
- Re-running the migration must not change the resulting file.

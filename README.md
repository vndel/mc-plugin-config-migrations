# Minecraft Plugin Config Migrations

Patterns for evolving plugin configuration while preserving operator intent. Treat config changes as data migrations: document them, make them deterministic, and validate them against realistic fixtures.

## Migration rules
- Preserve unknown keys unless there is a documented reason to remove them.
- Never overwrite an existing user configuration with defaults during upgrade.
- Make each migration idempotent and advance the schema version only after success.
- Write to a temporary file, validate the result, then replace atomically where supported.
- Back up the original and report exactly which keys changed.
- Keep secrets out of migration logs and test fixtures.

Test upgrade paths from every supported schema version and verify both successful migration and recovery from malformed input. Do not silently replace invalid configuration.
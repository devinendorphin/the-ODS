# Profile Layer — Overview

The profile layer is the foundation of the ODS. It is what makes the agent *you* rather than a generic assistant.

## Structure

```
profile/
├── README.md                    ← this file
├── public_identity.md           ← who you are publicly; your voice and work [PUBLIC]
├── values.md                    ← your positions, red lines, principles [PUBLIC]
├── affective_network.md         ← your people; schema + current entries [PRIVATE data]
└── systems/
    ├── ny_benefits.md           ← NY benefits monitoring framework [PRIVATE data]
    └── surveillance_context.md  ← [to be built] known threat landscape
```

## Public vs. Private

**Public files** are intentionally committed to this public repository. They form the simulatability substrate — the coherent, well-documented public record that makes distortion and erasure harder.

**Private data** within files marked `[PRIVATE]` should never be committed to public repositories in populated form. The schema and template are public; your actual case numbers, contact information, and network entries are not.

When you're ready to run the agent locally, private data lives in a local config file (`.env` or `private_config.json`) that is `.gitignore`d.

## What Gets Built Next

The profile layer feeds the monitoring layer. Once the profile is sufficiently rich:

1. The agent knows what systems to watch (from `systems/`)
2. The agent knows what matters (from `values.md`)
3. The agent knows how to speak (from `public_identity.md`)
4. The agent knows who to protect (from `affective_network.md`)

See `BLUEPRINT.md` for the full architecture.

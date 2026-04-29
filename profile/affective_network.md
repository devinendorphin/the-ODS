# Affective Network — Schema & Template

*[PRIVATE — This template is public; actual entries should not be committed to public repositories.]*

---

## Purpose

The Affective Network is a structured map of the relationships the user wishes the agent to consider when making decisions about protection, communication, and resource allocation. It is not a contact list. It is a registry of qualitative, sentimental, and emotional bonds — the people whose well-being is within the agent's scope of concern.

---

## Schema

Each entry in the affective network follows this structure:

```json
{
  "id": "unique_internal_identifier",
  "relationship_type": "friend | family | chosen_family | collaborator | community_member",
  "bond_quality": "description of the nature of the bond",
  "current_situation": "what is currently happening for this person",
  "known_needs": ["list", "of", "known", "needs"],
  "active_support": ["list", "of", "ways", "the user is currently helping"],
  "threat_flags": ["known risks or vulnerabilities for this person"],
  "privacy_level": "how much detail the agent may share about this person with others",
  "contact_channels": "how to reach them (stored privately, never in this file)"
}
```

---

## Example Entry (Anonymized)

```json
{
  "id": "friend_name_change_01",
  "relationship_type": "friend",
  "bond_quality": "close friend navigating a complex identity transition",
  "current_situation": "Pursuing legal name change in New York State; process is difficult and stressful",
  "known_needs": [
    "Navigation assistance for NY Supreme Court name change petition",
    "Information about safety waivers for publication requirement",
    "Emotional support during process"
  ],
  "active_support": [
    "Research and documentation of NY name change process",
    "Accompaniment and advocacy if needed"
  ],
  "threat_flags": [
    "Publication requirement creates potential outing risk if not sealed",
    "Document update process is long and each gap period creates risk"
  ],
  "privacy_level": "high — no identifying details shared externally without explicit permission",
  "contact_channels": "[stored in private config only]"
}
```

---

## NY Name Change Quick Reference

For the friend currently navigating this process:

**Step 1: File a Petition**
- Supreme Court of the county where you live
- Forms: UD-11 (petition), UCS-NC1 (for any relevant checks)
- Filing fee: ~$65 (fee waiver available if income-eligible)

**Step 2: Publication (or Waiver)**
- Normally required: publish in two newspapers for one week
- **Safety exception**: Trans and non-binary people, domestic violence survivors, and others at risk can request the court seal the name change and waive publication. This is well-established in NY.
- Request the sealing at the time of filing. Judges routinely grant this.

**Step 3: Court Order**
- Judge issues an Order Granting Name Change
- Get certified copies — you'll need several (usually 3–5)

**Step 4: Update Documents (in this order)**
- Social Security Administration (first — everything else follows)
- NYS DMV (driver's license/ID)
- Passport (if applicable)
- Birth certificate (NYS Dept of Health — can update gender marker too)
- Banks, insurance, Medicaid, SNAP case records

**Timeline:** From filing to order: 4–8 weeks typically. Document updates: add another 1–3 months for the full chain.

**Cost waiver:** If on public benefits (Medicaid, SNAP, cash assistance), you likely qualify for fee waivers at every step. Ask explicitly.

---

## Maintenance Protocol

This file is reviewed and updated:
- When a person's situation significantly changes
- When new people enter the scope of care
- On a regular cadence (suggested: monthly)

Entries are never deleted — they are archived with a date and a reason, preserving the history of the network.

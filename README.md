# A Consumer Vehicle Accessory With No Working Trust Boundary

Firmware analysis of an Android automotive AI Box, and what it says about the
reference design behind it.

**Jay Puckett (Reckoner)** - Principal Security Researcher, Obsidian Watch Group
Version 1.0, published 2026-09-01

---

## Scope, and what is deliberately not here

Some threads remain open and some questions are unresolved. Both are marked as such
throughout rather than smoothed over: Appendix E lists what was observed but not
confirmed, and what was not attempted at all.

**Reproduction procedures are withheld**, and some findings with them, because the
affected hardware is in public use and the material is on a federal disclosure
track. That omission is deliberate and is not an oversight.

This is a maintained record. Where new evidence changes a finding, the finding is
updated in place and the paper remains the authoritative version.

If something here is wrong, the useful thing is to say so.

---

## Contents

| File | |
|---|---|
| `00_FRONT_AND_ACQUISITION.md` | Disclosure status, abstract, subject device, acquisition |
| `01_ANALYSIS_METHOD.md` | Method, and what it does not cover |
| `02_TRUST_AND_IDENTITY.md` | What the device claims to be, and the signing model |
| `03_CONTROL_AND_COLLECTION.md` | Control of the head unit, the services that persist, what was collected |
| `04_DELIVERY_SUPPLY_AND_PROOF.md` | Code delivery channels, the reference design, proof of concept |
| `05_DISCLOSURE_AND_CLOSE.md` | Disclosure history, and every check that could have caught this |
| `06_APPENDICES.md` | Indicator catalogue, evidence manifest, tooling, open items |

Read the disclosure status in the front matter before quoting anything.

---

## Thanks

**HaleHound™** built the hardware that makes this kind of work possible for an
independent researcher. Purpose-built RF and wireless survey tools, priced so that
somebody without a lab budget can actually own one, and supported by people who
answer when you ask a question.

**Saleae** extended a researcher discount that put precision logic analysis within
reach of a one-person practice. Their instruments are not the cheap option, and the
company chose to make them reachable anyway for somebody doing this work without an
employer behind him.

Their instrument was used in work that is not published here. It is credited even
though its output is not, because it earned the credit either way.

A great deal of security research never happens because the instrumentation is out
of reach. Jesse and the HaleHound team, and Saleae, are a direct answer to that.
This paper is one of the things that exists because they made the tools available.

Thank you, both of you.

---

## Scope

Analysis of a device purchased at retail with the researcher's own money, examined
on the researcher's own equipment. No third-party system was accessed. No production
vendor endpoint was contacted during the proof of concept.

Vehicle-safety analysis is carried in a separate case document routed to NHTSA,
Auto-ISAC and CISA. Chapter 10.5 summarizes it here.

## Reuse

Cite it, quote it, argue with it. If you reproduce a finding, reproduce the
qualification attached to it. Several of the strongest-sounding claims in this paper
are deliberately bounded, and the bounds are the reason the rest can be trusted.

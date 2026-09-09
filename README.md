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

Their analyzer did bus-level work that is not published here, and will not be.

That is not modesty and it is not a teaser. It is withheld because of what it is.
The hardware is in public use, there is no patch, and the vehicles are on the road
today. Publishing the method would hand it to anyone who wanted it, against people
who never agreed to be part of anyone's research and who cannot fix it themselves.
The capability is stated so regulators can act. The procedure stays with the
agencies, and the omission is permanent.

The instrument is credited even though its output is not, because it earned the
credit either way. Some of the most consequential work an instrument does is work
nobody gets to see.

**Valley Tech Custom Solutions** belongs here for a different reason. Kal did not
send an instrument. He kept faith with independent developers while a coordinated
campaign was running against him, and went on crediting the people being accused
alongside him rather than distancing himself to make it stop. Character under
pressure is worth more to this field than a discount, and it is rarer.

A great deal of security research never happens because the instrumentation is out
of reach. These three are a direct answer to that, and this paper is one of the
things that exists because of it.

**That is the whole list.** Not a selection from a longer one. Three small companies
decided that somebody working alone, with no employer and no lab budget, was worth
backing before he had anything to offer them. Every one of these relationships began
with credit given, not with a request made.

Thank you, all three of you.

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

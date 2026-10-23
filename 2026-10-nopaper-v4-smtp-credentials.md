# Unauthenticated exposure of SMTP credentials in NoPaper V4 Construtor

| | |
|---|---|
| Product | NoPaper V4, "Construtor" public module |
| Vendor | PH Informática e Micro Sistemas, SA (Portugal) |
| Vulnerability class | Exposure of sensitive information to an unauthorized actor (CWE-200); unprotected credentials in a server response (CWE-522) |
| Severity | High (reporter's assessment) |
| Status | Fixed by the vendor on 2026-10-22 for all affected customers |
| Reported by | Paulo Villalobos |
| CVE | Not assigned |

## Summary

The public, unauthenticated "Construtor" page of NoPaper V4 called a server-side page method on load whose JSON response included the platform's outbound email configuration, with the SMTP host, port, username and password in clear text. Any visitor to the public page received the credential in their browser.

NoPaper is used by Portuguese municipalities to publish and process administrative procedures. Because the method is part of the shipped product, the exposure was not specific to one installation.

## Impact

A holder of the credential could send email as the configured municipal account, which enables convincing phishing against citizens and other public bodies. Access to the mailbox itself depends on the account's permissions and was not tested.

## Remediation

The vendor confirmed on 2026-10-22 that the issue is resolved for the reporting municipality and for all other affected customers, and coordinated the rotation of the exposed credential with the municipality.

Operators of NoPaper V4 should confirm they run the fixed version and rotate any SMTP credential that was configured before 2026-10-22.

## Timeline

- 2026-10-22: Exposure observed on one municipal installation while browsing its public procedure catalogue. The credential was not used or stored.
- 2026-10-22: Reported to the municipality, the vendor and CERT.PT (CNCS).
- 2026-10-22: Vendor confirmed the fix for the reporting municipality and all other affected customers.
- 2026-10-23: CERT.PT acknowledged the report.
- 2026-10-23: Advisory published, after the fix was confirmed for all affected customers.

## Method

Observation was limited to the response a normal visitor's browser receives on a public page. No authentication was bypassed, no other installations were tested, and no data was kept. The research followed Article 8-A of the Portuguese Cybercrime Law (Lei 109/2009, as amended by DL 125/2025).

## Credit

Paulo Villalobos ([github.com/paulovillalobos](https://github.com/paulovillalobos)).

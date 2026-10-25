# Source notes for the reference list (Fardin)

Working notes for the 17 IEEE references in the plan: where each one was checked, what the plan uses it for,
and anything to be careful about if you're asked about it. Numbers in brackets are the plan's reference numbers
(order of first citation). All online sources were accessed 24 Oct 2026.

| # | Source | Checked at | Used in | What the plan takes from it |
|---|---|---|---|---|
| [1] | Verizon, *2026 Data Breach Investigations Report: Executive summary* | verizon.com/business/resources/executivebriefs/2026-dbir-executive-summary.pdf | §1, §2.1 | Vulnerability exploitation (31%) now outranks credential abuse (13%) as the initial way in worldwide; credential abuse is still 25% in Asia-Pacific; credentials were compromised in 25% of healthcare breaches. **Careful:** don't say stolen credentials are the #1 way in any more. |
| [2] | OAIC media release, 6 Jul 2026 (2025 NDB statistics) | oaic.gov.au/news/media-centre/… | §1 | 1,205 notifications in 2025, the highest since the scheme began; health service providers were the top sector (225, 19%). |
| [3] | OAIC, *Notifiable Data Breaches Report: July to December 2024* | oaic.gov.au/privacy/notifiable-data-breaches/… | §2.1 | Of 247 cyber incidents, 151 involved credentials (phishing 84, stolen credentials 51, brute force 16; 151 is our sum of the table). Health was the top sector (121, 20%). |
| [4] | Meyer et al. (Microsoft), "How effective is multifactor authentication at deterring cyberattacks?" | arxiv.org/abs/2305.00945 | §2.2 | MFA reduced the risk of compromise by 99.22% (98.56% for accounts with leaked credentials). **Careful:** preprint, not peer-reviewed; Microsoft authors using Azure AD data only. The plan says so. |
| [5] | CISA, "Implementing phishing-resistant MFA" fact sheet | cisa.gov (PDF) | §2.2 | Ranks MFA types; SMS/voice is a "last resort"; FIDO/WebAuthn is the "gold standard"; start with admins and other high-value targets. |
| [6] | NIST SP 800-63B-4 (Jul 2025) | csrc.nist.gov/pubs/sp/800/63/b/4/final | §2.2, §13 | Final since 31 Jul 2025 (replaces 800-63B). AAL2 must offer a phishing-resistant option; SMS/voice is "restricted"; no forced periodic password changes. |
| [7] | ASD, *Essential Eight maturity model* (last reviewed 27 Nov 2023) | cyber.gov.au/publication/essential-eight-maturity-model | §2.2, §2.3, §3, §13 | Maturity Level Two requires phishing-resistant MFA; privileged access revalidated every 12 months (or removed after 45 days inactive). |
| [8] | Gordon et al., *JAMA Network Open* 2019 | pmc.ncbi.nlm.nih.gov/articles/PMC6484661 | §2.2 | ~2.97 million simulated phishing emails at six US health institutions; 14.2% clicked. Repeated campaigns lowered click rates. |
| [9] | Reynolds et al., USENIX Security 2020 | usenix.org/conference/usenixsecurity20/presentation/reynolds | §2.3 | Mandatory 2FA at two universities: more than 1 in 20 attempts failed or were abandoned; many separate login services multiply the burden. |
| [10] | Cobrado et al., *Informatics in Medicine Unlocked* 2024 | Crossref record for doi 10.1016/j.imu.2024.101552 | §2.3 | Systematic review (20 studies) of EHR access control: attribute-based models most common; gaps in MFA, emergency access and accountability. **Careful:** details were confirmed from the DOI registry and abstract because the publisher page was blocked. Open the DOI once yourself to double-check. |
| [11] | NIST SP 800-207 *Zero Trust Architecture* (2020) | csrc.nist.gov/pubs/sp/800/207/final | §2.3 | Identity plus attributes as the basis for policy; migrate one business process at a time; run new policies in report-only mode first. |
| [12] | PMI, *PMBOK Guide*, 8th ed. (2025) | pmi.org/standards/pmbok | §2.4, §8 | Published Nov 2025; principles and seven performance domains; tailoring. Place of publication (Newtown Square) is PMI's usual imprint — check against a library record. |
| [13] | ISO 21502:2020 | iso.org/standard/74947.html | §2.4 | Project management guidance that applies to predictive, iterative and hybrid delivery. |
| [14] | ISO 31000:2018 | iso.org/standard/65694.html | §2.4, §8 | Generic risk process: identify, analyse, evaluate, treat, monitor. Does not define EMV; EMV is standard practice, so it isn't cited to a source. |
| [15] | Willumsen et al., *Int. J. Project Management* 2019 | research.cbs.dk + Crossref | §2.4, §8 | The value of project risk management depends on how stakeholders perceive and use it. |
| [16] | ISO 9001:2026 | iso.org/standard/88464.html | §13 | Published 16 Sep 2026; ISO 9001:2015 is withdrawn, which is why the plan cites the 2026 edition. |
| [17] | ISO/IEC 27001:2022 | iso.org/standard/27001 | §13 | ISMS requirements. The plan names the access-control topics but not Annex A control numbers, because those weren't checked against the standard. |

## Where the sources agree and disagree (for questions in the walkthrough)

- **Is any MFA good enough?** Microsoft's data [4] says almost any MFA removes ~99% of account takeovers. CISA [5], NIST [6] and the Essential Eight [7] say SMS/codes are weak and require or prefer phishing-resistant MFA. The healthcare phishing data [8] explains why: codes can be phished. Plan decision: passkeys/FIDO2 for everyone.
- **Are credentials still the main threat?** Globally no [1], but in Asia-Pacific, in healthcare [1] and in Australian notifications [3] they're still central. Plan decision: IAM is necessary but not sufficient; patching stays out of scope.
- **Roles or attributes?** EHR research [10] and NIST [11] lean to attribute-based rules; standards don't prescribe one. Plan decision: roles from HR job codes plus site/shift conditions.
- **Quarterly access reviews?** No source requires them; the Essential Eight requires yearly revalidation of admin access [7]. Plan decision: quarterly because of the risk, and the plan says it's a choice, not a mandate.
- **Which delivery approach?** PMBOK [12] and ISO 21502 [13] don't pick one; risk research [15] says process only helps if people use it. Plan decision: hybrid (gates and change control, plus iterative SSO waves).

Version: NAFATH-V1
Track: AI

## Overview
A government authority plans to provide citizens with one digital identity for accessing multiple services through a website and mobile app. OpenID Connect supports identity verification, while OAuth 2.0 controls delegated access to protected resources. An AI system may flag suspicious logins, but incorrect or biased decisions could deny legitimate users access. Android permissions limit unnecessary access to device features, and DNS over HTTPS protects DNS traffic between clients and their resolvers. Phishing-resistant authenticators help prevent credential theft through imitation login pages. Oman's applicable personal-data legislation and government policies shape how citizen information is processed and safeguarded. These fields must work together: secure protocols, trustworthy AI, privacy protections, and accountable decisions all contribute to public confidence in the national service.
## Software
OAuth 2.0 is an authorization framework that allows applications to receive limited access to protected resources, commonly through access tokens. It does not, by itself, define a standard way to authenticate users. OpenID Connect (OIDC) builds an identity layer on OAuth 2.0, introducing an ID Token that conveys authentication information to the client. For the national service, OIDC supports user sign-in, whereas OAuth 2.0 enables delegated access to government APIs.

Resource: OpenID Connect Core 1.0 incorporating errata set 2 - https://openid.net/specs/openid-connect-core-1_0.html
## AI
Using NIST AI RMF 1.0, the authority should Govern responsibilities, Map impacts, Measure performance, and Manage identified risks. Before deployment, it should test false positives that block legitimate citizens, missed attacks, unequal outcomes across groups, privacy exposure, and adversarial manipulation. Representative test data, documented thresholds, human review of disputed flags, and fallback access procedures reduce harm. After launch, the team should monitor model drift and reassess security, fairness, and reliability as threats evolve.

Resource: Artificial Intelligence Risk Management Framework (AI RMF 1.0), NIST AI 100-1 - https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf
## Mobile
Android isolates apps through application sandboxing and restricts access to sensitive capabilities. On Android 6.0 (API 23) and later, apps using the runtime permission model must request dangerous permissions, such as camera or location access, while the app is running. The national login app should request only necessary permissions when their features are used, explain the request in context, and handle denial or later revocation. Basic sign-in should not depend on unrelated permissions.

Resource: Request runtime permissions | Android Developers - https://developer.android.com/training/permissions/requesting
## Networking
DNS over HTTPS (DoH), defined in RFC 8484, sends DNS queries and responses over an encrypted HTTPS connection to a selected resolver. It reduces interception and modification of DNS traffic along that path. However, the resolver can still observe queries, and DoH does not hide the destination IP address or encrypt the entire browsing session. It also does not independently verify DNS records without additional protections such as DNSSEC. Website HTTPS remains essential.

Resource: RFC 8484 - DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484
## Cybersecurity
Phishing-resistant authentication uses cryptographic binding to the legitimate verifier or authenticated channel, preventing attackers from simply reusing credentials captured on fake sites. Under NIST SP 800-63B, correctly implemented FIDO2/WebAuthn authenticators, including passkeys, and suitable PKI smart cards can provide phishing resistance. Manually entered SMS, email, or authenticator-app one-time codes are not phishing-resistant because they can be relayed. The authority should prioritize appropriately implemented phishing-resistant multi-factor authentication.

Resource: NIST SP 800-63B - Digital Identity Guidelines: Authentication and Authenticator Management - https://pages.nist.gov/800-63-4/sp800-63b.html
## Data
Oman's Personal Data Protection Law (Royal Decree 6/2022, amended by 68/2026) exempts processing by government bodies when exercising powers assigned by law. Such bodies fall under the government's Personal Data Protection Policy (Circular 6/2024), which addresses privacy notices, secure handling, access, disclosure, and transfers. The authority should verify the exemption for each processing activity, apply the relevant policy, restrict unnecessary collection, and establish safeguards for citizen records. Non-exempt processing must meet applicable statutory requirements.

Resource: Personal Data Protection | Ministry of Transport, Communications and Information Technology - https://www.mtcit.gov.om/sectors/governance/personal
## Misconception in My Track
A common misconception is that high test accuracy makes a suspicious-login AI model safe to deploy. NIST AI RMF 1.0, Section 3, "AI Risks and Trustworthiness," explains why accuracy alone is insufficient: systems can be accurate yet opaque, or secure yet unfair. A model may wrongly flag legitimate users, perform differently across groups, or deteriorate as attacks change. The authority should therefore measure false-positive and false-negative rates, assess fairness and explainability, document decisions, provide human review and recovery, and continue monitoring after release. Trustworthiness is a lifecycle responsibility, not a single accuracy score.
## Open Question
How can the authority audit false-positive rates across citizen groups while minimizing sensitive-data collection, and what measurable review and account-recovery deadlines should apply to wrongly flagged logins?

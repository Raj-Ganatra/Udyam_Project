# Privacy and security note

This prototype treats synthetic case records as if they were real customer information. It shows a consent gate before order placement, limits collection to customer contact details, business profile and the identifiers used for KYC demonstration, and masks identifiers returned by the verification API. The stated purpose is order processing and KYC/service provisioning.

The mock registry endpoints query only the supplied synthetic GSTIN and Udyam CSV files; they do not contact government systems. Uploaded documents are stored locally for this demo. A production deployment must use encrypted object storage, TLS, access controls, malware scanning, signed upload URLs, audit logging and automated deletion based on an approved retention schedule. Logs and analytics must not contain full identifiers, phone numbers or document contents.

Only the minimum business profile and catalogue recommendations should be sent to the LLM. Identity documents and full government identifiers must never be sent to the AI provider. API keys stay on the backend. Add authentication, role-based authorization, rate limiting, incident response and legal review before production. This note is a prototype design summary, not a legal compliance certification.

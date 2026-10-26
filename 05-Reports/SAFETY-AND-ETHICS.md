# Lab Safety and Ethical Boundaries

## Authorisation first
- Test only systems I own or have explicit permission to assess.
- Keep practice inside isolated VMs, local networks, or approved training platforms.
- Confirm the target scope and allowed techniques before beginning.
- Do not perform unauthorised scanning, exploitation, credential attacks, persistence, or disruption.

## Protect information
- Never commit passwords, API keys, access tokens, private keys, session cookies, or recovery codes.
- Keep secret configuration in local environment variables or an appropriate secrets manager.
- Review staged files before publishing.
- Sanitise personal data, sensitive IP addresses, internal hostnames, and packet captures.
- Do not publish real customer data or confidential organisational logs.

## Keep labs safe
- Prefer host-only or internal virtual networks for vulnerable VMs.
- Take VM snapshots before risky configuration changes.
- Keep intentionally vulnerable machines isolated from the internet and production networks.
- Use test accounts and synthetic data.
- Stop if an activity affects systems outside the authorised scope.

## Report responsibly
- Describe methods accurately and provide reproducible evidence without exposing secrets.
- Explain impact, limitations, and remediation.
- Do not claim a vulnerability exists without sufficient evidence.
- Follow applicable laws, platform rules, and responsible disclosure procedures.

## Pre-publication checklist
- [ ] No credentials or secrets
- [ ] No confidential or personal data
- [ ] Target and scope are authorised
- [ ] Screenshots and outputs are sanitised
- [ ] Commands are explained and results are accurate
- [ ] Cleanup steps are documented

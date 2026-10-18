# Incident Response Workflow: Brute Force (T1110)

Triggered by the analytics rule **Brute Force – Excessive Failed Logons from Single IP**.

## 1. Validate the alert
- Confirm the burst of failed logons (Event ID 4625) in the alert's 5-minute window.
- Review the logon type: RDP (type 10) vs. network (type 3).
- Run the triage hunt in `detection/brute-force-failed-logons.kql` to check whether the same IP later produced a **successful** logon (Event ID 4624). A success after many failures is the strongest sign of compromise.

## 2. Assess scope and impact
- Check whether the source IP targeted multiple accounts (`TargetedAccounts` custom detail).
- Check how many hosts the IP touched (`Host` custom detail, incident graph).
- Review historical activity for the affected accounts.

## 3. Containment
- Temporarily disable the affected account if compromise is suspected.
- Block the source IP with network security controls (e.g., NSG rule).

## 4. Escalation and documentation
- Escalate to Tier 2 if a successful logon or lateral movement is suspected.
- Record findings, actions, and resolution in the incident record.

**MITRE ATT&CK:** T1110 – Brute Force (Credential Access, TA0006)

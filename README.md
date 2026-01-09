SOC-focused Sentinel authentication detection lab

## Incident Response Workflow

When this analytics rule triggers, the following SOC triage steps are performed:

1. Validate the alert
   - Confirm failed and successful logons occurred within the defined time window
   - Review logon types (RDP vs network)

2. Assess scope and impact
   - Check whether the source IP has targeted multiple accounts
   - Review historical activity for the affected account

3. Containment actions
   - Temporarily disable the affected account if compromise is suspected
   - Block the source IP using network security controls

4. Escalation and documentation
   - Escalate to Tier 2 if lateral movement is suspected
   - Document findings and resolution in the incident record

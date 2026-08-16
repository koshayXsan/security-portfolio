# Incident Response Case Study: XYZ University Worm Outbreak

Information Security & Management coursework analyzing a real-world style incident: a Win32.VB worm outbreak at a university lab, caused by outdated antivirus software. Covers root cause analysis, policy recommendations, incident response process mapping, stakeholder roles, severity classification, and an evaluation framework for information security management effectiveness.

---

## Case Summary

An employee (John) noticed a warning message indicating a Win32.VB worm infection. The antivirus software present on the system failed to catch it because it hadn't been updated. The worm spread across multiple lab machines before IT and the incident response team intervened, forcing a one-day suspension of lab activities.

---

## 1. Key Observations

- **Outdated antivirus software** was the root security lapse. It existed but wasn't effective because it wasn't kept current.
- **An alert employee** caught the issue early through basic vigilance (slow internet, unusual file names) and reported it instead of ignoring it.
- **Lack of network segmentation** let the worm spread across multiple machines with little resistance.
- **Operational disruption**: a full day of lab downtime, showing that security failures have real business/academic impact, not just technical ones.
- **No internal incident handling capability**: the case had to be escalated externally, suggesting the organization lacked in-house expertise for large-scale incidents.

---

## 2. Recommended Information Security Policies

**Patch Management**
- Frequent, automated updates for antivirus, OS, and applications
- Regular vulnerability scanning, prioritized by exploit potential and severity

**Employee Awareness & Training**
- Recurring cybersecurity training covering phishing, social engineering, and safe computing practices
- Clear reporting path for suspicious activity

**Incident Response Plan**
- Documented procedures for detection, reporting, containment, eradication, and recovery
- Defined roles per stakeholder group
- Regular tabletop exercises to pressure-test the plan

**Network Segmentation & Access Control**
- Segment the network to limit lateral movement during a breach
- Role-based access control and principle of least privilege

**Data Security**
- Encrypt sensitive data at rest and in transit
- DLP tooling to monitor and control data exfiltration

**Vulnerability Management**
- Scheduled vulnerability assessments and penetration testing

**Third-Party Risk Management**
- Formal vendor security assessment framework tied to the org's own policy

---

## 3. Incident Response Process & Lessons Learned

1. **Detection** – John noticed abnormal system behavior and acted on it instead of dismissing it.
2. **Reporting** – Followed the existing protocol to escalate to IT/security contact.
3. **Investigation** – System logs reviewed, infected machines isolated, antivirus scans run to identify the worm variant.
4. **Containment** – Infected machines isolated to stop lateral spread; scope of infection assessed.
5. **Eradication** – Safe-mode scans, reinstalling OS where needed, patching all systems to prevent recurrence.
6. **Recovery** – Restoring from backups, verifying data integrity, redeploying software before bringing labs back online.
7. **Post-incident review** – Root cause analysis, impact assessment, and identifying gaps to close before the next incident.

---

## 4. Stakeholders & Containment/Recovery Measures

| Group | Role |
|---|---|
| **Employees** | First line of detection; trained to spot phishing, suspicious emails, and abnormal system behavior |
| **System Administrator** | Identifies infected machines, isolates them, analyzes logs/traffic, coordinates eradication |
| **Management** | Allocates resources, makes continuity/recovery-priority decisions, owns communication strategy |
| **Legal & PR** | Engaged if the incident involves data breach or regulatory exposure; manages disclosure obligations and public messaging |

**Containment & recovery practices:**
- Transparent, regular stakeholder communication without leaking details that could compromise the investigation
- Offsite backups tested regularly, not just taken
- Post-incident, targeted retraining on the specific vulnerability that was exploited

---

## 5. Severity Assessment & Detection Improvements

**Severity: Medium**
- **Impact** – One day of lab downtime, no confirmed data loss or critical system compromise
- **Scope** – Multiple machines infected within a single lab network, not org-wide
- **Disruption** – Meaningful but contained operational impact

**Recommended detection improvements:**
- **IDS/IPS** for real-time alerting on unauthorized access or malware behavior
- **EDR** for deeper endpoint visibility than traditional antivirus provides
- **Ongoing security awareness training** so employees catch the early signs faster next time

---

## 6. Evaluating ISM Program Effectiveness

Effectiveness should be assessed across five areas:

- **Policy & procedures** – coverage of patch management, access control, data security, incident response
- **Employee awareness** – training frequency/relevance, and whether staff feel safe reporting issues
- **Technical safeguards** – firewalls, IDS/IPS, antivirus, and whether they're actually maintained
- **Vulnerability management** – cadence of assessments/pen tests and how patching is prioritized
- **Incident response readiness** – documented plan, tested via tabletop exercises, clear ownership

**Core recommendations:**
- Build a comprehensive security policy covering acceptable use, password management, data classification, access control, and incident response
- Run continuous (not one-off) security awareness training
- Keep technical safeguards patched and properly configured, not just installed
- Run a real vulnerability management program, not ad hoc scans
- Build and rehearse an incident response plan with a dedicated response team if resourcing allows

**Why it matters:** a working ISM program reduces attack likelihood, speeds up incident recovery, protects sensitive data, and keeps the organization aligned with regulatory/compliance expectations.

---

📄 [Full assignment writeup (PDF)](./response_plan.pdf)

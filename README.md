# Enterprise Intune Enrollment Project
A complete solution to migrate 180+ unmanaged devices (Windows &amp; macOS) into [Microsoft Intune](https://www.microsoft.com/en-us/security/business/microsoft-intune) using automation, compatibility checks, and leadership-focused communications.

## Problem
The client needed to migrate over 2,000 user devices across 11 subsidiaries into Microsoft Intune. While most were successfully onboarded, 180+ devices were unaccounted for and could not be enrolled remotely.

### Challenges
- A remote, non-technical user base, often unaware of IT compliance requirements.
- Manual enrollment processes that were error-prone, time-consuming, and inconsistent.
- Limited leadership buy-in across subsidiaries, slowing adoption.
- Seasonal workload variations that made timing and prioritization critical.

## Solution
To address these issues, a multi-pronged approach was designed:
1. Device Identification & Pathways
   - Developed scripts (Windows PowerShell + macOS Bash) to scan compatibility, OS version, and enrollment readiness.
   - Created clear enrollment pathways for each device type: upgrade, Autopilot, admin-assisted, or replacement.
2. User Engagement & Surveys
   - Deployed targeted surveys to collect device details from end users where technical data was missing.
   - Mapped survey responses against script results to close visibility gaps.
3. Communication & Scheduling
   - Built a SharePoint hub site as the central self-service portal with:
   - Enrollment guides
   - FAQ and troubleshooting
   - Integrated Microsoft Bookings so users could schedule IT enrollment sessions without back-and-forth emails.
   - Published a communications playbook for subsidiary leadership to drive awareness and accountability.
4. Reporting & Dashboards
   - Created Power BI and JIRA dashboards with real-time visibility into enrollment progress, broken down by subsidiary and device category.
   - Automated reporting flows using Power Automate + Microsoft Graph API, cutting manual tracking efforts.

```mermaid
---
config:
  layout: dagre
---
flowchart TD
 subgraph P1["Phase 1: Discovery"]
        A1["Inventory export - AAD_Entra, HRIS, ConnectWise"]
        A2["Unknown device list - 180+"]
        A3["SharePoint Hub: guides, FAQ"]
        A4["Compatibility scripts - Win PS, macOS Bash"]
        A5["User Survey - Forms to fill gaps"]
  end
 subgraph P2["Phase 2: Plan & Pathways"]
        B1["Normalize data: Power Automate"]
        B2["Map users ↔ devices"]
        B3{"Pathway decision"}
        B3a["Autopilot/ABM ready"]
        B3b["Upgrade OS/firmware"]
        B3c["Admin-assisted/remote"]
        B3d["Replace device"]
  end
    A1 --> A2
    A2 --> A3
    A3 --> A4
    A4 --> A5
    B1 --> B2
    B2 --> B3
    B3 --> B3a & B3b & B3c & B3d

 %% PHASE 3: ENGAGE
 subgraph P3["Phase 3: Engage & Schedule"]
        C1["SharePoint Hub: guides, FAQ"]
        C2["Targeted comms (leaders + users)"]
        C3["MS Bookings self-serve slots"]
        C4["Subsidiary rollout calendar (seasonality)"]
    C1 --> C2 --> C3 --> C4
  end

  %% PHASE 4: ENROLL
  subgraph P4["Phase 4: Enrollment Execution"]
        D1["OneDrive/Files backup verification"]
        D2["Run enrollment scripts"]
        D3["Autopilot/ABM provisioning"]
        D4["Admin-assisted join (remote/in-person)"]
        D5["Device replacement logistics"]
    D1 --> D2
    D2 --> D3
    D2 --> D4
    D2 --> D5
  end

  %% PHASE 5: VALIDATE
  subgraph P5["Phase 5: Validate & Report"]
    E1["Compliance policy assignment"]
    E2["Conditional Access check"]
    E3["App provisioning (Win/Mac)"]
    E4["Health checks & success criteria"]
    E5["Dashboards: Power BI + JIRA"]
    E6["Automations (Graph API, Power Automate)"]
    E1 --> E2 --> E3 --> E4 --> E5 --> E6
  end

  %% PHASE 6: SUSTAIN
  subgraph P6["Phase 6: Sustain & Improve"]
    F1["Leadership cadence & SLA reviews"]
    F2["Refine playbooks & training"]
    F3["Backlog: stragglers & exceptions"]
    F4["Telemetry-driven optimizations"]
    F1 --> F2 --> F3 --> F4
  end

P1 --> P2 --> P3 --> P4 --> P5 --> P6
```


## Results
- 180+ previously unknown devices identified and processed through structured pathways.
- 90% reduction in enrollment-related support tickets, freeing IT staff for higher-priority work.
- Cut rollout time by 3 months, thanks to automation and self-service.
- Leadership adoption improved significantly due to clear reporting and scheduled sessions, ensuring sustained compliance.200+ devices enrolled securely.
  
## Lessons Learned
- Leadership alignment was just as critical as technical execution.
- Mobile-first, simplified training content drove adoption in a younger, non-technical workforce.
- Embedding self-service tools (SharePoint, Bookings) reduced friction and scaled IT’s impacLeadership buy-in was just as critical as technical execution.

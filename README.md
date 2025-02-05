# Vulnerability Management Program Implementation

In this project, we simulate the implementation of a comprehensive vulnerability management program, from inception to completion.

_**Inception State:**_ the organization has no existing policy or vulnerability management practices in place.

_**Completion State:**_ a formal policy is enacted, stakeholder buy-in is secured, and a full cycle of organization-wide vulnerability remediation is successfully completed.

---

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/cfc5dbcf-3fcb-4a71-9c13-2a49f8bab3e6">

# Technology Utilized
- Tenable (enterprise vulnerability management platform)
- Azure Virtual Machines (Nessus scan engine + scan targets)
- PowerShell & BASH (remediation scripts)

---


# Table of Contents

- [Vulnerability Management Policy Draft Creation](#vulnerability-management-policy-draft-creation)
- [Mock Meeting: Policy Buy-In (Stakeholders)](#step-2-mock-meeting-policy-buy-in-stakeholders)
- [Policy Finalization and Senior Leadership Sign-Off](#step-3-policy-finalization-and-senior-leadership-sign-off)
- [Mock Meeting: Initial Scan Permission (Server Team)](#step-4-mock-meeting-initial-scan-permission-server-team)
- [Initial Scan of Server Team Assets](#step-5-initial-scan-of-server-team-assets)
- [Vulnerability Assessment and Prioritization](#step-6-vulnerability-assessment-and-prioritization)
- [Distributing Remediations to Remediation Teams](#step-7-distributing-remediations-to-remediation-teams)
- [Mock Meeting: Post-Initial Discovery Scan (Server Team)](#step-8-mock-meeting-post-initial-discovery-scan-server-team)
- [Mock CAB Meeting: Implementing Remediations](#step-9-mock-cab-meeting-implementing-remediations)
- [Remediation Round 1: Outdated Wireshark Removal](#remediation-round-1-outdated-wireshark-removal)
- [Remediation Round 2: Insecure Protocols & Ciphers](#remediation-round-2-insecure-protocols--ciphers)
- [Remediation Round 3: Guest Account Group Membership](#remediation-round-3-guest-account-group-membership)
- [Remediation Round 4: Windows OS Updates](#remediation-round-4-windows-os-updates)
- [First Cycle Remediation Effort Summary](#first-cycle-remediation-effort-summary)

---

### Vulnerability Management Policy Draft Creation

This phase focuses on drafting a Vulnerability Management Policy as a starting point for stakeholder engagement. The initial draft outlines scope, responsibilities, and remediation timelines, and may be adjusted based on feedback from relevant departments to ensure practical implementation before final approval by upper management.  
[Draft Policy](https://docs.google.com/document/d/1CLSWm1_9JL1oUqgyNNwtPXW6FzXJ7ddVnSAUQTyqC8I/edit?usp=drive_link)

---

### Step 2) Mock Meeting: Policy Buy-In (Stakeholders)

In this phase, a meeting with the server team introduces the draft Vulnerability Management Policy and assesses their capability to meet remediation timelines. Feedback leads to adjustments, like extending the critical remediation window from 48 hours to one week, ensuring collaborative implementation.

# Policy Remediation Discussion  

## Participants  
- **Josh**  
- **Jimmy**  

## Conversation  

**Josh:** *Hey, good morning, Jimmy. How’s everything been? I know everyone’s been busy these last few weeks.*  

**Jimmy:** *Good morning, Josh. Yeah, it’s been a bit hectic, but we’re hanging in there. Thanks for asking. I had a chance to read through the policy draft, and overall, it makes sense. However, with our current staffing, we can’t meet the aggressive remediation timelines—especially the 48-hour window for critical vulnerabilities.*  

**Josh:** *Yeah, I totally understand. It is a bit aggressive, especially to start. Perhaps we can extend the critical vulnerability deadline to one week as a compromise for now. We could then reserve the 48-hour window for truly severe zero-day vulnerabilities.*  

**Jimmy:** *That sounds reasonable. We appreciate the flexibility. Can we also have some leeway in the beginning as we get used to the remediation and patching process? Maybe just for the first few months?*  

**Josh:** *Absolutely. After the policy is finalized, we’ll officially start the program, but we’re planning to give all departments about six months to adjust and get comfortable with the new process. Does that sound fair?*  

**Jimmy:** *Thanks, Josh. We’ll do our best. I appreciate you including us in the decision-making process—it really helps us feel like we’re part of the solution.*  

**Josh:** *Of course! We’re all in this together. Thanks for working with us.*  

**Jimmy:** *No problem. Thanks for the quick meeting.*  

**Josh:** *Yeah, those are my favorite types. Bye now!*  

**Jimmy:** *See you later!*  


---

### Step 3) Policy Finalization and Senior Leadership Sign-Off

After gathering feedback from the server team, the policy is revised, addressing aggressive remediation timelines. With final approval from upper management, the policy now guides the program, ensuring compliance and reference for pushback resolution.  
[Finalized Policy](https://docs.google.com/document/d/1rvueLX_71pOR8ldN9zVW9r_zLzDQxVsnSUtNar8ftdg/edit?usp=drive_link)
<div style="text-align: center;">
    <img src="https://github.com/user-attachments/assets/9afcdbc1-0493-4af2-9287-1cb9b8f59b40" alt="image" width="400">
</div>

---

### Step 4) Mock Meeting: Initial Scan Permission (Server Team)

The team collaborates with the server team to initiate scheduled credential scans. A compromise is reached to scan a single server first, monitoring resource impact, and using just-in-time Active Directory credentials for secure, controlled access.  

# Vulnerability Scanning Discussion  

## Participants  
- **Josh**  
- **Jimmy**  

## Conversation  

**Josh:** *Good morning, Jimmy.*  

**Jimmy:** *Good morning! I heard you're ready to conduct some scans.*  

**Josh:** *Yep! Now that our vulnerability management policy is in place, I want to start scheduled credential scans of your environment.*  

**Jimmy:** *Sounds good to me. What’s involved, and how can we help?*  

**Josh:** *We’re planning to schedule weekly scans of the server infrastructure. It should take about 4 to 6 hours to scan all 2,200 assets. We’ll need administrative credentials so the scan engine can remotely log in and assess the targets.*  

**Jimmy:** *Hold on—what exactly does scanning entail? I’m a bit concerned about resource utilization. Also, you need admin credentials for all 200 machines? That doesn’t sound safe.*  

**Josh:** *Those are valid concerns. The scan engine sends different types of traffic to the servers to check for vulnerabilities, such as outdated software, insecure protocols, or weak ciphers. It also looks into the registry to assess system security, which is why credentials are required.*  

**Jimmy:** *I see. As long as it doesn’t take the servers offline, we should be okay.*  

**Josh:** *Absolutely. Let’s start by scanning a single server and monitor resource utilization.*  

**Jimmy:** *Not a bad idea.*  

**Josh:** *Also, for the credentials, can you set up an Active Directory account for us? You can keep it disabled until we’re ready to scan, then enable it during the scan and disable it afterward. Kind of like a just-in-time access setup.*  

**Jimmy:** *That sounds good. I’ll ask Susan to get started on automating the account provisioning.*  

**Josh:** *Awesome. Talk soon!*  

**Jimmy:** *Sounds good. I’ll get back to you once the credentials are set up. See you later!*  

**Josh:** *See you later!*  


---

### Step 5) Initial Scan of Server Team Assets

In this phase, an insecure Windows Server is provisioned to simulate the server team's environment. After creating vulnerabilities, an authenticated scan is performed, and the results are exported for future remediation steps.  

<img width="635" alt="image" src="https://github.com/user-attachments/assets/937cccbd-36bb-4445-97b9-e915085cda81" style="border: 2px solid black;">

[Scan 1 - Initial Scan](https://drive.google.com/file/d/1RBPVj_azKJMwmRZ8QILlb4hxIjQU3wQ7/view?usp=drive_link)




---

### Step 6) Vulnerability Assessment and Prioritization

We assessed vulnerabilities and established a remediation prioritization strategy based on ease of remediation and impact. The following priorities were set:

1. Third Party Software Removal (Wireshark)
2. Windows OS Secure Configuration (Protocols & Ciphers)
3. Windows OS Secure Configuration (Guest Account Group Membership)
4. Windows OS Updates

---

### Step 7) Distributing Remediations to Remediation Teams

The server team received remediation scripts and scan reports to address key vulnerabilities. This streamlined their efforts and prepared them for a follow-up review.  

<img width="635" alt="image" src="https://github.com/user-attachments/assets/bbf9478f-e1d1-4898-846e-b510ec8c6f72">

[Remediation Email](https://github.com/joshmadakor1/lognpacific-public/blob/main/misc/remediation-email.md)

---

### Step 8) Mock Meeting: Post-Initial Discovery Scan (Server Team)

The server team reviewed vulnerability scan results, identifying outdated software, insecure accounts, and deprecated protocols. The remediation packages were prepared for submission to the Change Control Board (CAB). 

# Vulnerability Scan Review & Remediation Plan  

## Participants  
- **Josh**  
- **Jimmy**  

## Conversation  

### Scan Results  

**Josh:** *Good morning, Jimmy! How are you doing?*  

**Jimmy:** *Not bad for a Monday. And you?*  

**Josh:** *Still alive, so I can't complain! Before we get into the vulnerabilities, how did the actual scan go? Any outages or resource overutilization?*  

**Jimmy:** *The scan went well. We were monitoring the systems, and aside from the open connections, we wouldn’t have even known a scan was happening.*  

**Josh:** *That’s great news! As expected, no major resource utilization issues. We’ll continue monitoring, but I don’t foresee any problems. Do you mind if we dive into the vulnerability findings?*  

**Jimmy:** *Absolutely, go ahead.*  

**Josh:** *I’ll share my screen. The majority of vulnerabilities are due to outdated installations of Wireshark. It’s significantly out of date and needs to be updated or removed.*  

### Key Findings  

1. **Wireshark Installations:**  
   - Outdated versions present across multiple servers.  

2. **Local Guest Account Permissions:**  
   - The local guest account is part of the **Local Administrators** group.  
   - Needs investigation and potential removal.  

3. **Software & OS Updates:**  
   - Some vulnerabilities, such as **Microsoft Edge Chromium**, may be automatically resolved with Windows updates.  

4. **TLS & Cipher Suite Issues:**  
   - **Deprecated Cipher Suites (Medium Strength).**  
   - **TLS 1.0 and 1.1 detected (deprecated protocols).**  
   - These need remediation to align with security best practices.  

### Remediation Plan  

**Jimmy:** *Interesting findings. The good news is that most of our servers probably have the same vulnerabilities, so remediation should be uniform.*  

**Josh:** *That’s actually a plus—it simplifies the fix. Do you foresee any challenges in remediating the cipher suites and insecure protocols?*  

**Jimmy:** *I highly doubt there will be issues. We’ll run it through the Change Control Board. As for Wireshark and the guest account, those shouldn’t be on the servers in the first place, so removing them won’t be a problem. I’ll check with our CIS admins about the guest account.*  

**Josh:** *Sounds good. I’ll start building remediation packages to make fixing these easier.*  

### Patch Management & Next Steps  

**Jimmy:** *By the way, do you have anything in place for handling Windows Update-related vulnerabilities?*  

**Josh:** *Yes, our patch management should take care of those automatically by next week.*  

**Jimmy:** *Perfect. I’ll research the best ways to remediate these issues and get back to you before the next Change Control Board.*  

**Jimmy:** *Sounds good. Talk to you soon!*  

**Josh:** *Cool, talk to you soon!*  
)

---

### Step 9) Mock CAB Meeting: Implementing Remediations

The Change Control Board (CAB) reviewed and approved the plan to remove insecure protocols and cipher suites. The plan included a rollback script and a tiered deployment approach.  


---
### Step 10 ) Remediation Effort

**Remediation Round 1: Outdated Wireshark Removal**

The server team used a PowerShell script to remove outdated Wireshark. A follow-up scan confirmed successful remediation.  
[Wireshark Removal Script](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/remediation-wireshark-uninstall.ps1)  

<img width="634" alt="image" src="https://github.com/user-attachments/assets/7b4f9ab2-d230-4458-ac0f-c0ff070ae79a">

[Scan 2 - Third Party Software Removal](https://drive.google.com/file/d/1UiwPPTtuSZKk02hiMyXf31pXUIeC5EWt/view?usp=drive_link)


**Remediation Round 2: Insecure Protocols & Ciphers**

The server team used PowerShell scripts to remediate insecure protocols and cipher suites. A follow-up scan verified successful remediation, and the results were saved for reference.  
[PowerShell: Insecure Protocols Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-protocols.ps1)
[PowerShell: Insecure Ciphers Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-cipher-suites.ps1)

<img width="630" alt="image" src="https://github.com/user-attachments/assets/0e96120d-8ec9-4f76-8e42-79c752200010">

[Scan 3 - Ciphersuites and Protocols](https://drive.google.com/file/d/1Qc6-ezQvwReCGUZNtnva0kCZo_-zW-Sm/view?usp=drive_link)


**Remediation Round 3: Guest Account Group Membership**

The server team removed the guest account from the administrator group. A new scan confirmed remediation, and the results were exported for comparison.  
[PowerShell: Guest Account Group Membership Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-guest-local-administrators.ps1)  

<img width="627" alt="image" src="https://github.com/user-attachments/assets/870a3eac-3398-44fe-91c0-96f3c2578df4">

[Scan 4 - Guest Account Group Removal](https://drive.google.com/file/d/1jVgikjfrV1YjOcL3QRT_oUB0Y82w22V7/view?usp=drive_link)


**Remediation Round 4: Windows OS Updates**

Windows updates were re-enabled and applied until the system was fully up to date. A final scan verified the changes  

<img width="627" alt="image" src="https://github.com/user-attachments/assets/870a3eac-3398-44fe-91c0-96f3c2578df4">

[Scan 5 - Post Windows Updates](https://drive.google.com/file/d/1tmDjeHl5uiGitRwWy8kFRi33q-nGi1Zt/view?usp=drive_link)

---

### First Cycle Remediation Effort Summary

The remediation process reduced total vulnerabilities by 80%, from 30 to 6. Critical vulnerabilities were resolved by the second scan (100%), and high vulnerabilities dropped by 90%. Mediums were reduced by 76%. In an actual production environment, asset criticality would further guide future remediation efforts.  

<img width="1920" alt="image" src="https://github.com/user-attachments/assets/51f0aae8-7f36-4d90-b29f-5257e57155f9">

[Remediation Data](https://docs.google.com/spreadsheets/d/1FTtFfZYmFsNLU6pm8nTzsKyKE-d2ftXzX_DPwcnFNfA/edit?gid=0#gid=0)

---

### On-going Vulnerability Management (Maintenance Mode)

After completing the initial remediation cycle, the vulnerability management program transitions into **Maintenance Mode**. This phase ensures that vulnerabilities continue to be managed proactively, keeping systems secure over time. Regular scans, continuous monitoring, and timely remediation are crucial components of this phase. (See [Finalized Policy](https://docs.google.com/document/d/1rvueLX_71pOR8ldN9zVW9r_zLzDQxVsnSUtNar8ftdg/edit?usp=drive_link) for scanning and remediation cadence requirements.)

Key activities in Maintenance Mode include:
- **Scheduled Vulnerability Scans**: Perform regular scans (e.g., weekly or monthly) to detect new vulnerabilities as systems evolve.
- **Patch Management**: Continuously apply security patches and updates, ensuring no critical vulnerabilities remain unpatched.
- **Remediation Follow-ups**: Address newly identified vulnerabilities promptly, prioritizing based on risk and impact.
- **Policy Review and Updates**: Periodically review the Vulnerability Management Policy to ensure it aligns with the latest security best practices and organizational needs.
- **Audit and Compliance**: Conduct internal audits to ensure compliance with the vulnerability management policy and external regulations.
- **Ongoing Communication with Stakeholders**: Maintain open communication with teams responsible for remediation, ensuring efficient coordination.

By maintaining an active vulnerability management process, organizations can stay ahead of emerging threats and ensure long-term security resilience.

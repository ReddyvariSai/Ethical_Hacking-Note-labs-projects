# **Company Intelligence: The Social Engineer's Corporate Blueprint**

Company intelligence is the **strategic collection and analysis of organizational data** to identify vulnerabilities, understand internal dynamics, and craft highly targeted social engineering attacks. It transforms public information into a detailed roadmap for corporate intrusion.

---

## **Core Concept**
This intelligence layer focuses on understanding the **organization as a system**—its people, processes, technologies, and culture—to identify the most effective attack vectors and pretexts.

### **Why It's So Powerful:**
1. **Contextual Precision:** Attacks are tailored to specific departments, roles, and company events.
2. **Authority Mimicry:** Understanding hierarchy enables perfect executive impersonation.
3. **Cultural Exploitation:** Leverages company-specific jargon, processes, and pressure points.
4. **Timing Optimization:** Aligns attacks with business cycles, mergers, crises, or deadlines.

---

## **Intelligence Categories & Sources**

| Category | Key Intelligence | Sources | Social Engineering Application |
|:---|:---|:---|:---|
| **Organizational Structure** | Hierarchy, departments, reporting lines | LinkedIn, org charts, email signatures | Impersonating superiors, targeting specific roles |
| **Employee Data** | Names, roles, contact info, tenure | Hunter.io, ZoomInfo, company directories | Personalized spear phishing, vishing name-drops |
| **Technology Stack** | Software, platforms, vendors | BuiltWith, Wappalyzer, job postings | IT support scams, fake vendor communications |
| **Financial Health** | Revenue, funding, stock performance | Crunchbase, SEC filings, news | Fake investor/auditor pretexts, merger scams |
| **Operational Rhythms** | Deadlines, busy seasons, events | Social media, press releases, calendars | Urgency creation, event-based pretexts |
| **Security Posture** | Policies, training frequency, past incidents | Job postings, vendor pages, news | Bypassing controls, exploiting known weaknesses |

---

## **Key Tools for Corporate Intelligence Gathering**

### **1. Professional Network Analysis**
**LinkedIn Sales Navigator** is the gold standard:
```python
# Typical attack reconnaissance flow
1. Search: "Current company: Acme Corp, Title: Accounts Payable"
2. Filter: "2nd degree connections, Recently posted, Active"
3. Extract: 
   - Department structure (who reports to whom)
   - New hires (most vulnerable to policy questions)
   - Employees mentioning "stress" or "overwhelmed"
   - Job changes (recent promotions = authority targets)
```

**Intel Gained:**
- **Authority Mapping:** Who has approval authority for payments?
- **Influence Networks:** Who do employees trust/respect?
- **Pain Points:** Who's complaining about processes?
- **Onboarding Targets:** New employees unfamiliar with procedures

### **2. Corporate Communication Pattern Analysis**
**Tools:** Hunter.io, VoilaNorbert, Clearbit Connect
```
Email Pattern Discovery:
→ Format detection: first.last@company.com, f.last@company.com
→ Department aliases: ap@, it@, hr@, security@
→ Executive variations: e.first@, initials@

Communication Analysis:
- Response times (who answers quickly?)
- Formality levels (formal vs. casual culture)
- Common phrases/lingo ("circle back," "EOD," "ASAP")
```

### **3. Technology Footprinting**
**BuiltWith/Wappalyzer** reveals:
```json
{
  "company": "Acme Corp",
  "cms": "WordPress 6.2",
  "crm": "Salesforce Enterprise",
  "communication": "Slack, Zoom, Microsoft Teams",
  "cloud": "AWS, Azure AD",
  "finance": "QuickBooks Online, Bill.com",
  "security": "Okta SSO, CrowdStrike EDR"
}
```
**Attack Vector Identification:**
- Salesforce login = fake "session expired" phishing
- QuickBooks = fake invoice scams
- Slack = impersonation in public channels
- Azure AD = fake MFA push fatigue attacks

### **4. Financial & Event Intelligence**
**Sources:** Crunchbase, SEC Edgar, Google Alerts
```
Key Intelligence Indicators:
• Just raised $50M Series C → Growth pressure, hiring spree
• Q4 earnings next week → Urgent "confidential" pretexts  
• CEO speaking at RSA Conference → Travel absence exploitation
• Recent layoffs announced → Morale low, processes disrupted
• Merger rumors with Beta Inc → Fake integration communications
```

---

## **The Corporate Attack Matrix**

### **Department-Specific Targeting**

| Department | Vulnerabilities | Pretext Examples |
|:---|:---|:---|
| **Finance/AP** | Payment urgency, invoice processing | Fake vendor invoices, CEO wire requests |
| **HR** | Employee data access, onboarding | Fake background check requests, policy updates |
| **IT Help Desk** | Password resets, access provisioning | Fake employee lockout calls, "urgent" access needs |
| **Executive Assistants** | Calendar control, gatekeeping | Fake meeting changes, document requests |
| **Sales** | Commission urgency, client pressure | Fake lead notifications, bonus structure changes |
| **New Hires** | Policy uncertainty, desire to please | Fake onboarding tasks, "HR" compliance requests |

### **Temporal Attacks (Right Time, Right Pretext)**
```python
# Attack Calendar Builder
attacks = {
    "Monday AM": ["Weekend system alerts", "Urgent Monday meetings"],
    "Month-end": ["Invoice processing", "Commission calculations"],
    "Q4": ["Budget use-it-or-lose-it", "Annual report prep"],
    "Post-conference": ["Follow-up requests", "Travel expense issues"],
    "Post-merger": ["Integration tasks", "New system logins"]
}
```

### **Cultural Exploitation**
```
Company Culture Analysis → Tailored Approach
──────────────────────────────────────────────
"Fast-paced startup": Use urgency, break-glass scenarios
"Corporate hierarchical": Use authority, formal tone
"Remote-first": Exploit isolation, lack of in-person verification
"Security-conscious": Mimic security team, use jargon
```

---

## **Advanced Corporate Intelligence Techniques**

### **1. Supply Chain Mapping**
```python
# Identify third-party vulnerabilities
$ python3 supply_chain_map.py --company "Acme Corp"

VENDOR DISCOVERY:
• IT Managed Services: "TechSupport Inc"
• Cloud Provider: "AWS, Azure"
• Payment Processor: "Stripe, PayPal"
• Law Firm: "LegalPartners LLP"
• Cleaning Service: "OfficeClean Co"

ATTACK VECTORS:
1. Impersonate TechSupport for network access
2. Fake AWS bill requiring "immediate payment"
3. Fake LegalPartners subpoena request
4. OfficeClean uniform for physical access
```

### **2. Physical Office Intelligence**
**Google Street View + Satellite Imagery:**
- Building entrances/exits
- Parking lots (badge swipe locations)
- Dumpster locations (for document retrieval)
- Smoking areas (eavesdropping opportunities)

**Job Postings Analysis:**
```
Security Analyst posting reveals:
• "Experience with CrowdStrike and Proofpoint"
• "Monitors SIEM alerts during business hours"
• "Participates in quarterly phishing tests"

Translation for attackers:
• They use CrowdStrike (target for evasion)
• Limited after-hours monitoring
• Phishing tests happen quarterly (employees alert)
```

### **3. Internal Process Reverse Engineering**
From public data:
- **Invoice approval limits:** "All invoices >$10k require CFO approval"
- **New vendor onboarding:** "7-day vendor approval process" 
- **Remote access:** "VPN required for external access, RSA tokens"
- **Incident response:** "Report suspicious emails to security@"

**Process Exploitation:**
```
Fake "Urgent Vendor Payment" Attack:
1. Send invoice for $9,999 (below approval threshold)
2. Use actual vendor name from past invoices
3. Reference real PO format from leaked documents
4. Send to AP clerk identified as "quick responder"
```

---

## **Real-World Attack Scenarios**

### **Scenario 1: The Strategic Merger Play**
```
Intelligence: 
- Acme Corp acquiring Beta Inc (press release)
- Integration team: John (Acme), Sarah (Beta)
- Using SharePoint for document sharing

Attack:
From: john.smith@acme.com (spoofed)
To: sarah.j@beta.com

"Sarah - urgent integration doc on SharePoint. 
Can't access Beta's instance. Please upload to:
https://acme-sharepoint-fake.com/login
Use your Beta credentials for access tracking."

(Steals Beta credentials, accesses pre-merger data)
```

### **Scenario 2: The Vendor Exploitation Chain**
```
1. Identify Acme's primary SaaS vendor: "CloudSuite Inc"
2. Find CloudSuite's support portal: support.cloudsuite.com
3. Spoof: "CloudSuite Security Alert <security@cloudsuite-support.com>"
4. Email Acme IT: "Critical vulnerability in your instance. Click to patch."
5. Malware drops, establishes foothold in Acme's network
```

### **Scenario 3: The Physical-Social Hybrid**
```
Intelligence:
- Office layout: Main entrance has reception, side door for deliveries
- Uniform: Delivery drivers wear "QuickDrop" uniforms
- Timing: Lunch hour (12-1 PM) has minimal security

Attack:
1. Purchase QuickDrop uniform online
2. Arrive at 12:30 PM with "urgent package for CFO"
3. "Need signature immediately" pressure
4. Tailgate employee through side door
5. Plant malicious device in server room
```

---

## **Defensive Countermeasures**

### **1. Intelligence Minimization**
| Data Type | Protection Strategy |
|:---|:---|
| **Employee Directories** | Limit public access, use generic contact forms |
| **Email Formats** | Use non-standard formats, implement aliases |
| **Technology Stack** | Obfuscate with generic headers, limit disclosure |
| **Org Charts** | Keep internal, avoid LinkedIn org mapping |
| **Financial Data** | Control timing of public disclosures |

### **2. Process Hardening**
```
Verification Protocols:
• Payment changes: Always callback to known number
• New vendors: Multi-person approval, physical verification
• Credential resets: In-person or video verification required
• Urgent requests: Mandatory secondary channel confirmation
```

### **3. Employee Training Focus Areas**
- **New Hire Security Briefings:** First week, emphasis on verification
- **Department-Specific Scenarios:** Finance (invoices), HR (data requests), IT (access)
- **Executive Protection:** Assistants as human firewalls
- **Physical Security Awareness:** Tailgating, social engineering at entrances

### **4. Technical Controls**
```yaml
corporate_intelligence_defense:
  monitoring:
    - dark_web_monitoring: "Employee credential exposure"
    - domain_monitoring: "Spoofed domains, typosquats"
    - social_media_monitoring: "Executive impersonation"
  
  access_controls:
    - principle_of_least_privilege: "Departmental data segregation"
    - attribute_based_access: "Time, location, device context"
    - session_monitoring: "Anomalous access patterns"
  
  communication_protection:
    - dmarc/dkim/spf: "Email authentication"
    - banner_notices: "External email warnings"
    - encrypted_channels: "For sensitive communications"
```

---

## **The Corporate Intelligence Marketplace**

### **Commercial Intelligence Services** (Used by Both Sides)
```
LEGITIMATE SERVICES:          DARK WEB EQUIVALENTS:
──────────────────────────    ──────────────────────────
• ZoomInfo ($15k+/year)       • "Full corporate dumps" ($5k+)
• DiscoverOrg                 • "Employee database leaks"
• LinkedIn Recruiter          • "LinkedIn scraped databases"
• Clearbit                    • "Email validation services"
• Crunchbase Pro              • "Private financial forecasts"
```

### **Asymmetric Advantage:**
**Attackers** often have **fresher data** from:
- Recent breaches not yet public
- Insider threats selling current org charts
- Real-time social media scraping
- Dumpster diving/physical intelligence

**Defenders** must assume attackers have **90%+ accurate intelligence** about their organization.

---

## **The Future: AI-Driven Corporate Intelligence**

### **Predictive Targeting Systems:**
```python
# AI that identifies ideal targets
ai_target_scoring(
    employee_data,
    social_activity,
    breach_history,
    department_role
) → vulnerability_score

# Output: "Sarah Johnson (AP Clerk): 94% susceptibility"
# Reasons: New hire, active on social, reused passwords
```

### **Dynamic Pretext Generation:**
```
Current Event: "Acme Corp Q2 earnings miss"
AI Generates:
1. CFO impersonation: "Urgent financial restatement"
2. Investor relations: "Shareholder damage control"
3. PR department: "Media response coordination"
4. Legal: "SEC investigation preliminary questions"
```

### **Organization-Wide Weakness Mapping:**
```
AI Analysis of Acme Corp:
• Communication Gaps: IT-Finance handoff unclear
• Process Exceptions: Emergency payment bypass exists
• Cultural Pressure: Sales team commission-driven urgency
• Technology Debt: Legacy system with weak auth
```

---

## **Key Insight**

**Company intelligence transforms social engineering from a numbers game to a surgical strike.** Modern attackers don't just send phishing emails; they:

1. **Understand the organizational nervous system**—who makes decisions, who has access, where pressure points exist.
2. **Speak the internal language**—using correct jargon, referencing actual projects, mimicking communication styles.
3. **Time attacks to organizational rhythms**—quarter ends, mergers, system migrations, busy seasons.
4. **Exploit process weaknesses** identified through public information.

**The most dangerous insight:** Attackers often understand a company's internal processes **better than new employees do**, and sometimes better than the company understands itself.

**Defense requires:** 
- Assuming your corporate intelligence is already in adversary hands
- Building verification into every process, not just exceptional ones
- Creating a culture where "unusual but plausible" requests trigger verification
- Regularly conducting intelligence gathering on your own organization to see what's exposed

The line between competitive intelligence and attack reconnaissance has blurred completely. What appears as innocent LinkedIn browsing or public financial analysis is often the first phase of a sophisticated social engineering operation. Organizations must defend not just their networks, but their **informational footprint** with equal vigilance.

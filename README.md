# 📘 iVend Add-on Documentation Guidelines

This repository defines a lean and scalable documentation workflow for iVend Add-on development using AI prompts (Claude Code).

---

## ⚡ Quick Start (Follow These Steps)

Use this guide when starting any new iVend Add-on development.

### 🧭 Step-by-Step Workflow

1. **Create BRD**

   * Describe the business requirement
   * Generate using BRD prompt

2. **Create PRD**

   * Convert BRD into detailed functional document
   * Customer-facing (no technical details)

3. **Create IMPL**

   * Developer implementation plan
   * Includes classes, methods, DB, validations

4. **Write & Run Unit Tests**

   * Create UT document
   * Execute tests → generate UT-RESULT

5. **Perform QA Testing**

   * Create QA Test Plan (80–120 cases)
   * Execute → generate QA-RESULT

6. **Code Review (PR)**

   * Review PR using PR-RESULT prompt

7. **(Optional) Create User Manual**

   * Only if needed for customer

---

## 🎯 In Scope

The following documents are part of the standard iVend Add-On workflow:

* BRD — Business Requirement Document
* PRD — Product Requirement Document
* IMPL — Implementation Plan
* UT — Unit Test Specification
* UT-RESULT — Unit Test Execution Result
* QA — QA Test Plan
* QA-RESULT — QA Execution Result
* PR-RESULT — Peer Review Result
* UM — User Manual *(Optional)*

---

## 📂 Repository Structure

### ✅ Case 1: Single Feature / Simple Add-on

Use this when:

* Only **one CR / feature**
* No major enhancements

```id="single2"
iVend-Addon-Project/
├── docs/
│   ├── 1. BRD-FeatureName-iVendAddOn.md
│   ├── 2. PRD-FeatureName-iVendAddOn.md
│   ├── 3. IMPL-FeatureName-iVendAddOn.md
│   ├── 4. UT-FeatureName-iVendAddOn.md
│   ├── 4.1 UT-FeatureName-iVendAddOn-RESULT.md
│   ├── 5. QA-FeatureName-iVendAddOn.md
│   ├── 5.1 QA-FeatureName-iVendAddOn-RESULT.md
│   ├── 6. PR-FeatureName-iVendAddOn-RESULT.md
│   ├── 7. UM-FeatureName-iVendAddOn.md   (Optional)
```

---

### ✅ Case 2: Multiple CRs / Enhancements in Same Add-on

Use this when:

* Multiple CRs (Change Requests)
* Continuous enhancements in same add-on

```id="multi2"
iVend-Addon-Project/
├── docs/
│   ├── CRD-XXXX/
│   │   ├── 1. BRD-FeatureName-iVendAddOn.md
│   │   ├── 2. PRD-FeatureName-iVendAddOn.md
│   │   ├── 3. IMPL-FeatureName-iVendAddOn.md
│   │   ├── 4. UT-FeatureName-iVendAddOn.md
│   │   ├── 4.1 UT-FeatureName-iVendAddOn-RESULT.md
│   │   ├── 5. QA-FeatureName-iVendAddOn.md
│   │   ├── 5.1 QA-FeatureName-iVendAddOn-RESULT.md
│   │   ├── 6. PR-FeatureName-iVendAddOn-RESULT.md
│   │   ├── 7. UM-FeatureName-iVendAddOn.md   (Optional)
```

📌 Example:

```id="exmulti2"
docs/
 ├── CRD-001/
 ├── CRD-002/
 ├── CRD-003/
```

---

## 🔄 Documentation Lifecycle (MANDATORY ORDER)

```id="flow4"
BRD → PRD → IMPL → UT → QA → PR
                   ↓     ↓
             UT-RESULT  QA-RESULT
```

📌 Optional:

```id="flow5"
→ UM (User Manual)
```

---

## ⚠️ Core Rules

* Always follow document sequence
* Each document depends on previous
* Do NOT skip BRD or PRD
* Use CRD-based folder for multiple changes
* UM should NOT delay delivery

---

## 🧠 AI Prompt Workflow

👉 Copy the below prompts into Claude Code and generate documents step-by-step.

---

## 1️⃣ BRD — Business Requirement Document

**When:** Feature idea is ready  
**Input:** Business understanding + optional customer doc

```id="brd3"
I need to build a new iVend Add-On or implement an enhancement to an existing iVend Add-On for iVend Retail.

Here's what it should do:
[Describe the feature in your own words — 3-5 sentences. What problem does it solve? Who needs it? If porting from another system, mention that.]

Customer Requirement Document (optional but recommended):
[Attach or paste the customer-shared requirement document, email, or specification here]

Create a BRD (Business Requirements Document) for this. Include business objectives, scope, stakeholders, functional requirements, validation rules with error messages, non-functional requirements, acceptance criteria (numbered AC-01 to AC-XX), and a glossary.
Save as:
docs/CRD-XXXX/1. BRD-[FeatureName]-iVendAddOn.md
(or directly under docs/ if single CR)
```

---

## 2️⃣ PRD — Product Requirement Document

**When:** BRD is done.  
**Input:** The BRD you just created.  
⚠️ This is a **customer-facing document** — keep it simple and non-technical

```id="prd3"
You are a business analyst creating a Product Requirements Document (PRD)
for an iVend Retail add-on project.
 
Read the BRD document from:
docs/CRD-XXXX/1. BRD-[FeatureName]-iVendAddOn.md

👉 If this is a single CR / standalone feature, read from:
docs/1. BRD-[FeatureName]-iVendAddOn.md
 
Create a concise, customer-friendly PRD and Save the document as:
docs/CRD-XXXX/2. PRD-[FeatureName]-iVendAddOn.md

👉 If this is a single CR / standalone feature, save it under:
docs/2. PRD-[FeatureName]-iVendAddOn.md
 
---
 
DOCUMENT HEADER
Include a header table at the top with these fields:
  - Customer      : [Customer Name]
  - Project       : [Project Code, e.g. CXS.A1CC – CRD005]
  - Platform      : [e.g. iVend Retail 6.6 (Management Console + Point of Sale)]
  - Prepared by   : CitiXsys Custom Development Team
  - Document date : [Today's date]
  - Version       : 1.0
  - Status        : Draft — Pending Customer Approval
 
---
 
TABLE OF CONTENTS
After the header, add a numbered Table of Contents listing all sections
in the document.
 
---
 
SECTIONS TO INCLUDE (in this order):
 
1. Original Requirement (Verbatim)
   - Copy the full content from the source document exactly as written.
   - Do not rephrase, summarise, or omit anything.
   - Include all clarification notes, updates, and examples from the source.
 
2. Overview
   - Brief summary of what the feature does and why it is needed.
   - Keep it business-friendly — no technical terms.
 
3. Scope
   - In Scope  : List all capabilities included in this delivery.
   - Out of Scope : List anything explicitly excluded or removed.
     If nothing is excluded, write:
     "All scenarios mentioned under In Scope are part of this requirement.
      Any other scenarios are considered out of scope."
 
4. Business Scenarios / User Flows
   - Describe how the feature will be used in real business terms.
   - Write as step-by-step flows (e.g. manager sets up promotion,
     cashier processes a sale, etc.).
 
5. Functional Requirements
   - List what the system must do, in plain business language.
   - Group by area if needed (e.g. Setup, POS Behaviour).
   - Number each requirement (FR-01, FR-02, ...).
 
6. Worked Examples
   - Include only if the feature involves calculations or conditional logic.
   - Use realistic sample data with clear inputs and expected outputs.
 
7. Screen Details
   - Include only for features that have a user interface (MC or POS).
   - For each screen provide:
       - Screen name and menu path
       - Fields with their purpose and whether they are mandatory
       - Action buttons and what they do
       - All messages and alerts shown to the user
 
8. Impact Analysis
   - List all previously delivered add-ons and features for this customer.
   - For each, state whether this new feature has any impact and explain why.
   - Also cover impact on iVend configuration, SAP/ERP, and master data.
 
9. Data Requirements
   - List the key data the feature needs to store or work with.
   - Present as named groups (e.g. Promotion Header, Slabs, Store Mapping)
     with a table of fields and their business purpose.
   - Keep it high-level — no database or technical terms.
 
10. Validation Rules
    - List only the important business rules that affect what a user can or
      cannot save/do.
    - Number each rule (V-01, V-02, ...).
 
11. Dependencies & Assumptions
    - Dependencies: What must be in place before this feature can work.
    - Assumptions: What has been agreed or taken for granted during design.
 
12. UAT Scenarios
    - List the key test cases the customer must validate.
    - Present as a table: Test Case ID | Scenario | Steps | Expected Result.
    - After the last test case, add this note exactly:
      "These are the UAT scenarios required to be validated by the customer.
       If the customer has any additional UAT scenarios, they must be
       communicated and agreed upon before SOW finalization."
 
13. Estimation
    - Provide a high-level effort estimate broken down by component.
    - Present as a table: Component | Estimated Hours.
    - Include a Total row at the bottom.
    - Add a note: "Any scope changes after sign-off will be estimated
      separately."
 
---
 
STRICT RULES:
- Do NOT include any technical details (no code, no database schema,
  no architecture, no API references).
- Keep all language simple and business-oriented.
- The document must be suitable for customer review and sign-off.
- Keep it structured, concise, and easy to read.
- Use Markdown formatting throughout.
```

---

## 3️⃣ IMPL — Implementation Plan

**When:** PRD is done and approved.  
**Input:** The BRD + PRD + your project's CLAUDE.md.  
👉 This is **developer-focused (technical)**

```id="impl3"
Read the following documents:
BRD: docs/CRD-XXXX/1. BRD-[FeatureName]-iVendAddOn.md
PRD: docs/CRD-XXXX/2. PRD-[FeatureName]-iVendAddOn.md
Project Guidelines: CLAUDE.md (iVend AddOn Specific)

👉 If this is a single CR / standalone feature, read from:
docs/1. BRD-[FeatureName]-iVendAddOn.md
docs/2. PRD-[FeatureName]-iVendAddOn.md

Create a step-by-step Implementation Plan broken into phases. For each phase give:
exact file paths, class/method names, field lists, validation logic, error constants.
Include test groups A–F. End with a deployment checklist and rollback plan.

Save the document as:
docs/CRD-XXXX/3. IMPL-[FeatureName]-iVendAddOn.md

👉 If this is a single CR / standalone feature, save it under:
docs/3. IMPL-[FeatureName]-iVendAddOn.md
```

---

## 4️⃣ UT — Unit Test Specification

**When:** IMPL is done. Tests are written.  
**Input:** The IMPL testing section + the actual test code file.

```id="ut3"
Read the following:
Implementation Document (IMPL – Testing Section):
docs/CRD-XXXX/3. IMPL-[FeatureName]-iVendAddOn.md
Actual Test Project / Codebase:
[Path to test project / test files]

👉 If this is a single CR / standalone feature, read IMPL from:
docs/3. IMPL-[FeatureName]-iVendAddOn.md

Create a Unit Test Specification document. For each test, list: Test ID, method name, description, setup, expected result. Group them by test class. Add an IMPL traceability section showing which IMPL test IDs map to which actual tests, noting any deviations.

Save the document as:
docs/CRD-XXXX/4. UT-[FeatureName]-iVendAddOn.md

👉 If this is a single CR / standalone feature, save it under:
docs/4. UT-[FeatureName]-iVendAddOn.md
```

---

## 4.1️⃣ UT-RESULT — Unit Test Results

**When:** After running unit tests.  
**Input:** Just tell Claude to run the tests.

```id="utr3"
Run the unit tests for iVend Addon:

[Project_Root_Path]/[Addon_Project_Name]

👉 Example:
CXS-Git\ivendcd\[SolutionFolder]\[Addon_Project_Name]

🕒 Logging Rules
Each run should be timestamped and appended — never overwrite previous runs. Include a summary table (total/passed/failed/time) and per-test results.

Save the results to:
docs/CRD-XXXX/4.1 UT-[FeatureName]-iVendAddOn-RESULT.md

👉 If this is a single CR / standalone feature, save it under:
docs/4.1 UT-[FeatureName]-iVendAddOn-RESULT.md
```

---

## 5️⃣ QA — QA Test Plan

**When:** IMPL is done. Code is written.  
**Input:** The IMPL (manual test groups) + PRD (acceptance criteria) + source code.

```id="qa3"
Read the following:

Implementation Document (IMPL):
docs/CRD-XXXX/3. IMPL-[FeatureName]-iVendAddOn.md

Product Requirement Document (PRD):
docs/CR-XXXX/2. PRD-[FeatureName]-iVendAddOn.md

Source Code: [Path to addon source code]

👉 If this is a single CR / standalone feature, read from:
docs/

Create a QA Test Plan: Form UI, Validation Rules, Integration, Dialogs, End-to-End,
Offline, Negative/Edge Cases, API Endpoints, Permissions.
Each case: ID, description, steps, expected result, PRD AC reference.
Target 80-120 test cases. End with AC traceability matrix.

Save the document as:
docs/CRD-XXXX/5. QA-[FeatureName]-iVendAddOn.md

👉 If this is a single CR / standalone feature, save it under:
docs/5. QA-[FeatureName]-iVendAddOn.md
```

---

## 5.1️⃣ QA-RESULT — QA Test Results

**When:** After a QA tester executes the QA test cases.  
**Input:** The tester's results.  
👉 Works for both **manual + automated testing**

```
Read the following:

QA Test Plan:
docs/CRD-XXXX/5. QA-[FeatureName]-iVendAddOn.md

Source Code:
[Path to addon source code]

👉 If this is a single CR / standalone feature, read from:
docs/

---

Execute all QA test cases for the iVend Add-on using iVend Retail POS and Management Console (MC).

- If automation scripts are available, execute only fully automated test cases  
- Otherwise, execute test cases manually  

Ensure the latest add-on DLL is deployed and required test data is prepared before execution.

---

Log the results for each test case with:
ID, Result (PASS / FAIL / BLOCKED), Notes (if failed)

Include:
- Summary (Total / Passed / Failed / Blocked / Pass %)  
- List of defects identified during execution  

---

Save the document as:
docs/CRD-XXXX/5.1 QA-[FeatureName]-iVendAddOn-RESULT.md

👉 If this is a single CR / standalone feature, save it under:
docs/5.1 QA-[FeatureName]-iVendAddOn-RESULT.md
```

---

## 6️⃣ PR RESULT — Peer Review

**When:** PR is created and ready for review.  
**Input:** The PR number or branch name.  
👉 Focus on quality + correctness

```id="pr3"
Read the following:

PR Details:
PR #[number] or [branch name]

👉 If required, refer to related documents from:
docs/CRD-XXXX/

---

Review the PR for the iVend Add-on.

---

Log the review findings with:

- Critical Issues  
- Important Issues  
- Medium Issues  
- Positive Observations  

Only report issues with confidence >= 80%.

---

Include:
- Final Verdict (Approve / Request Changes)  

---

Save the document as:
docs/CRD-XXXX/6. PR-[FeatureName]-iVendAddOn-RESULT.md

👉 If this is a single CR / standalone feature, save it under:
docs/6. PR-[FeatureName]-iVendAddOn-RESULT.md
```

---

## 7️⃣ UM — User Manual (Optional)

**When:** Feature is complete and tested.  
**Input:** The BRD + PRD.  
👉 Only needed for client/demo/training

```id="um3"
Read the following:

Business Requirement Document (BRD):
docs/CRD-XXXX/1. BRD-[FeatureName]-iVendAddOn.md

Product Requirement Document (PRD):
docs/CRD-XXXX/2. PRD-[FeatureName]-iVendAddOn.md

👉 If this is a single CR / standalone feature, read from:
docs/

---

Create a user manual for store managers and cashiers. Write step-by-step instructions with "Go to...", "Click...", "Enter..." language. Include: creating the configuration (with a worked example using real data), testing before going live, assigning to items, what happens at the POS, disabling/deleting, troubleshooting table (Problem → Cause → Solution), and a field description reference table.  

---

Save the document as:
docs/CRD-XXXX/7. UM-[FeatureName]-iVendAddOn.md

👉 If this is a single CR / standalone feature, save it under:
docs/7. UM-[FeatureName]-iVendAddOn.md
```

---

## 📌 Naming Convention

```id="name3"
[Order]. [Type]-[FeatureName]-iVendAddOn.md
```

---

## ✅ Best Practices

* Use CRD number consistently across all docs
* One CR = one folder
* Avoid mixing multiple CRs in one document
* Feed previous docs into prompts
* Maintain UT & QA history (append-only)


# Healthcare Payer

## What is Healthcare Payer?
In healthcare, a payor (or payer) is a person, organization, or entity responsible for covering the cost of medical care provided by a healthcare professional. This term most often applies to health insurance companies that offer plans covering treatment costs and reimbursing providers for services rendered.

There are three main types of payers:
- Government or public payors:  Include Medicare, Medicaid, and CHIP, funded by the U.S. government to assist specific groups.
- Commercial payors: Publicly traded insurance companies like UnitedHealth, Aetna, and Humana, providing health insurance through employers, direct purchases, or marketplaces.
- Private payors: Private insurance companies like Blue Cross Blue Shield and non-insurance payments, including direct cash payments for services.

## What’s the difference between “payor,” “payer” and “payee”?
The terms “payor” and “payer” have the same meaning and are often used interchangeably.

A payee is the person or entity who receives payment in exchange for services. In healthcare, this is typically the provider (e.g., physician, hospital, clinic), depending on how the claim is processed.

When you visit a doctor, the payer determines eligibility, coverage, benefit limits, and how much to pay the provider based on complex rules, contracts, and regulatory requirements. Payers are responsible for:
- Managing member enrollment and eligibility
- Defining and administering health plans and benefits
- Processing and adjudicating claims (medical, dental, pharmacy)
- Contracting and credentialing providers
- Pricing and reimbursement methodologies
- Regulatory compliance (HIPAA, ACA, CMS, state laws)
- Data exchange via EDI (837, 835, 270, 271, etc.)
- Quality reporting (HEDIS, MLR, risk adjustment)
 
Payer systems like Facets must support all these functions, integrating business logic, regulatory rules, and data standards to ensure accurate, timely, and compliant healthcare payments.

## Key Domain Concepts
 
### 1. Members & Enrollment
| Term | Meaning |
|---|---|
| Member | A person enrolled in a health plan |
| Subscriber | The primary person who purchased/holds the plan |
| Dependent | Spouse, child covered under subscriber's plan |
| Enrollment | The act of signing up for a health plan |
| Effective Date | When coverage starts |
| Termination Date | When coverage ends |
| Open Enrollment | Annual window when people can enroll/change plans |
| Qualifying Life Event (QLE) | Marriage, birth, job loss — allows mid-year enrollment changes |
| Member ID / MEME_CK | Unique identifier for each member in Facets |
 
### 2. Health Plans & Benefits
| Term | Meaning |
|---|---|
| Health Plan | The insurance product (e.g., "Gold PPO 500") |
| Line of Business (LOB) | Category: Commercial, Medicare, Medicaid, Exchange |
| Benefit Package | Set of covered services and cost-sharing rules |
| Deductible | Amount member pays before insurance kicks in (e.g., first $2,000) |
| Copay | Fixed amount member pays per visit (e.g., $25 for doctor visit) |
| Coinsurance | Percentage member pays (e.g., 20% after deductible) |
| Out-of-Pocket Maximum (OOPM) | Maximum a member pays in a year — after this, plan pays 100% |
| Prior Authorization (PA) | Approval required BEFORE certain services |
| Formulary | List of covered prescription drugs |
| Network | Group of contracted providers (in-network = cheaper for member) |
 
### 3. Claims Processing (Core of Facets)
| Term | Meaning |
|---|---|
| Claim | A request for payment submitted by a provider |
| Claim Header (CLCL) | Top-level claim info: member, provider, dates, diagnosis |
| Claim Line (CDML) | Individual services on a claim (each procedure is a line) |
| Adjudication | The decision-making process: approve, deny, or pend |
| Auto-adjudication | Claims processed without human intervention (target: 85-95%) |
| Pended Claim | Claim stopped for manual review |
| Denied Claim | Claim rejected (not covered, not eligible, etc.) |
| Approved/Paid Claim | Claim accepted and payment issued |
| Clean Claim | Claim that passes all edits and can be auto-adjudicated |
| Dirty Claim | Claim with errors requiring correction |
| Duplicate Claim | Same service submitted twice — must be caught |
| EOB (Explanation of Benefits) | Document sent to member explaining what was paid |
| ERA (Electronic Remittance Advice) | EDI 835 sent to provider explaining payment |
 
### 4. Pricing & Reimbursement
| Term | Meaning |
|---|---|
| Allowed Amount | Maximum the plan will pay for a service |
| Billed Amount | What the provider charged |
| Paid Amount | What the plan actually pays |
| Member Responsibility | Deductible + Copay + Coinsurance the member owes |
| Fee Schedule | Contracted rates for each procedure code |
| DRG (Diagnosis Related Group) | Hospital payment methodology (per-case) |
| Per Diem | Hospital payment per day |
| Capitation | Fixed monthly payment to provider regardless of services used |
| UCR (Usual, Customary, Reasonable) | Benchmark for out-of-network pricing |
| RBRVS | Resource-Based Relative Value Scale (Medicare physician pricing) |
 
### 5. Medical Coding
| Code Type | What It Is | Example |
|---|---|---|
| CPT (Current Procedural Terminology) | Procedure codes | 99213 = Office visit |
| ICD-10 | Diagnosis codes | J06.9 = Upper respiratory infection |
| HCPCS | Healthcare Common Procedure Coding | A0425 = Ambulance |
| Revenue Codes | Facility/hospital codes | 0120 = Room & board |
| NDC | National Drug Code | Drug identification |
| Place of Service (POS) | Where service happened | 11 = Office, 21 = Hospital |
 
### 6. Provider Management
| Term | Meaning |
|---|---|
| Provider | Doctor, hospital, lab, pharmacy |
| NPI | National Provider Identifier (10-digit unique ID) |
| Tax ID / TIN | Provider's tax identification |
| Credentialing | Verifying provider qualifications |
| Contracting | Negotiating payment rates with providers |
| In-Network | Provider has contract with the plan (lower rates) |
| Out-of-Network | No contract — member pays more |
| Provider Directory | List of available in-network providers |
 
### 7. Accumulators
Track how much a member has spent toward limits:
 
| Accumulator | Tracks |
|---|---|
| Deductible Accumulator | How much of deductible has been met |
| OOPM Accumulator | How much toward out-of-pocket max |
| Visit Limit Accumulator | Number of visits used (e.g., 20 PT visits/year) |
| Dollar Limit Accumulator | Amount used toward a dollar cap |
| Lifetime Maximum | Total plan will ever pay (rare now due to ACA) |
 
### 8. Coordination of Benefits (COB)
When a member has multiple insurance:
- Rules determine which plan is primary (e.g., employer plan > spouse's plan)
- Birthday Rule: For dependents, parent whose birthday comes first in the year is primary
- Complex logic — major source of claim errors
 
### 9. Regulatory & Compliance
| Regulation | What It Governs |
|---|---|
| HIPAA | Privacy and security of health data (PHI) |
| ACA (Affordable Care Act) | Essential health benefits, no lifetime limits, no pre-existing exclusions |
| CMS | Centers for Medicare & Medicaid Services — federal oversight |
| State DOI | State Dept. of Insurance — state-level regulations |
| ERISA | Self-funded employer plan regulations |
| MLR (Medical Loss Ratio) | Must spend 80-85% of premiums on medical care |
| HEDIS | Quality measures health plans must report |
| Risk Adjustment | Transfer payments between plans based on member health risk |
 
### 10. Payer Business Lines
| Line of Business | Who's Covered | Funded By |
|---|---|---|
| Commercial (Fully Insured) | Employees of small/medium companies | Premiums |
| Commercial (Self-Funded/ASO) | Large employer — employer pays claims, payer administers | Employer funds |
| Medicare | 65+ or disabled | Federal government |
| Medicare Advantage (MA) | Medicare through private plan | CMS capitation |
| Medicaid | Low-income individuals | State + federal government |
| Exchange/Marketplace (ACA) | Individuals via healthcare.gov | Premiums + subsidies |
| Dental | Dental only plans | Premiums |
| Vision | Vision only plans | Premiums |
| Pharmacy (PBM) | Drug benefits | Premiums |

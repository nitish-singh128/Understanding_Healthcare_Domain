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

## What is EDI in Healthcare: Importance and How to Implement It
An enormous number of documents, tons of paper, and hundreds of returned claims—that’s how the healthcare industry looked before introducing electronic data interchange (EDI). Using EDI in healthcare helps medical organizations secure data exchanges, provides a quicker turnaround of information, and eliminates claim processing delays. All this makes EDI implementation a crucial part of delivering a high quality of care. EDI healthcare systems are essential for modern medical practices, ensuring efficient and secure data handling.

### What is EDI in healthcare?
Electronic data interchange in healthcare is a secure way of transmitting data between healthcare institutions, insurers, and patients using established message formats and standards. EDI transactions in healthcare facilitate seamless communication and data exchange, reducing errors and improving efficiency.

**Healthcare EDI transaction types**
In general, organizations in the healthcare industry use ten types of HIPAA electronic data interchange transactions: these EDI healthcare transactions are vital for efficient operations and accurate data management.

- **Healthcare claim transaction set (837)**. It allows healthcare providers and patients to submit healthcare claim information and encounter information.

- **Retail pharmacy claim transaction**. It allows healthcare professionals and regulatory agencies to submit retail pharmacy claims. It also lets them transmit claims for retail pharmacy services and billing payment information to payers.

- **Healthcare claim payment/advice transaction set (835)**. It is used by insurers to make payments and send Explanation of Benefits (EOB) remittance advice to healthcare providers.

- **Benefits enrollment and maintenance set (834)**. It is used by employers, unions, government agencies, insurance agencies, associations, or healthcare organizations paying claims. Its aim is to enroll members in a healthcare benefit plan. 

- **Payroll deducted and other group premium payment for insurance products (820)**. This transaction serves to make premium payments for insurance products and is used by healthcare institutions to send information to financial organizations.

- **Healthcare eligibility/benefit inquiry (270)**. This transaction set is used by healthcare institutions to transmit inquiries for healthcare benefits and subscriber eligibility to financial institutions and government agencies. 

- **Healthcare eligibility/benefit response (271)**. Its main purpose is to respond to request inquiries about the healthcare benefits and eligibility associated with a subscriber or dependent. Like the previous transaction, it is used by healthcare institutions to transmit information to financial institutions and government agencies.

- **Healthcare claim status request (276)**. This transaction is used by healthcare providers to request or verify the status of healthcare previously submitted to a payer, such as an insurance company.

- **Healthcare claim status notification (277)**. It serves for reporting on the status of claims (EDI 837 transactions) previously submitted by providers. EDI 277 is used by healthcare payers and insurance companies.

- **Healthcare service review Information (278)**. It is used by hospitals to request an authorization from a payer, such as an insurance company.

The EDI transactions list also includes EDI Functional Acknowledgement Transaction Set (997). But it doesn’t cover any semantic meaning of the information encoded in the transaction sets. It is only necessary for X12 transaction set processing.

### What does EDI mean in medical billing
[Medical billing](https://demigos.com/blog-post/edi-in-healthcare) is a complex process due to the complexity of billing and coding and the many different parties that need to be involved. Standardization is particularly important here to avoid getting lost in a huge number of services, procedures, and diagnoses. Understanding the EDI full form in medical billing is crucial for efficient processing and compliance.

Healthcare providers use an X12 HIPAA 837 Healthcare Claim to request payment from a health insurance provider. A medical billing process starts with an inquiry from the care provider and ends with a payer response. Here is how it happens:

- Step 1. Inquiry. Care providers make an inquiry that includes member ID number, date of birth, and Payer ID. In most cases, it goes through a clearinghouse, an intermediary used to help reformat claims to conform to the HIPAA standard, but it can also reach a payer directly. The role of the clearinghouse is to facilitate inquiries to the payers.

- Step 2. Response. When a payer receives an inquiry, they respond to the intermediary (clearinghouse), which, in turn, sends the data to the care provider’s system. If there is an error in the data, the care provider corrects it and resubmits it again to the clearinghouse. 

Without the use of medical electronic data interchange, all these transactions would be much more difficult to handle because the various systems of providers and insurers would use different data formats. This was initially the case, and healthcare payment and remittance processes took weeks, especially when some errors occurred in the process. Simplifying the medical billing process is not the only positive aspect of implementing EDI. Let’s look at some other benefits an organization can expect when it uses HIPAA EDI formats.

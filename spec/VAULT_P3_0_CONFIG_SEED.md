# VAULT P3.0 - Config Seed Contract

Sprint P3.0 of the P3 (living mockup) track. One subject: replace the demo substantiation dataset in
`the-vault-app.html` with the real validated MMSP EOT001 Staff Cost configuration. Nothing else.

## Context

The substantiation matrix was validated by the Cost Controller on 2026-08-13. The configuration below is
his return, verbatim, serialized. The Vault principle is configuration over specification: the app must
demonstrably read its rules from this config object, not from hardcoded screen content. This sprint makes
the mockup show the real project the stakeholders will recognize.

## Scope

IN:
- One config object (the JSON below) embedded as a single source of truth constant in the-vault-app.html.
- S20 (substantiation matrix screen) renders the config read-only: all 40 rows, the excluded element
  visibly inactive, the two to_discuss elements subtly flagged.
- Every surface that reads substantiation data is driven by the config: the contributor owed list, the
  attach form (shows the required and optional proofs for the selected element), the validator checklist,
  the gap panel, the export block reasoning.
- Tallies and counts (elements per category, gaps, owed documents) recomputed from the config so the app
  is internally consistent. Do not chase the previous demo tallies.
- Seeded amounts, staff names and period data stay simulated as they are today.

OUT:
- No motion or transition work (P3.1 and P3.2).
- No new screens, no visual changes, DA frozen (Showroom, tokens v1.1).
- The guided pitch demo HTML is a separate artifact: do not touch it.
- No real extraction logic: the engine stays simulated (honest phasing, palier doctrine unchanged).

## Phase A (read-only, STOP and report before any edit)

1. Verify the P2.1 state of the-vault-app.html: fluid shell without the stage transform, S23
   legibility-first rendering, VIEW AS vertical role switcher. If any of the three is absent, STOP and
   report: P2.1 is not merged and P3.0 must wait.
2. Locate the current demo substantiation dataset and every surface that consumes it. List them.
3. Confirm the injection plan: where the config constant lives, how each surface maps to it, what tallies
   are recomputed. Flag any collision (element count changes category totals, longer proof labels in
   narrow columns, the excluded row in filters).
4. STOP. Wait for GO.

## Phase B (one additive commit, only after GO)

1. Inject the config object exactly as provided below.
2. Wire S20 and the consuming surfaces to it.
3. Recompute tallies from config.
4. Excluded element (1.3.16): rendered muted with an excluded tag, out of gap counts.
5. to_discuss elements (1.1.2, 1.1.3): a discreet marker, no colour drama, one line of note on hover or
   detail. Do not surface their defensibility debate in the UI copy.
6. Names render as provided (Donnarica Dela Paz, Donna Dalida, Donna Marie Velo, Janelle Tumblod, Jeanette
   Tuhao, Ella Baral, Khoa Nguyen, Irish Apple Neulid, Sharizal Isa).

## Acceptance checklist (smoke test, file:// and Live Server)

- S20 shows 40 rows, 39 active, grouped by the three categories, read-only.
- Selecting a manual element (1.3.10 School Fees) in the attach form lists its required proofs from config.
- The gap panel counts derive from config; 1.3.14 IT software appears with its evidence requirement.
- Role switch still works across all six roles; no console errors; theme and persistence intact.
- The pitch demo file is untouched (diff shows one file changed).

## The configuration (verbatim from the validated return)

```json
{
  "project": "MMSP EOT001",
  "costHead": "A",
  "costHeadName": "Staff Cost",
  "validatedBy": "Mohd Sharizal Isa (Cost Controller)",
  "validatedOn": "2026-08-13",
  "categories": [
    "1.1 Salary",
    "1.2 Contribution",
    "1.3 Fringe Benefit"
  ],
  "activeElements": 39,
  "mappedElements": 40,
  "elements": [
    {
      "ref": "1.1.1",
      "name": "Basic Salary",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month), Colas Origin Package (COrigin) and Host/Home Based Package (HBased); PDF for invoices for Mainby (Quarterly invoice), VIE Staff, Remote Staff",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip for Local, Colas Origin and Host/Home Based Package",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Invoice for Staff Mainby, Remote and VIE",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        },
        {
          "doc": "Notarized payroll record",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": true,
      "appliesTo": "All origins",
      "flags": [],
      "note": "Not sure if payslip for Mainby, Remote Staff and VIE are available. Substantiate with invoices. Submission of evidence can be either payroll record or payslip. Contract Team will advice once confirm by client."
    },
    {
      "ref": "1.1.2",
      "name": "13th Month",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Computed",
      "comesFrom": "Computed from Basic Salary base (formulated in Power Query, no separate file)",
      "depositedBy": "Sharizal Isa (Cost Control)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Justify in the submission letter and details claim summary (subject to change)",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": null
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [
        "to_discuss"
      ],
      "note": "13th month salary only shown in the December payslip but for the purpose of the claims we calculated every months to avoid the duration gap and calculated provision being made internally."
    },
    {
      "ref": "1.1.3",
      "name": "Performance Bonus",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Computed",
      "comesFrom": "Computed from Basic Salary base (formulated in Power Query, no separate file)",
      "depositedBy": "Sharizal Isa (Cost Control)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Justify in the submission letter and details claim summary (subject to change)",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": null
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [
        "to_discuss"
      ],
      "note": "Bonus only shown in the March payslip but for the purpose of the claims we calculated every months to avoid the duration gap and calculated provision being made internally."
    },
    {
      "ref": "1.1.4",
      "name": "Per Diem Allowance",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Notarized payroll record",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "Local only",
      "flags": [],
      "note": "Per diem allowance is applicable to local staff only."
    },
    {
      "ref": "1.1.5",
      "name": "Living Allowance",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Host/Home Based Package (HBased)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Notarized payroll record",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "HBased only",
      "flags": [],
      "note": "Living allowance is applicable to Host/Home Based staff only."
    },
    {
      "ref": "1.1.6",
      "name": "Expat Allowance",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Colas Origin Package (COrigin); PDF for invoices for Mainby (Quarterly invoice)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Invoice for Staff Mainby",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "Refer item 1.1.1"
    },
    {
      "ref": "1.1.7",
      "name": "Paid Holidays",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "PDF for invoices for Mainby (Quarterly invoice)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Quarterly",
      "proofs": [
        {
          "doc": "Invoice for Staff Mainby",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "Mainby only",
      "flags": [],
      "note": "Paid holidays is applicable to Mainby staff only."
    },
    {
      "ref": "1.1.8",
      "name": "Double Foyer",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Colas Origin Package (COrigin)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Notarized payroll record",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "COrigin only",
      "flags": [],
      "note": "Double Foyer is applicable to Colas Origin staff only."
    },
    {
      "ref": "1.1.9",
      "name": "Household Allowance",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Colas Origin Package (COrigin)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Notarized payroll record",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "COrigin only",
      "flags": [],
      "note": "Household Allowance is applicable to Colas Origin staff only."
    },
    {
      "ref": "1.1.10",
      "name": "Phone Allowance",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month) and Host/Home Based Package (HBased)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Notarized payroll record",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "Local + 1 HBased staff (Muhammad Azri)",
      "flags": [],
      "note": "Phone allowance provided to Local staff and only 1 staff in Host/Home Based Package i.e. Muhammad Azri."
    },
    {
      "ref": "1.1.11",
      "name": "Accommodation Allowance",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month) and Host/Home Based Package (HBased)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Notarized payroll record",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "Selected Local + HBased",
      "flags": [],
      "note": "Housing allowance provided to selected Local staff and Host Based Package."
    },
    {
      "ref": "1.1.12",
      "name": "Transport Allowance",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month) and Host/Home Based Package (HBased)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Notarized payroll record",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "Selected Local + HBased",
      "flags": [],
      "note": "Tranport allowance provided to selected Local staff and Host Based Package."
    },
    {
      "ref": "1.1.13",
      "name": "Adjustment",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Host/Home Based Package (HBased)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "1 HBased staff (Simon Bennette)",
      "flags": [],
      "note": "Adjustment only found in one Home Based Staff i.e. Simon Bennette"
    },
    {
      "ref": "1.1.14",
      "name": "Mainby Admin Fees",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "PDF for invoices for Mainby (Quarterly invoice)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Quarterly",
      "proofs": [
        {
          "doc": "Agency invoice",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "Sufficient to substantiate with Mainby invoice only"
    },
    {
      "ref": "1.1.15",
      "name": "Provisional Charges",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "PDF for invoices for Mainby (Quarterly invoice)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Quarterly",
      "proofs": [
        {
          "doc": "Agency invoice",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "Sufficient to substantiate with Mainby invoice only"
    },
    {
      "ref": "1.1.16",
      "name": "End of Contract Deposit",
      "category": "1.1 Salary",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "PDF for invoices for Mainby (Quarterly invoice)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Quarterly",
      "proofs": [
        {
          "doc": "Agency invoice",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "Sufficient to substantiate with Mainby invoice only"
    },
    {
      "ref": "1.2.1",
      "name": "SSS",
      "category": "1.2 Contribution",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month), Colas Origin Package (COrigin), Host/Home Based Package (HBased) and payroll summary for Mainby",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Electronic Contribution Collection List",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Proof of payment / remittance receipt",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "SSS Payment Slip",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "This is statutory contribution and government mandated employee benefit. It is applicable to everyone. It won't be challenged."
    },
    {
      "ref": "1.2.2",
      "name": "SSS-ee",
      "category": "1.2 Contribution",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month), Colas Origin Package (COrigin), Host/Home Based Package (HBased) and payroll summary for Mainby",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Electronic Contribution Collection List",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Proof of payment / remittance receipt",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "SSS Payment Slip",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "This is statutory contribution and government mandated employee benefit. It is applicable to everyone. It won't be challenged."
    },
    {
      "ref": "1.2.3",
      "name": "PHIC",
      "category": "1.2 Contribution",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month), Colas Origin Package (COrigin), Host/Home Based Package (HBased) and payroll summary for Mainby",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Employee Premium Remittance Statement",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Proof of payment / remittance receipt",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Statement of Premium Account (SPA)",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "This is statutory contribution and government mandated employee benefit. It is applicable to everyone. It won't be challenged."
    },
    {
      "ref": "1.2.4",
      "name": "PHIC-ee",
      "category": "1.2 Contribution",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month), Colas Origin Package (COrigin), Host/Home Based Package (HBased) and payroll summary for Mainby",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Employee Premium Remittance Statement",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Proof of payment / remittance receipt",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Statement of Premium Account (SPA)",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "This is statutory contribution and government mandated employee benefit. It is applicable to everyone. It won't be challenged."
    },
    {
      "ref": "1.2.5",
      "name": "HDMF",
      "category": "1.2 Contribution",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Local Package (2 files per month)",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Excel document of Monthly Contributions (PAGIBIG) File Writer",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "Selected employees with a housing loan",
      "flags": [],
      "note": "This is statutory contribution and government mandated employee benefit. It is applicable to selected employee taken the housing loan."
    },
    {
      "ref": "1.2.6",
      "name": "Withholding Tax",
      "category": "1.2 Contribution",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Colas Origin Package (COrigin), Host/Home Based Package (HBased) and payroll summary for Mainby",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "BIR Form 1601-C",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Janelle Tumblod"
        },
        {
          "doc": "BIR filing reference",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Janelle Tumblod"
        },
        {
          "doc": "BIR EFPS payment confirmation",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Janelle Tumblod"
        }
      ],
      "notarised": false,
      "appliesTo": "COrigin, Mainby + 1 HBased staff (Simon Bennette)",
      "flags": [],
      "note": "Withholding taxes borne by Colas Rail for all Colas Origin, Mainby staff and 1 Home Based Staff i.e. Simon Bennette"
    },
    {
      "ref": "1.3.1",
      "name": "Phone Bill",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Manual entry",
      "comesFrom": "Telco billing statement",
      "depositedBy": "Jeanette Tuhao (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Telco invoice / billing statement",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Jeanette Tuhao (Account)"
        },
        {
          "doc": "Official receipt / proof of payment",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Jeanette Tuhao (Account)"
        },
        {
          "doc": "Line-to-staff allocation list",
          "level": "Optional",
          "granularity": "Per staff",
          "provider": "Jeanette Tuhao (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.2",
      "name": "Pension Scheme",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel for audited payroll file for Host/Home Based Package (HBased) and PDF invoices for Mainby",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Staff payslip for Host/Home Based Package",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Invoice for Staff Mainby",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "Mainby + selected HBased",
      "flags": [],
      "note": "Pension scheme provided to Mainby staff and selected Home Based Package."
    },
    {
      "ref": "1.3.3",
      "name": "Life Insurance",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Insurer billing / policy schedule",
      "depositedBy": "Donna Dalida (HR)",
      "frequency": "Annual",
      "proofs": [
        {
          "doc": "Insurer invoice",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Policy schedule with covered member list",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.4",
      "name": "Medical Insurance",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Insurer billing / policy schedule",
      "depositedBy": "Donna Dalida (HR)",
      "frequency": "Annual",
      "proofs": [
        {
          "doc": "Insurer invoice",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        },
        {
          "doc": "Covered member list",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Ella Baral (HR)"
        },
        {
          "doc": "Official receipt / proof of payment",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.5",
      "name": "Medical Claim",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Philcare's Fund Utilization Report, Philcare Service Invoice",
      "depositedBy": "Donna Dalida (HR)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Philcare's Fund Utilization Report, Philcare Service Invoice",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Dalida (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.6",
      "name": "Accomodation Rental",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Admin excel working file for Subscription Order",
      "depositedBy": "Donna Marie Velo (Admin)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Lease agreement",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Marie Velo (Admin)"
        },
        {
          "doc": "Bi-annual invoice / official receipt",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Marie Velo (Admin)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "Lease is the cost incurred every 6 months but for the purpose of the claim we cost it monthly based on subscription form."
    },
    {
      "ref": "1.3.7",
      "name": "Accomodation Association Dues",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Admin excel working file for Subscription Order",
      "depositedBy": "Donna Marie Velo (Admin)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Lease agreement",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Marie Velo (Admin)"
        },
        {
          "doc": "Bi-annual invoice / official receipt",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donna Marie Velo (Admin)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "Lease is the cost incurred every 6 months but for the purpose of the claim we cost it monthly based on subscription form."
    },
    {
      "ref": "1.3.8",
      "name": "Accomodation Furnitures",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Manual entry",
      "comesFrom": "Official receipt / delivery note",
      "depositedBy": "Jeanette Tuhao (Account)",
      "frequency": "One-off (new joiner)",
      "proofs": [
        {
          "doc": "Official receipt / delivery note",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Jeanette Tuhao (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.9",
      "name": "Utility (Power / Water)",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Manual entry",
      "comesFrom": "Utility billing statement",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Utility bill",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.10",
      "name": "School Fees",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Manual entry",
      "comesFrom": "School invoice",
      "depositedBy": "Jeanette Tuhao (Account)",
      "frequency": "Quarterly",
      "proofs": [
        {
          "doc": "School invoice",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Jeanette Tuhao (Account)"
        },
        {
          "doc": "Official receipt",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Jeanette Tuhao (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.11",
      "name": "Visa",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Manual entry",
      "comesFrom": "Approved expense claim form",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Official receipt",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.12",
      "name": "Flight",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Manual entry",
      "comesFrom": "Travel agency invoice",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "One-off",
      "proofs": [
        {
          "doc": "Travel agency invoice",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        },
        {
          "doc": "E-ticket / boarding pass",
          "level": "Optional",
          "granularity": "Per staff",
          "provider": "Donna Marie Velo (Admin)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "E-ticket is a good substantiation"
    },
    {
      "ref": "1.3.13",
      "name": "Expenses Claim",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Manual entry",
      "comesFrom": "Approved expense claim form",
      "depositedBy": "Donnarica Dela Paz (Account)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Approved expense claim form",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        },
        {
          "doc": "Supporting receipts",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Donnarica Dela Paz (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.14",
      "name": "IT software",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Manual entry",
      "comesFrom": "CDS invoice",
      "depositedBy": "Khoa Nguyen (Cost Control)",
      "frequency": "Quarterly",
      "proofs": [
        {
          "doc": "CDS invoice",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Khoa Nguyen (Cost Control)"
        },
        {
          "doc": "Official receipt / proof of payment",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Khoa Nguyen (Cost Control)"
        }
      ],
      "notarised": true,
      "appliesTo": "All origins",
      "flags": [],
      "note": "CDS is just issuing an Excel file without proper invoices."
    },
    {
      "ref": "1.3.15",
      "name": "Fringe Benefit Tax",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel working file from Tax Specialist",
      "depositedBy": "Janelle Tumblod (Account)",
      "frequency": "Quarterly",
      "proofs": [
        {
          "doc": "BIR Form 1601-Q",
          "level": "Required",
          "granularity": "Per batch",
          "provider": "Janelle Tumblod (Account)"
        },
        {
          "doc": "BIR EFPS Payment System",
          "level": "Optional",
          "granularity": "Per batch",
          "provider": "Janelle Tumblod (Account)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.16",
      "name": "IT hardware",
      "category": "1.3 Fringe Benefit",
      "active": false,
      "mode": null,
      "comesFrom": null,
      "depositedBy": null,
      "frequency": null,
      "proofs": [],
      "notarised": null,
      "appliesTo": "n/a",
      "flags": [
        "excluded"
      ],
      "note": null
    },
    {
      "ref": "1.3.17",
      "name": "Transport Taxi",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Extracted",
      "comesFrom": "Excel working file from Admin",
      "depositedBy": "Irish Apple Neulid (Admin)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Grab's Tax Invoice",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Irish Apple Neulid (Admin)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": null
    },
    {
      "ref": "1.3.18",
      "name": "Training",
      "category": "1.3 Fringe Benefit",
      "active": true,
      "mode": "Manual entry",
      "comesFrom": "Training provider invoice",
      "depositedBy": "Ella Baral (HR)",
      "frequency": "Monthly",
      "proofs": [
        {
          "doc": "Training provider invoice",
          "level": "Required",
          "granularity": "Per staff",
          "provider": "Ella Baral (HR)"
        }
      ],
      "notarised": false,
      "appliesTo": "All origins",
      "flags": [],
      "note": "Training frequency is depending on the training plan from HR"
    }
  ]
}
```

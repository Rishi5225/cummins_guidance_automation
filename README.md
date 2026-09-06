# Cummins Guidance Application – Automation

## 1. Overview

This repository is for automation testing of the Cummins Guidance Application using Robot Framework.

The system under test follows the communication flow:

Cummins Engine → ECU → Adapter → Mobile/Windows → Guidance Application

The automation will validate that ECU-generated faults, parameters, calibrations, and other relevant data are correctly communicated through the Adapter and reflected in the Guidance Application.

## 2. ECU Variants

The automation framework will support multiple ECU variants:

- CSAR
- CORE 2
- PCC2300
- PCC3300
- PCC3400
- Future ECU variants as required

## 3. Proposed Repository Structure

```text
cummins-guidance-automation/
│
├── tests/
│   ├── common/
│   ├── csar/
│   ├── core2/
│   ├── pcc2300/
│   ├── pcc3300/
│   └── pcc3400/
│
├── resources/
│   ├── keywords/
│   ├── locators/
│   └── variables/
│
├── config/
│   ├── csar/
│   ├── core2/
│   ├── pcc2300/
│   ├── pcc3300/
│   └── pcc3400/
│
├── testdata/
│
├── libraries/
├── utils/
├── scripts/
│
├── artifacts/
│   ├── logs/
│   ├── screenshots/
│   ├── reports/
│   ├── videos/
│   └── raw_data/
│
├── docs/
│
├── .gitignore
├── README.md
└── requirements.txt

4. Folder Purpose
Folder	Purpose
tests/	            Robot Framework test cases, separated into common and ECU-specific tests
resources/	        Reusable keywords, locators and variables
config/	            ECU-specific configurations
testdata/	          Input data and expected results
libraries/	        Custom Robot/Python libraries
utils/	            ECU, Adapter and Application utilities
scripts/	          Test execution and environment setup scripts
artifacts/	        Runtime logs, screenshots, reports, videos and raw data
docs/	              Architecture, test strategy and setup documentation

5. Common vs ECU-Specific Approach

The framework will follow a common framework + ECU-specific configuration/test approach.

Common functionality will be implemented once and reused across ECU variants wherever applicable.

              Common Framework
                     │
       ┌─────────────┼─────────────┐
       ↓             ↓             ↓
     CSAR          CORE 2       PCC2300
       │             │             │
 ECU-specific    ECU-specific   ECU-specific
 configuration   configuration  configuration

This will minimize duplicate automation code and simplify maintenance.

6. Test Execution Artifacts

Execution artifacts will be generated under:

artifacts/
├── logs/
├── screenshots/
├── reports/
├── videos/
└── raw_data/

These artifacts will primarily be used for debugging, failure analysis and test evidence.

Generated artifacts should not be committed to Git for every execution. They can be archived through the CI/CD pipeline (e.g., Jenkins).

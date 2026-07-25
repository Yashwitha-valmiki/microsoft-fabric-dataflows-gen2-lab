# Microsoft Fabric Dataflows Gen2 Lab

End-to-end ETL pipeline built with **Microsoft Fabric Dataflows Gen2**. This lab ingests, transforms, and loads sales orders data into a **Lakehouse** using **Power Query M**.

This repository was built as part of **DP-600 exam preparation**.

---

## Author

- GitHub: **Yashwitha-valmiki**

---

## Project Overview

This project demonstrates a practical ETL workflow in Microsoft Fabric:

1. **Extract** sales orders data from source files/tables.
2. **Transform** data using Power Query M (cleaning, shaping, type handling).
3. **Load** curated data into a Fabric Lakehouse.

The goal is to simulate a common analytics engineering pattern and reinforce DP-600 skills.

---

## Tech Stack

- Microsoft Fabric
- Dataflows Gen2
- Power Query M
- Lakehouse (OneLake)

---

## ETL Flow

- **Ingestion Layer**
  - Connect to source sales orders dataset.
  - Configure schema detection and initial profiling.

- **Transformation Layer**
  - Rename and standardize columns.
  - Convert data types (dates, numeric, text).
  - Handle nulls and invalid records.
  - Derive additional business fields where needed.

- **Load Layer**
  - Write transformed output to Lakehouse tables.
  - Validate row counts and key fields after load.

---

## Repository Structure

```text
.
├── README.md
└── LAB_GUIDE.md
```

---

## Learning Outcomes (DP-600 Aligned)

- Build and orchestrate ETL with Dataflows Gen2.
- Apply robust Power Query transformations.
- Deliver cleaned analytical data into a Lakehouse.
- Understand practical medallion-style data preparation patterns.

---

## How to Use This Repository

1. Review the implementation steps in `LAB_GUIDE.md`.
2. Recreate the same flow in your Fabric workspace.
3. Adapt transformations to your own source schema.
4. Validate final output in Lakehouse tables.

---

## Notes

- This lab is educational and intended for Microsoft Fabric learning.
- Naming conventions and transformations can be customized for enterprise standards.

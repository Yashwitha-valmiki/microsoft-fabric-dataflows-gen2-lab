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
3. **Load** curated data into Lakehouse tables.
4. **Orchestrate** refresh with a Data Pipeline.

---

## Tech Stack

- Microsoft Fabric
- Dataflows Gen2
- Power Query M
- Lakehouse (OneLake)
- Data Pipeline

---

## Architecture Flow

CSV Source (GitHub Raw URL)
→ Dataflow Gen2 (Power Query transformations)
→ Lakehouse table (`orders_raw`, append mode)
→ Pipeline orchestration (`PL_Load_Orders_Data`)

---

## Dataset

- **Source**: Microsoft Learn sample dataset
- **URL**: `https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/orders.csv`

Expected columns include:
- `SalesOrderID`
- `OrderDate`
- `CustomerID`
- `LineItem`
- `ProductID`
- `OrderQty`
- `LineItemTotal`
- `MonthNo` (custom column, derived from `OrderDate`)

---

## Power Query M Formula

```m
= Date.Month([OrderDate])
```

---

## Naming Conventions

- Dataflow: `DF_Orders_Ingestion`
- Connection: `CONN_GitHub_Orders_CSV`
- Lakehouse table: `orders_raw`
- Pipeline: `PL_Load_Orders_Data`

---

## What to Upload (Recommended)

- `README.md`
- `LAB_GUIDE.md`
- `screenshots/` folder containing execution evidence:
  - Power Query transformations
  - Destination settings (Append)
  - Dataflow run success
  - Pipeline activity setup
  - Pipeline run success
  - Lakehouse `orders_raw` table verification

---

## How to Use This Repository

1. Open `LAB_GUIDE.md`.
2. Recreate the ETL steps in your Fabric workspace.
3. Use the dataset URL above as source input.
4. Validate output in Lakehouse table `orders_raw`.

---

## References

- Microsoft Fabric docs: https://learn.microsoft.com/fabric/
- Power Query M reference: https://learn.microsoft.com/powerquery-m/

# LAB GUIDE — Microsoft Fabric Dataflows Gen2 ETL Pipeline

## Purpose

This guide walks through building an end-to-end ETL pipeline in Microsoft Fabric Dataflows Gen2 for sales orders data, then loading the curated output into a Lakehouse.

---

## Author

- GitHub: **Yashwitha-valmiki**

---

## Prerequisites

- Microsoft Fabric workspace access.
- Permission to create Dataflows Gen2 and Lakehouse artifacts.
- Source sales orders dataset (CSV, Excel, SQL, or similar).

---

## Lab Steps

## 1) Create / Select a Lakehouse

1. Open Microsoft Fabric workspace.
2. Create a new **Lakehouse** (or use an existing one).
3. Note the target table names for loaded data.

---

## 2) Create a Dataflow Gen2

1. In the same workspace, create a new **Dataflow Gen2**.
2. Name it clearly (example: `df_sales_orders_etl`).
3. Save initial draft.

---

## 3) Connect to Source Data

1. Add a new data source.
2. Choose connector type (CSV / Excel / SQL / etc.).
3. Authenticate and load source table/file.
4. Confirm source columns and preview quality.

---

## 4) Apply Transformations (Power Query M)

Perform transformations like:

- Promote headers
- Remove unnecessary columns
- Rename fields to standardized names
- Set correct data types (date, decimal, integer, text)
- Handle null/blank values
- Remove duplicates (if required)
- Add calculated columns (if needed)

### Example M Pattern (illustrative)

```powerquery
let
    Source = ...,
    PromotedHeaders = Table.PromoteHeaders(Source, [PromoteAllScalars=true]),
    ChangedTypes = Table.TransformColumnTypes(
        PromotedHeaders,
        {
            {"OrderID", Int64.Type},
            {"OrderDate", type date},
            {"CustomerName", type text},
            {"Amount", type number}
        }
    ),
    FilteredRows = Table.SelectRows(ChangedTypes, each [OrderID] <> null)
in
    FilteredRows
```

> Replace sample column names with your actual schema.

---

## 5) Configure Destination (Lakehouse)

1. Set destination to the target **Lakehouse**.
2. Choose target table name (example: `sales_orders_curated`).
3. Configure write behavior (append/replace as needed).

---

## 6) Publish and Refresh

1. Publish the Dataflow Gen2.
2. Trigger a refresh run.
3. Monitor run status for success/failure.

---

## 7) Validate Output

1. Open Lakehouse table.
2. Validate:
   - Row count
   - Data types
   - Null handling
   - Key business fields
3. Compare sampled records with source data for integrity.

---

## Suggested Validation Checklist

- [ ] All expected source records are loaded.
- [ ] Numeric/date/text types are correct.
- [ ] No unintended nulls in required columns.
- [ ] Duplicate records handled as designed.
- [ ] Table naming follows workspace standards.

---

## Troubleshooting Quick Notes

- **Schema drift**: Re-check source headers and type mapping.
- **Refresh failure**: Verify credentials and connector permissions.
- **Type conversion errors**: Add safe conversion steps or filter bad records.
- **Missing rows**: Review filter logic in transformation steps.

---

## DP-600 Skill Mapping

This lab strengthens DP-600-relevant skills in:

- Data ingestion with Fabric Dataflows Gen2
- Data transformation with Power Query M
- Loading curated data to Lakehouse
- Data quality validation in analytics workflows

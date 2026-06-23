# Model Selection Note

**Date:** 2026-06-23
**Author:** Dzianis Dziadkou - Engineer
**Project:** INNIO
**Task:** Generate a first-draft test plan to validate table content/datatypes after integration between Oracle source and Azure Synapse target
**Committed location:** "C:\study\AI\AIRun\kata1"

---

## Evaluation Criteria

| # | Criterion | Why it matters for this task |
|---|-----------|------------------------------|
| 1 | No data loss after integration, null validation | Data quality is important
| 2 | Build standard list of datatypes annd its precissions | Using standard types as milestones
| 3 | Use smallest standard datatype possible | Affects size of the DWH
| 4 | Checks should be on the Source and Target sizes | In case of recent data creation/modification

---

## Prompt Used

1. Name:
Generate a first-draft test plan to validate table content/datatypes after integration between Oracle source and Azure Synapse target

2. Evaluation:
- No data loss after integration, null validation;
- Build standard list of datatypes annd its precissions
- Use smallest standard datatype possible
- Checks should be on the Source and Target sizes

Make the output 3-5 sentences only

---

## Output Comparison

### Model A: Deepseek r1
> Okay, the user wants a test plan to validate data after moving from Oracle to Azure Synapse. The key points are ensuring no data loss, checking nulls, data types with precision, using the smallest possible types, and comparing source and target sizes.
First, I need to check row counts and null values. So, for each table, compare the count in Oracle and Synapse. Also, check if any non-nullable columns in Oracle have nulls in Synapse. That covers d

### Model B: Anthropic Sonnet 4.5
> Data Integration Validation is a systematic testing framework that ensures zero data loss between Oracle source and Azure Synapse target by comparing row counts, checksums, and performing null validation to verify NULL values are correctly preserved or transformed during migration. The plan includes a standardized datatype mapping reference (e.g., Oracle NUMBER(10,2) to Synapse DECIMAL(10,2), CLOB to VARCHAR(MAX)) with defined precisions, prioritizing the smallest viable datatype to optimize storage efficiency. Source and target size comparisons validate both record counts and column-level byte allocations to detect truncation or overflow issues. Null distribution checks ensure that nullable columns maintain data consistency and that no unintended NULL injection or elimination occurs post-integration.

---

## Scorecard

| Criterion | Model A score (1–3) | Model A evidence | Model B score (1–3) | Model B evidence |
|-----------|---------------------|------------------|---------------------|------------------|
| [Criterion 1] | 1 | The key points are ensuring no data loss, checking nulls, ...| 1 | that ensures zero data loss between Oracle source and Azure Synapse target 
| [Criterion 2] | 1 | No info. Datatype Alignment: Map Oracle types (e.g., NUMBER(10,0) → Synapse INT, VARCHAR2(50) → VARCHAR(50)) via system tables, enforcing Synapse types use minimal precision without overflow | 2 | The plan includes a standardized datatype mapping reference (e.g., Oracle NUMBER(10,2) to Synapse DECIMAL(10,2), CLOB to VARCHAR(MAX)) with defined precisions, prioritizing the smallest viable datatype to optimize storage efficiency
| [Criterion 3] | 2 | using the smallest possible types  | 2 | prioritizing the smallest viable datatype to optimize storage efficiency
| [Criterion 4] | 1 | Maybe create a table that lists each column's source and target types, precision, and any issues | 2 | Source and target size comparisons validate both record counts and column-level byte allocations to detect truncation or overflow issues
| **Total** | 1.25| Lack of standartization datatypes| 1.75 | includes standartization approach

---

## Decision

**Selected model:** Anthropic Sonnet 4.5

**Rationale:** Both look good by the Sonnet includes standartization approach

---

## Active Constraint

**What could change this decision within 30 days:**
[Real cases and examples]

---

## Revision history

| Version | Date | Change |
|---------|------|--------|
| 1.0 | 2026-06-23 | Initial commit |
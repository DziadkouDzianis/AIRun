# Model Selection Note

**Date:** 2026-06-23
**Author:** Dzianis Dziadkou - Engineer
**Project:** INNIO
**Task:** I need to know the lineage of the specific table and the place where data got lost. Write a concept
**Committed location:** "C:\study\AI\AIRun\kata1"

---

## Evaluation Criteria

| # | Criterion | Why it matters for this task |
|---|-----------|------------------------------|
| 1 | Queries are well-writen with proper style, intentions and SQL Syntax | Easy and convenient to read the SQL |
| 2 | All downstream objects could be queried based on the given/missed ID(s). If the exact ID cannot be used then lookup/derived query should be used instead in the same query | Easy access to the root object |
| 3 | Checks should be done against every subobject if it can directly disappear the line (ex, INNER JOIN) | Exclude extra JOIN and finding IDs by human |
| 4 | Ignore if there is any datagap | Datagap can affect the output if this is a new record|
| 5 | Make sure based on the table/column names that PII data is not exposed | Security reasons|

---

## Prompt Used

1. Name:
I need to know the lineage of the specific table and the place where data got lost. Write a concept.

2. Evaluation:
- Queries are well-writen with proper style, intentions and SQL Syntax;
- All downstream objects could be queried based on the given/missed ID(s). If the exact ID cannot be used then lookup/derived query should be used instead in the same query;
- Checks should be done against every subobject if it can directly disappear the line (ex, INNER JOIN);
- Ignore if there is any datagap;
- Make sure based on the table/column names that PII data is not exposed.

Make the output 3-5 sentences only

---

## Output Comparison

### Model A: Deepseek r1
> Okay, let's tackle this problem. The user wants a concept to determine the lineage of a specific table and identify where data was lost. They mentioned using SQL queries with proper syntax and style. First, I need to ensure that the queries can track downstream objects using the given or derived IDs. If the exact ID isn't available, I should use lookups or derived queries.
Next, I have to check every subobject, especially those using INNER JOINs, because they can exclude records if there's no match. That's a common place where data might disappear. Also, need to ignore data gaps and avoid exposing PII by checking table and column names...

### Model B: Anthropic Opus 4.5
> Data Lineage Traceability is a systematic approach to track the flow of data through a pipeline, identifying the exact transformation step or table where specific records are dropped or lost. The investigation involves writing well-structured SQL queries that trace downstream objects using given or derived IDs, while examining each subobject (particularly INNER JOINs, WHERE clauses, and filtering conditions) that could eliminate records from the result set. Queries must follow proper SQL syntax and naming conventions, ensuring that lookups are embedded within the same query when exact IDs are unavailable. The evaluation excludes known data gaps and validates that no Personally Identifiable Information (PII) is exposed through column names or query outputs. This methodology enables root cause identification of data loss while maintaining data governance and query quality standards...

---

## Scorecard

| Criterion | Model A score (1–3) | Model A evidence | Model B score (1–3) | Model B evidence |
|-----------|---------------------|------------------|---------------------|------------------|
| [Criterion 1] | 2 | They mentioned using SQL queries with proper syntax and style. | 2 | The investigation involves writing well-structured SQL queries that trace |
| [Criterion 2] | 2 | If the exact ID isn't available, I should use lookups or derived queries. | 2 | that trace downstream objects using given or derived IDs |
| [Criterion 3] | 2 | I have to check every subobject, especially those using INNER JOINs, because they can exclude records if there's no match | 2 | while examining each subobject (particularly INNER JOINs, WHERE clauses, and filtering conditions) that could eliminate records from the result set |
| [Criterion 4] | 1 | Also, need to ignore data gaps  | 2 |  The evaluation excludes known data gaps |
| [Criterion 5] | 2 | Avoid exposing PII by checking table and column names| 2 | hat no Personally Identifiable Information (PII) is exposed through column names or query outputs. This methodology enables root cause identification of data loss while maintaining data governance and query quality standards.|
| **Total** | 1.8| | 2 | |

---

## Decision

**Selected model:** Anthropic Opus 4.5

**Rationale:** Currently it is hard to decide which is better as there was no any real example to find the gap. Will check later in anothe modules.

---

## Active Constraint

**What could change this decision within 30 days:**
[Context window. No project file was reviewd during the task. I think it will affect the ouput]

---

## Revision history

| Version | Date | Change |
|---------|------|--------|
| 1.0 | 2026-06-23 | Initial commit |
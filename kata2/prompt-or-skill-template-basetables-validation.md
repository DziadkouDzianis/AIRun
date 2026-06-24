# Prompt Template: Test Case

**Date:** 2026-06-27
**Author:** Dzianis Dziadkou - Engineer
**Project:** INNIO
**Model:** Claude Sonnet 4.5 via DIAL
**DIAL location:** https://chat.lab.epam.com/share/8H4PWze5Vz4ZZYJk5ygtY2fYau88Rd2bGP4iVVu33U71qrrVTyb4QdmEFZh1VWoZa9xjaCZ8BJc7setM4gCMSGs1k4meA9LviXH883AnHEhnJF1aBY7i5SkJfbZ6wi1obwnWvBsDSA5Ri8bmfzbJW7dEe
**Committed location:** (https://github.com/DziadkouDzianis/AIRun/blob/main/)

---

## Purpose

Generate a test case list from a {{user_story}} description. Is used by QA and Engineers before the release to make sure changes were properly implemented and applied.

---

## Variable Placeholders

| Placeholder | Description | Example value |
|---|---|---|
| `{{user_story}}` | User story description | Variable text |
| `{{jira_ticket}}` | Jira ticket number | DA-2369 |
| `{{assignee}}` | Assignee | Dzianis Dziadkou |
| `{{labels}}`(Optional) | Labels. Might be filled based on the description| Backend/Frontend/Python/LogicApp or any if empty|

---

## Output Format Instruction

Return a markdown table with columns "Case ID", "Scope for Label", "Test case description", "Steps to reproduce". Maximum 10 rows, no more then 150 words. No preamble.

---

## Prompt Body


Analyze the following user story and generate test cases for validation:

Ticket: {{jira_ticket}} Assignee: {{assignee}} Labels: {{labels}}

User Story: {{user_story}}

Based on the user story above, generate comprehensive test cases covering:

Happy path scenarios
Edge cases
Negative scenarios
Integration points (if applicable)
For each test case, provide:

Case ID: Sequential number (TC-01, TC-02, etc.)
Scope for Label: Technology scope (Backend, Frontend, Python, LogicApp, ADF, Database, API, etc.)
Test case description: Brief description of what is being tested
Steps to reproduce: Numbered steps to execute the test



---

## Test Run (Author)

**Input values used:**
- `{{jira_ticket}}` = DA-1232
- `{{assignee}}` = Dzianis Dziadkou

**Output quality:** Looks good and comprehensive based on the input context.

---

## Peer Review

**Reviewer:** Volha Vuntsevich
**Date reviewed:** 2026-06-24
**Model used by reviewer:** Anthropic Sonnet 4.5

**Reviewer input values used:**
- `{{jira_ticket}}` = DA-2346
- `{{assignee}}` = Volha Vuntsevich

| Review question | Reviewer answer |
|---|---|
| Could you run the template without asking the author anything? | Yes |
| Was the output format what you expected? | No. Some paragraphs were mixed |
| Would you use this template on your own work? | Yes |
| One concrete improvement suggestion | Better context as an input |

---

## Revision History

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | YYYY-MM-DD | Initial commit | Dzianis Dziadkou |
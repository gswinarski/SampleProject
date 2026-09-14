---
id: AC-ADDRESS
title: Address validation and FTTH qualification — acceptance criteria
type: acceptance-criteria
topic_id: ADDRESS
status: draft
relates_to:
- BP-ADDRESS
---

# Address validation and FTTH qualification — acceptance criteria

| ID | Given / When | Then |
|---|---|---|
| AC-ADDR-01 | One reliable match for a complete address | Show the normalized address and ask the user to confirm. |
| AC-ADDR-02 | Several candidates | The user selects a candidate; qualification never uses an arbitrary address. |
| AC-ADDR-03 | No match | Allow correction or manual verification. |
| AC-ADDR-04 | Required unit number is missing | Require completion before qualification. |
| AC-ADDR-05 | Verified address with an available result | Store address reference, result, time and qualification ID. |
| AC-ADDR-06 | Unavailable result | Show the reason without implying the address is invalid. |
| AC-ADDR-07 | Pending/unknown result | Show a pending state and retain the reference for follow-up. |
| AC-ADDR-08 | Registry or qualification timeout | Show a technical error and retry; do not store unavailable. |
| AC-ADDR-09 | Address or unit changes after qualification | The old result is no longer current for the form. |
| AC-ADDR-10 | An older response arrives for a previous address | Do not overwrite the current address result. |

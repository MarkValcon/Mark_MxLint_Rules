# Mark_MxLint_Rules
Public rules repository for MxLint

RegoMark 1.2 — release notes

**Removed**
008_0016 UncommittedStatusChangeReturned has been retired because it produced too many false positives. As a result, uncommitted status changes returned to the client are no longer detected. The number 008_0016 will not be reused.

**Changed**
008_0009 NoPrimitiveParamsOnUserRoleMicroflows no longer flags Enumeration parameters. An enumeration can only take its defined values. String, Integer, Decimal and DateTime parameters are still reported as before.

**Fixed**
008_0006 RetrieveOrCreateCompleteness: a database retrieve used only as a lookup is no longer reported as an entity mismatch. A lookup retrieve is one whose result is only set as a value on the newly created object.
008_0004 CustomErrorHandlingMustUseLatestError: two identical $latestError log activities are now both counted. Before, they were counted as one, which caused false "$latestError is only used 1 times" findings. The same fix applies to all microflow rules, so identical activities in a microflow are no longer merged when rules count them.
008_0007 UnneededListOperations:
A Head after a database retrieve with a custom range (skip/amount) is no longer flagged. A custom range always returns a list, so the Head is needed.
A list operation inside a loop is no longer flagged when the retrieve is outside that loop. Sort inside a loop is still flagged, and so is a list operation in the same loop body as its retrieve.

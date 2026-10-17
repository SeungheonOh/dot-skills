---
name: refresh-connected-workbook
description: "Refresh selected existing Excel data connections through their native consumer, reconcile source freshness, loaded tables and dependent reports, and preserve workbook edits through a verified saved result. Use for a bounded external-data refresh, not new connections, query redesign, formula repair, data cleanup or scheduled reporting."
---

# Refresh the workbook people actually use

Deliver the selected workbook with its intended external-data results refreshed and its required reports checked, or an exact account of the layer that remains stale. Preserve its existing query definitions, input choices and unrelated work. A recent preview, completed connection or changed total alone does not establish a usable saved report.

This workflow operates an existing supported Excel connection or Power Query pipeline. Use [formula repair](../repair-spreadsheet-formulas/SKILL.md) when a calculation is wrong, [spreadsheet modeling](../build-spreadsheet-model/SKILL.md) when relationships need designing, and [integration reconciliation](../integration-delivery-reconciliation/SKILL.md) for missing event deliveries between services. Do not turn a refresh into a new data-import system, source-data correction, workbook-link migration or recurring job.

## Establish the refresh contract

Resolve the essentials from the request, workbook and available authorized records:

- Exact workbook identity/revision, application/version, platform and actual user session
- Selected report, query, connection, loaded table or model table that needs updating
- Expected source account, environment, file or endpoint, and existing parameter/filter values
- Required freshness: latest available source, a named published batch, or a specific reporting cutoff
- Outputs that must agree, manual inputs/annotations that must survive, and expected data shape
- Whether the user requested inspection, a separate refreshed copy, or an in-place refresh of the named shared workbook

For a simple one-table workbook, keep this to a small checklist. Ask only when an unresolved source, cutoff or destination changes the result. Do not demand a full data dictionary before refreshing an established ordinary report. If no freshness requirement is stated, use the latest available authorized source and report what its freshness evidence actually establishes; do not invent a historical snapshot.

Use the user's chosen application and supported refresh capability. A library that reads cached cells or writes workbook XML cannot perform the connection's native refresh. If that consumer is unavailable, finish the connection/dependency inventory and acceptance plan, mark execution unperformed and state the missing capability. Do not rebuild the workbook as plain tables to simulate success.

## Keep refresh within the approved data boundary

A refresh can contact sources, execute stored query logic, replace loaded data and save newly retrieved content to the workbook's audience. Establish those effects before starting. A refresh request does not authorize another tenant, a new source, a broader dataset, new recipient access, query rewrites or source-database changes. Keep private report content out of public searches and support sites.

Inspect the existing source bindings and query definitions through a passive route before any operation that might evaluate them. Opening the query editor, loading a preview or opening a refresh-on-open workbook can be an execution boundary; do not use those actions merely to discover whether access is safe. If a safe inspection route cannot establish an unfamiliar query's destinations and effects, hold execution and obtain the missing definition or owner confirmation.

In particular, a native database query is not guaranteed read-only merely because it is used by Power Query. [Microsoft's native-query guidance](https://learn.microsoft.com/en-us/power-query/native-database-query) explicitly distinguishes import intent from possible database effects. Do not run unknown SQL, stored procedures, scripts, custom connectors or workbook macros as a diagnostic experiment. Hold unapproved effects rather than approving a new native-query prompt automatically.

Combining sources can also transmit one source's values to another during query folding. Preserve the existing privacy boundary and verify that any such transfer is authorized for the data and destination. [Microsoft explains this cross-source behavior and the Data Privacy Firewall](https://learn.microsoft.com/en-us/power-query/data-privacy-firewall). Do not ignore privacy levels, mark private data public or weaken certificate checks to remove an error.

Use an existing authorized session. If sign-in is required, use the supported secure handoff; never extract stored credentials or ask for a password, API key or connection-string secret in chat. Newly creating or materially expanding persistent access requires action-time confirmation. Enabling trusted content, changing security settings, installing a driver/add-in or granting new permissions needs its own applicable approval. Do not clear all source permissions, save authentication or trust an entire folder as an incidental fix.

Check whether saving will expose new data through an already shared or automatically synchronized workbook. Confirm that the selected data and audience are within scope; hidden sheets and model tables are not a privacy boundary. Prepare a private copy only when that destination and use are authorized, without treating a copy as permission for broader source access.

## 1. Preserve the starting workbook and locate each layer

Preserve current unsaved edits through a supported save or separate copy before replacement can occur. For an in-place refresh, establish a recoverable baseline and check for concurrent editors. Do not force-close another session or overwrite an intervening revision. When working on a copy, verify that relative paths, workbook-derived parameters and source bindings still resolve to the intended source; changing location can change what is read.

Record the relevant native objects and their relationships:

| Layer | Evidence to retain | What it does not prove |
| --- | --- | --- |
| Source | Account/environment, exact file/object, batch or available cutoff, selected parameters | That Excel has read that version |
| Query/connection | Native name/identity, source bindings, dependencies, enabled load destinations | That a visible preview reached the report |
| Loaded result | Worksheet table/range or Data Model table, row/key coverage, selected values | That every dependent report refreshed |
| Report | PivotTable source/cache relationship, formulas, filters/slicers, required charts | That a saved workbook contains this view |
| Saved delivery | Exact file/revision, save result and readback evidence | That every future opener can refresh it |

Distinguish an input Excel table from the query's output table, even when their columns look alike. Identify connection-only queries and which loaded outputs depend on them. A workbook formula link, a Power Query connection and a PivotTable cache are different mechanisms; do not select a similarly named object without tracing its role.

Inspect relevant refresh settings without changing them: refresh on open, timed refresh, background operation, participation in Refresh All, and whether retrieved data is retained when saving. [Excel connection properties](https://support.microsoft.com/en-us/excel/connection-properties) distinguish refresh timing from saved-data retention and warn that changing connection names can disrupt references. Keep native identities and unrelated settings intact.

Preserve manual content inside or beside loaded regions, formulas, validation, named ranges, table relationships and required formatting. Establish whether refresh can replace edits, reorder records or expand into nearby content. Match annotations by stable record identity, never by their current row number. If manual work cannot be preserved reliably, stop before refresh rather than promising that Undo will recover it. Moving annotations or redesigning the sheet is a separate change.

## 2. Choose a bounded refresh path and freshness check

Follow the selected output backward through its real dependencies. Include the prerequisites it actually consumes, but not every connection merely because it is listed. Record the smallest supported command that refreshes the selected loaded output. Use Refresh All only when its actual target set and effects fit the request; inspect excluded connections and hidden outputs rather than assuming “all” means everything required.

For Excel, the native route commonly begins at Data > Queries & Connections, then the selected query/connection or the table that consumes it. Verify the visible controls for the installed version. Microsoft's [external-data refresh guide](https://support.microsoft.com/en-us/excel/refresh-an-external-data-connection-in-excel) distinguishes worksheet refresh from Power Query Editor's Refresh Preview: preview refresh updates the editor cache but does not update the worksheet or Data Model. Use the route that reaches the requested load destination.

Define an independent freshness discriminator before starting, such as a known changed record, published batch ID, source-provided completion marker or a bounded source total under the same filters. A timestamp written by the workbook's own refresh expression shows evaluation time, not source completeness. File modification time, a preview timestamp and the newest record date each have narrower meanings; label them accordingly.

Check source readiness through already authorized evidence. An empty result may be legitimate, but absence from a preview sample or a permission-limited source is not proof that the dataset is empty. Do not seed a live source with a test record. Use existing source evidence or an approved disposable copy for any distinguishing check.

When related outputs must describe one batch, establish a common supported snapshot/batch boundary. Power Query may evaluate referenced queries independently and make multiple source requests; [Microsoft documents this behavior](https://learn.microsoft.com/en-us/power-query/multiple-queries). Do not assume one click, a shared query name or manual sequential refresh creates a transaction across sources. If the source changes during the refresh and no consistent boundary exists, report per-output observation times and keep a cross-table snapshot claim unverified. Do not change queries or add buffering to conceal that limitation.

Retain established data-shaping rules. Unexpected column names/types, parameter values, units or access scope are a compatibility hold. Do not delete a failing transformation step, replace errors with zero, broaden a filter or redirect to a similarly named source to make refresh finish. If current data no longer fits the existing contract, return the exact mismatch for a separately authorized repair.

## 3. Run once and follow each selected output to completion

Immediately before starting, recheck the workbook revision, relevant unsaved/concurrent work, selected source and parameter values. Ensure no refresh already owns the same output. Preserve the baseline identity, start time and requested target list.

Invoke the supported native refresh for the selected scope. If it launches background work, wait on the actual status and output evidence. A responsive worksheet or dismissed progress dialog is not a terminal result. Do not issue repeated refreshes because no visible value changed. Background behavior differs by connection type, so use the status exposed by the actual consumer rather than prescribing one universal wait period.

Record per-output states: not started, running, completed, failed, cancelled or unknown. Retain the useful error boundary without copying secrets. A completed refresh with unchanged values can be correct if source identity and the independent freshness check agree. A connection success followed by load failure is still an unfinished workbook refresh.

For authentication or permission errors, compare the expected source/account with the actual prompt and stop for the necessary authorized access. [Microsoft's data-source settings guidance](https://support.microsoft.com/en-us/excel/manage-data-source-settings-and-permissions-power-query) separates current-workbook sources from global permissions affecting other workbooks. Inspect the narrow source; do not reset global permissions or switch identities to bypass access restrictions.

For unavailable sources, capacity limits, schema errors or partial results, retain which outputs completed and which still contain older data. Do not present a mixed-age workbook as a coherent current report. If the user asked for a specific source batch, a newer but different batch is also a mismatch.

## 4. Reconcile loaded data and dependent reports

Inspect the actual destination table or model, not just the query editor. Check the selected source discriminator, expected schema/types, representative identifiers and relevant error/null handling. Reconcile counts in their correct units: source records, transformed rows, distinct keys and grouped report rows are not interchangeable. Account for established filters, joins and aggregations instead of demanding that every layer have the same count.

Check a meaningful added, changed or removed record when source evidence supports it, and an unchanged protected input or annotation. Equal row counts can conceal one missing and one duplicate record. If the source population cannot be fully established, state the narrower checks and remaining completeness limit. Do not invent an exact reconciliation from a sampled preview.

Once the required load is complete, update or inspect its dependent report through the appropriate native route. [Microsoft's PivotTable refresh guidance](https://support.microsoft.com/en-us/excel/refresh-pivottable-data) documents refreshing a selected PivotTable and checking its status; automatic behavior depends on version and source. Confirm the actual PivotTable's source, filters, grouping and values instead of assuming it followed the loaded table. Check a dependent total or chart against the refreshed inputs, including any intentionally filtered-out rows.

Recalculate required formulas only within the approved execution boundary. Calculation is not a substitute for retrieving source data, and a data refresh is not proof that every formula has recalculated. Preserve the established calculation mode and other open workbooks; route a wrong expression to formula repair rather than altering it under a refresh-only request.

Inspect for displaced notes, overwritten manual values, broken references, changed table extent and unreadable output. If source data is correct but a report remains stale or fails to expand, identify that downstream boundary. Do not erase nearby content, change report definitions or remove filters simply to force agreement.

## 5. Save, read back and report the actual result

Save to the authorized destination with native features intact. Keep a separate candidate separate; do not replace the shared original unless that was requested. Check the saved file/revision and its relevant data, parameters, inputs and report outputs through a preserving readback route.

A reopen must not accidentally initiate another refresh or run active content outside the agreed scope. Use a supported inspection mode that preserves that boundary, or explicitly include a further native refresh only when authorized and necessary. If safe saved-state readback is unavailable, report the completed in-session observations and the unverified saved-state boundary rather than weakening security settings. Distinguish data actually saved from a workbook intentionally configured to discard retrieved data on save.

Acceptance for the requested result requires:

- Correct workbook, sources, parameters and selected refresh scope
- Evidenced completion at each required loaded destination, with source freshness stated honestly
- Required dependent reports checked against those loaded results
- Manual work, unrelated data and native features preserved
- Exact saved destination read back at the claimed level, with failures and mixed-age outputs visible

Return the refreshed workbook or verified location, a short source-to-output refresh record, completed checks and any remaining holds. For each important output include the source/batch basis, observed completion and saved-readback state; one small table is usually enough. Do not promise that a recipient has source access merely because they can open the saved data.

Stop when the selected refresh and available acceptance checks are complete, or when a specific permission, source, definition or consumer capability blocks further progress. Do not add a schedule, change source permissions or send the report elsewhere as implied follow-up.

## Interrupted or failed refresh

After a timeout, lost control or cancellation, inspect native refresh status and current outputs before retrying. Cancellation is not proof that earlier completed outputs were rolled back. Preserve the partial candidate and mark each output's actual state; keep it out of the accepted-delivery slot.

Retry only the affected supported scope after confirming that the prior operation ended, the source/query effects remain authorized and the same data contract still applies. A retry may read a later source version; update its evidence rather than merging observations into the first attempt. Unknown database side effects or uncertain ownership block an automatic retry.

If recovery requires returning to the baseline, prefer a separate preserved copy. Do not restore an entire shared workbook over later edits or treat Excel Undo as guaranteed refresh rollback. For an uncertain save, inspect the exact destination before saving again. Keep recovery scoped to this task and retain unresolved outputs with the smallest next action.

## Fictional, unexecuted illustration

A fictional stock workbook contains an existing query that loads a table, a PivotTable grouped by category, and a separate keyed notes table. The approved source batch is `B-24`: item `P-004` changed from 7 to 9 units, item `P-008` was removed, and the established filter excludes reserved stock. A recent editor preview already shows `B-24`, but the worksheet table still reflects `B-23`.

The planned action refreshes the existing loaded output, checks `P-004`, the supported removal and the filter's population, then checks the PivotTable against that completed load. Notes remain attached to their item IDs even if row order changes. If the table reaches `B-24` but the PivotTable still shows the old total, the table stage is complete and the report stage remains open; a preview timestamp cannot close it.

These identifiers, quantities and states are invented. No workbook was opened, source contacted, query executed, credential entered, data refreshed, report recalculated or file saved for this illustration.

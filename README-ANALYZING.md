

# Named Search variables
## Settings
### Exclusion
In Mining search, exclusion controls how results are deduplicated when browsing:

None (default): Every match is reported. If turn 5 matches "National" and "African", you get 2 results. If 3 terms in "National" match turn 5, you still get 1 (first term wins per subgroup per segment — that's hardcoded).
Exclude turn: Once a turn matches any subgroup, it's skipped entirely for all remaining subgroups. Each turn appears at most once across all results.
Exclude subgroup: Once a subgroup captures a match in any turn, that subgroup stops searching. Each subgroup captures at most one turn total.
# BottleneckIQ Validation Summary

Last verified: 22 July 2026

## Automated checks

| Validation pack | Passed |
|---|---:|
| Broad warehouse scenarios | 112 / 112 |
| Edge-case robustness | 33 / 33 |
| Decision consistency | 5 / 5 |
| Workflow configuration | 9 / 9 |
| Capacity and staffing conditions | 9 / 9 |
| Close-decision handling | 7 / 7 |
| Reporting and consistency safeguards | 26 / 26 |
| Input quality checks | 18 / 18 |
| Public-data robustness | 3 / 3 |
| **Non-overlapping total** | **222 / 222** |

The older 9-case core regression pack also passes but is excluded from the total because it overlaps the broad matrix.

The synthetic matrix covers all six operation slots, balanced and constrained
conditions, changing operating patterns, missing optional fields, timestamp
defects, and low-volume inputs. Expected outcomes are defined before
BottleneckIQ receives the generated event logs.

## Public real-data checks

The closest public real warehouse source contains anonymized outbound WMS milestones:

- Full scope: **767,723 selected stage events** and **130,835 traces**
- Clean scope: **246,449 selected stage events** and **41,927 traces**
- Independent analytical rank correlation: **1.000**
- Under one fixed workflow interpretation, the same candidate appeared in **12 / 12** complete months of 2024

The public source has milestone timestamps but no measured task intervals or
resource field. It validates large-file handling, temporal analysis,
conservative confidence behavior, and implementation consistency; it cannot
validate every internal component at once.

## Interpretation limits

- `222 / 222` is test coverage, not universal warehouse accuracy.
- Correlation `1.000` verifies agreement with an independent implementation, not true-bottleneck ground truth.
- Workflow assumptions must be confirmed with warehouse process knowledge.
- ROI remains a scenario until financial inputs and operational evidence are confirmed.
- A floor-confirmed pilot with before/after system throughput is still required for causal field validation.

The production implementation and reproducible validation code are maintained in the private repository.

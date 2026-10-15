# TravelTide — Customer Segmentation and Rewards Proposal

## Purpose

This project supports the design of TravelTide’s rewards program. It groups customers by observed activity and proposes a benefit approach for each group. The recommendation is to test these proposals in a controlled pilot before a wider rollout.

## Recommended segments and benefits

The final segmentation covers 5,782 customers. It uses engagement recency and recent noncanceled booking frequency. RFM and LRFM were explored as benchmarks; the final model is an activity-based segmentation, not classic RFM or LRFM.

| Segment | Customers | Observed activity | Proposed benefit |
| --- | ---: | --- | --- |
| The Regulars | 2,041 | Higher booking activity, more recent engagement | Availability-based partner stay enhancement |
| The Reconnectors | 2,239 | Higher booking activity, less recent engagement | Capped next-booking partner credit |
| The Explorers | 666 | Lower booking activity, more recent engagement | Member trip tracker with saved options and useful alerts |
| The Occasional Visitors | 836 | Lower booking activity, less recent engagement | Preference-led welcome with a choice of approved benefits |

The names describe relative activity patterns, not verified customer identities or preferences. Five Regulars without observed hotel bookings receive the trip-tracker proposal instead of a hotel-related benefit.

## Handover materials

- **Presentation and English report:** the business recommendation, supporting figures, methodology, and limitations.
- **`results/named_segment_profiles.csv`:** segment sizes and original-unit profiles, including spending-data coverage.
- **`results/segment_benefit_summary.csv`:** proposed benefit counts by segment, including the hotel-applicability exception.
- **`notebooks/`:** the analysis from feature preparation to the final segment names and benefit proposal.

Customer-level assignments are kept separate from the public repository. The summary tables do not contain customer identifiers.

## Decisions before a pilot

1. Confirm which services and partner benefits can actually be delivered.
2. Approve eligibility, funding, cost caps, and cancellation handling.
3. Randomize customer invitations between the proposed message and a generic invitation or approved alternative.
4. Measure enrollment, subsequent repeat bookings, and cost across all randomized customers—not only those who open an invitation.

Benefits are hypotheses, not validated favorite perks. No retention or profit uplift has been demonstrated. Booking expenditure is estimated where inputs support it and must not be treated as contribution margin.

## Technical handover

The notebooks retain their original numbering. Run them in this order:

| Notebook | Role |
| --- | --- |
| `01_build_own_features_fixed.ipynb` | Validate the source exports and build customer features |
| `03_prepare_rfm_lrfm.ipynb` | Prepare windowed features and RFM/LRFM inputs |
| `04_compare_and_profile_segments.ipynb` | Compare benchmark models and create preliminary assignments |
| `06_assign_provisional_perks.ipynb` | Build the earlier policy required by notebook 08 |
| `07_test_full_cohort_clustering.ipynb` | Evaluate activity-based clustering across the full cohort |
| `08_consolidate_segments_and_perks.ipynb` | Consolidate the selected four-group solution |
| `09_update_names_and_business_proposal.ipynb` | Apply the final names and business-aligned benefit policy |

Notebook 09 supersedes the earlier benefit policy. The earlier policy remains in the workflow as a dependency, not as the final recommendation.

### Local setup

Use Python 3.10 or later. From the project root, install the dependencies and start JupyterLab:

```bash
python -m pip install -r requirements.txt
python -m jupyterlab
```

Place the matching authorized study-cohort exports—`users.csv`, `sessions.csv`, `flights.csv`, and `hotels.csv`—in `data/raw/`. Raw exports are not included. The notebooks expect the original study exports and their columns, not arbitrary full-database exports.

Derived features are written to `data/own_processed/`; subsequent outputs go to `reports/`. Rerunning a notebook replaces its generated outputs. The final customer-level export is:

```text
reports/business_aligned_delivery/customer_segments_business_aligned.csv
```

Keep source data and customer-level outputs in an access-controlled location unless publication is explicitly authorized.

### Reproduction status and limits

Notebook syntax and agreement between the existing aggregate tables and final customer export have been checked. The packaged workflow has not been rerun end to end from raw exports, and dependencies are not a frozen environment.

The segmentation describes observed behavior; it does not establish causes of retention or churn. Feature windows differ, signup exposure is unequal, and spending coverage is incomplete. These limitations should remain visible when interpreting the segments and evaluating the pilot.

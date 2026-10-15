# Submission note

*For Anuar — presentation clarification and next learning priorities.*

## Scope of the repository cleanup

I have kept this cleanup deliberately limited: selecting the relevant notebooks, removing saved outputs and local editor files, correcting setup paths, and adding a short handover. This is not a production refactor or a new analysis. My understanding of the assessment guidance was that the code itself would not affect the project evaluation, so I prioritized the presentation, report, and business recommendation rather than extensive repository polishing.

## Clarification of my presentation and Q&A

I became very nervous and experienced a significant mental block during both the presentation and the questions. I would like to clarify two points that I did not explain accurately.

**RFM/LRFM:** When I said these approaches “did not work,” that was too broad. What I meant was that the exploration did not confirm my initial expectation of their usefulness for this particular recommendation. That is not the same as the methods failing. They remained useful benchmarks. The final choice emphasized coverage of the full study cohort and interpretable activity patterns, not a claim that RFM or LRFM is generally unsuitable.

**The two-variable model:** The final K-means model used each individual customer's engagement recency—time since the last session—and recent noncanceled booking frequency. The medians in the presentation summarized the resulting groups; the model was not fitted to those group medians. Other measures were considered in feature preparation, the RFM/LRFM comparison, and segment profiling, but they were not additional inputs to the final two-feature clustering. I did not make that distinction clear in my answer. The choice of two inputs also does not establish that this was the optimal model.

## Why I still wanted to prepare this handover

Beyond completing the submission, I want to start the AI Applications and Product Engineering courses on a stronger footing. My next priorities include revisiting object-oriented programming and understanding how backend and frontend responsibilities fit together in an application.

These courses feel particularly relevant to the career directions I want to explore: Customer Success Management, Implementation Management, and Technical Sales. I want to become more confident connecting a business problem with a technical solution, explaining the trade-offs, and supporting its implementation. Preparing a manageable project handover is a small step toward that goal—not an attempt to present this repository as production-ready software.

# Experiment Plan: Segment-Driven Campaign Validation

Goal:

- validate that segment-specific interventions outperform a generic campaign baseline.

## Hypotheses

1. Champions treatment increases IRPU vs control.
2. Frequent Explorers treatment increases 30-day reorder rate vs control.
3. Loyal Occasionals treatment increases monthly order frequency vs control.
4. At Risk treatment increases reactivation rate vs control.

## Experimental design

Unit of randomization:

- user-level randomization within each segment.

Arms:

1. Control: current/default campaign logic.
2. Treatment: segment-specific intervention from playbook.

Assignment:

- stratified randomization by segment and recent activity band.

Duration:

- minimum 4 weeks, extend to 6-8 weeks if event rates are low (especially At Risk).

## Success criteria

Primary:

- positive, statistically significant lift in each segment’s primary KPI.

Secondary:

- no significant degradation in guardrail KPI.

Decision rule:

1. Launch if primary KPI lift is positive and guardrail remains within agreed threshold.
2. Iterate if effect is mixed or confidence interval crosses zero.
3. Stop if guardrail damage exceeds threshold even when primary lift is positive.

## Sample size approach

Use historical baseline metrics to compute minimum detectable effect (MDE) per segment:

1. pick alpha = 0.05 and power = 0.80
2. estimate baseline conversion/reorder/activation rates from last 8-12 weeks
3. set realistic MDE bands:
- Champions: small MDE is acceptable due to high volume
- At Risk: larger MDE may be needed due to lower base rates

Document exact sample-size numbers in experiment launch ticket before execution.

## Guardrails

1. margin impact
2. opt-out / complaint rate
3. delivery SLA and stockout pressure (if campaign drives spikes)

## Reporting template

Every readout should include:

1. treatment and control sample sizes
2. absolute and relative lift
3. confidence interval
4. guardrail status
5. recommendation: launch, iterate, or stop

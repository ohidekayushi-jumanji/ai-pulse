AI Audit Evaluation Methodology

1. Objective

Establish a repeatable evaluation process for an AI-assisted quality audit system that identifies potentially misleading claims, disclosure failures, and inappropriate enrolment pressure.

The objective is not simply to maximise classification accuracy. The system must also minimise the risk of missing serious compliance violations.

2. Evaluation Dataset

The accompanying CSV contains 20 synthetic conversation examples.

Each record includes:

* A unique case identifier.
* A synthetic conversation excerpt.
* An expected violation label.
* A severity category.
* A simulated prediction from a baseline approach.
* A simulated prediction from a candidate approach.

The expected labels represent illustrative ground truth for this exercise. In a real deployment, they would require documented annotation guidelines and review by appropriately qualified human reviewers.

3. Evaluation Metrics

Accuracy

The proportion of all examples classified correctly.

Accuracy is useful as an overall measure but may conceal poor performance on rare, high-severity cases.

Precision

The proportion of predicted violations that are genuine violations.

Low precision can create unnecessary investigations and reviewer workload.

Recall

The proportion of genuine violations correctly identified.

Low recall means the system misses actual violations.

False-negative rate

The proportion of genuine violations incorrectly classified as compliant.

This metric deserves particular attention when the missed violation could cause material harm.

Critical misses

The number of critical violations incorrectly classified as compliant.

Critical misses should be reviewed individually rather than hidden within an aggregate score.

4. Evaluation Procedure

1. Freeze the labelled evaluation dataset before testing.
2. Evaluate the baseline and candidate using the same examples.
3. Compare their predictions against the expected labels.
4. Calculate accuracy, precision, recall, and false-negative rates.
5. Examine errors by severity.
6. Investigate regressions introduced by the candidate.
7. Document the release decision and its rationale.

5. Proposed Release Gate

The following is a proposed design for this prototype, not an established organisational policy.

A candidate should not be automatically released merely because overall accuracy improves.

A serious regression should trigger:

* A release hold.
* Human investigation of the affected examples.
* Targeted additions to the evaluation set.
* Repeat testing after the prompt is revised.
* Documented approval before release.

A real system would also require appropriate validation of the dataset, statistical uncertainty, monitoring, and operational requirements.

6. Limitations

The supplied predictions are simulated. They do not establish the performance of a real language model.

The dataset is small and illustrative, and the labels simplify context-dependent compliance decisions.

The current dashboard demonstrates the proposed workflow but does not automatically calculate its displayed prompt-comparison results from this CSV.

7. Future Work

* Expand the evaluation dataset.
* Introduce independent human annotation and adjudication.
* Implement automated metric calculations.
* Test actual prompts against a fixed evaluation set.
* Track performance by violation category and severity.
* Establish documented release thresholds and monitoring procedures.

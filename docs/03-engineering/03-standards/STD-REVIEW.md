---
title: Engineering Review Standard
id: STD-REVIEW
version: 1.0.0
status: Draft
owner: Invara Labs
classification: Engineering Standard
review_cycle: Quarterly
created: 2026-07-30
last_updated: 2026-07-30
approved_by: TBD
authors:
  - Invara Labs Engineering
tags:
  - review
  - governance
  - quality
  - engineering
related:
  - DOC-STYLE
  - PB-AUTHORING
  - TERM-STANDARD
keywords: []
supersedes: null
superseded_by: null
---

# Overview

Engineering excellence depends not only on creating high-quality artefacts but also on validating them through disciplined, structured review. Independent review improves technical accuracy, strengthens consistency, encourages knowledge sharing, and ensures that engineering decisions align with organisational standards and long-term architectural goals.

The Engineering Review Standard establishes the governance framework for reviewing engineering artefacts within the Invara Labs Engineering Operating System (ILOS). It defines the principles, lifecycle, responsibilities, evaluation criteria, and approval process used to assess engineering documentation before publication or implementation.

Within ILOS, review is considered an essential engineering practice rather than an administrative checkpoint. Every governed artefact should undergo an appropriate level of review to ensure that it is technically correct, complete, maintainable, traceable, and aligned with applicable engineering principles, playbooks, standards, and organisational objectives.

This standard applies to all engineering artefacts maintained within the Engineering Operating System, including but not limited to:

- Engineering Principles
- Engineering Playbooks
- Engineering Standards
- Engineering References
- Engineering Examples
- Architecture Decision Records (ADRs)
- Requests for Comments (RFCs)
- Technical proposals
- Templates
- Checklists

The Engineering Review Standard complements other governance standards by defining how engineering artefacts are evaluated before approval and publication. It promotes consistency in review practices across teams while supporting continuous improvement, accountability, and engineering excellence.

By establishing a repeatable, transparent, and measurable review process, this standard helps ensure that every published engineering artefact contributes to a reliable, trusted, and sustainable body of organisational knowledge.

# Purpose

The purpose of the Engineering Review Standard is to establish a consistent, transparent, and repeatable framework for reviewing engineering artefacts across the Invara Labs Engineering Operating System (ILOS). It ensures that every governed artefact is evaluated against defined quality expectations before approval, publication, or implementation.

This standard provides a common review process that promotes technical accuracy, architectural consistency, documentation quality, and organisational alignment. By defining how reviews are conducted, who participates, and what criteria are applied, it reduces subjectivity and helps engineering teams make informed, evidence-based decisions.

The Engineering Review Standard exists to:

- Establish a uniform review process for all governed engineering artefacts.
- Improve the quality, accuracy, and completeness of engineering documentation.
- Verify alignment with engineering principles, playbooks, standards, and organisational objectives.
- Encourage constructive collaboration and knowledge sharing across engineering teams.
- Identify issues early, reducing the cost and risk of downstream corrections.
- Promote accountability by defining clear review roles, responsibilities, and approval expectations.
- Maintain traceability of review decisions throughout the lifecycle of an engineering artefact.
- Support continuous improvement by incorporating review feedback into future revisions.

This standard applies equally to documentation, architectural artefacts, governance documents, technical proposals, reference material, and other engineering knowledge assets. While the depth and scope of a review may vary depending on the type, complexity, and impact of the artefact, the underlying governance principles defined by this standard remain consistent.

By adopting a disciplined review process, ILOS strengthens confidence in its engineering knowledge base, supports organisational learning, and ensures that published artefacts remain reliable, maintainable, and fit for long-term use.

# Objectives

The Engineering Review Standard aims to establish a robust and consistent review process that improves the quality, reliability, and maintainability of engineering artefacts throughout the Invara Labs Engineering Operating System (ILOS).

The objectives of this standard are to:

- Establish a standardised review process that can be applied consistently across all governed engineering artefacts.
- Ensure engineering artefacts are technically accurate, complete, and fit for their intended purpose before approval or publication.
- Promote consistency with established engineering principles, playbooks, standards, and organisational governance.
- Define clear review roles, responsibilities, and approval authorities to improve accountability and decision-making.
- Encourage constructive collaboration by incorporating feedback from relevant stakeholders throughout the review process.
- Detect defects, inconsistencies, ambiguities, and omissions early, reducing the cost and impact of corrective actions.
- Improve the readability, maintainability, and long-term value of engineering documentation and related artefacts.
- Preserve traceability by recording review outcomes, significant feedback, approval decisions, and revision history.
- Support risk management by ensuring that high-impact engineering decisions receive an appropriate level of review before implementation.
- Enable continuous improvement by analysing review outcomes, recurring issues, and quality metrics to refine engineering practices over time.
- Establish measurable quality criteria that allow engineering teams to evaluate artefacts objectively rather than relying on subjective judgement.
- Encourage the responsible use of AI-assisted review capabilities while ensuring that final approval remains under human accountability.

By achieving these objectives, the Engineering Review Standard strengthens engineering governance, improves organisational knowledge quality, and ensures that engineering artefacts remain trustworthy, consistent, and sustainable throughout their lifecycle.

# Scope

The Engineering Review Standard applies to all governed engineering artefacts produced, maintained, or approved within the Invara Labs Engineering Operating System (ILOS). It establishes the minimum review requirements that engineering teams shall follow before an artefact is approved, published, or adopted as an organisational reference.

This standard applies regardless of whether an artefact is newly created, significantly modified, or undergoing a scheduled review as part of its governance lifecycle.

---

## In Scope

The following engineering artefacts are governed by this standard:

- Engineering Principles
- Engineering Playbooks
- Engineering Standards
- Engineering References
- Engineering Examples
- Architecture Decision Records (ADRs)
- Requests for Comments (RFCs)
- Technical proposals
- Design documents
- Engineering templates
- Governance documents
- Checklists
- Process documentation
- Technical guidelines

The review process defined by this standard may also be applied to other engineering artefacts where independent review improves quality, consistency, or organisational alignment.

---

## Organisational Scope

This standard applies to all individuals responsible for creating, reviewing, approving, or maintaining engineering artefacts, including:

- Engineers
- Technical Leads
- Software Architects
- Engineering Managers
- Technical Writers
- Engineering Governance Representatives
- Subject Matter Experts (SMEs)
- Designated Reviewers
- Approvers and Document Owners

Every participant is responsible for fulfilling the review responsibilities assigned to their role.

---

## Review Activities Covered

This standard governs review activities throughout the lifecycle of an engineering artefact, including:

- Initial technical review
- Peer review
- Architecture review
- Editorial and documentation review
- Governance review
- Compliance review
- Approval review
- Periodic review of published artefacts
- Review following significant revisions

The type and depth of review should be appropriate to the complexity, criticality, and intended audience of the artefact.

---

## Out of Scope

This standard does not define:

- Software code review processes.
- Automated testing or quality assurance procedures.
- Product or project management workflows.
- Release management or deployment approvals.
- Security, legal, or regulatory compliance processes beyond their interaction with engineering documentation.
- Organisation-wide business approval processes unrelated to engineering governance.

These activities may be governed by separate organisational standards and should be referenced where applicable.

---

## Relationship to Other Standards

The Engineering Review Standard complements other engineering governance artefacts within ILOS and should be applied alongside:

- Engineering Documentation Style Guide (DOC-STYLE)
- Engineering Playbook Authoring Standard (PB-AUTHORING)
- Engineering Terminology Standard (TERM-STANDARD)
- Engineering Governance Standard (STD-GOVERNANCE)
- Architecture Decision Record Standard (ADR-STANDARD)
- Request for Comments Standard (RFC-STANDARD)

Where multiple standards apply, this standard governs the review process, while the corresponding standards define the specific quality, structure, or governance requirements to be assessed.

---

## Scope Maintenance

The scope of this standard should be reviewed periodically to ensure it remains aligned with organisational practices, engineering governance, and the evolving structure of the Engineering Operating System.

Changes to the scope should follow the Engineering Review Standard's defined review and approval process before publication.

---

## Summary

The Engineering Review Standard establishes a consistent review framework for all governed engineering artefacts within ILOS. By clearly defining what is included, who is responsible, and where the standard applies, it promotes uniform review practices, strengthens governance, and ensures that engineering knowledge is reviewed with an appropriate level of rigour before publication or adoption.

# Review Philosophy

Engineering review is a collaborative quality assurance practice that strengthens engineering artefacts through independent evaluation, constructive feedback, and informed decision-making. Its primary purpose is to improve the quality of an artefact, reduce risk, and ensure alignment with organisational engineering standards—not to evaluate individual performance.

Within the Invara Labs Engineering Operating System (ILOS), reviews are viewed as an integral part of the engineering lifecycle rather than a final approval gate. Every review is an opportunity to validate assumptions, identify risks, share knowledge, and improve the clarity, consistency, and maintainability of engineering artefacts.

The Engineering Review Standard is founded on the belief that high-quality engineering outcomes result from diverse perspectives, open communication, and evidence-based evaluation. Reviewers are expected to assess artefacts objectively against established standards and documented criteria rather than personal preferences or informal conventions.

Engineering reviews should embody the following principles:

- **Quality First** – Prioritise the technical accuracy, completeness, and long-term maintainability of engineering artefacts.
- **Constructive Collaboration** – Provide feedback that is respectful, actionable, and focused on improving the artefact.
- **Evidence-Based Decisions** – Base review outcomes on documented standards, requirements, and objective evaluation criteria.
- **Shared Ownership** – Treat quality as a collective responsibility shared by authors, reviewers, and approvers.
- **Transparency** – Record significant review findings, decisions, approvals, and rationale to maintain organisational traceability.
- **Consistency** – Apply the same review expectations and governance processes across comparable engineering artefacts.
- **Continuous Improvement** – Use review outcomes and recurring observations to refine engineering practices, standards, and documentation over time.

Reviews should encourage discussion and learning while maintaining a focus on achieving the best possible engineering outcome. Differing technical opinions should be resolved through reasoned analysis, documented evidence, and alignment with established organisational guidance.

Engineering reviews are not intended to:

- Judge an individual's competence or performance.
- Delay delivery through unnecessary bureaucracy.
- Enforce personal coding or documentation preferences that conflict with established standards.
- Replace technical ownership or decision-making responsibilities.
- Prevent innovation where appropriate governance and risk management are maintained.

The effectiveness of the Engineering Review Standard depends on fostering a culture of trust, professionalism, and continuous learning. Every participant should approach reviews with the shared objective of improving engineering quality and preserving the integrity of the Engineering Operating System.

By embedding these principles into every review activity, ILOS ensures that engineering artefacts evolve through thoughtful collaboration, objective assessment, and disciplined governance, creating a reliable and sustainable engineering knowledge ecosystem.

# Review Principles

The Engineering Review Standard is founded on a set of core principles that ensure reviews are objective, consistent, transparent, and effective. These principles apply to all engineering reviews conducted within the Invara Labs Engineering Operating System (ILOS), regardless of the artefact type, complexity, or review participants.

All reviewers, authors, approvers, and stakeholders shall adhere to these principles throughout the review lifecycle.

---

## Objectivity

Reviews shall be based on documented evidence, established engineering standards, and defined acceptance criteria rather than personal preferences or subjective opinions.

Review comments should reference applicable engineering artefacts wherever possible, including:

- Engineering Principles
- Engineering Playbooks
- Engineering Standards
- Architecture Decision Records (ADRs)
- Requests for Comments (RFCs)
- Organisational policies

Objective reviews improve consistency and reduce ambiguity in engineering decisions.

---

## Independence

Where practical, reviews should be performed by individuals who were not the primary authors of the artefact.

Independent review provides fresh perspectives, increases the likelihood of identifying issues, and reduces confirmation bias.

The degree of independence should be proportional to the impact and criticality of the artefact.

---

## Constructive Feedback

Review feedback shall be professional, respectful, and focused on improving the artefact.

Feedback should:

- Clearly identify the issue.
- Explain why it is important.
- Reference supporting standards or guidance where applicable.
- Provide actionable recommendations.

Reviews should encourage collaboration rather than criticism.

---

## Consistency

Comparable engineering artefacts shall be reviewed using consistent processes, quality criteria, and governance expectations.

Review outcomes should not vary solely because different reviewers are involved.

Standardised review practices improve fairness, predictability, and organisational quality.

---

## Traceability

Significant review comments, decisions, approvals, and requested changes shall be recorded and preserved as part of the artefact's governance history.

Traceability enables:

- Historical reference.
- Auditability.
- Knowledge preservation.
- Decision transparency.
- Continuous improvement.

---

## Risk-Based Review

The level of review should reflect the potential impact of the artefact.

Higher-risk artefacts should receive broader and more rigorous review than low-risk artefacts.

Factors influencing review depth include:

- Business impact.
- Technical complexity.
- Architectural significance.
- Organisational scope.
- Regulatory or compliance implications.

---

## Timeliness

Reviews should be completed within agreed organisational timeframes to avoid unnecessary delays while maintaining review quality.

Review participants should:

- Respond promptly.
- Raise concerns early.
- Avoid prolonged review cycles.
- Escalate unresolved issues when appropriate.

Efficient reviews support engineering delivery without compromising quality.

---

## Accountability

Every review participant has clearly defined responsibilities.

Authors are responsible for producing review-ready artefacts.

Reviewers are responsible for providing objective and constructive feedback.

Approvers are responsible for ensuring that all required review criteria have been satisfied before approval.

Accountability strengthens governance and ensures that review outcomes are appropriately owned.

---

## Continuous Improvement

Engineering reviews should contribute to the ongoing improvement of engineering practices.

Recurring review findings should be analysed to:

- Improve engineering standards.
- Refine templates.
- Enhance playbooks.
- Update reference materials.
- Strengthen organisational knowledge.

Review is not only a quality gate but also a learning mechanism for the engineering organisation.

---

## Proportionality

Review effort should be proportionate to the size, complexity, and impact of the artefact.

Small editorial changes should not require the same level of review as major architectural decisions or governance updates.

Applying an appropriate level of review ensures that governance remains effective without creating unnecessary administrative overhead.

---

## Summary

These principles establish the foundation for all engineering reviews within ILOS. By promoting objectivity, independence, collaboration, consistency, traceability, accountability, and continuous improvement, they ensure that reviews deliver meaningful quality improvements while supporting efficient engineering governance.

# Review Lifecycle

The Engineering Review Lifecycle defines the standard process for evaluating, approving, publishing, and maintaining engineering artefacts within the Invara Labs Engineering Operating System (ILOS).

A structured lifecycle ensures that reviews are performed consistently, responsibilities are clearly understood, decisions are traceable, and artefacts meet the required quality standards before becoming authoritative engineering references.

While the complexity of a review may vary depending on the artefact, every review should follow the same high-level lifecycle.

---

## Review Lifecycle Overview

```text
Author Completes Artefact
          │
          ▼
Review Request
          │
          ▼
Reviewer Assignment
          │
          ▼
Review Preparation
          │
          ▼
Review Execution
          │
          ▼
Feedback & Discussion
          │
          ▼
Author Updates Artefact
          │
          ▼
Verification
          │
          ▼
Approval Decision
          │
          ▼
Publication
          │
          ▼
Periodic Review
          │
          ▼
Revision or Retirement
```

This lifecycle provides a repeatable process that balances engineering quality with efficient delivery.

---

## Stage 1 – Review Request

The review lifecycle begins when the author determines that an artefact is ready for review.

Before requesting a review, the author should ensure that the artefact:

- Is technically complete.
- Meets applicable documentation standards.
- Includes required metadata.
- Has been self-reviewed.
- Is ready for independent evaluation.

Incomplete or draft work should not be submitted for formal review.

---

## Stage 2 – Reviewer Assignment

An appropriate reviewer or review panel is assigned based on:

- Artefact classification.
- Technical domain.
- Architectural impact.
- Governance requirements.
- Subject matter expertise.

Reviewers should have sufficient knowledge to evaluate the artefact objectively.

Where practical, reviewers should be independent of the primary author.

---

## Stage 3 – Review Preparation

Before beginning the review, reviewers should:

- Understand the purpose of the artefact.
- Identify applicable standards.
- Review related documentation.
- Understand the intended audience.
- Clarify any review expectations.

Preparation enables reviewers to provide informed and meaningful feedback.

---

## Stage 4 – Review Execution

Reviewers evaluate the artefact against the applicable engineering standards and review criteria.

Depending on the review type, evaluation may include:

- Technical accuracy.
- Architecture.
- Documentation quality.
- Terminology.
- Governance compliance.
- Traceability.
- Maintainability.

Review findings should be evidence-based and reference applicable standards whenever possible.

---

## Stage 5 – Feedback and Discussion

Review feedback should be communicated clearly, respectfully, and constructively.

Each review comment should:

- Describe the issue.
- Explain its impact.
- Reference applicable guidance.
- Recommend an improvement where appropriate.

Authors and reviewers should collaborate to resolve disagreements through technical discussion and documented evidence.

---

## Stage 6 – Artefact Revision

The author evaluates review feedback and updates the artefact accordingly.

For each significant review comment, the author should:

- Accept and implement the recommendation.
- Provide justification for an alternative approach.
- Explain why the recommendation is not applicable.

Significant review decisions should be recorded where organisational traceability is required.

---

## Stage 7 – Verification

Following revision, reviewers verify that agreed changes have been addressed.

Verification confirms that:

- Required issues have been resolved.
- No unintended changes were introduced.
- Review objectives have been satisfied.
- The artefact is ready for approval.

Additional review iterations may be required if substantial changes are introduced.

---

## Stage 8 – Approval Decision

Once verification is complete, the designated approver determines whether the artefact should:

- Be approved for publication.
- Require additional revisions.
- Be rejected pending significant rework.
- Be escalated for further review.

Approval signifies that the artefact satisfies the applicable review requirements defined by this standard.

---

## Stage 9 – Publication

Approved artefacts become official engineering references within ILOS.

Publication activities typically include:

- Assigning the approved version.
- Updating revision history.
- Publishing to the documentation repository.
- Updating related references.
- Notifying relevant stakeholders where appropriate.

Only approved artefacts should be treated as authoritative organisational guidance.

---

## Stage 10 – Periodic Review

Publication does not conclude the review lifecycle.

Engineering artefacts should be reviewed periodically to ensure they remain:

- Accurate.
- Relevant.
- Current.
- Consistent with organisational practices.

Periodic reviews may result in:

- Continued publication.
- Minor revision.
- Major revision.
- Deprecation.
- Retirement.

---

## Review Iterations

Not every artefact will progress through the lifecycle in a single review cycle.

Complex or high-impact artefacts may require multiple iterations before approval.

Each iteration should:

- Resolve outstanding review comments.
- Improve artefact quality.
- Preserve review history.
- Maintain traceability of significant decisions.

Iterative review is an expected part of engineering quality assurance rather than an indication of failure.

---

## Lifecycle Governance

Throughout the review lifecycle:

- Authors remain responsible for the accuracy of their artefacts.
- Reviewers remain responsible for objective evaluation.
- Approvers remain responsible for publication decisions.
- Governance processes ensure consistency, traceability, and accountability.

Every stage contributes to maintaining a trusted and sustainable engineering knowledge base.

---

## Summary

The Engineering Review Lifecycle provides a structured and repeatable framework for reviewing engineering artefacts from initial submission through publication and ongoing maintenance.

By defining clear stages, responsibilities, and decision points, the lifecycle ensures that engineering knowledge is evaluated consistently, improved collaboratively, and governed effectively throughout its lifecycle within the Engineering Operating System.

# Roles and Responsibilities

Effective engineering reviews depend on clearly defined roles and responsibilities. Every participant in the review process contributes to the quality, consistency, and governance of engineering artefacts.

This section defines the primary roles involved in the Engineering Review Lifecycle and establishes the responsibilities associated with each role. While an individual may fulfil multiple roles depending on organisational size or team structure, the responsibilities assigned to each role remain distinct.

---

## Guiding Principles

Roles and responsibilities should be assigned to ensure:

- Clear ownership and accountability.
- Independent and objective evaluation.
- Appropriate subject matter expertise.
- Efficient decision-making.
- Transparent approval processes.
- Complete traceability throughout the review lifecycle.

---

## Engineering Artefact Author

The Engineering Artefact Author is responsible for creating and maintaining the engineering artefact.

### Responsibilities

The author shall:

- Produce technically accurate and complete artefacts.
- Ensure compliance with applicable engineering standards.
- Perform a self-review before requesting formal review.
- Provide sufficient context for reviewers.
- Respond to review feedback in a timely manner.
- Update the artefact based on accepted review comments.
- Document significant decisions where required.
- Maintain the artefact throughout its lifecycle.

The author remains accountable for the technical accuracy of the published artefact.

---

## Reviewer

A Reviewer performs an independent evaluation of the engineering artefact.

### Responsibilities

The reviewer shall:

- Review the artefact objectively.
- Evaluate the artefact against applicable standards.
- Provide constructive and actionable feedback.
- Identify technical, documentation, governance, or quality issues.
- Explain review findings with appropriate rationale.
- Verify that review comments have been addressed.
- Recommend approval or further revision.

Reviewers should focus on improving the artefact rather than evaluating the author.

---

## Subject Matter Expert (SME)

A Subject Matter Expert provides specialised knowledge for specific domains.

SMEs may participate when an artefact involves:

- Architecture
- Security
- Infrastructure
- Compliance
- Performance
- Domain-specific engineering knowledge

### Responsibilities

The SME shall:

- Validate specialised technical content.
- Identify domain-specific risks.
- Recommend improvements within their area of expertise.
- Confirm technical correctness where required.

SMEs provide expert guidance but do not automatically approve the artefact unless explicitly assigned that responsibility.

---

## Technical Lead

The Technical Lead ensures that engineering artefacts align with team practices and technical direction.

### Responsibilities

The Technical Lead shall:

- Ensure technical consistency.
- Validate implementation feasibility.
- Resolve technical disagreements.
- Escalate significant engineering risks.
- Support engineering quality improvements.

The Technical Lead may participate as both reviewer and approver depending on organisational governance.

---

## Engineering Architect

The Engineering Architect reviews artefacts with architectural significance.

Typical responsibilities include:

- Validating architectural alignment.
- Evaluating scalability.
- Reviewing system interactions.
- Assessing long-term maintainability.
- Ensuring consistency with enterprise architecture.

Architecture reviews are typically required for significant design or platform decisions.

---

## Documentation Reviewer

The Documentation Reviewer evaluates the quality of engineering communication.

### Responsibilities

The Documentation Reviewer shall verify:

- Structure
- Readability
- Clarity
- Terminology
- Metadata
- Cross-references
- Formatting
- Compliance with DOC-STYLE

Documentation reviewers focus on communication quality rather than technical implementation.

---

## Governance Reviewer

The Governance Reviewer ensures organisational compliance.

### Responsibilities

The Governance Reviewer shall verify:

- Required approvals.
- Versioning.
- Ownership.
- Traceability.
- Lifecycle compliance.
- Alignment with engineering governance.
- Compliance with applicable standards.

Governance reviews ensure organisational consistency across engineering artefacts.

---

## Approver

The Approver has the authority to accept or reject an engineering artefact for publication.

Approval should only occur after all required review activities have been completed.

### Responsibilities

The Approver shall:

- Review outstanding issues.
- Confirm completion of mandatory reviews.
- Verify that approval criteria have been satisfied.
- Approve publication or request further revision.
- Record the approval decision.

Approval signifies that the artefact satisfies organisational review expectations at the time of publication.

---

## Engineering Governance Team

Where applicable, the Engineering Governance Team oversees the operation of the review framework.

Typical responsibilities include:

- Maintaining engineering review standards.
- Monitoring review quality.
- Reviewing governance metrics.
- Supporting continuous improvement.
- Updating review processes.
- Providing organisational guidance.

The Governance Team owns the review process but does not replace technical ownership.

---

## Stakeholders

Stakeholders may provide feedback when engineering artefacts affect their area of responsibility.

Examples include:

- Product teams
- Operations
- Platform engineering
- Security
- Compliance
- Technical writers
- Business representatives

Stakeholder participation should be proportionate to the scope and impact of the artefact.

---

## Responsibility Matrix

The following table summarises the primary responsibilities of each role.

| Activity | Author | Reviewer | SME | Technical Lead | Architect | Documentation Reviewer | Governance Reviewer | Approver |
|----------|:------:|:--------:|:---:|:--------------:|:---------:|:----------------------:|:-------------------:|:---------:|
| Create artefact | ✓ | | | | | | | |
| Self-review | ✓ | | | | | | | |
| Technical review | | ✓ | ✓ | ✓ | ✓ | | | |
| Documentation review | | | | | | ✓ | | |
| Governance review | | | | | | | ✓ | |
| Respond to feedback | ✓ | | | | | | | |
| Verify changes | | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | |
| Final approval | | | | | | | | ✓ |
| Publication | ✓ | | | | | | | ✓ |
| Periodic review | ✓ | ✓ | | ✓ | ✓ | ✓ | ✓ | ✓ |

---

## Separation of Responsibilities

To maintain objectivity and governance integrity:

- Authors should not approve their own artefacts.
- Significant architectural decisions should undergo independent review.
- Governance approval should remain independent of authorship.
- High-impact artefacts should involve multiple reviewers.
- Conflicts of interest should be disclosed before participation.

Independent review strengthens trust in published engineering artefacts.

---

## Summary

Clearly defined roles and responsibilities ensure that engineering reviews are collaborative, accountable, and consistent. By assigning ownership for authoring, reviewing, approving, and governing engineering artefacts, ILOS establishes a transparent review process that improves quality, supports effective decision-making, and preserves the integrity of the Engineering Operating System.

# Review Criteria

The Engineering Review Criteria define the minimum quality expectations that every governed engineering artefact shall satisfy before approval and publication.

These criteria provide a consistent and objective framework for evaluating engineering artefacts, reducing subjective interpretation and ensuring that reviews focus on measurable quality attributes rather than personal preferences.

While individual review types may apply additional evaluation criteria, every engineering review should assess the applicable criteria defined in this standard.

---

## Overview

Engineering artefacts should be evaluated across the following quality dimensions:

| Quality Dimension | Purpose |
|-------------------|---------|
| Technical Accuracy | Ensures information is technically correct and supported by evidence. |
| Completeness | Ensures all required information is present. |
| Clarity | Ensures the artefact is understandable by its intended audience. |
| Consistency | Ensures alignment with organisational standards and terminology. |
| Traceability | Ensures decisions, references, and relationships can be followed. |
| Maintainability | Ensures the artefact can be updated and managed over time. |
| Governance Compliance | Ensures adherence to organisational review and documentation standards. |

Each quality dimension should be considered during every applicable engineering review.

---

## Technical Accuracy

Engineering artefacts shall present technically correct information that reflects the current state of the system or engineering practice.

Reviewers should verify:

- Facts are accurate.
- Technical statements are supported by evidence.
- Assumptions are clearly identified.
- Design decisions are technically sound.
- Examples are correct.
- References are accurate and current.

Technical inaccuracies should be corrected before approval.

---

## Completeness

An engineering artefact should contain all information necessary for its intended purpose.

Reviewers should verify that:

- Required sections are present.
- Metadata is complete.
- Required diagrams are included where applicable.
- Dependencies are identified.
- Constraints and assumptions are documented.
- References are provided where necessary.

Incomplete artefacts should not be approved.

---

## Clarity

Engineering documentation should communicate information clearly and unambiguously.

Reviewers should evaluate:

- Logical organisation.
- Readability.
- Appropriate terminology.
- Concise language.
- Defined technical concepts.
- Clear explanations.
- Appropriate use of examples.

The intended audience should be able to understand the artefact without unnecessary interpretation.

---

## Consistency

Engineering artefacts should remain consistent with organisational documentation and engineering practices.

Reviewers should verify consistency with:

- Engineering Principles.
- Engineering Playbooks.
- Engineering Standards.
- Approved terminology.
- Naming conventions.
- Documentation style.
- Cross-referenced artefacts.

Consistency reduces ambiguity and improves maintainability.

---

## Traceability

Engineering knowledge should be traceable throughout its lifecycle.

Reviewers should verify:

- Requirements are referenced where applicable.
- Architectural decisions are linked to supporting documentation.
- Cross-references are valid.
- Revision history is maintained.
- Ownership is identified.
- Related artefacts are referenced.

Traceability supports governance, auditing, and future maintenance.

---

## Maintainability

Engineering artefacts should remain sustainable throughout their lifecycle.

Reviewers should evaluate whether the artefact:

- Is easy to update.
- Uses reusable content where appropriate.
- Avoids duplication.
- Follows organisational templates.
- Separates stable information from frequently changing information.
- Can evolve without significant restructuring.

Maintainability reduces long-term documentation effort.

---

## Governance Compliance

Every engineering artefact shall comply with applicable organisational governance requirements.

Reviewers should verify:

- Required metadata is present.
- Document identifiers follow organisational standards.
- Required reviews have been completed.
- Version information is accurate.
- Ownership is assigned.
- Review cycle is defined.
- Approval requirements have been satisfied.

Governance compliance is required before publication.

---

## Risk Assessment

Reviewers should consider the potential impact of issues identified during the review.

Typical factors include:

- Technical risk.
- Business impact.
- Security implications.
- Architectural significance.
- Organisational impact.
- Regulatory considerations.

Higher-risk findings should receive greater attention during review and approval.

---

## Review Severity Levels

Review findings should be classified according to their impact.

| Severity | Description | Typical Action |
|----------|-------------|----------------|
| Critical | Prevents approval due to significant technical, governance, or compliance issues. | Must be resolved before approval. |
| Major | Significantly reduces quality or introduces unacceptable risk. | Should be resolved before approval. |
| Minor | Improves clarity, consistency, or maintainability but does not invalidate the artefact. | Resolve where practical before publication. |
| Suggestion | Recommended improvement that is optional and does not affect approval. | Consider during revision. |

Consistent severity classification helps reviewers prioritise feedback and enables approvers to make informed decisions.

---

## Applying Review Criteria

Not every criterion applies equally to every engineering artefact.

For example:

| Artefact | Primary Review Criteria |
|----------|-------------------------|
| Engineering Principle | Clarity, Consistency, Governance Compliance |
| Engineering Playbook | Completeness, Clarity, Traceability |
| Engineering Standard | Technical Accuracy, Governance Compliance, Consistency |
| ADR | Technical Accuracy, Traceability, Risk Assessment |
| RFC | Technical Accuracy, Completeness, Maintainability |
| Reference Document | Accuracy, Consistency, Maintainability |
| Example | Accuracy, Clarity, Maintainability |

Reviewers should apply professional judgement while ensuring that all applicable criteria are evaluated.

---

## Continuous Improvement

Recurring findings should be analysed to identify opportunities for improving:

- Engineering standards.
- Documentation templates.
- Review processes.
- Training materials.
- Engineering guidance.
- Organisational best practices.

Review criteria should evolve alongside the Engineering Operating System while maintaining consistency and governance.

---

## Summary

The Engineering Review Criteria establish a common quality framework for evaluating engineering artefacts across the Invara Labs Engineering Operating System.

By applying consistent evaluation criteria focused on technical accuracy, completeness, clarity, consistency, traceability, maintainability, governance compliance, and risk, reviewers can perform objective, repeatable, and high-quality reviews that strengthen engineering knowledge and support long-term organisational excellence.

# Review Checklist

The Engineering Review Checklist provides a structured approach for verifying that engineering artefacts satisfy the quality expectations defined by this standard.

The checklist promotes consistency across review activities, reduces the likelihood of overlooked issues, and supports objective, repeatable evaluations.

While individual review types may introduce additional checks, every engineering review should consider the applicable items defined in this checklist.

---

## Checklist Usage

Reviewers should:

- Apply the checklist appropriate to the artefact being reviewed.
- Record significant findings and recommendations.
- Classify findings using the defined review severity levels.
- Confirm that mandatory items have been addressed before approval.
- Exercise professional judgement where a checklist item is not applicable.

The checklist is intended to support—not replace—engineering expertise.

---

# 1. Pre-Review Checklist

Before beginning a formal review, verify that the artefact is ready for evaluation.

| Item | Status |
|------|:------:|
| Artefact is complete | ☐ |
| Required metadata is present | ☐ |
| Version information is correct | ☐ |
| Author has completed a self-review | ☐ |
| Required supporting documents are available | ☐ |
| Related artefacts are referenced | ☐ |
| Diagrams are included where required | ☐ |
| Review scope has been defined | ☐ |

---

# 2. Technical Review Checklist

Evaluate the technical quality of the artefact.

| Item | Status |
|------|:------:|
| Technical information is accurate | ☐ |
| Assumptions are documented | ☐ |
| Constraints are identified | ☐ |
| Design decisions are justified | ☐ |
| Risks are identified where applicable | ☐ |
| Examples are technically correct | ☐ |
| References are valid and current | ☐ |
| No conflicting technical guidance exists | ☐ |

---

# 3. Documentation Review Checklist

Evaluate the quality of engineering communication.

| Item | Status |
|------|:------:|
| Document structure follows organisational standards | ☐ |
| Language is clear and concise | ☐ |
| Terminology is consistent | ☐ |
| Grammar and spelling are correct | ☐ |
| Formatting complies with DOC-STYLE | ☐ |
| Headings are meaningful | ☐ |
| Cross-references are accurate | ☐ |
| Tables and diagrams are readable | ☐ |

---

# 4. Governance Review Checklist

Verify compliance with organisational governance requirements.

| Item | Status |
|------|:------:|
| Document identifier is correct | ☐ |
| Ownership is assigned | ☐ |
| Classification is correct | ☐ |
| Review cycle is defined | ☐ |
| Version follows organisational policy | ☐ |
| Required approvals have been obtained | ☐ |
| Revision history is updated | ☐ |
| Related artefacts are linked | ☐ |

---

# 5. Traceability Checklist

Ensure that engineering decisions can be traced throughout the documentation lifecycle.

| Item | Status |
|------|:------:|
| Supporting references are provided | ☐ |
| Related ADRs are referenced where applicable | ☐ |
| Related RFCs are referenced where applicable | ☐ |
| Dependencies are identified | ☐ |
| External standards are cited where required | ☐ |
| Historical decisions remain traceable | ☐ |

---

# 6. Maintainability Checklist

Verify that the artefact can be maintained over time.

| Item | Status |
|------|:------:|
| Information is logically organised | ☐ |
| Duplication is minimised | ☐ |
| Reusable content is referenced instead of copied | ☐ |
| Future updates can be applied easily | ☐ |
| Obsolete content has been removed | ☐ |
| Stable and frequently changing content are appropriately separated | ☐ |

---

# 7. Approval Readiness Checklist

Before approval, verify that the artefact is ready for publication.

| Item | Status |
|------|:------:|
| All critical findings have been resolved | ☐ |
| Major findings have been addressed or accepted | ☐ |
| Outstanding issues have documented justification | ☐ |
| Reviewer comments have been resolved | ☐ |
| Final approval has been obtained | ☐ |
| Publication version is assigned | ☐ |
| Artefact is ready for publication | ☐ |

---

## Recording Review Findings

Review findings should include:

- Description of the issue.
- Severity classification.
- Location within the artefact.
- Supporting rationale.
- Recommended action.
- Resolution status.

Recording findings consistently improves traceability and supports future reviews.

---

## Tailoring the Checklist

Not every checklist item applies to every engineering artefact.

Reviewers should adapt the checklist based on:

- Artefact classification.
- Review type.
- Technical complexity.
- Organisational impact.
- Risk level.
- Intended audience.

Mandatory governance requirements should always be verified.

---

## Checklist Maintenance

The Engineering Review Checklist should be reviewed periodically to ensure that it remains aligned with:

- Engineering Standards.
- Engineering Playbooks.
- Documentation practices.
- Governance requirements.
- Organisational objectives.

Updates to the checklist should follow the Engineering Review Lifecycle defined in this standard.

---

## Summary

The Engineering Review Checklist transforms the Engineering Review Criteria into a practical review tool that promotes consistency, completeness, and objectivity.

By providing structured verification steps for technical quality, documentation, governance, traceability, maintainability, and approval readiness, the checklist enables reviewers to perform thorough, repeatable, and high-quality reviews across all engineering artefacts within the Engineering Operating System.

# Review Outcomes

Every engineering review shall conclude with a clearly documented outcome. The review outcome represents the collective assessment of the engineering artefact against the applicable review criteria and determines the next stage in its lifecycle.

A review outcome should be objective, evidence-based, and supported by documented review findings. The outcome shall be communicated to the author and, where appropriate, recorded as part of the artefact's governance history.

Review outcomes enable consistent decision-making, improve traceability, and provide a clear path for authors to resolve outstanding issues before publication.

---

## Overview

The Engineering Review Standard defines the following review outcomes:

| Outcome | Description | Next Action |
|----------|-------------|-------------|
| Approved | The artefact satisfies all mandatory review requirements. | Proceed to publication. |
| Approved with Conditions | Minor issues remain but do not prevent publication. | Address agreed actions within the specified timeframe. |
| Revisions Required | The artefact requires additional work before approval. | Update the artefact and resubmit for review. |
| Rejected | The artefact does not meet the required quality or governance expectations. | Significant rework is required before a new review. |
| Escalated | The review identified issues requiring a higher level of decision-making. | Escalate to the appropriate authority for resolution. |

Each outcome should be selected based on the severity and impact of the review findings.

---

## Approved

An artefact may be approved when it satisfies all mandatory review criteria and no unresolved issues remain that would affect its technical accuracy, governance, or organisational suitability.

Typical characteristics include:

- No critical findings.
- All major findings resolved.
- Required approvals completed.
- Governance requirements satisfied.
- Ready for publication.

Approval indicates that the artefact is suitable for organisational use at the time of publication.

---

## Approved with Conditions

An artefact may be approved with conditions when only minor issues remain that do not materially affect its correctness or intended use.

Examples include:

- Minor editorial improvements.
- Formatting corrections.
- Additional examples.
- Non-essential clarifications.

Conditions should:

- Be documented.
- Include an owner.
- Define an expected completion timeframe.

Conditional approval should not be used for unresolved critical or major issues.

---

## Revisions Required

This outcome is appropriate when review findings prevent approval but can reasonably be addressed through further revision.

Examples include:

- Missing required sections.
- Incomplete technical information.
- Inconsistent terminology.
- Governance non-compliance.
- Unresolved review comments.

The artefact should be updated and resubmitted for verification once the identified issues have been addressed.

---

## Rejected

An artefact should be rejected when it fails to meet the minimum quality expectations defined by this standard.

Reasons for rejection may include:

- Significant technical inaccuracies.
- Major architectural concerns.
- Serious governance deficiencies.
- Unsupported assumptions.
- Inadequate evidence.
- Failure to address previous review findings.

A rejected artefact should undergo substantial revision before entering a new review cycle.

---

## Escalated

Certain review findings may require decisions beyond the authority of the assigned reviewers or approvers.

Escalation may be appropriate when:

- Significant architectural disagreements exist.
- Conflicting organisational standards are identified.
- Business, security, or regulatory risks require specialist input.
- Cross-functional agreement cannot be reached.

Escalated reviews should identify:

- The reason for escalation.
- The responsible decision-maker.
- Required actions.
- Final resolution.

---

## Documenting Review Outcomes

Every completed review should record, at a minimum:

- Review date.
- Artefact identifier.
- Review type.
- Review participants.
- Review outcome.
- Summary of findings.
- Outstanding actions.
- Approval decision.
- Reviewer and approver names.

Maintaining consistent review records improves auditability and organisational traceability.

---

## Resolving Outstanding Actions

Where conditions or revisions are required, each outstanding action should include:

| Field | Description |
|--------|-------------|
| Action ID | Unique identifier for the action. |
| Description | Summary of the required change. |
| Owner | Individual responsible for resolution. |
| Priority | Critical, Major, Minor, or Suggestion. |
| Due Date | Target completion date, where applicable. |
| Status | Open, In Progress, Resolved, or Accepted. |

Outstanding actions should be verified before the artefact progresses to its next lifecycle stage.

---

## Appeals and Dispute Resolution

Where significant disagreements arise regarding review findings or outcomes, the issue should be resolved through the established engineering governance process.

Disputes should:

- Be based on documented evidence.
- Reference applicable engineering standards.
- Involve the appropriate technical or governance authorities.
- Be resolved transparently.
- Preserve the rationale for the final decision.

Escalation should be viewed as a governance mechanism rather than a failure of the review process.

---

## Continuous Improvement

Review outcomes should be analysed periodically to identify organisational trends.

Examples include:

- Frequently recurring review findings.
- Common documentation issues.
- Governance compliance gaps.
- Review turnaround times.
- Areas requiring additional training or guidance.

Insights gained from review outcomes should be used to improve engineering standards, templates, training materials, and review practices.

---

## Summary

The Engineering Review Outcomes establish a consistent framework for concluding engineering reviews and determining the appropriate next steps.

By defining standard outcomes, documenting decisions, managing outstanding actions, and supporting transparent escalation where necessary, ILOS ensures that review decisions are objective, traceable, and aligned with organisational governance while promoting continuous improvement across the Engineering Operating System.

# Review Metrics

The Engineering Review Metrics establish a framework for measuring the effectiveness, efficiency, quality, and governance of engineering reviews within the Invara Labs Engineering Operating System (ILOS).

Metrics provide objective evidence that the review process is achieving its intended outcomes and enable engineering teams to identify opportunities for continuous improvement. Review metrics should support informed decision-making rather than individual performance evaluation.

The objective of measurement is to improve engineering processes, documentation quality, and organisational governance—not to assess or rank individuals.

---

## Measurement Principles

Review metrics should be:

- Objective and evidence-based.
- Consistently measured across engineering teams.
- Relevant to organisational goals.
- Actionable and easy to interpret.
- Reviewed periodically.
- Used to drive continuous improvement.

Metrics should encourage quality engineering practices without creating unnecessary administrative overhead.

---

## Metric Categories

Engineering review metrics are organised into the following categories:

| Category | Purpose |
|----------|---------|
| Quality Metrics | Measure the quality of engineering artefacts and review findings. |
| Efficiency Metrics | Measure the speed and effectiveness of the review process. |
| Governance Metrics | Measure compliance with engineering governance requirements. |
| Improvement Metrics | Measure the long-term effectiveness of organisational improvements. |

Together, these categories provide a balanced view of review performance.

---

## Quality Metrics

Quality metrics evaluate how effectively reviews identify and resolve issues before publication.

Typical metrics include:

| Metric | Description |
|---------|-------------|
| Review Findings per Artefact | Average number of findings identified during a review. |
| Critical Findings | Number of critical issues identified before approval. |
| Major Findings | Number of significant issues requiring revision. |
| Minor Findings | Number of low-impact improvements identified. |
| Finding Resolution Rate | Percentage of review findings resolved before approval. |
| Reopened Findings | Number of previously closed findings reopened due to incomplete resolution. |

Quality metrics help determine whether reviews are consistently improving engineering artefacts.

---

## Efficiency Metrics

Efficiency metrics evaluate how effectively the review lifecycle operates.

Typical metrics include:

| Metric | Description |
|---------|-------------|
| Average Review Duration | Time from review request to final outcome. |
| Average Reviewer Response Time | Time taken for reviewers to begin evaluation. |
| Average Resolution Time | Time taken to resolve review findings. |
| Number of Review Iterations | Average review cycles required before approval. |
| Approval Lead Time | Time from completion of review to approval. |

These metrics help identify process bottlenecks and opportunities for streamlining the review workflow.

---

## Governance Metrics

Governance metrics assess adherence to organisational review requirements.

Typical metrics include:

| Metric | Description |
|---------|-------------|
| Review Compliance Rate | Percentage of artefacts reviewed before publication. |
| Metadata Compliance | Percentage of artefacts with complete metadata. |
| Standards Compliance | Percentage of artefacts compliant with applicable engineering standards. |
| Review Completion Rate | Percentage of planned reviews completed within the required timeframe. |
| Periodic Review Compliance | Percentage of artefacts reviewed according to their defined review cycle. |

Governance metrics provide visibility into the health and maturity of the Engineering Operating System.

---

## Improvement Metrics

Improvement metrics measure how review insights contribute to organisational learning.

Typical metrics include:

| Metric | Description |
|---------|-------------|
| Recurring Finding Categories | Frequently repeated review issues. |
| Standards Updated from Review Feedback | Number of standards improved through review insights. |
| Template Improvements | Enhancements made to engineering templates. |
| Guidance Updates | Documentation improvements resulting from review observations. |
| Training Opportunities Identified | Areas where additional engineering education is required. |

Improvement metrics help ensure that review findings drive long-term organisational enhancement.

---

## Metric Interpretation

Metrics should always be interpreted within their organisational context.

Examples include:

- A higher number of findings may indicate a thorough review rather than poor quality.
- Longer review durations may be appropriate for high-risk or architecturally significant artefacts.
- Fewer findings should not be interpreted as evidence of review effectiveness without considering review quality.

Engineering judgement should always accompany quantitative analysis.

---

## Metric Reporting

Review metrics should be reported periodically using a consistent reporting format.

Typical reporting should include:

- Reporting period.
- Number of reviews completed.
- Distribution of review outcomes.
- Review duration trends.
- Common finding categories.
- Governance compliance.
- Improvement actions.
- Recommended follow-up activities.

Reports should be accessible to engineering leadership and governance stakeholders.

---

## Continuous Improvement

Review metrics should be analysed regularly to identify opportunities for improving:

- Review processes.
- Engineering standards.
- Documentation quality.
- Templates.
- Engineering guidance.
- Training programmes.
- Governance practices.

Recurring trends should result in measurable improvement initiatives rather than repeated corrective actions.

---

## Metric Limitations

Review metrics should support engineering improvement rather than become performance targets.

Metrics should not be used in isolation to:

- Evaluate individual performance.
- Compare reviewers without context.
- Incentivise reducing review findings.
- Encourage superficial or rushed reviews.

Qualitative judgement remains essential when interpreting review outcomes and organisational performance.

---

## Example Review Metrics Dashboard

| Metric | Target | Current Status |
|---------|:------:|:--------------:|
| Review Compliance Rate | ≥ 95% | ✓ |
| Finding Resolution Rate | 100% (Critical & Major) | ✓ |
| Average Review Duration | ≤ 5 Working Days | ✓ |
| Metadata Compliance | 100% | ✓ |
| Periodic Review Compliance | ≥ 90% | ✓ |

Targets should be reviewed periodically and adjusted to reflect organisational maturity and evolving engineering practices.

---

## Summary

The Engineering Review Metrics provide an objective framework for measuring the effectiveness and maturity of engineering reviews within ILOS.

By monitoring quality, efficiency, governance, and continuous improvement indicators, engineering teams can evaluate the health of the review process, identify opportunities for optimisation, and ensure that the Engineering Operating System continues to evolve through evidence-based governance rather than subjective judgement.

# AI-Assisted Reviews

Artificial Intelligence (AI) can significantly improve the efficiency and consistency of engineering reviews by automating repetitive validation tasks, identifying potential issues, and providing contextual recommendations. Within the Invara Labs Engineering Operating System (ILOS), AI is recognised as an assistive capability that enhances the review process while preserving human accountability for engineering decisions.

AI-assisted reviews should support reviewers by improving productivity, increasing consistency, and identifying issues that may otherwise be overlooked. AI does not replace engineering judgement, organisational governance, or formal approval processes.

Every engineering review remains a human-led activity.

---

## Purpose

The purpose of AI-assisted reviews is to:

- Improve review efficiency.
- Increase consistency across engineering reviews.
- Reduce repetitive manual validation activities.
- Identify potential quality issues early.
- Support reviewers with contextual recommendations.
- Enhance organisational knowledge reuse.

AI should augment engineering expertise rather than replace it.

---

## Guiding Principles

The use of AI during engineering reviews shall follow these principles:

### Human Accountability

Final responsibility for review findings, recommendations, approvals, and publication decisions always remains with authorised human reviewers and approvers.

AI-generated output shall never be considered an approval.

---

### Transparency

Review participants should understand when AI has been used during the review process.

Where AI-generated recommendations materially influence an engineering decision, the rationale should be documented where appropriate.

---

### Verification

All AI-generated findings shall be independently validated before acceptance.

Reviewers should verify:

- Technical correctness.
- Applicability.
- Accuracy.
- Completeness.
- Organisational alignment.

AI recommendations should never be accepted without appropriate human review.

---

### Confidentiality

AI-assisted reviews shall comply with organisational information security and data classification policies.

Reviewers should ensure that:

- Sensitive information is handled appropriately.
- Confidential artefacts are only processed using approved AI services.
- Intellectual property is protected.
- Applicable regulatory and contractual obligations are respected.

The use of public AI services should follow organisational governance requirements.

---

### Continuous Learning

Lessons learned from AI-assisted reviews should be used to improve:

- Review guidance.
- Documentation quality.
- Engineering standards.
- Templates.
- Knowledge repositories.

AI should contribute to organisational learning while maintaining governance controls.

---

## Appropriate Uses of AI

AI may assist reviewers with activities such as:

- Grammar and spelling validation.
- Documentation readability assessment.
- Terminology consistency checks.
- Metadata validation.
- Broken reference detection.
- Duplicate content identification.
- Cross-reference verification.
- Standards compliance suggestions.
- Checklist assistance.
- Risk identification.
- Review summarisation.

These activities improve reviewer efficiency while allowing humans to focus on engineering judgement.

---

## Activities Requiring Human Review

The following activities shall always require human evaluation and approval:

- Technical decision-making.
- Architectural assessment.
- Risk acceptance.
- Governance approval.
- Approval decisions.
- Standards interpretation.
- Conflict resolution.
- Exception approval.
- Organisational policy decisions.

These activities require contextual understanding, organisational knowledge, and professional engineering judgement.

---

## AI Review Workflow

The following illustrates how AI may participate in the review process.

```text
Engineering Artefact
          │
          ▼
AI Pre-Review Analysis
          │
          ▼
Suggested Findings
          │
          ▼
Human Reviewer Evaluation
          │
          ▼
Discussion and Resolution
          │
          ▼
Approval Decision
          │
          ▼
Publication
```

AI provides recommendations throughout the review process, while humans retain responsibility for evaluation and approval.

---

## AI Quality Controls

Organisations using AI-assisted reviews should establish appropriate controls, including:

- Approved AI tools and services.
- Prompt management guidance.
- Output verification procedures.
- Data handling requirements.
- Security and privacy controls.
- Auditability of AI-assisted activities where appropriate.
- Periodic review of AI effectiveness.

Governance controls help ensure that AI is used responsibly and consistently.

---

## Risks and Limitations

AI-assisted reviews have inherent limitations.

Examples include:

- Hallucinated or incorrect information.
- Misinterpretation of organisational context.
- Outdated technical knowledge.
- Inconsistent recommendations.
- Inability to understand undocumented business context.
- Overconfidence in generated responses.

Reviewers should remain aware of these limitations and apply professional judgement at all times.

---

## Continuous Improvement

The effectiveness of AI-assisted reviews should be evaluated periodically.

Potential improvement activities include:

- Measuring review efficiency gains.
- Monitoring recurring AI errors.
- Updating review prompts and guidance.
- Expanding approved review capabilities.
- Improving reviewer training.
- Refining governance controls.

Continuous evaluation ensures that AI remains a trusted assistant within the engineering review process.

---

## Summary

AI-assisted reviews enhance the Engineering Review Standard by improving efficiency, consistency, and reviewer productivity while preserving human accountability for engineering decisions.

By defining appropriate uses of AI, establishing governance controls, requiring independent verification, and maintaining human ownership of review outcomes, ILOS enables responsible adoption of AI within engineering reviews without compromising quality, security, or organisational governance.

# Review Governance

The Engineering Review Standard establishes the governance framework for managing, maintaining, and continuously improving engineering reviews across the Invara Labs Engineering Operating System (ILOS).

Review governance ensures that engineering reviews remain consistent, objective, auditable, and aligned with organisational engineering practices. It defines how the review process is managed, who is responsible for its oversight, how compliance is verified, and how the review framework evolves over time.

Effective governance ensures that engineering reviews are not isolated activities but an integral part of organisational quality management and engineering excellence.

---

## Governance Objectives

The objectives of review governance are to:

- Maintain a consistent engineering review process across the organisation.
- Ensure compliance with engineering standards and governance requirements.
- Promote transparency and accountability throughout the review lifecycle.
- Support evidence-based engineering decisions.
- Preserve organisational knowledge through documented review records.
- Enable continuous improvement using review outcomes and metrics.
- Adapt the review framework as engineering practices evolve.

---

## Governance Principles

Review governance shall be based on the following principles.

### Consistency

All engineering reviews should follow the governance framework defined by this standard.

Comparable engineering artefacts should receive comparable levels of review regardless of team or business function.

---

### Accountability

Every stage of the review lifecycle shall have clearly assigned ownership.

Responsibilities for authors, reviewers, approvers, and governance representatives shall remain transparent and traceable.

---

### Transparency

Review activities, findings, approvals, and significant decisions should be documented and accessible to authorised stakeholders.

Transparency improves organisational trust and supports future engineering decisions.

---

### Traceability

Review records should provide sufficient information to understand:

- What was reviewed.
- Who participated.
- What issues were identified.
- How issues were resolved.
- Why approval decisions were made.

Traceability supports governance, auditing, and long-term knowledge preservation.

---

### Continuous Improvement

The review framework should evolve based on:

- Review metrics.
- Lessons learned.
- Organisational feedback.
- Engineering maturity.
- Emerging engineering practices.

Governance should encourage improvement without creating unnecessary process complexity.

---

## Governance Responsibilities

The Engineering Governance Team (or equivalent authority) is responsible for maintaining the Engineering Review Standard.

Typical responsibilities include:

- Maintaining this standard.
- Defining organisational review policies.
- Monitoring governance compliance.
- Reviewing engineering metrics.
- Coordinating periodic standard reviews.
- Approving governance updates.
- Supporting engineering teams with review guidance.

Engineering teams remain responsible for applying the review framework within their own engineering activities.

---

## Governance Compliance

Engineering artefacts should comply with the governance requirements defined by this standard before publication.

Compliance should include verification of:

- Required review activities.
- Applicable approvals.
- Metadata completeness.
- Version management.
- Ownership assignment.
- Revision history.
- Traceability requirements.

Governance compliance should be verified during every formal review.

---

## Governance Audits

Periodic governance audits should be performed to evaluate the effectiveness of the review framework.

Audits may assess:

- Review compliance.
- Approval consistency.
- Documentation quality.
- Review records.
- Governance metrics.
- Review lifecycle adherence.
- Continuous improvement activities.

Audit findings should be documented and incorporated into future governance improvements.

---

## Exceptions

Occasionally, an engineering artefact may require an exception to the standard review process.

Examples include:

- Emergency engineering guidance.
- Time-critical operational documentation.
- Temporary governance deviations.
- Experimental or pilot initiatives.

Exceptions should:

- Be documented.
- Include a clear business or technical justification.
- Be approved by the appropriate authority.
- Define any compensating controls.
- Specify an expiration or review date where applicable.

Exceptions should remain rare and should not become routine practice.

---

## Review of the Standard

This Engineering Review Standard should itself be reviewed periodically in accordance with its defined review cycle.

Periodic review should evaluate:

- Continued organisational relevance.
- Alignment with engineering practices.
- Effectiveness of governance controls.
- Feedback from engineering teams.
- Opportunities for simplification or enhancement.

Updates to this standard shall follow the Engineering Review Lifecycle defined within this document.

---

## Governance Metrics

The effectiveness of review governance should be monitored using measurable indicators, including:

- Review compliance rate.
- Approval turnaround time.
- Audit findings.
- Standards compliance.
- Periodic review completion.
- Exception frequency.
- Recurring governance issues.

Governance metrics should inform continuous improvement initiatives rather than individual performance assessments.

---

## Governance Maturity

As engineering practices mature, organisations should continually strengthen their review governance capabilities.

Indicators of governance maturity include:

- Consistent application of review processes.
- High compliance with engineering standards.
- Well-maintained review records.
- Measurable quality improvements.
- Reduced recurring review findings.
- Effective use of review metrics.
- Successful integration of AI-assisted review capabilities.

Governance maturity reflects the organisation's ability to sustain high-quality engineering practices over time.

---

## Continuous Evolution

Engineering review governance should evolve alongside organisational needs, technological advancements, and industry best practices.

Changes to governance should be:

- Evidence-based.
- Reviewed collaboratively.
- Approved through established governance processes.
- Communicated to affected stakeholders.
- Incorporated into supporting engineering artefacts where appropriate.

The goal is to ensure that the Engineering Review Standard remains effective, relevant, and sustainable throughout the evolution of the Engineering Operating System.

---

## Summary

Review Governance establishes the organisational framework for managing engineering reviews throughout their lifecycle.

By defining governance principles, responsibilities, compliance expectations, audit practices, exception management, and continuous improvement processes, ILOS ensures that engineering reviews remain consistent, transparent, measurable, and aligned with organisational objectives.

A well-governed review process strengthens engineering quality, preserves organisational knowledge, and enables the Engineering Operating System to evolve with confidence while maintaining the highest standards of engineering excellence.

# Examples

This section provides illustrative examples demonstrating how the Engineering Review Standard can be applied to different types of engineering artefacts. These examples are intended to clarify the review process and should be adapted to suit the complexity, scope, and governance requirements of individual artefacts.

The examples are informative rather than normative and complement the mandatory requirements defined elsewhere in this standard.

---

## Example 1 – Engineering Standard Review

**Artefact**

- Document: `TERM-STANDARD.md`
- Classification: Engineering Standard

### Review Types

- Peer Review
- Documentation Review
- Governance Review

### Review Outcome

**Approved**

### Example Findings

| ID | Category | Severity | Finding | Resolution |
|----|----------|----------|----------|------------|
| REV-001 | Documentation | Minor | Metadata field `review_cycle` was missing. | Metadata updated before approval. |
| REV-002 | Governance | Major | Related artefacts section omitted mandatory references. | Required references added. |
| REV-003 | Editorial | Suggestion | Improve wording in the Summary section. | Accepted and updated. |

---

## Example 2 – Architecture Decision Record (ADR)

**Artefact**

- Document: `ADR-012`
- Classification: Architecture Decision Record

### Review Types

- Technical Review
- Architecture Review

### Review Outcome

**Approved with Conditions**

### Conditions

- Add scalability considerations.
- Expand risk assessment.
- Reference the related RFC before publication.

Publication may proceed once the agreed conditions have been addressed.

---

## Example 3 – Engineering Playbook

**Artefact**

- Document: `PB-REQ.md`
- Classification: Engineering Playbook

### Review Types

- Peer Review
- Documentation Review
- Governance Review

### Review Outcome

**Revisions Required**

### Findings

- Missing acceptance criteria.
- Inconsistent terminology.
- Broken cross-reference.
- Incomplete lifecycle description.

The artefact should be updated and resubmitted for verification.

---

## Example 4 – Reference Document

**Artefact**

- Document: `REF-TERMINOLOGY.md`
- Classification: Engineering Reference

### Review Types

- Documentation Review
- Governance Review

### Review Focus

- Terminology consistency.
- Alphabetical ordering.
- Cross-reference validation.
- Metadata verification.
- Duplicate term detection.

### Outcome

**Approved**

---

## Example 5 – AI-Assisted Review

### AI Activities

AI performed the following tasks:

- Verified metadata completeness.
- Identified duplicate terminology.
- Detected broken internal references.
- Suggested documentation improvements.
- Flagged inconsistent terminology.

### Human Review

The reviewer:

- Validated every AI recommendation.
- Rejected two incorrect suggestions.
- Accepted five improvements.
- Approved the final artefact.

Final accountability remained with the human reviewer.

---

## Example Review Record

| Field | Example Value |
|--------|---------------|
| Review ID | REV-2026-014 |
| Artefact | TERM-STANDARD.md |
| Version | 1.0.0 |
| Review Type | Peer + Governance |
| Reviewer | Jane Smith |
| Author | John Doe |
| Outcome | Approved |
| Review Date | 2026-07-30 |
| Findings | 4 |
| Critical | 0 |
| Major | 1 |
| Minor | 2 |
| Suggestions | 1 |

---

## Example Review Workflow

```text
Author Completes Artefact
           │
           ▼
Self-Review
           │
           ▼
Peer Review
           │
           ▼
Documentation Review
           │
           ▼
Governance Review
           │
           ▼
Findings Recorded
           │
           ▼
Author Revises Artefact
           │
           ▼
Verification
           │
           ▼
Approval
           │
           ▼
Publication
```

---

## Example Finding Lifecycle

```text
Finding Raised
       │
       ▼
Severity Assigned
       │
       ▼
Assigned to Author
       │
       ▼
Correction Implemented
       │
       ▼
Reviewer Verification
       │
       ▼
Finding Closed
```

---

## Applying the Examples

These examples demonstrate typical review scenarios within ILOS but should not be interpreted as mandatory workflows for every engineering artefact.

Review activities should always be tailored based on:

- Artefact classification.
- Technical complexity.
- Organisational impact.
- Governance requirements.
- Applicable review types.

The principles, lifecycle, and criteria defined by this standard shall always take precedence over the illustrative examples provided in this section.

---

## Summary

The examples in this section illustrate how the Engineering Review Standard can be applied consistently across different engineering artefacts.

By demonstrating review workflows, review records, findings, and outcomes, these examples provide practical guidance for authors, reviewers, and approvers while reinforcing the governance principles established throughout this standard.

# Best Practices

This section provides recommended practices for conducting effective engineering reviews within the Invara Labs Engineering Operating System (ILOS). These practices are based on established engineering principles and organisational governance experience.

While the requirements defined throughout this standard are mandatory where applicable, the practices in this section provide additional guidance to improve the efficiency, consistency, and overall effectiveness of engineering reviews.

Engineering teams are encouraged to adopt these practices as part of their normal engineering workflow.

---

## Prepare Before Requesting Review

Authors should ensure that an engineering artefact is ready for review before requesting reviewer participation.

Recommended activities include:

- Complete a thorough self-review.
- Validate technical accuracy.
- Verify compliance with applicable standards.
- Ensure required metadata is complete.
- Resolve known issues where practical.
- Confirm that supporting artefacts are available.

Well-prepared artefacts enable reviewers to focus on meaningful engineering feedback rather than avoidable corrections.

---

## Select Appropriate Reviewers

Assign reviewers based on the knowledge and expertise required for the artefact rather than availability alone.

Consider:

- Technical expertise.
- Architectural knowledge.
- Domain experience.
- Documentation expertise.
- Governance responsibilities.

For high-impact artefacts, include reviewers with complementary perspectives to improve review quality.

---

## Define the Review Scope

Clearly communicate the purpose and expected outcome of the review.

Where appropriate, identify:

- Areas requiring particular attention.
- Known assumptions.
- Constraints.
- Related engineering decisions.
- Expected review timeframe.

A clearly defined scope helps reviewers focus their efforts effectively.

---

## Provide Constructive Feedback

Review feedback should improve the artefact rather than criticise the author.

Effective feedback should:

- Describe the issue objectively.
- Explain why it matters.
- Reference applicable standards where possible.
- Suggest practical improvements.
- Distinguish mandatory changes from recommendations.

Constructive communication promotes collaboration and continuous learning.

---

## Prioritise High-Impact Issues

Focus review effort on issues that materially affect engineering quality, organisational governance, or long-term maintainability.

Examples include:

- Technical inaccuracies.
- Architectural concerns.
- Governance non-compliance.
- Security considerations.
- Missing traceability.
- Ambiguous engineering guidance.

Minor editorial improvements should not distract from resolving higher-risk findings.

---

## Maintain Traceability

Document significant review activities and decisions to support future maintenance and governance.

Where appropriate, record:

- Review participants.
- Review outcomes.
- Significant findings.
- Approval decisions.
- Rationale for accepted exceptions.
- Links to related artefacts.

Traceability improves transparency, auditability, and organisational knowledge preservation.

---

## Keep Reviews Timely

Reviews should be completed within agreed organisational timeframes.

To reduce delays:

- Schedule reviews appropriately.
- Respond promptly to review requests.
- Resolve findings without unnecessary delay.
- Escalate blockers early.

Efficient reviews help maintain engineering momentum while preserving review quality.

---

## Encourage Collaborative Discussion

Complex engineering decisions benefit from open discussion between authors, reviewers, and subject matter experts.

Where disagreements arise:

- Discuss the underlying technical reasoning.
- Reference documented engineering guidance.
- Seek additional expertise where required.
- Record significant decisions and rationale.

Healthy technical discussion often results in stronger engineering outcomes.

---

## Use AI Responsibly

AI may assist reviewers with repetitive validation tasks and documentation analysis.

Recommended practices include:

- Validate all AI-generated findings.
- Use approved AI services.
- Protect confidential information.
- Apply human judgement to every recommendation.
- Record significant AI-assisted decisions where appropriate.

AI should enhance reviewer effectiveness while preserving human accountability.

---

## Learn from Review Findings

Recurring review findings provide valuable insight into engineering practices.

Engineering teams should periodically analyse review outcomes to identify opportunities to:

- Improve engineering standards.
- Refine templates.
- Update playbooks.
- Enhance reviewer guidance.
- Deliver targeted training.
- Strengthen governance processes.

Every review contributes to organisational learning.

---

## Promote a Positive Review Culture

Engineering reviews should foster professionalism, trust, and continuous improvement.

Review participants should:

- Respect differing viewpoints.
- Assume positive intent.
- Focus on the artefact rather than the individual.
- Recognise good engineering practices.
- Encourage knowledge sharing.

A positive review culture improves both engineering quality and team collaboration.

---

## Summary

Applying these best practices helps engineering teams conduct reviews that are efficient, objective, collaborative, and aligned with organisational governance.

By preparing thoroughly, engaging the right reviewers, focusing on meaningful feedback, maintaining traceability, using AI responsibly, and continuously learning from review outcomes, engineering teams strengthen the quality and sustainability of the Engineering Operating System while promoting a culture of engineering excellence.

# Common Mistakes

This section highlights common issues observed during engineering reviews and provides guidance on how to avoid them. Recognising these pitfalls helps improve review quality, reduces unnecessary rework, and promotes a consistent and effective review process across the Invara Labs Engineering Operating System (ILOS).

The examples below are illustrative rather than exhaustive. Engineering teams should continually identify and address recurring review challenges as part of their continuous improvement activities.

---

## Requesting Review Too Early

Submitting an engineering artefact before it is sufficiently complete often results in avoidable review findings and unnecessary review cycles.

Common indicators include:

- Incomplete sections.
- Missing metadata.
- Placeholder content.
- Unresolved technical questions.
- Broken references.

**Recommended Practice**

Complete a thorough self-review and ensure the artefact is review-ready before requesting formal review.

---

## Treating Reviews as Approval Gates Only

Reviews are intended to improve engineering quality, not merely to obtain approval.

Focusing solely on obtaining approval may result in:

- Superficial reviews.
- Missed quality issues.
- Reduced collaboration.
- Lost learning opportunities.

**Recommended Practice**

Approach reviews as collaborative quality improvement activities rather than administrative checkpoints.

---

## Reviewing Without Understanding the Context

Reviewers may identify issues that appear valid but are based on incomplete understanding of the artefact's purpose, assumptions, or constraints.

This can lead to:

- Irrelevant feedback.
- Conflicting recommendations.
- Unnecessary revisions.

**Recommended Practice**

Review supporting documentation and understand the intended audience, objectives, and scope before evaluating the artefact.

---

## Focusing on Minor Editorial Issues

Excessive attention to formatting or wording can distract from more significant engineering concerns.

Examples include:

- Architecture decisions.
- Technical correctness.
- Governance compliance.
- Security considerations.
- Traceability.

**Recommended Practice**

Prioritise findings based on organisational impact and engineering risk before addressing editorial improvements.

---

## Providing Subjective Feedback

Feedback based solely on personal preference creates inconsistency across reviews.

Examples include:

- Personal writing style preferences.
- Unexplained technical opinions.
- Inconsistent terminology suggestions.

**Recommended Practice**

Reference applicable engineering standards, documented guidance, or objective technical reasoning whenever possible.

---

## Combining Multiple Issues into a Single Finding

Recording unrelated issues within a single finding makes tracking and resolution more difficult.

This may result in:

- Confusion over ownership.
- Partial resolution.
- Ineffective verification.

**Recommended Practice**

Record each independent issue as a separate review finding with its own severity, recommendation, and resolution status.

---

## Assigning Inappropriate Severity

Incorrect severity classification may either overstate or understate the importance of a finding.

Examples include:

- Classifying editorial improvements as critical.
- Treating governance violations as minor.
- Underestimating architectural risks.

**Recommended Practice**

Assign severity based on organisational impact, engineering risk, and the criteria defined within this standard.

---

## Delaying Review Activities

Long delays reduce engineering momentum and increase the likelihood that artefacts become outdated before approval.

Common causes include:

- Late reviewer responses.
- Unclear ownership.
- Poor planning.
- Slow resolution of findings.

**Recommended Practice**

Establish clear review expectations, monitor review progress, and escalate blockers promptly where necessary.

---

## Accepting AI Recommendations Without Verification

AI can improve review efficiency but may produce inaccurate or incomplete recommendations.

Risks include:

- Incorrect technical guidance.
- Hallucinated references.
- Misinterpreted organisational context.
- Inconsistent recommendations.

**Recommended Practice**

Independently verify all AI-generated findings before incorporating them into review outcomes.

---

## Poor Documentation of Review Decisions

Important review decisions that are not documented become difficult to understand during future maintenance or audits.

Examples include:

- Missing approval rationale.
- Undocumented exceptions.
- Unrecorded design decisions.
- Incomplete review history.

**Recommended Practice**

Maintain complete and traceable review records for all significant findings, decisions, approvals, and exceptions.

---

## Ignoring Recurring Findings

Repeated review issues often indicate underlying weaknesses in engineering practices, standards, or documentation.

Ignoring recurring patterns can result in:

- Repeated corrective effort.
- Reduced engineering efficiency.
- Inconsistent documentation quality.

**Recommended Practice**

Periodically analyse review findings to identify root causes and implement long-term improvements to standards, templates, guidance, or training.

---

## Viewing Reviews as Personal Criticism

Engineering reviews evaluate artefacts—not individuals.

Treating review comments as personal criticism may discourage collaboration and reduce the effectiveness of the review process.

**Recommended Practice**

Maintain a professional, respectful, and objective review culture that focuses on improving engineering outcomes through constructive discussion.

---

## Summary

Many review challenges arise from inadequate preparation, unclear communication, subjective evaluation, or insufficient documentation rather than technical complexity.

By recognising these common mistakes and adopting the recommended practices outlined in this standard, engineering teams can conduct reviews that are more objective, collaborative, efficient, and effective, ultimately strengthening both engineering quality and organisational governance.

# Related Artefacts

The following engineering artefacts are related to this Engineering Review Standard and provide additional guidance for engineering documentation, governance, terminology, and review practices within the Invara Labs Engineering Operating System (ILOS).

## Engineering Principles

The following principles establish the foundational engineering values that underpin the review process:

- Engineering Quality Principles *(when available)*
- Documentation Principles *(when available)*
- Engineering Governance Principles *(when available)*

---

## Engineering Playbooks

The following playbooks describe operational processes that support engineering reviews:

- **PB-AUTHORING** — Engineering Authoring Playbook
- **PB-REQ** — Requirements Engineering Playbook

Additional playbooks may be referenced where review activities involve specialised engineering processes.

---

## Engineering Standards

The following standards should be applied in conjunction with this standard where applicable:

- **DOC-STYLE** — Documentation Style Standard
- **TERM-STANDARD** — Engineering Terminology Standard

Additional standards may apply depending on the type, classification, and governance requirements of the engineering artefact under review.

---

## Engineering References

The following reference documents provide supporting information used during engineering reviews:

- **REF-TERMINOLOGY** — Organisational engineering terminology.
- **REF-IDENTIFIERS** — Identifier naming conventions and prefixes.
- **REF-ACRONYMS** — Approved organisational acronyms and abbreviations.

Reference documents should be consulted whenever terminology, identifiers, or abbreviations require validation during a review.

---

## Engineering Examples

Examples illustrating review practices and documentation conventions may be provided in supporting example artefacts where appropriate.

Examples should be used to aid understanding and should not override the normative requirements defined by this standard.

---

## Cross-Reference Guidance

When conducting engineering reviews, reviewers should consult related artefacts as necessary to ensure:

- Consistent terminology.
- Compliance with engineering standards.
- Alignment with organisational governance.
- Correct use of templates and documentation structures.
- Consistent application of engineering practices.

The Engineering Review Standard should be interpreted as part of the wider ILOS documentation ecosystem rather than as an isolated document.

---

## Artefact Evolution

As the Engineering Operating System evolves, additional principles, playbooks, standards, references, and examples may be introduced.

This section should be reviewed periodically to ensure that cross-references remain current, accurate, and relevant.

# References

This Engineering Review Standard is informed by widely recognised engineering, documentation, quality management, and governance practices. The references listed below provide additional context and authoritative guidance that complements, but does not replace, the requirements defined within this standard.

Where organisational guidance differs from an external reference, the requirements of the Invara Labs Engineering Operating System (ILOS) shall take precedence.

---

## International Standards

The following international standards provide foundational guidance relevant to engineering reviews, documentation, quality management, and systems engineering.

- **ISO 9001** — *Quality Management Systems — Requirements*
- **ISO/IEC/IEEE 15288** — *Systems and Software Engineering — System Life Cycle Processes*
- **ISO/IEC/IEEE 12207** — *Systems and Software Engineering — Software Life Cycle Processes*
- **ISO/IEC 25010** — *Systems and Software Quality Models*
- **ISO/IEC 42001** — *Artificial Intelligence Management Systems*

These standards establish recognised practices for quality assurance, engineering governance, lifecycle management, and organisational processes.

---

## Documentation Standards

The following publications provide guidance on producing clear, maintainable, and consistent technical documentation.

- **IEEE 1063** — *IEEE Standard for Software User Documentation*
- **Google Developer Documentation Style Guide**
- **Microsoft Writing Style Guide**
- **Red Hat Supplementary Style Guide**
- **The Chicago Manual of Style** *(general editorial reference where appropriate)*

These references support documentation quality, readability, and consistency.

---

## Architecture and Engineering References

The following references provide guidance for engineering decision-making, architecture, and technical governance.

- **RFC 2119** — *Key Words for Use in RFCs to Indicate Requirement Levels*
- **RFC 8174** — *Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words*
- **The Open Group Architecture Framework (TOGAF)** *(where applicable)*
- **Software Engineering Body of Knowledge (SWEBOK Guide)**

These references support consistent engineering terminology and established technical practices.

---

## AI Governance References

The following publications provide guidance on the responsible use of Artificial Intelligence within engineering processes.

- **NIST AI Risk Management Framework (AI RMF)**
- **ISO/IEC 42001** — *Artificial Intelligence Management Systems*
- **OECD AI Principles**

These references inform the governance principles for AI-assisted reviews defined in this standard.

---

## Quality and Continuous Improvement

The following references support continual improvement and organisational quality management.

- **W. Edwards Deming — Plan-Do-Check-Act (PDCA) Cycle**
- **Capability Maturity Model Integration (CMMI)**
- **Lean Principles**
- **Kaizen Continuous Improvement**

These references provide established approaches for measuring, evaluating, and improving engineering processes over time.

---

## Informative References

The following publications provide additional guidance that may assist engineering teams but are not mandatory for applying this standard.

- *Clean Architecture* — Robert C. Martin
- *The Pragmatic Programmer* — David Thomas and Andrew Hunt
- *Accelerate* — Nicole Forsgren, Jez Humble, and Gene Kim
- *Team Topologies* — Matthew Skelton and Manuel Pais

These resources offer practical perspectives on engineering excellence, collaboration, and software delivery.

---

## Maintaining References

The references in this section should be reviewed periodically to ensure they remain:

- Relevant to current engineering practices.
- Published and maintained by authoritative sources.
- Applicable to the scope of this standard.
- Consistent with organisational governance objectives.

Obsolete or superseded references should be replaced during scheduled reviews of this standard.

---

## Reference Usage

References included in this section are intended to:

- Provide additional context.
- Support engineering best practices.
- Encourage consistent terminology.
- Promote recognised industry approaches.
- Inform continual improvement activities.

These references are informative unless explicitly adopted as organisational policy or incorporated into another ILOS engineering artefact.

# Revision History

This section records the revision history of the Engineering Review Standard. It provides traceability for significant changes made throughout the lifecycle of the document.

Revision history supports engineering governance by documenting when changes were made, the nature of those changes, and the version in which they were introduced.

Minor editorial corrections that do not affect the intent, requirements, or guidance of this standard may be omitted from the revision history at the discretion of the document owner.

---

## Revision Principles

The revision history should:

- Record significant changes only.
- Align with the document version.
- Provide a concise description of each revision.
- Preserve historical entries.
- Maintain chronological order with the most recent revision first.
- Support organisational traceability and auditing.

Revision entries should describe *what changed* rather than the detailed implementation of the change.

---

## Versioning

This standard follows the organisational document versioning strategy.

| Version Change | Description |
|----------------|-------------|
| Major (`X.0.0`) | Significant changes affecting the structure, scope, governance, or mandatory requirements of the standard. |
| Minor (`1.X.0`) | New sections, expanded guidance, or additional examples that do not fundamentally change existing requirements. |
| Patch (`1.0.X`) | Editorial corrections, clarification of wording, formatting improvements, or non-substantive updates. |

Version numbers should be updated before publication of an approved revision.

---

## Revision Log

| Version | Date | Author(s) | Summary of Changes |
|---------|------|-----------|--------------------|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Initial release of the Engineering Review Standard. |

Future revisions should append new entries to the top of this table while preserving the complete revision history.

---

## Recording Changes

Revision entries should summarise changes at an appropriate level of detail.

Examples include:

- Added new governance requirements.
- Updated review lifecycle.
- Introduced AI-assisted review guidance.
- Expanded review metrics.
- Clarified terminology.
- Improved review examples.
- Updated related artefacts.
- Revised references.

Revision history should describe the outcome of the change rather than the internal drafting process.

---

## Superseded Versions

When a new version of this standard is published:

- Previous approved versions should be retained according to organisational document retention policies.
- Superseded versions should remain identifiable for historical reference where required.
- The document metadata should accurately identify any superseded or replacement versions.

This ensures long-term traceability and supports governance, auditing, and historical analysis.

---

## Document Review Cycle

This standard shall be reviewed in accordance with the review cycle defined in the document metadata.

A scheduled review may result in:

- No changes required.
- Editorial improvements.
- Minor revisions.
- Major revisions.
- Withdrawal or replacement of the standard.

Scheduled reviews help ensure that the standard remains accurate, relevant, and aligned with evolving engineering practices.

---

## Change Approval

All substantive revisions should be reviewed and approved through the engineering governance process before publication.

Approval should confirm that:

- Changes have been appropriately reviewed.
- Related artefacts have been updated where necessary.
- Version information is correct.
- Metadata remains accurate.
- Cross-references have been validated.

Only approved revisions should be published as official versions of this standard.

---

## Summary

The Revision History provides a transparent and auditable record of the evolution of the Engineering Review Standard.

By maintaining accurate version information, documenting significant changes, and preserving historical records, ILOS ensures that engineering standards remain traceable, maintainable, and governed throughout their lifecycle.

# Summary

The Engineering Review Standard establishes a consistent, transparent, and governed framework for reviewing engineering artefacts throughout the Invara Labs Engineering Operating System (ILOS).

Engineering reviews are a fundamental quality assurance activity that improve the accuracy, consistency, maintainability, and long-term value of engineering knowledge. By providing a structured review process, this standard enables engineering teams to identify issues early, encourage collaboration, strengthen organisational governance, and continuously improve engineering practices.

This standard defines:

- The philosophy and objectives of engineering reviews.
- Principles that guide consistent review practices.
- Review types appropriate for different engineering artefacts.
- A structured review lifecycle.
- Clearly defined roles and responsibilities.
- Objective review criteria and practical review checklists.
- Standardised review outcomes and findings management.
- Metrics for evaluating review effectiveness.
- Governance for responsible AI-assisted reviews.
- Organisational oversight through review governance.
- Practical guidance, examples, best practices, and common pitfalls.

Together, these elements provide a comprehensive framework that supports engineering quality across the entire documentation lifecycle.

Engineering reviews should be:

- Objective and evidence-based.
- Collaborative and constructive.
- Proportionate to the complexity and impact of the artefact.
- Consistent across engineering teams.
- Fully traceable and auditable.
- Focused on continual improvement rather than individual evaluation.

Successful engineering reviews depend not only on well-defined processes but also on a culture of professionalism, openness, shared ownership, and continuous learning. Authors, reviewers, approvers, and governance representatives each contribute to maintaining the integrity and quality of engineering artefacts.

As engineering practices, technologies, and organisational needs evolve, the review process should evolve accordingly. Review metrics, lessons learned, governance activities, and periodic revisions ensure that this standard remains relevant, effective, and aligned with organisational objectives.

By adopting the Engineering Review Standard, Invara Labs establishes a repeatable and scalable review framework that promotes engineering excellence, preserves organisational knowledge, strengthens governance, and enables the Engineering Operating System to grow with confidence and consistency.

Ultimately, effective engineering reviews are not simply a checkpoint before publication—they are an essential mechanism for improving engineering quality, fostering collaboration, and ensuring that every engineering artefact contributes to a reliable, maintainable, and continuously evolving body of organisational knowledge.


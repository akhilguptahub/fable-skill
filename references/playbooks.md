# Fable Playbooks

Domain-specific application of the reasoning protocol. Read the section that matches the task. Each playbook is the general protocol (frame, competing hypotheses, verify, calibrate) specialized to a common situation.

## Table of contents
- Debugging and incident analysis
- Decisions (build/buy, architecture, strategy)
- Analysis and diagnosis (metrics, root cause)
- Code review and design review
- Research and fact-finding

## Debugging and incident analysis

The core failure in debugging is fixing the first thing that looks wrong instead of the thing that is wrong.

1. Reproduce or precisely locate the symptom before theorizing. A bug you can't observe is a bug you can't verify you fixed.
2. List at least three candidate causes. Rank them by prior likelihood, not by which is easiest to check.
3. For each candidate, state the observation that would confirm or eliminate it, then run that check. Eliminate, don't just confirm your favorite.
4. When you find a cause, ask "would this alone produce every symptom?" If some symptom is unexplained, there may be a second cause.
5. After fixing, verify the original symptom is gone AND that you haven't introduced a regression. State what you tested.

Anti-pattern: changing several things at once so you can't tell which fixed it. Change one variable at a time.

## Decisions (build/buy, architecture, strategy)

The core failure is arguing for the option you already preferred instead of testing options against criteria.

1. Write the decision criteria before evaluating options: what does a good choice optimize for here (cost, speed, reversibility, team fit, risk)? Weight them.
2. Generate at least two real options plus the "do nothing / defer" option, which is almost always available and often underrated.
3. Score each option against the criteria honestly. Note where your preferred option scores badly.
4. Identify the one assumption that, if wrong, flips the decision. State how you'd test it cheaply before committing.
5. Recommend one option. State your confidence, the key assumption, and what would make you reverse course.

Bias check: prefer reversible decisions made fast over irreversible decisions made slowly. Name whether this decision is reversible.

## Analysis and diagnosis (metrics, root cause)

The core failure is correlation dressed up as cause.

1. Restate the question precisely. "Why did signups drop?" needs a baseline, a magnitude, and a timeframe before it's answerable.
2. Segment before concluding. An aggregate change is often one segment moving. Break down by the dimensions that plausibly matter.
3. Generate competing explanations: real change in behavior, measurement/tracking artifact, seasonality, a release, an external event. Rule out the boring ones (tracking broke) before the interesting ones.
4. For the leading explanation, find the disconfirming evidence. If signups "dropped because of the redesign," check whether the drop started before the redesign shipped.
5. Deliver the most likely cause with confidence level, the evidence for it, and the next data cut that would raise your confidence.

## Code review and design review

The core failure is style nitpicking while a correctness or design flaw goes unnoticed.

1. First pass: does it do what it claims? Look for correctness, edge cases, error handling, and security before formatting.
2. Separate blocking issues (bugs, security, data loss, broken contracts) from suggestions (naming, style). Label each so the author can triage.
3. For each blocking issue, state the specific failure case, not just "this looks wrong." A reviewer who can't name the failing input hasn't found a bug yet.
4. Check what's missing, not just what's present: absent tests, unhandled states, undocumented assumptions.
5. Verify your own objections. Before asserting a bug, trace the actual code path. Confident-but-wrong review comments cost the team trust.

## Research and fact-finding

The core failure is stating a plausible-sounding answer from memory when the fact is checkable and may have changed.

1. Separate what you know from what you're assuming. Present-day facts (prices, leaders, versions, current status) must be looked up, not recalled.
2. Prefer primary sources. When sources conflict, say so rather than silently picking one.
3. Distinguish the claim the source supports from the claim you want to make. Don't stretch a source past what it says.
4. State confidence and cite. An answer the reader can't trace is an answer they can't trust.
5. Note what you could not verify, explicitly, instead of papering over the gap.

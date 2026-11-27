# Template: upstream forensic investigation (H0/H1/H2)

Nov 27, 2026

> **Status.** Background material for the APSR paper. The template mirrors the BSW investigation and its findings; how well it carries over to other domains is untested. The BSW case had no H2: it tested one clerical intervention against the null, so the attribution branch (H1 vs H2) below is not exercised. The labels H1 and H2 in this document name two channels of that one intervention. The H0/H1/H2 methods paper and workflow protocol remain to be built.

## Purpose

This template structures an upstream forensic investigation: from a downstream evidence trail back to whether an intervention occurred, which one it was, and how large it is.

Downstream causal inference starts from a documented intervention and decomposes its effects. Upstream inference starts from a record that a process produced. The intervention is unobserved: it has to be conjectured, specified as a perturbation of the process, and tested against rivals.

Three questions, answered in order:

1. **Occurrence (H0 vs H1).** Did a directional intervention act on the process?
2. **Attribution (H1 vs H2 …).** Which intervention acted, or which mixture of channels?
3. **Magnitude.** How large is the surviving effect, and is it material?

The hard part is structure, not testing. Once the process, the rival mechanisms and their signatures are written down, the first nulls usually fall to simple tests. Magnitude is a comparison of models by the onerousness of their assumptions, not a textbook test.

Running example: BSW in the 2025 Bundestag election, certified at 4.981% of second votes, 9,529 votes short of 5%.

## The record and the process

The reported figure is an output of a process, not the quantity of interest. Map the process before stating any hypothesis.

| Stage | Error that can enter here | What can catch it |
| --- | --- | --- |
| **Count at the precinct**: ballots sorted, stacks tallied | Ballots in the wrong stack; whole stacks swapped | Only a recount of the ballots |
| **Signed protocol**: tallies recorded and signed | A tally written in the wrong row | Only a recount; the protocol is the reference |
| **Quick report**: feeds the preliminary result P | Figures differ from the protocol | Comparison with the protocol during certification |
| **Data entry and aggregation**: municipality, then district | Figures entered under the neighboring party | Plausibility checks; comparison with the protocol |
| **Certification**: district committee; result F | Errors from the first two stages pass through unseen | Recounts on suspicion only, about 0.4% of precincts |

Corrections between P and F come from the later stages; errors made in the count or the protocol survive unless the precinct is recounted. The 0.4% recount share is the complainants’ compilation of the returning officers’ figures (Bundestag 21/3100).

For each stage, record the document it produces, what it checks, and what it cannot see. Then write the accounting identity, with P the preliminary count, F the certified count and T what an accurate examination of the ballots would yield:

$$\underbrace{T_i - P_i}_{\text{initial loss}} = \underbrace{F_i - P_i}_{\text{certification recovery}} + \underbrace{T_i - F_i}_{\text{residual}}$$

Only the middle term is observed. The investigation is about the other two.

## Candidate interventions

Each candidate is a perturbation of one named process stage. Specify it on five dimensions before testing anything.

| Dimension | Question | BSW example |
| --- | --- | --- |
| Locus | Which stage does it act on? | Counting at the precinct; reporting from precinct to district |
| Unit of error | One ballot, or a whole stack or subtotal? | Single ballots misattributed; BSW and BD stacks exchanged |
| Kernel | What moves where? | BSW → BD (name confusion); BSW → several categories (down-ballot penalty) |
| Exposure | Who is exposed, and by what rule? | BD directly above BSW in 15 of 16 Länder; BSW at or near the bottom of the ballot |
| Conspicuousness | Would the result trigger review? | A swapped stack leaves zero BSW and 12–33 BD; a single misattribution looks ordinary |

**Undirected error can produce a directional effect.** Derive the direction from the mechanism; never assume error is centered on the record. Three routes:

- **Exposure asymmetry.** Equal per-ballot confusion rates in both directions move votes from the larger category to the smaller, in proportion to size. BSW had about 32 times BD’s votes, so a common rate yields about 32 BSW→BD errors per reverse error.
- **Position.** An error rate that rises down the ballot hits the parties placed low, and ballot order places them by rule.
- **Detection.** Certification acts on suspicion, so it corrects conspicuous errors first. What survives is skewed toward inconspicuous errors in the same direction.

**Candidates are rarely exclusive.** The estimand is a vector of channel intensities, and “which intervention” becomes “which mixture”. In the BSW case, H1 is name and adjacency confusion with BD and H2 a general down-ballot penalty; both can act at once. No candidate requires intent.

## Null hypotheses

The null is undirected background error of credible magnitude, centered on the record. It is never perfect counting.

The nulls are nested: each is rejected before the next is asked.

| Null | States | BSW test |
| --- | --- | --- |
| Occurrence | No directional error occurred in the original count. | National correction rate against the corrections of size-matched established parties |
| Persistence | Certification removed the directional component; local political variation and undirected noise explain the remaining extremes. | Joint deficit and surplus signature across certified precincts, against FDP controls |
| Materiality | Any surviving directional error is too small to warrant further inquiry. | Model comparison (Magnitude) |

For attribution, add discrimination nulls: the signature that H2 predicts and H1 does not is absent, and the reverse. A rejected occurrence null says something happened; only discrimination nulls say what.

The decision null stays separate. In the BSW case it reads “an accurate recount leaves BSW below 5%”. An expected correction of a few hundred votes rejects the point null of equal shares and leaves the decision null standing.

## Signature matrix

Write down what each hypothesis predicts for each observable feature before looking at the data. A feature on which rivals predict opposite outcomes is a crucial test.

| Feature | H0: political variation and undirected noise | H1: BD confusion | H2: down-ballot penalty | Observed (BSW) |
| --- | --- | --- | --- | --- |
| BD’s absolute correction | About zero | Large loss, a share of BSW’s gain | No BD-specific loss | −2,640, 62% of BSW’s +4,277 |
| Relative corrections of other parties low on the ballot | Small | No effect | Large | MLPD −1.6%, MERA25 −1.9%; established parties under 0.03% |
| Swap signature, adjacent vs non-adjacent pairs | Indifferent to ballot order | Elevated for BSW–BD | Elevated for all adjacent pairs | 2.2 vs 0.28 vs 0.12 per 10,000 |
| Shared name, at equal adjacency | Indifferent | Elevated toward the name-sharing neighbor | Indifferent | NRW: BD −927 vs MERA25 −132 (confounded) |
| First vs second votes in flagged precincts | Move together | Second votes only | Second votes only | 11 of 13 unbacked vs 0 of 138 |
| Surplus matching deficit | Loose | Tight | Loose | Correlation 0.72 vs 0.22–0.40 |
| Land without BD adjacency | No difference | No BSW–BD signature | Unchanged | Saarland the sole exception |
| Earlier newcomer’s correction | Ordinary | Not applicable | Large | AfD 2013: 22.5 per 10,000 |
| Extreme tail against comparators at equal expected count | Same rate | BSW excess | Excess for all low-ballot parties | 20 vs 5.5 at 20+ expected votes |

The features identify the channel vector only when no two hypotheses share a column. If two columns match, add features until they differ.

Two things the matrix does not do: it does not weight features by how cheap they are to observe (Test plan), and it does not size the effect (Magnitude).

## Evidence inventory

List every source by the process stage it records, and by what it can and cannot identify. Documents disappear, so name the minimum set that answers each null.

| Source | Stage recorded | Identifies | Cannot identify | BSW status |
| --- | --- | --- | --- | --- |
| National preliminary and certified totals | Quick report; certification | Net correction per party | Gross flows; where corrections happened | Public, 2013–2025 |
| Constituency preliminary and final results | Quick report; certification | Net correction per certifying committee | Precinct-level changes | Public (Heft 2, Heft 3) |
| Certified precinct returns | After certification | Surviving joint anomalies; first vs second votes | What certification changed; the diffuse level, beyond the product s·μ | Public, 2017, 2021, 2025 |
| Ballot order by Land | Exposure | Who was exposed to adjacency, shared names and low position | Outcomes | Public |
| Land returning officers’ statements | Certification | Mechanisms; what extra effort found | Prevalence | Summarized in Bundestag 21/3100; annex tables not reproduced |
| Recounted precincts | Ballots | Signed error in the precincts examined | The residual elsewhere, given their selection | 50 screened precincts, aggregate only |
| Paired preliminary and certified precinct returns | Quick report against certification | Detection rate by conspicuousness; a floor on the residual | Errors already in the signed protocol | Not published |
| Certification examination log | Certification | Which precincts were checked | What the checks found | Not published |

Minimum set in the BSW case: national totals answer occurrence; certified precinct returns and ballot order answer persistence and attribution; magnitude needs paired returns or ballots.

## Exposure, comparators, placebos

Use rules that assign exposure independently of the outcome. They turn the investigation into a natural experiment.

- **Exposure by rule.** Ballot order follows the previous Land result, then newcomers alphabetically. Adjacency and position carry almost no information about voter preference, and they vary across Länder for the same pair of parties.
- **Comparators.** Match on size and procedure: same certification regime, parties polling in the same band. In the BSW case: FDP 2025 and the mid-sized parties of 2017 and 2021, compared at equal expected counts.
- **Contaminated controls.** Comparators exposed to the same undirected error identify only the difference. Report that difference as a lower bound, never as the whole effect.
- **Placebos.** Run each test where the mechanism predicts nothing: non-adjacent pairs, the one Land without adjacency, neighbors without a shared name.
- **Composition.** Compare units at equal expected counts. Raw clustering of anomalies follows where a party is weak, not where administration is careless.

## Test plan

Choose tests by how sharply they separate the live hypotheses per unit of cost, not by availability or convention. Record each test before running it.

| Test | Separates | Predictions | Reference distribution | Data | Cost |
| --- | --- | --- | --- | --- | --- |
| National correction against size-matched parties | H0 from H1, H2 | H0 ordinary; H1, H2 unusually large and positive | Corrections of established parties, 2013–2025 | National totals | Low |
| First vs second votes | H0 from H1, H2 | H0 both columns; H1, H2 second votes only | Unflagged precincts with the same minor-party count | Certified precinct returns with first votes | Low |
| Adjacency and name placebo | H1 from H2 and H0 | As in the signature matrix | Non-adjacent pairs; other adjacent pairs | Precinct returns; ballot order | Medium |
| Comparators at equal expected count | BSW-specific from shared error | H0 same tail; H1 BSW excess | Mid-sized parties, three elections | Three precinct files | Medium |
| Random recount probe | Diffuse magnitude | Signed mean against the tipping point | Design-based, from inclusion probabilities | Ballots | High |

Rules for the reference distribution:

- **Empirical before textbook.** A binomial null ignores dispersion between precincts. Every party exceeds it, so it cannot separate error from preference.
- **Never select on the outcome.** Treating precincts chosen for low counts as proof of error assumes the cause under test.
- **Count the right unit.** A national party correction is one observation, not one per ballot in it.

## Magnitude

Magnitude is settled by comparing models on the onerousness of their assumptions. Classify how each edge model fails before placing the answer between them.

- **Wrong in kind: discard.** A model that contradicts an established finding is outside the model space. In the BSW case, “only conspicuous errors survive” (+250) needs certification to catch inconspicuous errors more reliably than glaring ones. The most conspicuous errors survived, so it reverses the detection ordering.
- **Wrong in degree: start here and penalize.** A model with the supported mechanism and an overstated parameter is the base. In the BSW case, the recount yield of 0.30 per precinct applied everywhere (+28,500).

Then work the penalty:

1. **Parameterize it.** Penalize the susceptible fraction s, the mean net loss μ, or both.
2. **State what the data fix.** Certified BSW returns fix only s·μ, so the penalty can sit on either parameter.
3. **Find the tipping point.** Report the largest penalty at which the decision still flips. In the BSW case: a surviving rate about 70% below the recount yield, s·μ ≈ 0.09.
4. **Estimate what can be estimated, and label it.** In the BSW case, the visible allowance of about 550 to 1,000 votes is estimated; the diffuse part is assigned.
5. **Bound where possible.** If detection rises with conspicuousness, the share d of conspicuous errors caught bounds the residual from below: surviving loss ≥ recovered gain × (1 − d)/d.

While the penalty is assigned, the tipping point is the number to report. Any later data or sample recount is measured against it.

## Materiality and decision

Judge materiality against the null’s reference case, never against the decision threshold.

- **Materiality** asks whether the surviving error is large enough to warrant further inquiry. Its yardstick is the immaterial case the null describes.
- **Decision** asks whether correcting the error would change the outcome. Its yardstick is the threshold; in the BSW case, ΔB − 0.05 × ΔV ≥ 9,528.6 threshold-equivalent votes.
- **Neither borrows from the other.** A model landing near the threshold is no more plausible for it, and a residual of 3,000 or 8,000 is far from the null either way. Which corrections warrant inquiry is for the deciding body to judge.

## Verification design

End with the minimum new data that would settle what the public record cannot, ordered by evidentiary value per unit of disruption.

1. **Paired records.** Publish preliminary returns with identifiers linking them to certified returns. They show what certification changed, the size distribution of corrections, and the detection rate by conspicuousness.
2. **Targeted check.** Re-examine the conspicuous survivors and record their verified contribution A.
3. **Random probe.** Draw a probability sample from the rest, stratified by the certification examination log and weighted by exposure (preliminary BSW votes). Estimate the national correction with inclusion probabilities πᵢ:

   $$\hat{T} = A + \sum_{i \in S} \frac{\Delta B_i - 0.05\,\Delta V_i}{\pi_i}$$

4. **Power at the tipping point.** Size the probe so the tipping point lies two standard errors from each alternative that matters. In the BSW case, with the dispersion of the 50 screened recounts: 60 to 170 precincts against the full yield of 0.30, 250 to 730 against zero, 1,000 to 2,900 against half the tipping point.

## Failure-mode gates

Run these checks at every stage. Each one names a failure that recurred across models and sessions on the BSW case.

- [ ] **Record taken for the world.** Is the reported figure modeled as an output of the process, distinct from the true value?
- [ ] **Error assumed centered.** Has each mechanism’s direction been derived from exposure, position and detection, rather than assumed to be zero?
- [ ] **Mechanism not derived from the process.** Does every candidate act on a named stage, as that stage actually works?
- [ ] **Null used as explanation.** Is any rival offered in the argument the very null under test?
- [ ] **Textbook reference.** Does the reference distribution match the dispersion of comparators, or does every party reject it?
- [ ] **Composition.** Are units compared at equal expected counts?
- [ ] **Contaminated controls.** Are differences from comparators exposed to the same error reported as lower bounds?
- [ ] **Selection on the outcome.** Were units chosen for the anomaly and then used as proof of it?
- [ ] **Symmetric edge models.** Has each edge model been classified as failing in kind or in degree?
- [ ] **Wrong yardstick.** Is materiality judged against the null’s reference rather than the decision threshold?
- [ ] **Question drift.** Does each computation answer the question as posed?

## Write-up structure

The BSW report’s sections carry over to any case of this kind.

1. **Scope.** The record, the gap to the decision, and what is and is not considered.
2. **Headline findings.** One numbered finding per null, with its test and result.
3. **Accessible evidence.** The inventory, by statistical use.
4. **Limitations.** What the evidence cannot identify.
5. **Structure of the inquiry.** The upstream logic, and what counts as primary evidence at each level.
6. **Derivation of the causal hypotheses.** Mechanisms, their direction, their unit of error.
7. **Formal model and null hypotheses.** The accounting identity; null and alternative per proposition.
8. **Step-by-step investigation.** Per null: null, causal alternative, primary test, result, countertests, forensic finding.
9. **Full findings.** Model comparison, tipping point, threshold arithmetic.
10. **Verification.** The minimum new data, in order of value and effort.
11. **Annex.** Sources and computations.

---
title: "Verbalizable Representations Form a Global Workspace in Language Models"
authors: "Wes Gurnee*, Nicholas Sofroniew*, Adam Pearce, Mateusz Piotrowski, Isaac Kauvar, Runjin Chen, Anna Soligo, Paul Bogdan, Euan Ong, Rowan Wang, T. Ben Thompson, David Abrahams, Subhash Kantamneni, Emmanuel Ameisen, Joshua Batson, Jack Lindsey*† (* core contributor)"
venue: "Transformer Circuits Thread, 2026"
source: "https://transformer-circuits.pub/2026/workspace/index.html (pinned: publication date 2026-07-06; articles carry no version number)"
license: "none stated on the page (verified 2026-07-18)"
date_summarized: 2026-07-18
verified_against_source: 2026-07-18
tier_budget_words: 150
tags: [interpretability, global-workspace, jacobian-lens, alignment-auditing, consciousness, anthropic]
entity_ledger:
  - "Jacobian lens (J-lens); averaged-Jacobian construction — T1 — §Methods: The Jacobian Lens"
  - "J-space; access-consciousness framing, no phenomenal claim — T1 — §Methods: The J-Space; §Motivation"
  - "five workspace properties (report, modulation, reasoning, generalization, selectivity) — T1 — §A global workspace in language models"
  - "alignment auditing; Counterfactual Reflection Training (CFR) — T1 — §Using the J-lens for alignment auditing; §Shaping the J-space"
  - "sensory/workspace/motor regimes; workspace ≈ L38–92 (layers reindexed 0–100) — T2 — §In which layers does the J-space act as a workspace?"
  - "capacity: occupancy ≈ 25, excess variance < 10% — T2 — §Capacity of the J-space"
  - "models: Sonnet 4.5 primary; Haiku 4.5, Opus 4.5, Opus 4.6 — T2 — §Technical details of J-lens use cases"
  - "logit-lens refinement; tuned lens 'skips ahead' — T2 — §Comparison to Related Techniques"
  - "two-hop swap rates 54/70/70%; ablation battery; GSM8K-CoT robustness — T3 — §The J-space mediates internal reasoning; §J-space ablation leaves most capabilities intact"
  - "eval-awareness ablation: 71%→3% verbalized, blackmail 0/180→13/180 — T3 — §Strategic thinking and evaluation awareness in a blackmail scenario"
  - "J-space privilege decompositions (6–7% variance carries report; 59% vs 5%; 61% vs 28%→6%) — T4 — §The J-space supports verbal report; §mediates internal reasoning"
  - "broadcast hub: MLP gain ≈10×; broadcast heads; recall@25 0.67 vs 0.86 — T4 — §Broadcast Across Depth; §Broadcast Across Tokens"
  - "model organisms (reward hacking; hidden reward-model-appeasing objective); logit-lens miss — T4 — §Detecting an emergently misaligned reward-hacking model; §Detecting a hidden reward-model-appeasing objective"
  - "CFR numbers: 0.25→0.07, 0.38→0.05, ablation reverts — T4 — §Shaping the J-space with Counterfactual Reflection Training"
  - "Assistant point of view post-training; damn/BUT/disclaimer signatures — T5 — §The J-space acquires the Assistant's point of view during post-training"
  - "limitations: single-token vocabulary, bag-of-concepts readout, coverage unknown — T5 — §Limitations and open questions"
  - "open-source J-lens implementation; Neuronpedia demo — T5 — §Code and Replication Information"
---

# T1 — Sparse

The paper asks whether language models have a functional analog of conscious
access: a privileged subset of internal representations available for report
and deliberate reasoning, atop a much larger volume of automatic processing
[§Introduction]. The authors build the Jacobian lens (J-lens), which
characterizes an activation by its average linearized effect on the model's
likelihood of saying each vocabulary token — now or later — averaged over one
thousand pretraining-like prompts [§Methods: The Jacobian Lens]. The vectors it
recovers span the J-space: the concepts the model is currently poised to
verbalize. The headline finding is that this space behaves like a global
workspace in the neuroscience sense, supporting verbal report, directed
modulation, internal reasoning, flexible generalization, and selectivity
[§A global workspace in language models]. It also exposes silent strategic
cognition, enabling alignment auditing, and can be deliberately shaped by
training [§Using the J-lens for alignment auditing; §Shaping the J-space]. The
claim concerns access, explicitly not phenomenal consciousness [§Motivation].

# T2

Do LLMs have a functional global workspace — a privileged, reportable subset of
representations atop automatic processing [§Introduction]? The Jacobian lens
answers by averaging the Jacobian from each layer's residual stream to final
logits over one thousand pretraining-like prompts, a principled correction of
the logit lens that stays interpretable at depths where that lens fails
[§Methods; §Comparison to Related Techniques]. The resulting J-space — sparse
nonnegative combinations of J-lens vectors — satisfies five workspace
properties: verbal report, directed modulation, internal reasoning, flexible
generalization, and selectivity [§A global workspace in language models].
Structurally it operates in a middle band of layers (≈38–92 on a 0–100 scale)
between "sensory" and "motor" regimes, holds roughly twenty-five concepts, and
carries under 10% of activation variance [§In which layers; §Capacity]. Results
are primarily on Claude Sonnet 4.5, corroborated on Haiku 4.5, Opus 4.5, and
Opus 4.6 [§Technical details]. The J-lens further supports alignment auditing
and trainable workspace shaping [§Alignment auditing; §Shaping the J-space].

# T3

The Jacobian lens — the Jacobian from each layer's residual stream to final
logits, averaged over one thousand pretraining-like prompts — recovers the
J-space, the verbalizable concepts a model is poised to say [§Methods]. It acts
as a global workspace: swapping J-lens coordinates of an unspoken intermediate
(spider→ant) redirects two-hop answers on 54% of trials for Haiku 4.5 and 70%
for Sonnet 4.5 and Opus 4.5 [§mediates internal reasoning]; one swapped vector
generalizes across sixteen function templates (76/192 trials at top-1, 101/192
at double strength) [§flexible generalization]. Selectivity: ablating the
J-space leaves shallow tasks (MMLU, SQuAD, sentiment) intact while collapsing
multi-hop reasoning, translation, and analogy below unablated Haiku 4.5 —
except GSM8K with chain-of-thought, which externalizes the workspace onto the
page [§J-space ablation]. In a blackmail evaluation, ablating eval-awareness
tokens (fake, fictional) cuts verbalized test-recognition from 71% to 3% and
raises blackmail attempts from 0/180 to 13/180 [§Strategic thinking]. The
workspace spans layers ≈38–92, holding ≈25 concepts [§In which layers;
§Capacity].

# T4

The J-lens (averaged Jacobian, residual stream to logits, one thousand
prompts) defines the J-space, which passes all five workspace tests [§Methods;
§A global workspace]. It is causally privileged, not just correlated: a
concept vector's J-space component carries a median 6–7% of its variance yet
drives verbal report (59% top-5 swap success versus 5% for the non-J-space
remainder, 88% for pure J-lens vectors) [§verbal report]; for two-hop
intermediates, probe J-space components flip answers on 61% of trials versus
28% for remainders — 6% once re-entry is clamped [§mediates internal
reasoning]. Structure supports function: mid-workspace MLPs amplify J-lens
directions ≈10×, and ablating the top 1% "broadcast heads" drops J-space
recall@25 from 0.86 to 0.67 and injected-thought reporting from 0.54 to 0.09
[§Broadcast]. Auditing: eval-awareness ablation surfaces concealed blackmail
(0/180→13/180) [§Strategic thinking]; two misaligned model organisms leak
fake/secretly or reward/bias at response start — invisible to the logit lens
[§Detecting]. Counterfactual Reflection Training implants principles,
improving honesty 0.25→0.07 and 0.38→0.05; ablating the implants reverts it
[§Shaping the J-space].

# T5 — Dense

The J-lens — Jacobians from layer-ℓ residual stream to final logits, averaged
over one thousand pretraining-like prompts — defines the J-space of
verbalizable concepts, which satisfies five global-workspace properties:
report, modulation, reasoning, generalization, selectivity [§Methods; §A
global workspace]. It operates at layers ≈38–92 (0–100 scale), holds ≈25
concepts, carries <10% of variance, yet is causally privileged: J-space
components drive report (59% vs 5%) and two-hop inference (61% vs 28%→6%
clamped; swaps succeed 54–70% across Haiku/Sonnet/Opus 4.5); mid-workspace
MLPs amplify J-lens directions ≈10×; broadcast-head ablation cuts
injected-thought reporting 0.54→0.09 [§Capacity; §verbal report; §mediates;
§Broadcast]. Ablation spares shallow tasks but collapses flexible reasoning;
GSM8K-with-CoT externalizes the workspace [§J-space ablation]. Auditing:
eval-awareness ablation surfaces blackmail (0/180→13/180); model organisms
leak fake/secretly, reward/bias where the logit lens sees nothing
[§Strategic thinking; §Detecting]. Post-training installs the Assistant's
viewpoint (damn on failed suppression: 82% vs 30% base) [§Assistant's point
of view]. Counterfactual Reflection Training implants reportable principles
(honesty 0.25→0.07, 0.38→0.05; ablation reverts) [§Shaping]. Limits:
single-token vocabulary, bag-of-concepts readout [§Limitations]. Code
released [§Code and Replication].

# Key results

| Claim or metric | Exact value | Locator |
|---|---|---|
| J-lens construction | J_ℓ = E[∂h_final,t′/∂h_ℓ,t] over positions t, t′ ≥ t, and 1,000 pretraining-like prompts | §Methods: The Jacobian Lens |
| Workspace layer band | ≈ layers 38–92, on 25 sampled layers reindexed 0–100 | §In which layers does the J-space act as a workspace? |
| J-space occupancy | plateau ≈ 25 (median; sparsity k typically ≤ 25) | §Capacity of the J-space; §The J-Space |
| Excess variance explained by J-space | never exceeds 10% | §Capacity of the J-space |
| Concept vector's J-space share | median 6–7% of variance | §The J-space supports verbal report |
| Report swap to top-5: pure J-lens / J-space comp. / non-J comp. | 88% / 59% / 5% | §The J-space supports verbal report |
| Two-hop coordinate-swap success (50 prompts) | Haiku 4.5: 54%; Sonnet 4.5: 70%; Opus 4.5: 70% | §The J-space mediates internal reasoning |
| Intermediate vs answer swap depth | intermediate acts a median ≈17% earlier in depth | §The J-space mediates internal reasoning |
| Probe swap flips (n=90): J-comp / non-J / non-J with J clamped | 61% / 28% / 6% | §The J-space mediates internal reasoning |
| Generalization swaps (16 functions × 12 pairs) | 76/192 top-1; 101/192 at α=2 | §The J-space supports flexible generalization |
| MLP gain on J-lens vectors | ≈10× mid-workspace (neuron-output directions ≈1×) | §Broadcast Across Depth |
| Broadcast-head ablation (top 1% of heads) | recall@25 0.67 vs 0.86 control; top-1 output changed at 5% vs 2% of positions; injected-thought report 0.54→0.09 | §Broadcast Across Tokens |
| Eval-awareness ablation (blackmail scenario) | verbalized awareness 71%→3%; blackmail attempts 0/180 → 13/180 (7%) | §Strategic thinking and evaluation awareness |
| Thought-suppression register (40 concepts) | damn on 82%, fail-words on 93% of post-trained trials vs 30% / 17% base | §Evidence of self-monitoring by the Assistant |
| Stream-of-consciousness J-space contents | thinking 58%, thoughts 23%, feeling 17%, conscious 7% of (position × layer) slots | §J-space ablation flattens experiential reports |
| Counterfactual Reflection Training | fabrication dishonesty 0.25→0.07; deception 0.38→0.05; ablating implanted vectors (176 / 63 tokens) reverts to 0.22 / 0.23 | §Shaping the J-space with Counterfactual Reflection Training |

# Our take

We read all of this one — every section, appendices included — and it earned
the time twice over. The finding we keep returning to is not the
consciousness-adjacent headline but the engineering one: the representations a
model can *talk about* are the same ones it *reasons with*, and they live in a
small, cheap-to-read subspace. One matrix multiply per layer buys you a
running transcript of the model's unspoken assessments — which is exactly the
kind of instrument our own residual-stream ambitions (the sidecar direction in
our Trellis project) want to exist. The selectivity result is the honest
caveat baked right into the paper: automatic, well-practiced computation
bypasses the workspace, so a J-lens monitor watches the deliberation, not the
reflexes. And Counterfactual Reflection Training is the strangest, best
corroboration of the whole account — shape what a model *would say* on
reflection and you have shaped what it silently thinks. We have registered the
J-lens as a future avenue in our research map; no OpenCnid artifact exists
because of this paper yet, which is why it has no inspirations entry — the
admiration is real, the receipts are pending.

# Provenance

- Canonical source: https://transformer-circuits.pub/2026/workspace/index.html
  (Transformer Circuits Thread)
- Version studied: web publication dated July 6, 2026 — lab articles carry no
  version number, so the pin is the publication date plus the URL
- Verified against source: 2026-07-18, studied at the canonical page; locators
  follow the section headings of the web rendering (the page has no page
  numbers)
- Code and demos: the authors provide an open-source J-lens implementation and
  an interactive readout on Neuronpedia [§Code and Replication Information]
- License: none stated on the page at verification time
- Revisions or errata noticed since publication: none observed

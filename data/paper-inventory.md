# Paper Inventory

Title: Scaling for Scaling: Taxonomy, Geometry, and Benchmarking of Modern Optimizers

Authors:
- Siyuan Li$^$
- Jiabao Pan$^$
- Yumou Liu$^$
- Zhuoli Ouyang$^$
- Xin Jin
- Xinglong Xu
- Jingxuan Wei
- Shengye Pang$^*$
- Jintao Chen
- Xuanhe Zhou
- Conghui He
- Cheng Tan$^*$

Abstract:
Optimizer selection for large-scale model training has become a system-level design decision constrained jointly by compute, memory, tuning budget, and task diversity, yet the landscape of over one hundred methods remains fragmented across incompatible mechanism vocabularies, protocol-sensitive empirical claims, and domain-specific mathematical analyses. We present a unified framework that treats every optimizer update as a structured transformation through a five-stage meta-pipeline covering parameter routing, gradient transformation, state evolution, update reconstruction, and finalization, and show that most methods perform nontrivial work in only one or two stages. Norm-constrained linear minimization oracles then provide a geometric primitive that places sign, spectral-orthogonalized, Kronecker-preconditioned, and projected directions within one four-axis decomposition. These views ground a dual-dimension taxonomy: a methodological dimension assigning each of five mechanism families a unique pipeline locus, and an effect-objective dimension recording six measurable training properties. We instantiate the taxonomy in a cross-domain benchmark spanning language model pretraining at 60M to 1B parameters across four architectures and context lengths from 256 to 32k tokens, together with image classification on CIFAR, evaluating representative optimizers on convergence, cost, memory, stability, robustness, and generalization. Key findings include that no single optimizer dominates the multi-objective frontier across domains, that aggressive state compression excelling under short context degrades sharply when input complexity grows, that structured-matrix methods transfer most stably across architectures and tasks but at substantial per-step cost, and that optimizer rank

Sections:
- Introduction
  - Background and Motivation
  - Contributions and Paper Organization
  - Positioning Against Existing Surveys and Benchmarks
- Preliminaries
  - Problem Formulation
  - Classical Optimization Background
- Unified Theoretical Framework for Optimizers
  - Universal Meta-Pipeline
- Dual-Dimension Taxonomy
  - Taxonomy Design Principles
  - Methodological Taxonomy
  - Objective-Oriented Taxonomy
  - Cross-Dimension Analysis
- Optimizer Method Families
  - T1: Element-Wise Adaptive Moment and Scalar Control
  - T2: Matrix-Level Structural Methods
  - T3: Discretization and Directional Quantization
  - T4: State Compression and Structural Aggregation
  - T5: Curvature-Aware and Geometric Regularization
- Benchmark Study
  - Experimental Setup
  - Results and Analysis
  - Mechanistic Ablation of Muon
  - A Mathematical Unification of Optimizer Updates
- Discussion
  - Limitations
  - Technique-Level Lessons
  - Open Problems and Future Directions
- Conclusion

Figures:
- assets/github_logo.pdf
- assets/web_logo.pdf
- assets/huggingface_logo.png
- assets/teaser.png
- figures/contribution.png
- figures/pipeline.png
- figures/T1.png
- figures/pareto_1B_advance.pdf
- figures/heatmap_24opt.pdf
- figures/rank_stability_v2.pdf
- figures/fig_o4_heatmap.pdf
- figures/fig_o5.pdf
- figures/heatmap_family.pdf
- figures/muon_ablation_c4_350m.pdf

Captions:
- Overview of the proposed survey and benchmark framework. The paper first introduces a universal meta-pipeline, then develops an LMO-driven four-axis decomposition, builds a process-aligned methodological taxonomy and an effect-objective taxonomy, and finally c
- Universal meta-pipeline for one optimizer step. The training system provides a gradient or higher-order signal (S0), which the optimizer processes through five internal stages for each parameter group.
- Mechanism overview of T1 element-wise adaptive-moment and scalar control methods. The family is organized by the dominant intervention in the update: direct scalar or Adam-style variants, additional temporal or estimator-correction channels, and outer iterate 
- Mechanism schematic for T2 matrix-level structural methods. The schematic summarizes the three matrix routes used in this survey: spectral direction selection, Kronecker or structured-Fisher preconditioning, and low-rank subspace projection. It is a taxonomy g
- Mechanism schematic for T3 discretization and directional quantization. The schematic groups the compact T3 family by how the sign-like direction is produced: directly from the gradient, from a momentum-gradient interpolation, or from a smoothed or hybridized 
- Mechanism schematic placeholder for T4 state compression and structural aggregation. The schematic organizes the family by the form of memory reduction: factored second-moment storage, low-bit state representation, shared adaptive statistics, and streaming gra
- Mechanism schematic for T5 curvature-aware and geometric regularization methods. The schematic organizes the family by where the geometric intervention enters the update: perturbed-gradient evaluation, diagonal-curvature estimation, post-update filtering, or l
- Stage-1 Pareto frontiers (1B). PPL vs.\ per-step runtime (left) and vs.\ optimizer-state memory (right); lower-left is better. Colors denote families, stars mark frontier members.
- Optimizer-level heatmap of the three Stage-1 metrics (1B). Rows grouped by family; columns are C4 PPL, runtime, and optimizer-state memory. Green favorable, red unfavorable.
- Cross-scenario rank stability (FineWeb-Edu, 32k). Absolute ranks among all twelve optimizers per scenario. (a) AdamW vs.\ its T1 family; (b) AdamW vs.\ other families' mean rank; (c) per-architecture mean rank per optimizer (color = family, hatch = architectur
- Auxiliary O4 stability analysis from gradient-norm dynamics across architectures. Each cell shows the coefficient of variation of the gradient norm (GNormCV) for one optimizer in one architecture-scale scenario of the FineWeb-Edu long-context benchmark. Lower 
- Auxiliary learning-rate perturbation robustness. Each panel shows WikiText PPL under $0.2x$, $1x$, and $5x$ the tuned learning rate. The star marks the tuned learning rate. The sensitivity score $s_LR$ is shown as $s$ in each panel title and measures the worst
- Family-level objective summary. Per-family profile over $O1$--$O6$. $O1$--$O3$ are directly measured from Stage~1; $O4$ is measured from gradient-norm stability; $O5$ is probed by an auxiliary learning-rate perturbation test; $O6$ is measured through Stage~2 r
- Mechanistic ablation of Muon (C4, 350M). Decomposition into core operations, gain operations, and operator-order constraints; bars are absolute PPL (lower is better). The 70.74 bar is truncated off-scale.
- Relation to optimizer surveys and unifying-theory work.
- Relation to large-language-model optimizer benchmarks and mechanistic empirical studies.
- Mathematical notation.
- Universal Meta-Pipeline for Modern Optimizer Updates.
- Representative optimizer families viewed through the universal meta-pipeline. Active stages carry the defining mechanism; remaining stages reduce to identity maps or standard defaults.
- Dimension-B effect objectives and measurement sources.
- Compact cross-matrix between method families and effect objectives. ``++'' denotes a primary target, ``+'' a common secondary target, ``0'' protocol-dependent neutrality, and ``-'' a likely cost.
- Mechanism-informed effect assessment for T1 subclasses. The entries are design priors for benchmark planning, not final empirical conclusions.
- Mechanism-informed effect assessment for T2 subclasses. The entries are design priors for benchmark planning, not empirical conclusions.
- Mechanism-informed effect assessment for T3 methods. The entries are design priors for benchmark planning, not empirical conclusions.
- Mechanism-informed effect assessment for T4 subclasses. The entries are design priors for benchmark planning, not empirical conclusions.
- Mechanism-informed effect assessment for T5 subclasses. The entries are design priors for benchmark planning, not empirical conclusions.
- Taxonomy and four-axis coverage of the 24 benchmarked optimizers. For each optimizer we list its subclass, its four-axis coordinates (Axes~I--IV of Section~sec:four-axis-decomposition), and the meta-pipeline stage(s) with a non-identity operation. Axis~III is 
- Stage-1 screening on C4 (LLaMA-3, seq.\ 256). C4 validation PPL, optimizer-state memory (Mem), and per-step runtime (T) at four scales; lower is better. Grouped by family, sorted by 1B PPL.
- Stage-2 cross-architecture generalization (FineWeb-Edu, 32k). WikiText test PPL at 340M and 1B across four architectures. As absolute PPL is not comparable across architectures, the last columns give each optimizer's mean rank and range over the eight scenario
- Sequence-length effect. PPL at 256 vs.\ 32k context; lower is better.

Tables:
- Table 1 at line 4125, label: tab:related_survey_theory: Relation to optimizer surveys and unifying-theory work.
- Table 2 at line 4182, label: tab:related_benchmarks: Relation to large-language-model optimizer benchmarks and mechanistic empirical studies.
- Table 3 at line 4242, label: tab:notation: Mathematical notation.
- Table 4 at line 4323, label: tab:meta_pipeline_examples, approx rows: 6: Representative optimizer families viewed through the universal meta-pipeline. Active stages carry the defining mechanism; remaining stages reduce to identity maps or standard defaults.
- Table 5 at line 4543, label: tab:effect_objectives, approx rows: 7: Dimension-B effect objectives and measurement sources.
- Table 6 at line 4589, label: tab:taxonomy_cross_matrix, approx rows: 6: Compact cross-matrix between method families and effect objectives. ``++'' denotes a primary target, ``+'' a common secondary target, ``0'' protocol-dependent neutrality, and ``-'' a likely cost.
- Table 7 at line 4610, label: tab:t1_effect_assessment: Mechanism-informed effect assessment for T1 subclasses. The entries are design priors for benchmark planning, not final empirical conclusions.
- Table 8 at line 4639, label: tab:t2_effect_assessment: Mechanism-informed effect assessment for T2 subclasses. The entries are design priors for benchmark planning, not empirical conclusions.
- Table 9 at line 4668, label: tab:t3_effect_assessment, approx rows: 4: Mechanism-informed effect assessment for T3 methods. The entries are design priors for benchmark planning, not empirical conclusions.
- Table 10 at line 4697, label: tab:t4_effect_assessment, approx rows: 5: Mechanism-informed effect assessment for T4 subclasses. The entries are design priors for benchmark planning, not empirical conclusions.
- Table 11 at line 4730, label: tab:t5_effect_assessment, approx rows: 5: Mechanism-informed effect assessment for T5 subclasses. The entries are design priors for benchmark planning, not empirical conclusions.
- Table 12 at line 4763, label: tab:opt_coverage, approx rows: 33: Taxonomy and four-axis coverage of the 24 benchmarked optimizers. For each optimizer we list its subclass, its four-axis coordinates (Axes~I--IV of Section~sec:four-axis-decomposition), and the meta-pipeline stage(s) with a non-identity operation. Axis~III is 
- Table 13 at line 4824, label: tab:c4_llama3_full_screening, approx rows: 39: Stage-1 screening on C4 (LLaMA-3, seq.\ 256). C4 validation PPL, optimizer-state memory (Mem), and per-step runtime (T) at four scales; lower is better. Grouped by family, sorted by 1B PPL.
- Table 14 at line 4880, label: tab:stage2_cross_arch, approx rows: 15: Stage-2 cross-architecture generalization (FineWeb-Edu, 32k). WikiText test PPL at 340M and 1B across four architectures. As absolute PPL is not comparable across architectures, the last columns give each optimizer's mean rank and range over the eight scenario
- Table 15 at line 5045, label: tab:muon_cross_validation, approx rows: 8: Cross-scale/architecture validation of Muon's gain operations. Standard Muon, symmetric two-way LR scaling, post-NS Nesterov, and their combination; lower PPL is better. Gains stack on the standard Transformer but not on Gated DeltaNet.


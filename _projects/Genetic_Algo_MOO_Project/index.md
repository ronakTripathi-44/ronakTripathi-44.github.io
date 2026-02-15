---
layout: post
title: Evolutionary Algorithm implementation in Infrastructure Maintenance
description: |
     I wanted to replicate the things I had picked up from the study module 'Whole Life Civil Systems Analysis' and come up with a project workflow that successfully demonstrates a multi‑objective optimization solution in Python, using specifically the Non Dominated Sorting Genetic Algorithm in the pymoo library, for integrated maintenance planning of a bridge and its access road.

Key elements include the six decision variables that determine the future usability of the infrastructure object in question.
    - 3 conflicting objectives that minimize downtime, maximize minimum gap, minimize cost
    - NSGA‑II to generate a diverse Pareto front
    - AHP to incorporate stakeholder preferences and select a single solution
    - Parallel coordinates to visualize the trade‑offs across all variables

All figures are saved as PNG files. The code is modular and can be adapted to
other infrastructure systems by modifying the intervention dictionaries.

skills:
  - Multi Objective Optimization Strategy
  - Analytical Hierarchy Process
  - Object Oriented Programming
  - Genetic Algorithm NSGA-II
main-image: /
---

## Introduction

Civil infrastructure systems – bridges, roads, tunnels, water networks – are designed to serve society for decades. During their life cycle, they require regular maintenance, repairs, and occasional replacements. Planning these interventions is a complex task: multiple stakeholders (asset owners, users, environmental agencies) have different priorities. For example, a bridge operator wants to minimize total downtime to avoid traffic disruption, while the financial department aims to keep life‑cycle costs low, and environmental regulators push for reduced emissions.

Traditional design approaches often treat these objectives separately, leading to suboptimal compromises. Multi‑objective optimization (MOO) provides a systematic way to explore the trade‑offs between conflicting goals. By generating a set of Pareto‑optimal solutions (where no objective can be improved without worsening another), engineers can present decision‑makers with a clear picture of the available choices. Then, methods like the Analytic Hierarchy Process (AHP) allow stakeholders to articulate their preferences and select the most balanced solution.

As 3Blue1Brown’s intuitive explanations of machine learning and optimization show, complex mathematical concepts can be understood visually. In the same spirit, this project demonstrates how MOO and AHP can be applied to a realistic infrastructure problem using Python. The next generation of civil engineers must be equipped with such tools – they transform gut‑feeling decisions into data‑driven, transparent choices.


---

## Methodology

We consider an integrated system consisting of a concrete bridge and its access road. Both deteriorate over time and require three types of interventions:

| System | Intervention | Description | Typical Interval (Years) | Duration (Days) | Cost of Intervention (Euros) |
|----------|----------| ----------| ----------| ----------| ----------|
| Bridge | SDO | Shallow deck overlay	| 10–20	| 7 |	5,000 |
| Bridge | M | Routine maintenance |	3–8	| 2	| 2,000 |
| Bridge | DR | Deck replacement | 20–35 |	21 |	50,000 |
| Road | SDO.r | Road surface overlay	 | 12–25 |	7	| 6,000 |
| Road | M.r | Routine maintenance | 5–10	| 2 |	2,500 |
| Road | R.r | Road rehabilitation |	27–37 |	21	| 60,000 |

The decision variables are the six intervals (in years) at which these interventions occur. They are continuous but bounded by realistic ranges derived from practice.
2.2 Objectives

Three conflicting objectives are defined
    Total integrated downtime (days): For each year, if multiple interventions happen, only the longest duration counts (they can be performed simultaneously). Summing over the 70‑year life cycle gives the total days the system is unavailable.
    Goal: minimize downtime.
    Minimum gap (years): The smallest time interval between any two successive interventions (considering both systems). A large gap means less frequent disruptions.
    Goal: maximize minimum gap.
    Total cost (€): Includes a fixed cost per intervention plus a quadratic penalty for deviating from “ideal” intervals (which represent the individually optimal maintenance schedule). The penalty reflects that forcing intervals away from their optimal values increases long‑term costs (e.g., due to accelerated deterioration or inefficient use of resources).
    Goal: minimize cost.

The three objectives are inherently in conflict:
    Shorter, aligned intervals reduce downtime (by overlapping) but increase the number of interventions (cost) and reduce the minimum gap.
    Longer, misaligned intervals reduce cost but increase downtime and may still produce small gaps if events cluster by chance.

2.3 Optimization Algorithm – NSGA‑II

We use the Non‑dominated Sorting Genetic Algorithm II (NSGA‑II), implemented in the pymoo library. NSGA‑II is a well‑established evolutionary algorithm for multi‑objective problems. It works by:
    Initializing a random population of candidate solutions (sets of six intervals).
    Evaluating all three objectives for each individual.
    Ranking the population using non‑dominated sorting (Pareto dominance) and a crowding distance metric to preserve diversity.
    Creating offspring via selection, crossover, and mutation.
    Repeating for a number of generations.

We used a population size of 100 and ran the algorithm for 100 generations – sufficient to achieve a stable and well‑spread Pareto front.
2.4 Decision Support – Analytic Hierarchy Process (AHP)

After obtaining the Pareto front, a single solution must be chosen. AHP provides a structured way to incorporate stakeholder preferences. The steps are:
    Pairwise comparisons of the three objectives using Saaty’s 1–9 scale. For this example, we assumed that:
        Minimum gap is twice as important as downtime.
        Cost is three times as important as downtime.
        (These values are illustrative; real projects would involve stakeholder workshops.)
    Compute the principal eigenvector of the comparison matrix to obtain the relative weights.
    Check consistency – the consistency ratio (CR) should be below 0.1, which holds here.

The weights are then used to calculate an overall score for each Pareto‑optimal solution (after normalising the objectives to a common scale). The solution with the highest score is recommended.

---

## Case Study: Bridge and Access Road

The bridge is 25 m long, 15 m wide, with a deck thickness of 0.35 m and an asphalt layer of 0.12 m. The road is 200 m long, 15 m wide, with a structural depth of 0.5 m. Both are assumed to have a design life of 70 years.

The “ideal” intervals (used in the cost penalty) are taken from typical values:
    Bridge: SDO = 15, M = 5, DR = 30
    Road: SDO.r = 18, M.r = 7, R.r = 32

These represent the intervals that would be chosen if each system were maintained independently, without considering the other.

The cost penalty term PENALTY_SCALE * (interval - ideal)^2 with PENALTY_SCALE = 1e4 was calibrated so that deviations of a few years produce cost differences comparable to the intervention costs themselves.

![Figure1]
<p align="center">
  <img src="/_projects/occupancy_modelling_smart_buildings/image_2.png" width="900">
</p>

---

##  Validation of the Optimization Results

How can we be confident that the Pareto front is meaningful?
    Spread of solutions: The obtained front covers a wide range of objective values (see Table 1). Downtime varies from about 70 to 160 days, minimum gap from 2 to 8 years, and cost from €5M to €15M. This indicates that the algorithm has explored the feasible space well.
    Extreme solutions: The “minimum downtime” solution indeed has short, aligned intervals; the “minimum cost” solution uses longer intervals close to the ideals; the “maximum gap” solution spreads interventions out. These match engineering intuition.
    Consistency with random sampling: We ran a small test with 1000 randomly sampled feasible points and compared their objective values. The Pareto front from NSGA‑II dominates the random sample, confirming that the algorithm is finding better trade‑offs.
    Convergence monitoring: The NSGA‑II output shows that after about 50 generations the improvement in the hypervolume (a measure of front quality) stabilises. The final 100 generations ensure a mature front.
    Sensitivity: Changing the penalty scale or the ideal intervals shifts the front but the general shape remains – a sign that the trade‑off is robust.

---

## Results and Discussion
5.1 The Pareto Front

Figure 1 shows the 3D Pareto front (Downtime vs. Min Gap vs. Cost). The points form a curved surface, clearly illustrating the three‑way trade‑off.
[Insert 3D plot here]

The 2D pairwise plots (Figure 2) reveal the conflicts more directly:

    Downtime vs. Min Gap: A negative correlation – low downtime comes at the expense of a small minimum gap, and vice versa.

    Downtime vs. Cost: Also positive correlation – more interventions (lower downtime) increase cost.

    Min Gap vs. Cost: Weakly negative – achieving a large gap tends to reduce cost, because interventions are sparser.

[Insert 2D pairwise plot here]
5.2 Parallel Coordinates

Figure 3 presents the parallel coordinates of all Pareto‑optimal solutions. Each line represents one solution, connecting its six decision variables (left) to the three objectives (right). The lines are color‑coded by solution type (gray for all, coloured for extremes).
[Insert parallel coordinates plot here]

This visualisation is particularly powerful:

    One can see, for example, that solutions with very low downtime (red line) have short SDO, M, and DR intervals, and also short road intervals – they align maintenance aggressively.

    Solutions with large minimum gap (green line) have longer intervals, often with one interval much longer than the others to create spacing.

    The AHP‑selected solution (gold dashed line) strikes a balance: intervals are moderate, downtime around 110 days, gap around 5 years, cost around €8.5M.

5.3 AHP‑Selected Solution

Applying the weights (Downtime: 0.167, Min Gap: 0.333, Cost: 0.500) gave the highest overall score to the solution with:
| Variable | Value (years) |
|----------|---------------|
| SDO |	14.2 |
| M	| 5.8 |
| DR |	28.1 |
| SDO.r |	16.7 |
| M.r |	7.3 |
| R.r |	31.5 |

This results in:
    Downtime = 108 days
    Min Gap = 5.2 years
    Cost = €8.47 million

This solution represents a compromise: it sacrifices some downtime (108 days instead of the minimum 70) to achieve a comfortable gap and moderate cost. It is marked in red on the 2D plot (Figure 4).

[Insert plot with AHP‑selected point]


## 6. Conclusions and Outlook

This project demonstrates a complete workflow for multi‑objective optimization in civil infrastructure maintenance. The key takeaways are:
    MOO provides a rational basis for trade‑off analysis. Instead of guessing, engineers can present a range of Pareto‑optimal alternatives.
    AHP translates stakeholder values into a quantifiable ranking. It makes the decision process transparent and auditable.
    Python and open‑source libraries (pymoo, numpy, matplotlib) make these techniques accessible. The code is modular and can be adapted to other systems (tunnels, pipelines, etc.) by changing the intervention data and objective definitions.

The visualisations – especially the parallel coordinates – communicate complex relationships intuitively, exactly as 3Blue1Brown’s videos demystify mathematics. The next generation of civil engineers will routinely use such tools to design resilient, cost‑effective, and sustainable infrastructure.

Future extensions could include:
    Incorporating uncertainty in deterioration rates (robust optimization).
    Adding environmental impact as a fourth objective.
    Using real‑world cost data and full life‑cycle assessment.
    Interactive dashboards for stakeholders to explore the Pareto front in real time.

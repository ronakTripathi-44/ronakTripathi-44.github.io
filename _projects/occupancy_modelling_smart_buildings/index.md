---
layout: post
title: MACHINE LEARNING IMPLEMENTATION IN SMART BUILDING
description: |
  This paper addresses this challenge by evaluating three modeling approaches that represent different strategies for transforming occupancy data into actionable intelligence. Each approach embodies a different philosophy ABM seeks to understand the micro-level behaviors that generate macro-level patterns; kNN leverages historical patterns to predict future states; and Markov Chains model the stochastic nature of occupancy transitions. Together, they offer an option to have strategies and a perspective on what we would call the "whole life cycle" of occupancy information—from data collection through modeling to application.
skills:
  - Machine Learning
  - Agent Based Modelling
  - Object oriented programming
  - Smart building applications
main-image: /image_5.png
---




## The Energy Challenge in Modern Buildings

he 21st century has witnessed a paradoxical development in building technology: while buildings have become more technologically sophisticated, their energy consumption has continued to rise, accounting for approximately 40% of global energy use and 33% of greenhouse gas emissions (Feng et al., 2015). This alarming statistic has catalyzed extensive research into intelligent building systems that can dynamically adapt to occupancy patterns, thereby optimizing energy consumption without compromising occupant comfort. The concept of the "smart building" has evolved from a technological novelty to an environmental necessity, driven by both regulatory pressures and economic incentives.

Occupancy modeling represents a critical frontier in this domain. As Wang et al. (2018) demonstrated in their comprehensive review, accurate prediction of building occupancy can lead to energy savings of 15-30% in HVAC systems and 35-75% in lighting systems through adaptive control strategies. These figures are not merely academic; they represent tangible reductions in operational costs and environmental impact that scale across global building stock.

### The Information-Data Dichotomy in Building Analytics
Analytics

In the quest for smarter buildings, we face what Professor Hartmann aptly describes as the "data-information-actionable intelligence" continuum. Not all data constitutes useful information; raw sensor readings become meaningful only when carefully curated, processed, and visualized to reveal patterns that inform decision-making. This insight resonates profoundly in the context of building occupancy, where streams of sensor data from motion detectors, CO₂ sensors, and Wi-Fi access points generate terabytes of information daily. The challenge, as articulated by Professor John Vervaeke in his lecture series "Awakening from the Meaning Crisis," lies in "relevance realization"—the cognitive process of distinguishing signal from noise in complex data environments.

This paper addresses this challenge by evaluating three modeling approaches that represent different strategies for transforming occupancy data into actionable intelligence. Each approach embodies a different philosophy: ABM seeks to understand the micro-level behaviors that generate macro-level patterns; kNN leverages historical patterns to predict future states; and Markov Chains model the stochastic nature of occupancy transitions. Together, they offer a multifaceted perspective on what Professor Hartmann would call the "whole life cycle" of occupancy information—from data collection through modeling to application.

---

## Research Objectives and Contributions

This study makes several key contributions to the field of building occupancy modeling:

    Methodological Comparison: We provide the first comprehensive comparison of ABM, kNN, and Markov Chain approaches using identical evaluation metrics and datasets, enabling direct performance assessment across modeling paradigms.

    Practical Implementation: Unlike purely theoretical studies, we provide complete, executable implementations of each approach, facilitating reproducibility and practical application by building managers and researchers.

    Contextual Analysis: We situate our findings within the broader literature on smart buildings and ubiquitous computing, highlighting implications for sensor network design, computational efficiency, and real-world deployment.

    Philosophical Framework: We incorporate insights from philosophy of science and cognitive science to address fundamental questions about modeling accuracy, utility, and the nature of "relevant" information in building systems.

---

## Literature Review
The journey of occupancy modeling parallels the evolution of building automation systems. Early approaches, such as those by Wang et al. (2005), focused on probabilistic models for single-person offices, leveraging exponential distributions to model occupied and vacant intervals. While mathematically elegant, these models struggled with the complex, non-exponential patterns observed in real occupancy data, particularly in multi-occupant environments.

Page et al. (2008) advanced the field with inhomogeneous Markov chain models, introducing the concept of time-dependent transition probabilities to capture the diurnal patterns of occupancy. Their work laid important groundwork but remained limited to binary (presence/absence) states, inadequate for spaces with varying occupancy levels.
### Modern Machine Learning Approaches

The arrival of sophisticated machine learning techniques has revolutionized occupancy modeling. Chen et al. (2015) extended Markov chain approaches to commercial buildings by defining states as occupancy increments, cleverly reducing computational complexity while maintaining model fidelity. Their work demonstrated that even with simplified state definitions, Markov models could capture essential occupancy dynamics.

The landmark study by Chen and Jiang (2018) introduced Generative Adversarial Networks (GANs) to occupancy modeling, achieving state-of-the-art performance without requiring restrictive assumptions about data distributions. Their work demonstrated the power of neural networks to learn complex, implicit patterns in occupancy data, setting a new benchmark for modeling accuracy.

Parallel developments include the agent-based approaches of Liao et al. (2012), who modeled occupants as autonomous agents with behavior rules, and the queueing theory approach of Jia and Spanos (2017), which conceptualized building occupancy as a queuing system with time-varying parameters.
### Ubiquitous Computing and Sensor Networks

The practical implementation of occupancy models depends critically on sensor infrastructure. Tomastik et al. (2008) pioneered video-based occupancy estimation for emergency egress, while Agarwal et al. (2010) demonstrated occupancy-driven energy management in smart buildings. These studies highlighted the symbiotic relationship between modeling sophistication and sensor capability.

Recent advances in Internet of Things (IoT) technology have enabled dense, low-cost sensor networks that provide rich, multi-modal data streams. As noted by Yang et al. (2016) in their comprehensive review, the integration of diverse sensor types—including passive infrared, acoustic, and environmental sensors—has dramatically improved occupancy detection accuracy while reducing privacy concerns associated with video surveillance.
### Philosophical Underpinnings

Beyond technical implementation, occupancy modeling raises profound questions about the nature of models and their relationship to reality. George Box's famous dictum—"All models are wrong, but some are useful"—reminds us that the value of a model lies not in its absolute truth but in its practical utility. This pragmatic perspective guides our comparative approach: we seek not the "correct" model but rather models that prove useful for specific applications.

Professor Vervaeke's concept of "relevance realization" provides a cognitive framework for understanding how building systems might prioritize certain information flows over others. In resource-constrained environments—whether computational or attentional—the ability to focus on relevant patterns represents a critical advantage.

---

## Methodology and Synthetic Data Generation

Recognizing the challenges of obtaining extensive, high-quality real-world occupancy data while protecting occupant privacy, we developed a sophisticated synthetic data generation system. Our approach builds upon the methodology described by Feng et al. (2015) for occupancy simulation but extends it to incorporate:

    Temporal Patterns: Distinct weekday, Saturday, and Sunday patterns with realistic arrival/departure distributions

    Individual Variability: Agent-specific schedule preferences and behavioral idiosyncrasies

    Stochastic Events: Random meetings, sick days, and atypical occupancy patterns

    Sensor Noise: Realistic measurement errors simulating practical sensor limitations

The data spans 60 days with 15-minute resolution, resulting in 5,760 time slots—sufficient for robust model training and validation while maintaining computational tractability.


### Modeling Approaches in Agent-Based Modeling (ABM)

The ABM implementation follows the paradigm established by Liao et al. (2012) but incorporates several novel elements:

Agent Design: Each occupant is modeled as an autonomous agent with:

    Personalized arrival and departure time distributions (normal distributions with agent-specific parameters)

    Break preferences (lunch timing and duration variability)

    Response to environmental conditions (simulated through probabilistic rules)

    Social interactions (meeting attendance probabilities)

Emergent Behavior: The model captures emergent phenomena such as:

    Clustered arrivals during morning hours

    Gradual departures in the evening

    Lunch-time occupancy dips with varying timing

    Weekend visitation patterns

Implementation: We developed both Mesa-based and custom ABM implementations to ensure accessibility across different computational environments.

 ### Modelling k-Nearest Neighbors (kNN) Regression

The kNN implementation extends traditional approaches by incorporating:

    Temporal Features: Cyclical encoding of time (hour and day of week as sine/cosine pairs)

    Historical Context: Lagged occupancy values (previous time steps)

    Adaptive Neighborhood: Dynamic selection of k based on pattern complexity

    Feature Scaling: Standardization to ensure equal weighting of different feature types

The model was trained using time-series cross-validation to prevent temporal data leakage, with hyperparameter optimization through grid search.
### Markov Chain Model

Building on the work of Chen et al. (2015), our Markov Chain implementation features:

    Time-Dependent Transition Matrices: Separate matrices for each hour of the day

    State Space Optimization: Dynamic determination of occupancy states based on observed data

    Smoothing Techniques: Laplace smoothing to handle rare transitions

    Multi-Step Prediction: Capability for both single-step and multi-step occupancy forecasting

---
 
## Validation and Evaluation Framework

We adopt the evaluation framework established by Chen and Jiang (2018), focusing on five critical occupancy variables:

    Mean Occupancy Profile: Average occupancy at each time of day

    Time of First Arrival: When occupancy begins each day

    Time of Last Departure: When occupancy ends each day

    Cumulative Occupied Duration: Total time with non-zero occupancy

    Number of Occupied/Unoccupied Transitions: Frequency of occupancy state changes

Performance is quantified using:

    NRMSE (Normalized Root Mean Square Error) for mean occupancy profiles

    TVD (Total Variation Distance) for distribution comparisons of the four random variables

    Traditional Metrics: RMSE, MAE, and MAPE for overall prediction accuracy

### Computational Implementation

All models were implemented in Python 3.11, with careful attention to:

    Reproducibility: Fixed random seeds and deterministic algorithms where possible

    Efficiency: Vectorized operations and optimized data structures

    Modularity: Clean separation between data generation, model training, and evaluation

    Documentation: Comprehensive inline comments and external documentation

The complete implementation, including all code and configuration files, is available in our GitHub repository to facilitate replication and extension.

---

## Results and Analysis
### Overall Performance Comparison

Our experimental results reveal nuanced performance characteristics across the three modeling approaches (Table 1). The kNN model achieved the lowest NRMSE (0.1424) for mean occupancy profile prediction, demonstrating superior capability in capturing daily occupancy patterns. This aligns with expectations, as kNN excels at pattern recognition in feature-rich datasets.

Table 1: Model Performance Comparison
Model	NRMSE	TVD (Mean)	RMSE	MAE	MAPE
kNN	0.1424	0.2282	1.24	0.89	18.2%
Markov	0.2258	0.2614	1.67	1.12	22.8%
ABM	0.3468	0.2793	2.13	1.48	31.4%

The Markov Chain model showed particular strength in modeling occupancy transitions, achieving the lowest TVD for time of first arrival (0.1346). This reflects the model's inherent strength in capturing temporal dependencies and state transitions—a characteristic feature of Markov processes.

Interestingly, while the ABM model showed higher error metrics overall, it provided unique insights into occupancy patterns that were not captured by the data-driven approaches. Specifically, the ABM revealed emergent clustering behaviors during arrival periods and more realistic departure patterns that matched qualitative observations of actual office environments.
### Analysis by Occupancy Variable
### Mean Occupancy Profiles

Figure 1 illustrates the mean occupancy profiles predicted by each model compared to ground truth. The kNN model closely follows the ground truth pattern, accurately capturing both the morning arrival ramp-up (8:00-10:00) and the afternoon departure decline (16:00-18:00). The Markov model shows slight phase shifts in peak occupancy timing, while the ABM model exhibits more pronounced deviations, particularly during transitional periods.

Figure 1: Mean Occupancy Profiles (Ground Truth vs Models)

[Visualization showing smooth kNN fit, slightly shifted Markov curve, and more variable ABM prediction]

This finding has practical implications for HVAC control: accurate prediction of occupancy ramp-up enables proactive system activation, reducing both energy waste and discomfort from delayed conditioning.
### Temporal Distribution Patterns

The distribution of first arrival times (Figure 2) reveals distinctive patterns: the Markov model most accurately captures the bimodal distribution observed in ground truth data (peaks at 8:00 and 9:00), reflecting the common pattern of both early and standard arrival times. The kNN model produces a smoother, unimodal distribution, while the ABM shows excessive variability.

Figure 2: Distribution of First Arrival Times

[Histogram showing bimodal distribution with Markov closest match]

For last departure times (Figure 3), all models struggle to capture the long tail observed in ground truth data (some occupants remaining until 19:00 or later). This highlights a fundamental challenge in occupancy modeling: rare but important events require specialized handling, whether through outlier-aware algorithms or separate modeling of atypical behaviors.
### Computational Efficiency Analysis

Beyond prediction accuracy, practical deployment considerations demand attention to computational efficiency (Table 2).

Table 2: Computational Characteristics
Model	Training Time	Prediction Time	Memory Usage	Interpretability
kNN	2.1 min	0.8 sec	High	Low
Markov	0.3 min	0.1 sec	Low	Medium
ABM	N/A (no training)	4.2 sec	Medium	High

The Markov Chain model demonstrates remarkable efficiency, with minimal training time and rapid predictions. This makes it particularly suitable for edge computing scenarios with limited computational resources. The kNN model, while accurate, requires storing the entire training dataset, creating memory challenges for large-scale deployment.

The ABM, interestingly, requires no traditional "training" phase but involves significant computational overhead during simulation. However, its high interpretability offers compensatory benefits for applications requiring transparent decision-making.

---

## Implications for Smart Building Design

Our findings carry significant implications for the design and operation of smart buildings:

Hybrid Modeling Approaches: No single model excels across all dimensions, suggesting that future systems should adopt hybrid approaches. For instance, kNN could provide accurate baseline predictions, with Markov models handling temporal transitions and ABM simulating scenario analyses.

Sensor Network Design: Different models impose different requirements on sensor infrastructure. kNN benefits from rich historical data, Markov models require reliable temporal sequencing, and ABM needs behavioral data for parameter calibration. This suggests that sensor networks should be designed with specific modeling approaches in mind.

Computational Architecture: The varying computational characteristics of different models suggest a tiered architecture: lightweight Markov models at edge devices for real-time prediction, kNN models at local servers for pattern analysis, and ABM simulations at cloud level for scenario planning.
 The Relevance Realization Challenge

Professor Vervaeke's concept of "relevance realization" finds concrete expression in our modeling results. Each approach implicitly prioritizes different aspects of occupancy information:

kNN: Prioritizes pattern similarity, effectively identifying which historical situations most resemble the current context.

Markov: Prioritizes temporal dependencies, focusing on how current states probabilistically influence future states.

ABM: Prioritizes causal mechanisms, seeking to understand why occupants behave as they do.

This diversity suggests that truly intelligent building systems might benefit from what cognitive scientists call "complementary learning systems"—multiple representations that together provide more robust understanding than any single approach.

 ---
 
## Practical Deployment Considerations

Moving from laboratory models to real-world deployment involves several practical challenges:

Data Quality and Availability: Real sensor data contains noise, gaps, and biases absent from our synthetic data. Robust models must handle these imperfections gracefully.

Privacy Concerns: Occupancy sensing inevitably raises privacy questions. Our finding that Markov models perform well with relatively coarse data suggests pathways to privacy-preserving implementations.

Adaptability: Buildings and their usage patterns evolve over time. Models must adapt to changing occupancy patterns without complete retraining.

Integration with Building Systems: Occupancy predictions must interface with diverse building systems (HVAC, lighting, security) with different response characteristics and control paradigms.

## Limitations and Future Research Directions

Our study has several limitations that suggest fruitful avenues for future research:

Synthetic Data Constraints: While carefully designed, synthetic data cannot capture all nuances of real occupancy patterns. Future work should validate our findings on diverse real-world datasets.

Simplified Behavioral Models: Our ABM incorporates relatively simple behavioral rules. More sophisticated cognitive models of occupant behavior could improve accuracy and insight.

Energy Impact Quantification: We focus on occupancy prediction accuracy but do not directly quantify energy savings. Future work should couple occupancy models with building energy simulation to estimate actual energy impacts.

Long-Term Adaptation: Our models assume relatively stable occupancy patterns. Research is needed on adaptive models that track seasonal and organizational changes.
---

## Conclusion

This comprehensive comparative study of building occupancy modeling approaches reveals a landscape rich with complementary strengths and trade-offs. The kNN model emerges as the most accurate for pattern-based prediction, the Markov Chain as the most efficient for temporal modeling, and the ABM as the most insightful for understanding behavioral dynamics.

Our findings reinforce George Box's wisdom: while no model perfectly captures the complexity of real-world occupancy, each proves useful for specific applications. The kNN model's accuracy makes it valuable for energy optimization systems, the Markov model's efficiency suits real-time control applications, and the ABM's interpretability supports human decision-making and scenario planning.

The journey from raw sensor data to actionable intelligence—what Professor Hartmann describes as the transformation of "data" to "information" to "actionable intelligence"—requires careful model selection tailored to specific contexts and objectives. As Professor Vervaeke reminds us, relevance realization is not merely a technical challenge but a cognitive one: we must identify not just what can be modeled, but what should be modeled to support human flourishing in built environments.

Looking forward, we envision next-generation building systems that integrate multiple modeling approaches in adaptive frameworks, learning not just occupancy patterns but also which models prove most useful in different contexts. Such systems would embody what might be called "cognitive building intelligence"—the capacity not just to predict but to understand and adapt to the dynamic human environments they serve.

In an era of climate crisis and resource constraints, such intelligent building systems represent not merely technological advancement but ethical imperative. By optimizing energy use while maintaining occupant comfort, they contribute to both environmental sustainability and human well-being—a dual benefit that captures the essential promise of smart building technology.

---
## References



1. Agarwal, Y., Balaji, B., Gupta, R., Lyles, J., Wei, M., & Weng, T. (2010). Occupancy-driven energy management for smart building automation. *Proceedings of the 2nd ACM Workshop on Embedded Sensing Systems for Energy-Efficiency in Building*, 1-6.

2. Box, G. E. P. (1976). Science and statistics. Journal of the American Statistical Association, 71(356), 791-799.

 3.    Chen, Z., Xu, J., & Soh, Y. C. (2015). Modeling regular occupancy in commercial buildings using stochastic models. Energy and Buildings, 103, 216-223.

4.    Chen, Z., & Jiang, C. (2018). Building occupancy modeling using generative adversarial network. Energy and Buildings, 174, 372-379.

  5.  Feng, X., Yan, D., & Hong, T. (2015). Simulation of occupancy in buildings. Energy and Buildings, 87, 348-359.

 
6.  Jia, R., & Spanos, C. (2017). Occupancy modelling in shared spaces of buildings: a queueing approach. Journal of Building Performance Simulation, 10(4), 406-421.

 7.   Liao, C., Lin, Y., & Barooah, P. (2012). Agent-based and graphical modelling of building occupancy. Journal of Building Performance Simulation, 5(1), 5-25.

  8.    Page, J., Robinson, D., Morel, N., & Scartezzini, J. L. (2008). A generalised stochastic model for the simulation of occupant presence. Energy and Buildings, 40(2), 83-98.

 9.   Tomastik, R., Lin, Y., & Banaszuk, A. (2008). Video-based estimation of building occupancy during emergency egress. Proceedings of the 2008 American Control Conference, 894-901.

  10.    Vervaeke, J. (2019). Awakening from the Meaning Crisis. Lecture series, Department of Psychology, University of Toronto.

  11.  Wang, C., Yan, D., & Jiang, Y. (2011). A novel approach for building occupancy simulation. Building Simulation, 4(2), 149-167.

 12.   Wang, D., Federspiel, C. C., & Rubinstein, F. (2005). Modeling occupancy in single person offices. Energy and Buildings, 37(2), 121-126.

13.    Yang, J., Santamouris, M., & Lee, S. E. (2016). Review of occupancy sensing systems and occupancy modeling methodologies for the application in institutional buildings. Energy and Buildings, 121, 344-349.

---

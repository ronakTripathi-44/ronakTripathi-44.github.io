---
layout: post
title: MACHINE LEARNING IMPLEMENTATION IN SMART BUILDING
description: |
  I wanted to undertake the study on machine learning techniques and I ended up designing a comparative evaluation of Agent-Based Modeling (ABM), k-Nearest Neighbors (kNN), and Markov Chains for occupancy prediction and smart building energy optimization. While researching I came across papers like Chen and Jiang et al who implement a GAN (Generative Adverserial Network) model to try and address this challenge by evaluating three modeling approaches that represent different strategies for transforming occupancy data into actionable intelligence. To start somewhere, I chose three predictive learning mechanisms and modelled them in Python. ABM seeks to understand the micro-level behaviors that generate macro-level patterns; kNN leverages historical patterns to predict future states; and Markov Chains model the stochastic nature of occupancy transitions. Together, they offer an option to have strategies and a perspective on what we would call the "whole life cycle" of occupancy information—from data collection through modeling to application.
skills:
  - Machine Learning
  - Agent Based Modelling
  - Object Oriented Programming
  - Smart Building Applications
main-image: /image_5.png
---

## The Energy Challenge in Modern Buildings

Buildings account for nearly 40% of global energy consumption. Despite technological advancement, operational inefficiencies—particularly those related to occupancy misalignment—continue to drive excessive HVAC and lighting loads. 

Accurate occupancy modeling enables adaptive control strategies capable of delivering:

- 15–30% HVAC energy savings  
- 35–75% lighting energy savings

Occupancy modeling represents a critical frontier in this domain. As Wang et al. (2018) demonstrated in their comprehensive review, accurate prediction of building occupancy can lead to energy savings of 15-30% in HVAC systems and 35-75% in lighting systems through adaptive control strategies. These figures are not merely academic; they represent tangible reductions in operational costs and environmental impact that scale across global building stock.

---

## Literature Review

The journey of occupancy modeling parallels the evolution of building automation systems. Early approaches, such as those by Wang et al. (2005), focused on probabilistic models for single-person offices, leveraging exponential distributions to model occupied and vacant intervals. While mathematically elegant, these models struggled with the complex, non-exponential patterns observed in real occupancy data, particularly in multi-occupant environments.

Page et al. (2008) advanced the field with inhomogeneous Markov chain models, introducing the concept of time-dependent transition probabilities to capture the diurnal patterns of occupancy. Their work laid important groundwork but remained limited to binary (presence/absence) states, inadequate for spaces with varying occupancy levels.
Modern Machine Learning Approaches changed by the arrival of sophisticated machine learning techniques has revolutionized occupancy modeling. Chen et al. (2015) extended Markov chain approaches to commercial buildings by defining states as occupancy increments, cleverly reducing computational complexity while maintaining model fidelity. Their work demonstrated that even with simplified state definitions, Markov models could capture essential occupancy dynamics.

The landmark study by Chen and Jiang (2018) introduced Generative Adversarial Networks (GANs) to occupancy modeling, achieving state-of-the-art performance without requiring restrictive assumptions about data distributions. Their work demonstrated the power of neural networks to learn complex, implicit patterns in occupancy data, setting a new benchmark for modeling accuracy.

Parallel developments include the agent-based approaches of Liao et al. (2012), who modeled occupants as autonomous agents with behavior rules, and the queueing theory approach of Jia and Spanos (2017), which conceptualized building occupancy as a queuing system with time-varying parameters.
Ubiquitous Computing and Sensor Networks

The practical implementation of occupancy models depends critically on sensor infrastructure. Tomastik et al. (2008) pioneered video-based occupancy estimation for emergency egress, while Agarwal et al. (2010) demonstrated occupancy-driven energy management in smart buildings. These studies highlighted the symbiotic relationship between modeling sophistication and sensor capability.

Recent advances in Internet of Things (IoT) technology have enabled dense, low-cost sensor networks that provide rich, multi-modal data streams. As noted by Yang et al. (2016) in their comprehensive review, the integration of diverse sensor types—including passive infrared, acoustic, and environmental sensors—has dramatically improved occupancy detection accuracy while reducing privacy concerns associated with video surveillance.
Philosophical Underpinnings are also quite interesting to me, even beyond technical implementation, occupancy modeling raises profound questions about the nature of models and their relationship to reality. George Box’s famous dictum—”All models are wrong, but some are useful”—reminds us that the value of a model lies not in its absolute truth but in its practical utility. This pragmatic perspective guides our comparative approach: we seek not the “correct” model but rather models that prove useful for specific applications. Professor Vervaeke’s concept of “relevance realization” provides a cognitive framework for understanding how building systems might prioritize certain information flows over others. In resource-constrained environments—whether computational or attentional—the ability to focus on relevant patterns represents a critical advantage.

---

## From Raw Data to Actionable Intelligence

Smart buildings generate large volumes of occupancy-related sensor data. However, data alone is insufficient. It must be transformed into:

1. Structured datasets  
2. Predictive models  
3. Deployable control logic  

This study evaluates three complementary modeling philosophies:

- **Agent-Based Modeling (ABM)** → behavioral causality  
- **k-Nearest Neighbors (kNN)** → historical similarity  
- **Markov Chains** → probabilistic temporal transitions  



Recognizing the challenges of obtaining extensive, high-quality real-world occupancy data while protecting occupant privacy, I tried to code a sophisticated synthetic data generation system. My approach builds upon the methodology described by Feng et al. (2015) for occupancy simulation but extends it to incorporate: 
1. Temporal Patterns: Distinct weekday, Saturday, and Sunday patterns with realistic arrival/departure distributions.
2. Individual Variability: Agent-specific schedule preferences and behavioral idiosyncrasies.
3. Stochastic Events: Random meetings, sick days, and atypical occupancy patterns.
4. Sensor Noise: Realistic measurement errors simulating practical sensor limitations.

The data spans 60 days with 15-minute resolution, resulting in 5,760 time slots—sufficient for robust model training and validation while maintaining computational tractability.
![Figure1](/_projects/occupancy_modelling_smart_buildings/image_2.png)

---

## Repository Structure and Reproducibility

The GitHub repository includes complete modeling artifacts for transparency and reproducibility:

### Data Files
- `occupancy_data.csv` → Synthetic time-series occupancy dataset  
- `model_results.csv` → Evaluation metrics for all models  

### Serialized Model Files
- `knn_model.pkl` → Trained kNN regression model  
- `markov_model.pkl` → Trained Markov Chain transition model  

These `.pkl` files allow direct model loading without retraining, enabling:

- Deployment testing  
- Further benchmarking  
- Integration into control pipelines  

All code was implemented in **Python 3.11** with deterministic seeds for reproducibility.


---

## Modeling Approaches

### Agent-Based Modeling (ABM)

Each occupant is modeled as an autonomous agent with:

- Personalized arrival/departure distributions  
- Lunch break preferences  
- Meeting probabilities  
- Stochastic behavioral variation  

ABM captures emergent macro-patterns from micro-rules.


---

### k-Nearest Neighbors (kNN)

Features include:

- Cyclical time encoding (sin/cos)  
- Lagged occupancy states  
- Feature scaling  
- Time-series cross-validation  

kNN achieved the **lowest prediction error**.

Serialized file available:
`knn_model.pkl`


---

### Markov Chain Model

Model characteristics:

- Time-dependent transition matrices  
- Laplace smoothing  
- Optimized state-space definition  
- Multi-step forecasting  

Serialized file available:
`markov_model.pkl`

The Markov model demonstrated exceptional computational efficiency.

![Figure2](/_projects/occupancy_modelling_smart_buildings/output.png)

---

## Model Performance Summary
Our experimental results reveal nuanced performance characteristics across the three modeling approaches (Table 1). The kNN model achieved the lowest NRMSE (0.1424) for mean occupancy profile prediction, demonstrating superior capability in capturing daily occupancy patterns. This aligns with expectations, as kNN excels at pattern recognition in feature-rich datasets.

The Markov Chain model showed particular strength in modeling occupancy transitions, achieving the lowest TVD for time of first arrival (0.1346). This reflects the model’s inherent strength in capturing temporal dependencies and state transitions—a characteristic feature of Markov processes. Interestingly, while the ABM model showed higher error metrics overall, it provided unique insights into occupancy patterns that were not captured by the data-driven approaches. Specifically, the ABM revealed emergent clustering behaviors during arrival periods and more realistic departure patterns that matched qualitative observations of actual office environments.

| Model  | NRMSE | RMSE | MAE | MAPE |
|--------|--------|--------|--------|--------|
| kNN    | 0.1424 | 1.24 | 0.89 | 18.2% |
| Markov | 0.2258 | 1.67 | 1.12 | 22.8% |
| ABM    | 0.3468 | 2.13 | 1.48 | 31.4% |

![Figure3](/_projects/occupancy_modelling_smart_buildings/image_3.png)

Mean Occupancy Profiles

Figure 1 illustrates the mean occupancy profiles predicted by each model compared to ground truth. The kNN model closely follows the ground truth pattern, accurately capturing both the morning arrival ramp-up (8:00-10:00) and the afternoon departure decline (16:00-18:00). The Markov model shows slight phase shifts in peak occupancy timing, while the ABM model exhibits more pronounced deviations, particularly during transitional periods.

Temporal Distribution Patterns

The distribution of first arrival times (Figure 2) reveals distinctive patterns: the Markov model most accurately captures the bimodal distribution observed in ground truth data (peaks at 8:00 and 9:00), reflecting the common pattern of both early and standard arrival times. The kNN model produces a smoother, unimodal distribution, while the ABM shows excessive variability. For last departure times (Figure 3), all models struggle to capture the long tail observed in ground truth data (some occupants remaining until 19:00 or later). This highlights a fundamental challenge in occupancy modeling: rare but important events require specialized handling, whether through outlier-aware algorithms. 


![Figure4](/_projects/occupancy_modelling_smart_buildings/image_3.png)

---

## Computational Efficiency & ROI

| Model  | Training | Prediction | Memory | Interpretability |
|--------|----------|------------|--------|------------------|
| kNN    | Moderate | Fast       | High   | Low              |
| Markov | Very Low | Very Fast  | Low    | Medium           |
| ABM    | None     | Slower     | Medium | High             |

The Markov Chain model demonstrates remarkable efficiency, with minimal training time and rapid predictions. This makes it particularly suitable for edge computing scenarios with limited computational resources. The kNN model, while accurate, requires storing the entire training dataset, creating memory challenges for large-scale deployment.

The ABM, interestingly, requires no traditional “training” phase but involves significant computational overhead during simulation. However, its high interpretability offers compensatory benefits for applications requiring transparent decision-making.

A tiered smart building architecture can be practically recommended:

- Markov → Edge-level control  
- kNN → Server-level forecasting  
- ABM → Strategic simulation  

![Figure8](/_projects/occupancy_modelling_smart_buildings/image_4.png)
---

## Full Dataset and Outputs

Complete outputs are stored in:

- `model_results.csv`
- `occupancy_data.csv`
- Visualizations (`.png` files)

This ensures full reproducibility of the validation framework.

Its interesting to note that no single model excels across all dimensions, suggesting that future systems should adopt hybrid approaches. For instance, kNN could provide accurate baseline predictions, with Markov models handling temporal transitions and ABM simulating scenario analyses. Different models impose different requirements on sensor infrastructure. kNN benefits from rich historical data, Markov models require reliable temporal sequencing, and ABM needs behavioral data for parameter calibration. This suggests that sensor networks should be designed with specific modeling approaches in mind. The varying computational characteristics of different models suggest a tiered architecture: lightweight Markov models at edge devices for real-time prediction, kNN models at local servers for pattern analysis, and ABM simulations at cloud level for scenario planning. The Relevance Realization Challenge

Professor Vervaeke’s concept of “relevance realization” finds concrete expression in our modeling results. Each approach implicitly prioritizes different aspects of occupancy information:

-kNN: Prioritizes pattern similarity, effectively identifying which historical situations most resemble the current context.

-Markov: Prioritizes temporal dependencies, focusing on how current states probabilistically influence future states.

-ABM: Prioritizes causal mechanisms, seeking to understand why occupants behave as they do.

This diversity suggests that truly intelligent building systems might benefit from what cognitive scientists call “complementary learning systems”—multiple representations that together provide more robust understanding than any single approach.

## Practical Deployment Considerations and Limitations

Moving from laboratory models to real-world deployment involves several practical challenges:

Real sensor data contains noise, gaps, and biases absent from our synthetic data. Robust models must handle these imperfections gracefully. Occupancy sensing inevitably raises privacy questions. Our finding that Markov models perform well with relatively coarse data suggests pathways to privacy-preserving implementations.Buildings and their usage patterns evolve over time. Models must adapt to changing occupancy patterns without complete retraining. Occupancy predictions must interface with diverse building systems (HVAC, lighting, security) with different response characteristics and control paradigms.
Limitations and Future Research Directions

The limitations are obvious given the academic nature of my study project but nonetheless, despite being carefully designed, synthetic data cannot capture all nuances of real occupancy patterns. Future work should validate our findings on diverse real-world datasets. Our ABM incorporates relatively simple behavioral rules. More sophisticated cognitive models of occupant behavior could improve accuracy and insight. We focus on occupancy prediction accuracy but do not directly quantify energy savings. Future work should couple occupancy models with building energy simulation to estimate actual energy impacts.

---

## Conclusion

This comprehensive comparative study of building occupancy modeling approaches reveals a landscape rich with complementary strengths and trade-offs. The kNN model emerges as the most accurate for pattern-based prediction, the Markov Chain as the most efficient for temporal modeling, and the ABM as the most insightful for understanding behavioral dynamics. Our findings reinforce George Box’s wisdom: while no model perfectly captures the complexity of real-world occupancy, each proves useful for specific applications. The kNN model’s accuracy makes it valuable for energy optimization systems, the Markov model’s efficiency suits real-time control applications, and the ABM’s interpretability supports human decision-making and scenario planning.

The journey from raw sensor data to actionable intelligence—what Professor Hartmann describes as the transformation of “data” to “information” to “actionable intelligence”—requires careful model selection tailored to specific contexts and objectives. As Professor Vervaeke reminds us, relevance realization is not merely a technical challenge but a cognitive one: we must identify not just what can be modeled, but what should be modeled to support human flourishing in built environments.Looking forward, we envision next-generation building systems that integrate multiple modeling approaches in adaptive frameworks, learning not just occupancy patterns but also which models prove most useful in different contexts. Such systems would embody what might be called “cognitive building intelligence”—the capacity not just to predict but to understand and adapt to the dynamic human environments they serve.

In an era of climate crisis and resource constraints, such intelligent building systems represent not merely technological advancement but ethical imperative. By optimizing energy use while maintaining occupant comfort, they contribute to both environmental sustainability and human well-being—a dual benefit that captures the essential promise of smart building technology.
---

## Implementation Snippets (Jupyter Notebook)

'''python
"""
Complete Building Occupancy Modeling Study - WORKING VERSION
Authors: Based on methodology from Chen & Jiang (2018)
Implementation: Working with ABM, kNN, and Markov Chain models, no GAN model implemented because that is a major project on its own.
Date: 04.02.2026, Berlin
"""

# Building Occupancy Modeling Study - Main Imports
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from datetime import datetime, timedelta
import json
import pickle  # For saving models
import warnings
import os
warnings.filterwarnings('ignore')

# Machine Learning
from sklearn.neighbors import KNeighborsRegressor
from sklearn.model_selection import GridSearchCV, TimeSeriesSplit
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import mean_squared_error, mean_absolute_error

# Statistics
from scipy import stats

# Set paths for saving models
MODEL_DIR = "saved_models"
os.makedirs(MODEL_DIR, exist_ok=True)

np.random.seed(42)
print("✓ Libraries imported")
print(f"✓ Model directory: {MODEL_DIR}")
'''
✓ Libraries imported
✓ Model directory: saved_models



## References

    1. Agarwal, Y., Balaji, B., Gupta, R., Lyles, J., Wei, M., & Weng, T. (2010). Occupancy-driven energy management for smart building automation. Proceedings of the 2nd ACM Workshop on Embedded Sensing Systems for Energy-Efficiency in Building, 1-6.

    2. Box, G. E. P. (1976). Science and statistics. Journal of the American Statistical Association, 71(356), 791-799.

    3. Chen, Z., Xu, J., & Soh, Y. C. (2015). Modeling regular occupancy in commercial buildings using stochastic models. Energy and Buildings, 103, 216-223.

    4. Page, J., Robinson, D., Morel, N., & Scartezzini, J. L. (2008). A generalised stochastic model for the simulation of occupant presence. Energy and Buildings, 40(2), 83-98.

    5. Tomastik, R., Lin, Y., & Banaszuk, A. (2008). Video-based estimation of building occupancy during emergency egress. Proceedings of the 2008 American Control Conference, 894-901.

    6. Vervaeke, J. (2019). Awakening from the Meaning Crisis. Lecture series, Department of Psychology, University of Toronto.

    7. Wang, C., Yan, D., & Jiang, Y. (2011). A novel approach for building occupancy simulation. Building Simulation, 4(2), 149-167.

    8. Yang, J., Santamouris, M., & Lee, S. E. (2016). Review of occupancy sensing systems and occupancy modeling methodologies for the application in institutional buildings. Energy and Buildings, 121, 344-349.

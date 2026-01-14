---
layout: post
title: Evaluating the Reuse of Recycled Asphalt- A Sensitivity Analysis for Circular Economy Integration 
description:  This term project aims to guide decision-makers by developing a risk assessment model that evaluates the reuse of recycled pavement materials under both optimistic and pessimistic degradation scenarios. The model examines key performance indicators such as compressive strength, flexural strength, rutting resistance, fatigue, and cost, with adjustable input variables to reflect different conditions. Through sensitivity analysis, the study assesses the feasibility of reusing degraded materials in new pavements. Ultimately, the project offers a framework to assist decision-makers in conducting risk assessments as we move toward a more sustainable "Era of Reuse." The findings suggest that even in worst-case scenarios, recycled materials retain adequate performance for use in less critical infrastructure, thus contributing to the circular economy.
skills: 
- Risk assessment
- Sensitivity Analysis
- Rstudio programming
- Data visualization

main-image: /stahel_book.png
---
## Project Overview

This term project develops a **risk assessment and sensitivity analysis framework** to evaluate the reuse of recycled asphalt pavements (RAP) within a **circular economy** context.

The model investigates both **optimistic and pessimistic degradation scenarios**, enabling decision-makers to evaluate material performance under uncertainty. Key performance indicators include:

- Compressive strength  
- Flexural strength  
- Rutting resistance  
- Fatigue performance  
- Cost implications  

The findings demonstrate that recycled materials can retain adequate performance for use in **less critical infrastructure**, even under conservative assumptions.

---

## Conceptual Background

![Circular economy framework](/_projects/projectone/stahel_book.png)

This project is conceptually grounded in circular economy principles, emphasizing **material reuse, value retention, and risk-informed decision-making** in civil infrastructure systems.

---

## Methodology

Monte Carlo simulations were conducted using **R** to quantify uncertainty in material properties across different RAP content levels:

- 0% (Virgin material)
- 25% RAP
- 50% RAP
- 75% RAP
- 100% RAP

Each scenario was evaluated using **100,000 simulations**, allowing robust sensitivity analysis of structural performance and economic trade-offs.

---

## Structural Performance Relationships

![Compressive vs Flexural Strength](/_projects/projectone/compressive-vs-flexural.png)

A strong positive correlation was observed between **compressive strength and flexural strength** for both virgin and recycled asphalt mixtures. While recycled mixtures exhibited slightly reduced strength levels, the overall trend suggests that RAPs can meet structural performance requirements, particularly at lower replacement ratios.

---

## Cost–Performance Trade-Offs

![Cost vs Compressive Strength](/_projects/projectone/cost-vs-compressive.png)

Scatterplot analysis revealed increased variability in cost and performance at higher RAP percentages:

- **25% RAP mixtures** showed reliable flexural performance with moderate cost reductions.
- **75% RAP mixtures** exhibited significant variability in cost and lower flexural strength, indicating higher uncertainty.
- **50% and 100% RAP mixtures** retained considerable load-bearing capacity when evaluated against reduced material costs.

These results highlight the **economic advantages of RAP utilization**, while also emphasizing the need for risk-aware material specifications at higher replacement levels.

---

## Sensitivity Analysis

![Sensitivity heatmap](/_projects/projectone/heatmap.png)

The sensitivity heatmap indicates that uncertainty in material performance increases with higher RAP percentages. This reinforces the importance of **risk-based thresholds** when incorporating recycled materials into structural pavement design.

---

## Analysis Workflow

![Pairwise scatterplot workflow](/_projects/projectone/pairwise-scatterplot-workflow.png)

The workflow integrates probabilistic sampling, performance modeling, and visualization to support transparent and reproducible decision-making.

---

## R Implementation

The following R script was used to perform the Monte Carlo simulations and generate the sensitivity analyses:

```r
library(dplyr)
library(ggplot2)

# Load data
data <- read.csv("asphalt_properties.csv")
names(data) <- c("Type", "Property", "Mean", "StdDev")

# Define number of simulations and RAP percentages
num_simulations <- 100000
rap_percentages <- c(0, 25, 50, 75, 100)

# Function to retrieve property values
get_property_values <- function(rap_percentage, property_name) {
  virgin_data <- data %>% filter(Type == "Virgin" & Property == property_name)
  rap_data <- data %>% filter(Type == "RAP" & Property == property_name)

  virgin_mean <- virgin_data$Mean
  virgin_sd <- virgin_data$StdDev
  rap_mean <- rap_data$Mean
  rap_sd <- rap_data$StdDev

  (1 - rap_percentage / 100) * rnorm(num_simulations, virgin_mean, virgin_sd) +
    (rap_percentage / 100) * rnorm(num_simulations, rap_mean, rap_sd)
}

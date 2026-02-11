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

The amount of construction and demolition (C&D) waste is produced during various phases of construction, including the erection, renovation, maintenance, and demolition of buildings, roadways, and bridges. The European Union (EU) alone generates approximately 450 million tonnes (MT) of C&D waste annually, yet only 28% of this waste is recycled, with the remaining 72% ending up in landfills (Bui et al., 2017) 1. This indicates a substantial opportunity for improving recycling practices. C&D waste constitutes a major component of solid waste globally. In the United States, the Environmental Protection Agency (EPA) reported the generation of 484 million metric tonnes of C&D waste in 2014 (USEPA, 2016)2. Similarly, in China, C&D waste represents 30–40% of the total municipal waste, with a recycling rate as low as 5% (Huang et al., 2018)3. In France, the building and public works sector recorded approximately 227.5 MT of C&D waste in 2014 (Mazhoud et al., 2022). 
In India, the Centre for Science and Technology in New Delhi reported 530 million tonnes of C&D waste generated in 2013 (Shiva Bhushan et al., 2019). Conversely, developed countries such as Denmark, the Netherlands, Singapore, and the United States have achieved recycling rates between 70% and 95% for C&D waste (Huang et al., 2018).

This term project develops a risk assessment and sensitivity analysis framework to evaluate the reuse of recycled asphalt pavements (RAP) within a circular economy context.

The model investigates both optimistic and pessimistic degradation scenarios, enabling decision-makers to evaluate material performance under uncertainty. Key performance indicators include:

- Compressive strength  
- Flexural strength  
- Rutting resistance  
- Fatigue performance  
- Cost implications  

The findings demonstrate that recycled materials can retain adequate performance for use in **less critical infrastructure**, even under conservative assumptions.

---

## Conceptual Background

As global infrastructure development continues to surge, the depletion of natural resources and the 
associated environmental impacts are pressing concerns for policymakers. One effective strategy to 
address resource exhaustion is the implementation of circular economy principles, which prioritize the 
reuse and recycling of materials to reduce waste and minimize resource extraction. In the construction 
industry, there is considerable potential in reusing recycled pavement materials, which can significantly 
reduce both environmental and economic costs associated with road construction. However, despite 
these benefits, the reuse of such materials is often underutilized due to uncertainties about their 
performance following degradation. 

<p align="center">
  <img src="/_projects/projectone/stahel_book.png" width="900">
</p>



This study aims to develop a reliable decision-making framework to guide the reuse of recycled 
pavement materials. Currently, the lack of standardized methods for assessing the quality and risks 
associated with degraded materials hinders their broader application. Policymakers and engineers need 
clear, data-driven guidelines to evaluate the performance of these materials across different usage 
scenarios. 



This project is conceptually grounded in circular economy principles, emphasizing **material reuse, value retention, and risk-informed decision-making** in civil infrastructure systems.

---

## Methodology

Asphalt chunks or millings are mixed in an asphalt recycler (or reclaimer) along with some water and 
additives. For hot mix asphalt, the mixture is tumbled and heated for approximately 20 minutes before 
it is ready for use. Cold recycling, on the other hand, avoids the use of heat and saves energy in the 
process (FHWA)
The sensitivity analysis was conducted by varying the percentage of Recycled Asphalt Pavement, 
henceforth referred to as RAPs, used in the pavement materials. The model can simulate both optimistic 
and pessimistic degradation scenarios based on synthetic data. The analysis was done using Rstudio and 
the script can be found with this paper. The model can be easily tested with actual data by plugging it 
into the .csv file. In each scenario, the degradation of performance was assessed by adjusting input 
values for the selected KPIs. These KPIs are critical to understanding the structural integrity, durability, 
and overall cost-effectiveness of the pavement materials. The following indicators were evaluated: 
1. Compressive Strength (MPa): A measure of the pavement material's ability to withstand axial 
loads. 
2. Flexural Strength (MPa): Indicates the material's resistance to bending and cracking under 
stress. 
3. Rutting Resistance (mm): Assesses the material's ability to resist deformation under repeated 
loading. 
4. Fatigue Life (cycles): Measures the number of load cycles the pavement can withstand before 
failure. 
5. Cost (Euros/ton): Evaluates the financial implications of using recycled versus virgin materials. 
Recycled asphalt is assumed to be cheaper than virgin materials but that is subject to geographic 
availability as well. 
Monte Carlo simulations were conducted using R to quantify uncertainty in material properties across different RAP content levels:

- 0% (Virgin material)
- 25% RAP
- 50% RAP
- 75% RAP
- 100% RAP

Each scenario was evaluated using **100,000 simulations**, allowing robust sensitivity analysis of structural performance and economic trade-offs.

Synthetic data was generated to represent various levels of pavement degradation for the analysis.  
However, the properties for Virgin Asphalt are taken from literature9. Key performance indicators, 
including compressive strength, flexural strength, rutting resistance, and fatigue life, were adjusted over 
multiple iterations to simulate both optimistic and pessimistic degradation scenarios. The simulation 
was conducted over 1,000 and 10,000 iterations; however, for clarity in the visual representation, results 
from the 1,000-iteration set were presented. Primarily because they are visually appealing and the cost 
of computation is not too high. 
The sensitivity analysis was carried out by incrementally adjusting the percentage of recycled asphalt 
pavements (RAPs) in the material mix, from low (25%) to high (100%) usage levels. For each scenario, 
the model recalculated the pavement material's performance based on the selected KPIs. In addition to 
performance metrics, cost was factored into the analysis to evaluate the economic feasibility of RAP 
usage relative to virgin materials. 


---

## Structural Performance Relationships

To effectively present the results, various visualization techniques were proposed to ensure that each 
option could be thoroughly considered. Utilizing the full range of visualization tools available in 
RStudio, I developed multiple versions of data presentation to appeal to policymakers. The goal was to 
generate visually compelling representations of the data, enabling decision-makers to easily interpret 
the findings and make informed choices. By presenting the analysis through different visual formats—
such as line graphs, bar charts, radar charts, and heatmaps—each key performance indicator (KPI) is 
highlighted in a manner that underscores the relationship between the degradation of recycled asphalt 
pavements (RAPs) and their reuse potential. This approach allows for the selection of the most effective visualization method depending on the 
audience's needs, ensuring that the data remains accessible and informative. Offering various 
visualization formats provides flexibility in presentation style, facilitating the optimum choice of visuals 
to support the decision-making process, particularly in the context of promoting circular economy 
practices. The histograms for each variable of the simulation can be found in the Appendix.

<p align="center">
  <img src="/_projects/projectone/compressive-vs-flexural.png" width="900">
</p>


A strong positive correlation was observed between **compressive strength and flexural strength** for both virgin and recycled asphalt mixtures. While recycled mixtures exhibited slightly reduced strength levels, the overall trend suggests that RAPs can meet structural performance requirements, particularly at lower replacement ratios.

---

## Cost–Performance Trade-Offs

<p align="center">
  <img src="/_projects/projectone/cost-vs-compressive.png" width="900">
</p>


Scatterplot analysis revealed increased variability in cost and performance at higher RAP percentages:

- **25% RAP mixtures** showed reliable flexural performance with moderate cost reductions.
- **75% RAP mixtures** exhibited significant variability in cost and lower flexural strength, indicating higher uncertainty.
- **50% and 100% RAP mixtures** retained considerable load-bearing capacity when evaluated against reduced material costs.

These results highlight the **economic advantages of RAP utilization**, while also emphasizing the need for risk-aware material specifications at higher replacement levels.

---

## Sensitivity Analysis

<p align="center">
  <img src="/_projects/projectone/heatmap.png" width="900">
</p>



The sensitivity heatmap indicates that uncertainty in material performance increases with higher RAP percentages. This reinforces the importance of **risk-based thresholds** when incorporating recycled materials into structural pavement design.

---

## Scatterplot matrix
This scatterplot matrix highlights the complex interactions between material properties in 
asphalt mixtures with varying RAP percentages. As RAP content increases, there is a general decrease 
in both compressive and flexural strength, accompanied by improved rutting resistance and a modest 
rise in cost. However, high RAP levels introduce significant variability in performance, making lower 
RAP percentages more predictable and reliable for certain applications. These findings suggest that 
while RAP offers economic and environmental benefits, its impact on material performance, 
particularly in terms of strength, should be carefully considered in pavement design decisions

<p align="center">
  <img src="/_projects/projectone/pairwise-scatterplot-workflow.png" width="900">
</p>

- Increasing RAP percentages (especially beyond 50%) lead to greater 
performance variability, particularly in terms of rutting resistance and flexural strength.
-The 25% RAP mixtures appear to offer the most consistent 
performance, striking a balance between strength, rutting resistance, and cost.
-Higher RAP percentages (75% and 100%) show increased variability 
in compressive strength and rutting resistance, indicating trade-offs in predictability when 
maximizing recycled content.
-50% RAP offers a balance between cost savings and acceptable 
performance, making it an especially viable choice.
-The negative correlation between cost and rutting resistance demonstrates that high 
RAP content can support circular economy goals by reducing costs and resource usage, 
especially in less demanding applications. 

---
## Discussion
The focus of this term project was the demonstration of the potential for reintegrating recycled materials 
into pavement construction without substantial loss of quality, but that is an illustration and the same 
tool can be used for other decisions that involve material degradation. The findings align closely with 
the objectives of the circular economy by emphasizing the reduction in the demand for virgin materials, 
conservation of natural resources, and minimization of waste. Notably, even under pessimistic 
degradation scenarios, recycled pavement materials exhibited a capacity to retain their structural 
integrity, particularly for use in non-essential applications. This research provides decision-makers with 
a data-driven foundation for approving the reuse of RAPs, reinforcing the idea that sustainability and 
functionality can coexist in infrastructure development. 
Despite the encouraging findings, several limitations warrant consideration for future research 
endeavors. The reliance on synthetic data in the sensitivity analysis, while beneficial for establishing 
controlled models, does not capture the real-world variability that can arise from factors such as 
environmental conditions, traffic patterns, and maintenance practices. 
Finally, this study primarily focused on short-term performance indicators, expanding the scope of 
performance indicators to encompass thermal properties, moisture sensitivity, and other long-term 
factors will yield a more comprehensive understanding of the material's behavior over time. Risk 
assessment models can often be supported by conducting a techno-economic analysis (TEA) to evaluate 
the economic viability of RAPs, alongside a life cycle assessment (LCA), would be key in providing a 
holistic view of the sustainability of recycled materials10. Additionally, employing a fuzzy Delphi 
analysis could further enhance the robustness of the research, ensuring a well-rounded examination of 
the implications of using RAPs in construction practices.

---
## Conclusion

The strong positive correlation observed between compressive strength and flexural strength across 
both virgin and recycled asphalt mixtures highlights the potential for RAPs to meet structural 
performance requirements, albeit at slightly reduced levels compared to virgin materials. Meanwhile, 
some scatterplots showed variability in cost and performance, particularly for higher RAP percentages. 
Although RAP inclusion typically results in cost savings in real-world applications, the observed dataset 
trends might reflect localized production complexities or specific project conditions. 
Notably, the scatterplot distribution for 75% RAP indicated high variability in cost incurred, while the 
flexural strength was significantly lower than that of mixtures with 25% RAP, which were more reliable 
as a result. Additionally, a comparison of performance across 50% and 100% RAP revealed that even 
at higher RAP percentages, load-bearing capacity remained considerably high, particularly when 
balanced against the reduced material costs. This reinforces the practical advantages of RAP utilization, 
but it also highlights the potential for performance variability at higher percentages. 
The findings underscore the potential of RAPs to contribute to a circular economy within the 
construction sector. In conclusion, this research provides a solid foundation for policymakers and 
engineers to consider reuse and repurposing of C&D products after evaluating the risk using such data driven models. The study's results, bolstered by both sensitivity analysis and scatterplot interpretation, 
advocate for the adoption of circular economy practices in the industry. Th strongly supports the idea 
that materials in their ‘Era of R’ or ‘Era of D’ can play a valuable role in sustainable infrastructure 
development, ensuring both economic and environmental benefits in the long term.

## R Implementation

The following R script was used to perform the Monte Carlo simulations and generate the sensitivity analyses:

```
# CIRCULAR ECONOMY TERM PROJECT
# RISK ASSESSMENT WITH RECYCLED ASHPHALT PAVEMENTS OR RAP

# Load necessary libraries
library(dplyr)
library(ggplot2)

# Load data
data <- read.csv("asphalt_properties.csv")
names(data) <- c("Type", "Property", "Mean", "StdDev")

# Define number of simulations and RAP percentages
num_simulations <- 100000
rap_percentages <- c(0, 25, 50, 75, 100)

# Function to get property values
get_property_values <- function(rap_percentage, property_name) {
  virgin_data <- data %>% filter(Type == "Virgin" & Property == property_name)
  rap_data <- data %>% filter(Type == "RAP" & Property == property_name)
  
  virgin_mean <- virgin_data$Mean
  virgin_stddev <- virgin_data$StdDev
  rap_mean <- rap_data$Mean
  rap_stddev <- rap_data$StdDev
  
  combined_mean <- (1 - rap_percentage / 100) * virgin_mean + (rap_percentage / 100) * rap_mean
  combined_stddev <- sqrt((1 - rap_percentage / 100)^2 * virgin_stddev^2 + (rap_percentage / 100)^2 * rap_stddev^2)
  
  rnorm(num_simulations, mean = combined_mean, sd = combined_stddev)
}

# Run simulations and store results
results <- list()
for (rap_percentage in rap_percentages) {
  compressive_strength <- get_property_values(rap_percentage, "Compressive Strength")
  flexural_strength <- get_property_values(rap_percentage, "Flexural Strength")
  rutting_resistance <- get_property_values(rap_percentage, "Rutting Resistance")
  fatigue_life <- get_property_values(rap_percentage, "Fatigue Life")
  cost <- get_property_values(rap_percentage, "Cost")
  
  results[[as.character(rap_percentage)]] <- data.frame(
    Compressive_Strength = compressive_strength,
    Flexural_Strength = flexural_strength,
    Rutting_Resistance = rutting_resistance,
    Fatigue_Life = fatigue_life,
    Cost = cost
  )
}

# Analysis function
analyze_results <- function(results) {
  analysis <- lapply(results, function(data) {
    sapply(data, function(property) {
      list(
        mean = mean(property),
        stddev = sd(property),
        percentile_5th = quantile(property, 0.05),
        percentile_95th = quantile(property, 0.95)
      )
    })
  })
  return(analysis)
}

# Risk assessment function
assess_risk <- function(analysis) {
  risk_results <- list()
  
  for (rap_percentage in names(analysis)) {
    risk_data <- analysis[[rap_percentage]]
    
    risk_summary <- sapply(risk_data, function(property) {
      if (is.list(property)) {  # Check if property is a list
        mean_value <- property$mean
        std_dev <- property$stddev
        percentile_5th <- property$percentile_5th
        percentile_95th <- property$percentile_95th
        
        thresholds <- c(Compressive_Strength = 300, 
                        Flexural_Strength = 200, 
                        Rutting_Resistance = 150, 
                        Fatigue_Life = 5000, 
                        Cost = 100)
        
        risk_assessment <- ifelse(mean_value < thresholds[names(thresholds) == names(property)], 
                                  "Risky", "Acceptable")
        
        return(c(Mean = mean_value, StdDev = std_dev, 
                 Percentile_5th = percentile_5th, Percentile_95th = percentile_95th, 
                 Risk = risk_assessment))
      } else {
        return(c(Mean = NA, StdDev = NA, Percentile_5th = NA, Percentile_95th = NA, Risk = "Data Missing"))
      }
    }, simplify = "data.frame")
    
    risk_results[[rap_percentage]] <- risk_summary
  }
  
  return(risk_results)
}

# Perform analysis
analysis <- analyze_results(results)

# Run risk assessment
risk_assessment_results <- assess_risk(analysis)


#modified function

assess_risk <- function(analysis) {
  risk_results <- lapply(analysis, function(property_analysis) {
    # Check if property_analysis is not empty
    if (length(property_analysis) == 0) {
      return(data.frame(Risk = "Data Missing"))
    }
    
    sapply(property_analysis, function(property) {
      if (is.null(property)) {
        return(c(Mean = NA, StdDev = NA, Percentile_5th = NA, Percentile_95th = NA, Risk = "Data Missing"))
      }
      
      return(c(
        Mean = property$mean,
        StdDev = property$stddev,
        Percentile_5th = property$percentile_5th,
        Percentile_95th = property$percentile_95th,
        Risk = ifelse(property$mean < threshold, "Risky", "Acceptable")
      ))
    })
  })
  return(risk_results)
}

print(analysis)


# Plotting results for visualization

plot_histograms <- function(results) {
  for (rap_percentage in names(results)) {
    data <- results[[rap_percentage]]
    
    # Create a new plot for each property
    par(mfrow = c(3, 2))  # Adjust layout for 5 properties
    
    hist(data$Compressive_Strength, main = paste("Compressive Strength at", rap_percentage, "% RAP"), xlab = " Compressive Strength (MPa)", breaks = 30, col = "lightblue")
    hist(data$Flexural_Strength, main = paste("Flexural Strength at", rap_percentage, "% RAP"), xlab = "Flexural Strength (MPa)", breaks = 30, col = "lightgreen")
    hist(data$Rutting_Resistance, main = paste("Rutting Resistance at", rap_percentage, "% RAP"), xlab = "Rutting Resistance (mm)", breaks = 30, col = "lightcoral")
    hist(data$Fatigue_Life, main = paste("Fatigue Life at", rap_percentage, "% RAP"), xlab = "Fatigue Life (cycles)", breaks = 30, col = "lightyellow")
    hist(data$Cost, main = paste("Cost at", rap_percentage, "% RAP"), xlab = "Cost ($/ton)", breaks = 30, col = "lightgray")
    
    # Pause to view the plots
    readline(prompt = "Press [Enter] to continue...")
  }
}

# After running the simulations and storing results
plot_histograms(results)




# Assuming 'results' is the output from your simulation
# Convert 'results' into a single data frame for easy plotting
plot_data <- do.call(rbind, lapply(names(results), function(x) {
  results[[x]] %>% mutate(RAP_Percentage = as.numeric(x))
}))

# Plot histograms for each property, using facet wrapping for RAP percentages
plot_histograms <- function(plot_data) {
  
  # Compressive Strength Plot
  ggplot(plot_data, aes(x = Compressive_Strength)) +
    geom_histogram(binwidth = 10, fill = "lightblue", color = "black") +
    facet_wrap(~ RAP_Percentage, nrow = 2) +
    theme_minimal() +
    labs(title = "Compressive Strength Distribution for Various RAP Percentages",
         x = "Compressive Strength (MPa)", y = "Frequency") +
    theme(plot.title = element_text(hjust = 0.5))
  
  # Flexural Strength Plot
  ggplot(plot_data, aes(x = Flexural_Strength)) +
    geom_histogram(binwidth = 10, fill = "lightgreen", color = "black") +
    facet_wrap(~ RAP_Percentage, nrow = 2) +
    theme_minimal() +
    labs(title = "Flexural Strength Distribution for Various RAP Percentages",
         x = "Flexural Strength (MPa)", y = "Frequency") +
    theme(plot.title = element_text(hjust = 0.5))
  
  # Rutting Resistance Plot
  ggplot(plot_data, aes(x = Rutting_Resistance)) +
    geom_histogram(binwidth = 5, fill = "lightcoral", color = "black") +
    facet_wrap(~ RAP_Percentage, nrow = 2) +
    theme_minimal() +
    labs(title = "Rutting Resistance Distribution for Various RAP Percentages",
         x = "Rutting Resistance (mm)", y = "Frequency") +
    theme(plot.title = element_text(hjust = 0.5))
  
  # Fatigue Life Plot
  ggplot(plot_data, aes(x = Fatigue_Life)) +
    geom_histogram(binwidth = 100, fill = "lightyellow", color = "black") +
    facet_wrap(~ RAP_Percentage, nrow = 2) +
    theme_minimal() +
    labs(title = "Fatigue Life Distribution for Various RAP Percentages",
         x = "Fatigue Life (cycles)", y = "Frequency") +
    theme(plot.title = element_text(hjust = 0.5))
  
  # Cost Plot
  ggplot(plot_data, aes(x = Cost)) +
    geom_histogram(binwidth = 10, fill = "lightgray", color = "black") +
    facet_wrap(~ RAP_Percentage, nrow = 2) +
    theme_minimal() +
    labs(title = "Cost Distribution for Various RAP Percentages",
         x = "Cost ($/ton)", y = "Frequency") +
    theme(plot.title = element_text(hjust = 0.5))
}

# Call the function to plot histograms
plot_histograms(plot_data)


# Convert 'results' into a single data frame for easy plotting
plot_data <- do.call(rbind, lapply(names(results), function(x) {
  results[[x]] %>% mutate(RAP_Percentage = as.numeric(x))
}))

# Scatterplot function to compare properties across RAP percentages
plot_scatterplots <- function(plot_data) {
  
  # Scatterplot: Compressive Strength vs Flexural Strength
  ggplot(plot_data, aes(x = Compressive_Strength, y = Flexural_Strength, color = as.factor(RAP_Percentage))) +
    geom_point(alpha = 0.7) +
    scale_color_brewer(palette = "Set1", name = "RAP Percentage") +
    theme_minimal() +
    labs(title = "Compressive Strength vs Flexural Strength",
         x = "Compressive Strength", y = "Flexural Strength") +
    theme(plot.title = element_text(hjust = 0.5))
  
  # Scatterplot: Rutting Resistance vs Fatigue Life
  ggplot(plot_data, aes(x = Rutting_Resistance, y = Fatigue_Life, color = as.factor(RAP_Percentage))) +
    geom_point(alpha = 0.7) +
    scale_color_brewer(palette = "Set2", name = "RAP Percentage") +
    theme_minimal() +
    labs(title = "Rutting Resistance vs Fatigue Life",
         x = "Rutting Resistance", y = "Fatigue Life") +
    theme(plot.title = element_text(hjust = 0.5))
  
  # Scatterplot: Cost vs Compressive Strength
  ggplot(plot_data, aes(x = Cost, y = Compressive_Strength, color = as.factor(RAP_Percentage))) +
    geom_point(alpha = 0.7) +
    scale_color_brewer(palette = "Set3", name = "RAP Percentage") +
    theme_minimal() +
    labs(title = "Cost vs Compressive Strength",
         x = "Cost", y = "Compressive Strength") +
    theme(plot.title = element_text(hjust = 0.5))
}

# Call the function to plot scatterplots
plot_scatterplots(plot_data)

```

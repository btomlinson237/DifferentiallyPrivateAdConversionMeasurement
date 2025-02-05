# Differentially Private Ad Conversion Measurement Prototype

This repository contains a prototype that demonstrates a differentially private ad conversion measurement system inspired by the study:

> **Differentially Private Ad Conversion Measurement**  
> John Delaney, Badih Ghazi, Charlie Harrison, Christina Ilvento, Ravi Kumar, Pasin Manurangsi, Martin Pál, Karthik Prabhakar, Mariana Raykova  
> *Proceedings on Privacy Enhancing Technologies 2024*

The prototype implements a simplified simulation of ad impressions and conversions and showcases several core concepts:
- **Ad Conversion Measurement:** Simulating ad impressions and conversions for users across publishers.
- **Attribution Rules:** Implementing multiple rules (Last-Touch, First-Touch, Uniform, Exponential Decay, and U-Shaped) to assign conversion credit.
- **Contribution Bounding:** Enforcing a simplified contribution bound to limit the impact of any single user.
- **Differential Privacy:** Adding Laplace noise (calibrated with a privacy parameter \(\epsilon\)) to aggregated conversion counts to ensure privacy.

## Overview

This notebook prototype is designed to illustrate how one can simulate and evaluate ad conversion measurement systems under differential privacy constraints. The core steps include:

1. **Simulating Ad Impressions and Conversions:**  
   - Generate a synthetic dataset where users view ad impressions (each associated with a publisher and an advertiser) and, with some probability, convert after their last impression.
   
2. **Attribution Rules:**  
   - Implement several attribution methods to assign conversion credit to impressions:
     - **Last-Touch Attribution (LTA):** Full credit to the last impression.
     - **First-Touch Attribution (FTA):** Full credit to the first impression.
     - **Uniform Attribution (UNI):** Equal credit to all impressions.
     - **Exponential Decay (EXP):** Credit decays with the time difference between the impression and the conversion.
     - **U-Shaped Attribution (U-S):** For 3+ impressions, first and last get 40% each and intermediates share the remaining 20%.
   
3. **Contribution Bounding Enforcement:**  
   - Limit the total contribution per (user, publisher) pair to control sensitivity.
   
4. **Aggregating Conversion Attributions:**  
   - For each conversion event, attribute the conversion using the impressions of that user and aggregate the weights by publisher.
   
5. **Adding Differential Privacy:**  
   - Apply the Laplace mechanism to the aggregated conversion counts, ensuring the published metrics preserve user privacy.
   
6. **Visualization:**  
   - Compare the true aggregated conversion attributions with the differentially private estimates using bar charts.
   
7. **Conclusion and Future Directions:**  
   - Summarize the prototype and discuss potential extensions for further research or real-world applications.

How to Run
Clone or Download the Repository:
Ensure you have the notebook file (e.g., diffPrivacyEcommercePrototype.ipynb).

Open the Notebook:
Use Jupyter Notebook or JupyterLab to open the notebook.

Execute the Notebook Cells:
Run the cells sequentially. The notebook will:

- Simulate ad impressions and conversions.
- Apply various attribution rules.
- Enforce contribution bounding.
- Add Laplace noise for differential privacy.
- Visualize the results.

Dataset
- No external dataset is required for this prototype as all data is simulated within the notebook. However, the concepts demonstrated here are inspired by real-world ad conversion measurement scenarios. I would be interested in applying this implementation with real-world data.

Future Directions
Possible extensions for this prototype include:

- Implementing additional or more sophisticated attribution rules.
- Enhancing the contribution bounding mechanism (e.g., applying bounds pre-attribution).
- Experimenting with alternative differential privacy mechanisms (such as Gaussian noise).
- Applying these methods to real ad conversion datasets for further evaluation.


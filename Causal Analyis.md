# Milestone 3: Causal Inference and Heatmap Correlation Analysis

## Heatmap Correlation Analysis

We started by exploring the **linear correlations** between key performance indicators (KPIs) using a heatmap.

### Correlation Heatmap:



### Key Observations:
- **Departure Delay** and **Arrival Delay** show a **strong positive correlation (0.96)**, which is expected.
- **Flight Delays** show a **weak negative correlation** with **Satisfaction Score** (-0.05), hinting at dissatisfaction with longer delays.
- **Seat Comfort**, **Inflight Service**, and **Check-in Service** have **moderate positive correlations** with **Satisfaction Score**, suggesting service quality plays a vital role.
- **Baggage Handling** shows **positive correlation** but with weaker strength.

##Causal Inference Analysis

We applied the **DoWhy** causal inference framework to model the causal effect of **Flight Delays** on **Passenger Satisfaction**, accounting for service quality as mediators.

### Assumed Causal Structure



This Directed Acyclic Graph (DAG) assumes:

- **Flight Delays** affect **Satisfaction** both **directly** and **indirectly** through:
  - **Seat Comfort**
  - **Inflight Service**
- **Check-in Service** and **Baggage Handling** also influence satisfaction independently or through interaction.

---

###  Potential Confounders

We identified possible **confounding variables** that can bias causal estimation if not controlled:

- **Flight Class** (e.g., Economy vs. Business)
- **Customer Type** (e.g., Loyal vs. Disloyal)
- **Type of Travel** (e.g., Personal vs. Business)
- **Demographics** (e.g., Age, Gender)

These variables may affect both delay likelihood and satisfaction and should ideally be controlled.

## Causal Estimation Results

We estimated the **Average Treatment Effect (ATE)** of **Flight Delays** on **Satisfaction Score** using the **backdoor linear regression method**.

### Findings:
- The **causal effect is negative** — as flight delays **increase**, satisfaction scores **decrease**.
- The effect remains **significant** even after accounting for mediators like **Seat Comfort** and **Inflight Service**.

## Key Takeaways

- Heatmap showed weak negative correlation, but **causal analysis confirmed**:  
  **Flight Delays directly and indirectly reduce passenger satisfaction**.
- **Service improvements** (e.g., better seating, inflight experience) can help **offset dissatisfaction** caused by delays.
- A data-driven causal approach helps **prioritize improvements** to maintain satisfaction during disruptions.

> This insight empowers airlines to focus both on operational punctuality and service quality to maximize passenger experience.


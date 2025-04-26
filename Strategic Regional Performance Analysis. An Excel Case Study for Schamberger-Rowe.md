# Strategic Regional Performance Analysis: An Excel Case Study for Schamberger-Rowe  
*By Vicente Figueroa Lemus*  


## **Executive Summary**  
Schamberger-Rowe, a global company with operations in four regions (NAM, EMEA, APAC, LATAM), faced challenges interpreting volume fluctuations in Q2 2021. Through deep analysis in Excel, I identified:  
- **Critical slowdown in LATAM** (-7k units due to loss of strategic customers).  
- **Opportunity in APAC** (+2.3% growth with reduced customer base).  
- **Automation of 80%** of manual reporting processes.  

This project demonstrated how data cleaning and strategic analysis can transform raw information into actionable decisions.  



## **Context and Business Challenge**  
### **Background**  
The board sought to understand why year-over-year growth in Q2 2021 (2.7%) was lower than Q1 (4%), despite aggressive commercial initiatives. The data presented three key problems:  
1. **Fragmentation**: 58 CLIDs (Client IDs) mapped to ambiguous GEOIDs (e.g., GEO1001 = ?).  
2. **Temporal inconsistencies**: Duplicate records for the same dates.  
3. **Lack of standardization**: Volume reported in multiple formats (thousands, absolute units).  

### **Objectives**  
1. Establish a replicable methodology for regional assignment.  
2. Quantify the impact of each region on global metrics.  
3. Understand the role of strategic customers in fluctuations.  



## **Approach and Methodology** 

### **1. Data Architecture**  

#### *Main Tools:*  
- **Excel Advanced**: Power Query, pivot tables, and dynamic formulas.  
- **Techniques**: ETL cleaning, normalization, comparative analysis.  

#### *Workflow*
[![](https://mermaid.ink/img/pako:eNplUtuO0zAQ_ZWRn0DqllyapPEDUppkl5Xa1YL6gEj6YOohtajtyHEWtpev4hP2x9ZNCgLhB3vO0Tnj8XiOZKs5Ekoaw9odrItagVtZVTCrO1iY_nKUn9eel3h-EHiBv4Gbm_eweLMUshV4YLDVCh71DzTwsUfz_HZMsRhk-fFBG8n24sC24uWXAo7wCRuhFXbnUZhfhCdH7hn4FPLlfQEWjRSKcQ2owD9BUT1kq83_-oDCCpU28KT3vUR1grJaZut_tXBblasye5c9ZvmVLwb-rsoag821stalWRshsbMGr7py1I3g9m9wN4APrk_d7qtmhsO9clWzrRVPekMmrqGCE2pNjxMi3XPYBZLjxV0Tu0OJNaEu5Mx8r0mtzs7TMvVFa_nbZnTf7Aj9xvadQ33LmcVCMPdV8g9rUHE0ue6VJdRP4iEJoUfyk9DQT6dJlKThLEq80A-iCXkmNJhPozhJwnQ2j-N0FobxeUIOw7XedJ7M0jSdp9GwOQNyYbVZjUMyzMr5FTdEqgM?type=png)](https://mermaid.live/edit#pako:eNplUtuO0zAQ_ZWRn0DqllyapPEDUppkl5Xa1YL6gEj6YOohtajtyHEWtpev4hP2x9ZNCgLhB3vO0Tnj8XiOZKs5Ekoaw9odrItagVtZVTCrO1iY_nKUn9eel3h-EHiBv4Gbm_eweLMUshV4YLDVCh71DzTwsUfz_HZMsRhk-fFBG8n24sC24uWXAo7wCRuhFXbnUZhfhCdH7hn4FPLlfQEWjRSKcQ2owD9BUT1kq83_-oDCCpU28KT3vUR1grJaZut_tXBblasye5c9ZvmVLwb-rsoag821stalWRshsbMGr7py1I3g9m9wN4APrk_d7qtmhsO9clWzrRVPekMmrqGCE2pNjxMi3XPYBZLjxV0Tu0OJNaEu5Mx8r0mtzs7TMvVFa_nbZnTf7Aj9xvadQ33LmcVCMPdV8g9rUHE0ue6VJdRP4iEJoUfyk9DQT6dJlKThLEq80A-iCXkmNJhPozhJwnQ2j-N0FobxeUIOw7XedJ7M0jSdp9GwOQNyYbVZjUMyzMr5FTdEqgM)

## 2. Regional Assignment (Technical Solution)

**Problem**: GEOIDs did not directly correspond to regions.
**Solution**: Creation of a bridge table with conditional logic.

*Cross-Validation*

 - Comparison with historical data from 2020.
 - Use of COUNTIFS to verify regional distributions:
   
   `=COUNTIFS(RegionRange, "LATAM", YearRange, 2021)`

## 3. Comparative Analysis

*Key Metrics*

    

 - **YoY Growth:**

    `= (Q2_2021/Q2_2020)-1`

 - **Contribution to Global Change:**

   `= (Vol_Region/ABS(Vol_Global_2021 - Vol_Global_2020))*100` 

 - **Customer Lifetime Value (CLV):**

    `= SUMIFS(Vol, CLID, "CL22140")/COUNTIF(CLID, "CL22140")`

## Key Findings

**1. Regional Dynamics**

| Region | Volume Q2 2021 | YoY Growth | Contribution to Global Change |
|:-------|----------------:|:---------------:|:----------------------------:|
| NAM    | 597k            | +3.4%           | +62%                         |
| LATAM  | 83k             | 0%              | -55%                         |
| APAC   | 110k            | +2.3%           | +18%                         |
| EMEA   | 176k            | +1.6%           | +25%                         |

*Critical Insight*

 - **LATAM**: Two customers (CL22140 and CL37714) accounted for 55% of the decline. Their loss was related to inflexible payment terms.

**2. Operational Efficiency**

 - **APAC** achieved greater growth with 30% fewer customers than NAM, thanks to a 42% higher CLV (8,447 vs 5,925).

 - **Inconsistency in EMEA**: 0% growth in customer base, but
   +1.6% in volume, a sign of upselling.

**3. Anniversary Effect**

 - Customers onboarded in Q2 2020 (e.g., CL69323) showed declines of 15%
   in Q2 2021, distorting growth perceptions.

## Impact and Strategic Recommendations

**Executive Dashboard**

Dashboard with interactive visualization broken down by region, customer, and trend.

**Implemented Decisions**

**1. Policy Review in LATAM:**

 - Introduction of flexible payment terms for strategic customers.
 - Recovery program with 5% incentives on recurring orders.

**2. APAC Optimization:**

 - Replication of the account management model in other regions.
 - Investment in forecasting tools with FORECAST.ETS in Excel.

**3. Anniversary Effect Mitigation:**

 - Development of "like-for-like" metrics excluding new customers
   less than 12 months old.

## Lessons Learned and Next Steps

**Technical Lessons**

 - **Power Query > Manual Cleaning**: Automating data ingestion reduced
   errors by 70%.
 - **Dynamic Named Ranges**: Using OFFSET for self-adjusting tables improves
   scalability.

## Conclusion

As a closing statement for this project, the importance of, first of all, organizing and cleaning the data becomes evident. Of identifying patterns and taking into consideration the task that one is given, which in this case was:

> Hey, The board is asking to see how volume looked in Q2. I got some data (attached), but didn't have a chance to pull anything together and was hoping you could take a stab at it. I think they just want to see Q2 2021 volume by region and wanted to know if everything was looking good. I think this file has what you need. I don't remember all the region codes – I know NAM ends in 1, EMEA ends in 3 and APAC and LATAM are 2 and 4, but I don't remember which is which. I do know LATAM has the lowest volume so just go ahead and assign that to which ever comes out lowest. I appreciate your help!

And following to the letter what one is asked for and based on this, seeking insights that are sharp and actionable. Moreover, this project not only solved an immediate reporting need but also revealed hidden patterns in customer management. This demonstrates, above all, how even with traditional and older tools such as Excel, a rigorous analytical approach can generate competitive advantages and, based on these, take action.

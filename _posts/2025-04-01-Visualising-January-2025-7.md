---
layout: post
title: UoE - Visualising Data January 2025 - Dashboard Design
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, assignment, Module E-Portfolio Learning Activities]
---
---
## Wekly Performance by Persona Tag in Ride-Hailing Company
---
### Introduction

In Vietnam’s fast-growing ride-hailing market, user behavior is constantly evolving. To sustain growth and improve decision-making, companies must deeply understand their customers and continuously monitor operational metrics. Our company, which offers both Bike and Car services nationwide, has invested in a segmentation-based performance dashboard to track weekly user activity and support strategic initiatives across business units.
This report outlines the purpose, design methodology, and key components of the dashboard we developed to evaluate user segmentation performance. Designed for use by both business and technical stakeholders, this dashboard plays a vital role in transforming complex user data into actionable insights. 

### Dashboard Design Method

The dashboard was developed using Tableau, a leading data visualization tool chosen for its flexibility, interactivity, and scalability. Tableau enables our team to create a centralized platform where performance metrics can be viewed and explored from multiple dimensions, allowing various departments such as marketing, operations, and product to use the same data but extract insights relevant to their needs.
Our primary goal was to create a dashboard that is not only visually intuitive but also capable of delivering granular insights on user segmentation. It supports weekly updates, enabling near real-time monitoring of behavioral trends and revenue performance.

### Dashboard Information

#### 1.	Overall Dashboard Concept

The core purpose of the dashboard is to serve as a performance monitoring and behavioral diagnostic tool for internal teams. The intended audience includes:
-	Marketing teams, who need to understand user personas and spending levels to design targeted promotions.
-	Operations teams, who require insights into service usage patterns to optimize supply-demand balance.
-	Product managers, who monitor user engagement and retention metrics for feature development.
-	Business leaders, who seek high-level overviews of segment performance and revenue trends.
By consolidating performance data into a single view with interactive filters, the dashboard supports cross-functional collaboration and fast decision-making.

#### 2.	Dashboard Details

The dashboard offers several key features and components that allow users to explore and analyze performance data by week, city, service type, and user characteristics.

![image](/assets/images/banners/V5-1.png)

##### 2.1. Filters
A set of global filters enables users to narrow down data according to:
-	City: View performance in specific locations
-	Service Type: Bike or Car
-	Week of Performance: Allows time-based trend analysis
-	User Segment: Retain (active users) or Churn (inactive users)
-	Persona: Office Worker, Student, Shopertainer, On-demand User
-	Spending Level: From Level 1 (highest spenders) to Level 5 (lowest)
These filters are essential for comparative analysis and micro-targeting, helping teams to answer specific business questions quickly.

![image](/assets/images/banners/V5-2.png)

##### 2.2. Overall Performance Summary
This section presents a table of key metrics, including:
-	Active Riders: Users with at least one trip during the selected week
-	Trips: Total rides completed
-	Gross Merchandise Value (GMV): Total revenue generated
-	Requests: Total service requests, regardless of fulfillment
This summary gives a high-level snapshot of weekly performance and enables week-to-week comparisons.

![image](/assets/images/banners/V5-3.png)

##### 2.3. Trendline Analysis by Persona
Using a set of line charts, this section visualizes the progression of each metric by persona type over time. It helps stakeholders detect seasonal shifts, emerging trends, or sudden changes in user behavior.
For example, a drop in GMV among Shopertainers might signal reduced mall traffic, while a spike in On-demand users may indicate a short-term campaign’s success.

![image](/assets/images/banners/V5-4.png)

##### 2.4. Spending Level Distribution
A bar chart illustrates the distribution of users across spending levels within each persona group. This view provides insight into:
-	Which personas contribute the most revenue.
-	Where upselling opportunities exist.
-	Whether the business relies too heavily on a specific spending tier.

![image](/assets/images/banners/V5-5.png)

##### 2.5. Preferred Service Distribution
A tree map (square map) visualizes users' preferred service (Bike or Car) within each spending level and persona. This is particularly useful for:
-	Allocating vehicle supply by user preference
-	Identifying pricing sensitivity by service type
-	Planning region-specific or persona-targeted promotions

![image](/assets/images/banners/V5-6.png)

##### 2.6. Persona Contribution Table
This table presents the percentage contribution of each persona to overall performance across all core metrics. It highlights how different user types contribute to:
-	Total active user base
-	Revenue (GMV)
-	Ride volume
These insights help identify high-impact user groups, validate campaign targeting, and inform investment priorities.

![image](/assets/images/banners/V5-7.png)

### CONCLUSION
The user segmentation performance dashboard offers a powerful lens into our business operations. By combining behavioral, transactional, and demographic layers, we gain a richer understanding of who our users are, how they engage with our services, and what drives their value.

This dashboard not only supports weekly tracking of retention, spending, and usage trends, but also enables stakeholders across functions to align around shared goals. Its design encourages data exploration, supports evidence-based decision-making, and promotes user-centric strategies.

As we continue to scale and evolve, we aim to enhance the dashboard further by integrating predictive analytics, churn forecasting, and real-time alerts, ensuring that we remain agile and responsive in a highly competitive market.

## Artefacts
---

![image](/assets/images/banners/V5-8.png)

---
## Relfection
---

### Introduction

Developing the "Weekly Performance by Persona Tag" dashboard for our ride-hailing company was a valuable experience that expanded my technical, analytical, and strategic thinking skills. Through this project, I combined user segmentation, operational metrics, and business objectives into a coherent, practical dashboard using Tableau. This reflection outlines what I learned during the process, the challenges I encountered, my feelings and motivations, and how I plan to build upon this experience in future projects.

#### 1. What I Have Learned

One of the major lessons I gained from this project was how critical clear segmentation and filtering are when dealing with operational data. Structuring filters (City, Service Type, Persona, Spending Level) enabled multi-dimensional exploration without overwhelming the users. I learned how to create a dashboard that serves different departments (marketing, operations, product) while maintaining a unified view of the data.

Moreover, designing trendline graphs, stacked bar charts, and treemaps taught me to match visualisation types to specific business questions. For instance, using trendlines helped detect behavior shifts over time, while treemaps offered a fast view of service preference patterns.

I also became more aware of the importance of user-centric reporting. Rather than just presenting data, the dashboard needed to support decision-making processes for marketing teams, operations managers, and business leaders. This shifted my mindset from simply "showing" data to truly "communicating" insights clearly and effectively.

Finally, I strengthened my Tableau technical skills, particularly in applying global filters across multiple dashboards and designing dashboards for multi-week performance monitoring.

#### 2. Why I Learned It

Understanding user behavior through segmentation is a core strategic lever in any customer-focused business, especially in highly competitive markets like ride-hailing. Developing this dashboard helped me connect data visualisation techniques directly to business value: improving retention, optimising resources, and targeting marketing investments.

Additionally, creating a dashboard usable by multiple teams taught me the importance of collaboration and cross-functional alignment. If different teams interpret the data differently, the business risks inefficiency. Thus, mastering clear, accessible, and flexible data communication became a key learning goal.

From a career perspective, these skills are vital for success in roles such as Business Analyst, Data Analyst, and Product Manager — where data-driven decision-making is fundamental.

#### 3. Feelings, Inspirations, and Motivation

While developing the dashboard, I felt both excited and challenged. I was excited to build something tangible that could deliver real business impact. However, designing a single platform that met the needs of very different audiences (technical vs non-technical users) was sometimes overwhelming.

Completing the persona segmentation, contribution tables, and spending level distributions gave me a strong sense of achievement. Each part of the dashboard felt like solving a small puzzle — making sure each graph told a story but also contributed to the larger narrative of operational performance.

This project also motivated me to think bigger: beyond tracking current performance to exploring predictive capabilities like churn forecasting and demand prediction. It made me realise that dashboard development is an evolving process, and there is always room to make tools smarter, faster, and more actionable.

#### 4. Challenges Faced

One major challenge was deciding how much detail to display without cluttering the dashboard. Striking the balance between offering detailed insights (like persona-specific spending trends) and maintaining visual simplicity took several design iterations.

Another difficulty was ensuring that filters interacted correctly across all dashboard components without breaking functionality. For instance, making sure the "Week" and "Persona" filters updated both the trendline and spending distribution graphs consistently required troubleshooting and careful testing.

Additionally, it was sometimes difficult to avoid duplication — for example, ensuring that the spending distribution chart and the preferred service distribution added complementary, not redundant, value.

Lastly, ensuring accessibility — making the dashboard intuitive for non-technical users — was a continuous design consideration. Tooltips, legends, and straightforward metric labels became critical features to solve this.

#### 5. How I Plan to Apply It and Improve

In the short term, I will apply what I learned by building even more dynamic dashboards that incorporate real-time data streams (e.g., live ride requests, weather conditions). I also plan to learn more about predictive analytics integration (e.g., using historical booking data to predict demand spikes).

My action plan for improvement includes:

Goal | Action Plan | Benchmark
Advance predictive analytics | Learn time-series forecasting models in Python (Prophet, ARIMA) | Build one predictive dashboard by end of year
Improve real-time dashboard capabilities | Study Tableau hyper data extracts and real-time data source integration | Create a real-time GMV tracker
Strengthen storytelling in dashboards | Practice weekly dashboard projects focused on narrative flow | Receive positive peer feedback on clarity of dashboard storytelling

### Conclusion
Building the "Weekly Performance by Persona Tag" dashboard was a transformative experience that enhanced both my technical proficiency and strategic thinking. It showed me that a successful dashboard is not only about aesthetic design or technical complexity — it is about crafting a tool that empowers users to make faster, better decisions.

This project has inspired me to continue developing not just my technical data skills, but also my storytelling, user empathy, and business problem-solving abilities. I look forward to applying these lessons to future projects, where I can create even more impactful and intelligent data solutions.


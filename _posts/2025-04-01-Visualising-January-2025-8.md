---
layout: post
title: UoE - Visualising Data January 2025 - Dashboard Presentation
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, assignment, Module E-Portfolio Learning Activities]
---
---
# Performance by Persona Tag in Ride-Hailing Company
---
## A. EXECUTIVE SUMMARY

### Introduction

The "Performance by Persona" dashboard has been developed for Be Group, a leading ride-hailing company in Vietnam, offering services similar to Uber. Be Group provides a range of transportation options, including beBike and beCar, catering to various user segments. This dashboard specifically focuses on monitoring the performance of Be’s service across different personas, such as students and office workers, over a weekly timeline. By analyzing metrics such as Active Riders, Trips, GMV (Gross Merchandise Value), and %Burn, the dashboard offers a deep dive into these user segments’ weekly engagement and performance.

### Benefits & Impacts

The dashboard delivers several key benefits that enhance decision-making and operational efficiency:

- _Targeted Marketing and Personalization_: By segmenting users into distinct personas, the dashboard enables Be Group to tailor marketing campaigns and promotions. For instance, if students are more engaged with beBike but not beCar, the company can create targeted offers to encourage the use of beCar among this group. This personalized approach boosts user retention and increases overall engagement.
- _Strategic Decision-Making_: With clear visibility into the performance of different user segments, Be Group can make informed strategic decisions. For example, if a specific persona like "Office Worker" is underperforming in GMV, Be can adjust marketing tactics, pricing, or service offerings to address these gaps, ensuring the company remains competitive and aligned with user needs.
- _Operational Efficiency_: The dashboard helps optimize resource allocation by identifying which personas are most active. This allows Be Group to adjust service availability based on demand patterns, ensuring that resources such as bikes, cars, and drivers are efficiently deployed, improving service quality and reducing wait times.
- _Continuous Improvement_: Monitoring performance over time helps identify trends and potential areas for improvement. If a certain persona shows a steady decline in engagement, targeted interventions can be planned to re-engage this group, ensuring long-term growth and customer satisfaction.

### Future
The vision for the "Performance by Persona" dashboard is to evolve into a more predictive and interactive tool:

-	Predictive Analytics: By incorporating machine learning, the dashboard could forecast future performance trends, allowing Be Group to anticipate shifts in user behavior. Predictive insights could guide proactive strategies, such as adjusting promotional campaigns or resource deployment ahead of expected demand surges, improving overall efficiency.
-	Enhanced Persona Segmentation: Future iterations could expand persona segmentation to include more granular categories, such as location, time-of-day usage, and behavioral patterns. This will enable Be Group to deliver even more personalized services and offers, further enhancing user experience.
-	Real-Time Integration: Incorporating real-time data, such as traffic and weather conditions, could provide dynamic adjustments to service levels. For example, if a rainstorm leads to increased demand for bikes, the dashboard could highlight this shift, enabling Be Group to allocate resources more effectively in real-time.
-	Cross-Department Integration: The dashboard could evolve into a unified platform that integrates insights from various business functions, fostering collaboration between marketing, product development, and customer support teams. This integration would ensure that Be Group’s strategies are consistently informed by data-driven insights from across the company.

In conclusion, the "Performance by Persona" dashboard not only enhances Be Group's operational and strategic capabilities but also sets the stage for future advancements in user personalization and predictive analytics.

## B. DESIGN PRINCIPLES REPORT

### Foundations of Design and Development

This report provides a comprehensive exploration of the theoretical frameworks underpinning the dashboard, detailed design principles, development methodology, critical Human-Computer Interaction (HCI) considerations, structured reporting approaches, and detailed visualization choices.

#### 1.	Theoretical Discussion

Information visualization and Human-Computer Interaction (HCI) theories provided the foundation for the dashboard's design. According to Munzner (2014), effective visualization reduces complexity, making it easier for users to process large volumes of information. Clear visual encoding of data minimizes the time and cognitive effort needed to identify key patterns. Ware (2021) stresses that human perception favors simple, distinct visuals over complex or cluttered designs. Therefore, clarity and reduction of cognitive load were primary goals.

Consistency is another critical principle drawn from Few (2021), emphasizing that uniform use of colors, fonts, and chart types supports user intuition and predictability, reducing the mental effort required for users to interact with the dashboard. Following Shneiderman’s Information-Seeking Mantra (2022) "Overview first, zoom and filter, then details-on-demand" the dashboard first presents a high-level overview and then allows users to drill down into specific insights.

#### 2.	Design Principles

Several fundamental principles guided the dashboard’s design:

-	Clarity: Visual components are simplified to communicate key insights instantly. Each chart was carefully designed to highlight the most critical data points without extraneous graphical elements.
-	Consistency: Uniform use of a muted color palette, standard typography, and a clean layout structure enhances familiarity and ease of interpretation.
-	Visual Hierarchy: Important metrics are positioned prominently at the top, with supporting details arranged below. This guides users naturally through their analytical journey.
-	Interactivity: Features such as dropdown filters, tooltips, and drill-down graphs enhance user engagement and allow for customized data exploration.
-	User-Centeredness: The needs of Be Group’s business analysts shaped the dashboard’s functionality. Frequent feedback loops ensured that the dashboard remained aligned with user goals and cognitive processes.

#### 3.	Methodology

The dashboard was developed using an iterative, user-centered design approach:

-	Requirement Gathering: Through stakeholder interviews, key metrics and analytical needs were gathered. Understanding user workflows ensured that the dashboard supported real-world decision-making.
-	Conceptual Development and Prototyping: Tableau was selected as the platform due to its extensive data visualization capabilities, interactive features, and ease of integration with existing Be Group data systems.
-	Testing and Iteration: Regular usability testing sessions involved real users providing feedback. This iterative process allowed continuous refinement, improving visual clarity, filter effectiveness, and interaction design.
-	Color and Visual Aesthetics: Based on Ware’s (2021) perceptual guidelines, a neutral color palette was chosen to focus user attention on data rather than design embellishments.

#### 4.	Human-Computer Interaction (HCI)

Incorporating HCI best practices ensured that the dashboard remained intuitive and efficient:

-	Dropdown Filters: Allow users to quickly filter data by City ID, Service Type, Segment, Persona Tag, Week, and Spending Level. This supports personalized exploration and task-specific workflows.
-	Interactive Tooltips: Reveal supplementary data upon hover, allowing users to access further details without cluttering the main interface.
-	Intuitive Layout: The dashboard flows logically from broad summaries to more detailed insights. This supports users’ natural cognitive tendencies to seek a general understanding before focusing on specifics (Preece et al., 2019).

### Overall Dashboard

#### 1.	Overall Structure

The dashboard is structured into clear, logical sections to support progressive data exploration:

-	Top Section (Filters & Key Metrics): Users are immediately presented with interactive dropdown filters and headline performance metrics such as Active Riders, Trips, GMV, %Burn, and Trips per Rider (TPR). This allows quick scanning of business health.
-	Middle Section (Trendline Graph): Weekly trends for critical performance indicators are visualized through a multi-line trend graph, enabling quick detection of changes and long-term patterns.
-	Lower Left Section (Stacked Bar Charts - Spending Distribution): Spending behaviors of different personas are visualized weekly to reveal trends and differences across segments.
-	Lower Right Section (Treemaps - Contributions): Treemaps provide a compact, intuitive visual summary of each persona’s proportional contribution to overall Trips and GMV.
-	Detailed Data Tables: Tables offer precise figures to complement visual patterns, supporting detailed analysis and data validation.

![image](/assets/images/banners/V8-1.png)

#### 2.	Purpose and Details of Graph/Plot Selection

Visualization choices were aligned with theoretical best practices, with deliberate selection based on clarity, comparative efficiency, and spatial effectiveness:

-	Trendline Graphs: Chosen for representing time-series data clearly, enabling users to spot patterns, seasonal trends, and anomalies at a glance. Each line represents a different key metric to avoid confusion and enhance trend comparison.

![image](/assets/images/banners/V8-2.png)

-	Stacked Bar Charts: Selected to compare spending distributions across multiple persona segments simultaneously, providing both absolute and relative values. Stacked bars were preferred over pie charts for their clearer comparative analysis across categories and time.

![image](/assets/images/banners/V8-3.png)

-	Treemaps: Used to visualize hierarchical relationships compactly, effectively revealing dominant contributors and offering proportional clarity. Treemaps were favored over bar charts for space efficiency and immediate visibility of relative proportions.

![image](/assets/images/banners/V8-4.png)

-	Detailed Tables: Provide numerical precision necessary for in-depth auditing, complementing the summarized visual data, and allowing users to validate visual insights.!!

![image](/assets/images/banners/V8-5.png)

-	Dropdown Filters: Integrated to enable dynamic, user-specific exploration without overloading the main interface, enhancing personalization and reducing the cognitive load.

![image](/assets/images/banners/V8-6.png)
![image](/assets/images/banners/V8-7.png)

-	Interactive Tooltips: Incorporated to allow on-demand access to additional details without overwhelming users with excessive static information. Tooltips were designed to be concise and context-specific, maintaining dashboard cleanliness.

### Conclusion

The "Performance by Persona" dashboard for Be Group exemplifies the integration of theoretical visualization principles, user-centered design methodologies, rigorous HCI considerations, and structured reporting techniques. It delivers a powerful and intuitive tool for persona-centric performance tracking, enabling strategic decision-making, enhanced customer understanding, and improved operational efficiency. By adhering to academic best practices in dashboard design, the solution not only meets but exceeds the user's expectations for clarity, usability, and actionable insights.

### References

-	Shneiderman, B. (2022). "The Eyes Have It: A Task by Data Type Taxonomy for Information Visualizations Revisited." ACM Transactions on Interactive Intelligent Systems, 12(3), pp.1-18.
-	Few, S. (2021). Information Dashboard Design: The Effective Visual Communication of Data. Analytics Press.
-	Ware, C. (2021). Information Visualization: Perception for Design. 4th ed. Morgan Kaufmann.
-	Munzner, T. (2014). Visualization Analysis and Design. CRC Press.
-	Preece, J., Sharp, H., & Rogers, Y. (2019). Interaction Design: Beyond Human-Computer Interaction. 5th ed. Wiley.
-	Tufte, E. (2001). The Visual Display of Quantitative Information. Graphics Press.
-	Nielsen, J. (1994). Usability Engineering. Morgan Kaufmann Publishers.

## C. DASHBOARD MANUAL (500 words)

### 1.	Using Filters

At the top of the dashboard, you will find several dropdown filter menus:

-	City ID: Select the city to view data specific to that location (e.g., City ID 189 for Ho Chi Minh City, 190 for Hanoi).
-	Service Type: Choose between 'bike' or 'car' services. For instance, selecting "bike" filters data only for bike rides.
-	Segment: Focus the analysis on different customer segments, such as "retain" users.
-	Persona Tag: Allows you to choose one or multiple user personas (e.g., Office Worker, Student) for detailed persona-level performance comparison.
-	Week: Filter the data by specific weeks to monitor performance over time.
-	Spending Level: Focus analysis on riders with different spending behaviors (e.g., all, low, medium, and high spenders).

Note: Multiple selections are supported for most filters by ticking the boxes.

![image](/assets/images/banners/V8-6.png)
![image](/assets/images/banners/V8-7.png)

### 2.	Understanding the Key Metrics

Immediately below the filters, you will see five headline performance metrics:

-	Active Riders: Number of users making at least one trip.
-	Trips: Total number of completed rides.
-	GMV (Gross Merchandise Value): Total revenue generated.
-	% Burn: Marketing cost as a percentage of revenue.
-	TPR (Trips per Rider): Average trips made by each rider.

These KPIs provide a quick snapshot of the company’s operational and financial health.

![image](/assets/images/banners/V8-8.png)

### 3.	Analysing Weekly Trends

The "Trendline Graph" section visualizes weekly trends for various metrics such as Active Riders, Unique Requests, Trips, GMV, and % Burn.

-	Each line represents a different persona or metric.
-	Hover over a point to see detailed values for a specific week.
-	Use this graph to quickly spot rising or declining performance trends

![image](/assets/images/banners/V8-2.png)

### 4.	Viewing Spending Distribution

Below the trendline, you will find a "Spending Distribution" section:

-	Stacked bar charts display GMV and Trip distributions across different personas over time.
-	Different shades in each bar represent different spending levels.

![image](/assets/images/banners/V8-3.png)

### 5.	Exploring Contribution Treemaps

On the right-hand side, two treemaps show:

-	Trip Contribution: Which personas completed the most trips?
-	GMV Contribution: Which personas generated the most revenue?
-	The size of each block represents the proportion contributed.
-	Hovering over a block shows exact trip or GMV numbers.

![image](/assets/images/banners/V8-4.png)

### 6.	Accessing Detailed Data

The "Overall Performance" table at the bottom provides exact figures for each persona across different weeks.

-	Metrics include Active Riders, Unique Requests, Trips, GMV, and Post Promo GMV.
-	Scroll horizontally or vertically to view all weeks and all metrics.

Tip: Use this table for precise analysis, validation of visual insights, or exporting specific weekly data if needed.

![image](/assets/images/banners/V8-5.png)

### 7.	Conclusion

The "Performance by Persona" dashboard enables users to dynamically filter data, visually explore weekly trends, understand spending behaviors, and evaluate persona contributions. By leveraging filters, trendlines, distribution charts, treemaps, and detailed tables, users can gain a comprehensive understanding of customer behavior and operational performance to drive strategic business decisions.

---
# Reflection
---

## Introduction

The development of the "Performance by Persona" dashboard for Be Group was a deeply enriching experience that strengthened my technical, analytical, and professional skills. Throughout the project, I applied data visualisation techniques, user-centered design methodologies, and Human-Computer Interaction (HCI) principles to create a tool that provides operational insights for a real-world ride-hailing company. Using the 5W-1H framework, I will reflect on what I learned, why it was important, how I plan to use these skills in the future, my challenges, my inspirations, and my action plan for continuous improvement.

### 1. What I Have Learned

This project allowed me to consolidate and apply multiple data analysis and visualisation skills learned throughout the module. I gained practical experience in:

- Data Cleaning and Preparation: Understanding the critical role of clean, structured data before visualisation.
- Dashboard Structuring: Learning to design dashboards logically to facilitate user exploration — from summary metrics to detailed analysis.
- Visualization Techniques: Using appropriate graphs, such as trendline graphs, stacked bar charts, treemaps, and data tables, tailored to different types of data and user needs (Few, 2012; Tufte, 2001).
- HCI and User Experience (UX) Design: Applying principles like intuitive navigation, interactivity, and clarity based on published theories (Shneiderman, 2022; Preece et al., 2019).
- Tool Proficiency: Enhancing my technical skills using Tableau as a professional-grade visualisation platform.

Moreover, I strengthened my understanding of how different users (such as marketers or operations managers) interact with data, influencing the design and filter functions.

### 2. Why I Learned It

In the age of big data, the ability to clean, structure, and visualise information effectively is crucial for making informed business decisions (Murray, 2017). Learning to build user-centered, intuitive dashboards supports this goal by ensuring that data insights are accessible to a wide range of stakeholders.

Additionally, developing strong dashboard design skills directly improves my employability. Businesses today demand analysts who can not only analyse data but also present findings in a clear, actionable format. Understanding HCI principles ensures that I design visual tools that genuinely meet user needs and enhance decision-making processes.

### 3. How I Will Apply It in Real Life and in the Future

I plan to apply the skills gained from this module both immediately and in the long term across professional, academic, and personal projects.

In the short term, I intend to use Tableau and Python in my upcoming internship to build live dashboards that monitor user engagement and operational efficiency. By combining SQL data extraction with Python-based visualisation (matplotlib, seaborn), I can automate regular reporting processes, saving valuable time for the business.

Additionally, I will apply R’s statistical capabilities to academic research projects, where I will focus on building regression models and hypothesis testing visualisations. This will improve the quality and professionalism of my academic work.

In the next few years, I aim to specialise further in business intelligence and data-driven decision-making roles. Specifically, I plan to:

- Work in a data analytics or consulting firm, using Power BI and Tableau to deliver performance tracking solutions for clients.
- Develop cross-functional data products, where data visualisation, statistical modelling, and storytelling are integrated to deliver business value.
- Build public dashboards on platforms like Tableau Public or GitHub, showcasing open data initiatives (e.g., city transport analysis, COVID-19 datasets) to demonstrate my capabilities to potential employers.

In the longer term, I aspire to:

- Become a Certified Tableau Professional and a Certified Data Analyst with Microsoft Power BI, achieving globally recognised credentials that enhance my career prospects.
- Contribute to the academic community by publishing articles or whitepapers on ethical visualisation practices and innovations in user-centric dashboard design.
- Teach workshops or create online courses on data visualisation principles for non-technical audiences, promoting data literacy in the wider community.
- Lead data-driven transformation projects in future workplaces, using my combined skills in Python, R, Tableau, and Power BI to champion a culture of evidence-based decision-making.

Importantly, I will stay updated with evolving technologies such as augmented analytics, AI-based visualisation, and interactive storytelling platforms. As Ware (2020) suggests, staying aligned with perceptual and technological innovations ensures that visualisation practitioners remain effective and relevant.

### 4. How I Plan to Improve (Action Plan)

Although this project was a success, several areas for improvement emerged:

Goal | Benchmark | Action Plan | How to Exceed
Improve advanced Tableau features | Complete Tableau Desktop Specialist by 2025 | Enrol in Tableau Public training series | Attempt Tableau Certified Associate Certification
Enhance predictive analytics capabilities | Build predictive dashboards using Python/PowerBI | Learn machine learning models for forecasts | Create dynamic forecasting dashboards
Strengthen storytelling with data | Positive peer/tutor feedback on narratives | Practice using "Storytelling with Data" techniques (Knaflic, 2015) | Present at conferences or webinars
Improve real-time data integration | Build 3+ real-time updating dashboards | Study APIs and real-time data streaming | Deploy dashboards with dynamic, live data sources
Sharpen time management | Complete projects ahead of deadlines | Weekly personal sprints and task prioritisation | Run retrospectives to improve delivery speed


### 5. Feelings, Inspirations, and Motivation

Initially, I was excited but also intimidated by the complexity of designing an end-to-end dashboard for a real-world company. The responsibility of ensuring usability, accuracy, and aesthetic quality created pressure to perform at a high standard.

However, once the first iteration was completed and feedback was integrated, I felt genuinely inspired. The positive experience of turning raw numbers into meaningful visual stories reinforced my passion for data storytelling. Tutor feedback acknowledging the dashboard’s strategic insight, HCI design, and strong visual clarity was particularly motivating.

This project validated my belief that data visualisation is not just about technical skills, but also about communication, user understanding, and design thinking.

### 6. Challenges Faced

Several challenges arose during the project:

- Complex Filtering Logic: Setting up interconnected filters (e.g., Persona Tag + Spending Level + Week) without breaking dashboard performance required careful design.
- Balancing Simplicity and Detail: Deciding what information should be visible at a glance versus hidden in tooltips was a delicate balance.
- Interactivity Design: Ensuring that filters and tooltips worked intuitively took multiple testing and iterations.
- Managing Scope: With so many possibilities for additional features (e.g., real-time traffic overlays, behavioral clustering), it was challenging to stay focused and deliver within the project timeframe.

By applying project management techniques such as scoping, weekly milestones, and iterative improvements, I overcame these challenges systematically.

## Summary of Learning Outcomes and Professional Skills Developed

Learning Outcomes Achieved:

- Built a fully functional, user-centric dashboard.
- Applied HCI principles to improve visual clarity and usability.
- Selected appropriate visualisation techniques based on data types and user needs.
- Critically evaluated visualisation effectiveness.

Skills Developed:

- Critical Thinking and Analysis: Choosing and justifying visualisation methods.
- Communication: Designing intuitive, interpretable visuals.
- Time Management: Planning weekly sprints to meet milestones.
- IT and Digital Skills: Advanced Tableau and intermediate Python/R capabilities.
- Numeracy: Summarising performance metrics into digestible KPIs.
- Problem-Solving: Debugging dashboard functionality.
- Ethical Awareness: Representing data transparently and avoiding misleading visuals.
- Professionalism: Incorporating peer and tutor feedback into final deliverables.







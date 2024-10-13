---
layout: post
title: UoE - Deciphering Big Data July 2024 - Backup Procedure
subtitle: Identify and manage challenges, security issues and risks, limitations, and opportunities in data wrangling. Critically analyse data wrangling problems and determine appropriate methodologies, tools, and techniques (involving preparing, cleaning, exploring, creating, optimising and evaluating big data) to solve them. Systematically develop and implement the skills required to be effective member of a development team in a virtual professional environment, adopting real life perspectives on team roles and organisation.
categories: EL-Activities Wiki
tags: [UoE, Module E-Portfolio Learning Activities]
---
---
## “Grandfather-Father-Son" GFS backup procedure | Dinh Khoi Dang
---

The Grandfather-Father-Son (GFS) backup procedure is a hierarchical backup strategy commonly used for large databases. It operates on a rotation system where daily, weekly, and monthly backups are performed. The "son" is the most recent backup (daily), the "father" refers to weekly backups, and the "grandfather" denotes monthly or longer-term backups. This method reduces resource intensity by avoiding constant full backups and instead staggering them, allowing for more efficient use of storage.

Compared to continuous backup methods or full daily backups, GFS is resource-efficient, offering a balance between recovery needs and storage management. However, modern alternatives like incremental or differential backups may be more effective in terms of speed and granularity of data recovery, especially for organizations needing real-time data availability. While GFS is robust, it may not be ideal for environments requiring frequent, high-speed recovery or minimal downtime.

---
## Individual Reflecion
---

### Reflection

Writing the essay on the Grandfather-Father-Son (GFS) backup procedure provided me with a deeper understanding of backup strategies and their importance in data management, particularly for large databases. Engaging with the intricacies of GFS helped me appreciate the complexities of maintaining data integrity and availability, which are crucial in today's data-driven environments.

### Understanding GFS Backup Procedure

Delving into the hierarchical structure of the GFS backup procedure illuminated how this strategy efficiently organizes backups into daily, weekly, and monthly categories. I found it particularly interesting how the GFS method effectively balances resource management with the need for reliable data recovery. By implementing a rotation system, GFS avoids the overhead associated with constant full backups, which can be resource-intensive. This practical aspect of GFS underscores the importance of efficient storage use, especially in organizations where data volumes are substantial.

### Comparative Analysis with Other Methods

In my exploration of GFS, I compared it to alternative backup strategies, such as incremental and differential backups. This analysis was enlightening, as it highlighted the trade-offs involved in different backup methodologies. While GFS is a robust and resource-efficient approach, I recognized that it may not be the best fit for all scenarios, particularly in environments where high-speed recovery is essential. This reflection on the limitations of GFS led me to consider the specific needs of an organization when determining the most suitable backup strategy. Understanding the context in which these backup methods are applied will be invaluable in my future work, especially in data management and IT.

### Practical Implications and Considerations

The essay prompted me to think critically about the practical implications of implementing a GFS backup strategy in real-world scenarios. While GFS offers several advantages, I also realized that its effectiveness depends on proper planning and execution. Factors such as the frequency of data changes, recovery time objectives, and available storage capacity all play significant roles in determining the success of the GFS approach. This consideration of practical implementation will guide my thinking in future projects involving data backup and recovery solutions.

### Conclusion

Overall, the process of researching and writing about the GFS backup procedure deepened my understanding of backup strategies and their critical role in data protection. This experience reinforced the importance of evaluating various backup methods against organizational needs and operational contexts. Moving forward, I feel better equipped to make informed decisions about data management strategies, ensuring that they align with the specific recovery and storage requirements of different environments.

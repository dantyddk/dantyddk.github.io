---
layout: post
title: UoE - Visualising Data January 2025 - Plotly Developments
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Plotly Developments
---

    import pandas as pd
    import numpy as np
    import plotly.express as px
    
    import plotly.express as px
    tdf = px.data.gapminder()
    fig = px.scatter(tdf, x="gdpPercap", y="lifeExp", animation_frame="year", animation_group="country",
               size="pop", color="continent", hover_name="country", facet_col="continent",
               log_x=True, size_max=45, range_x=[100,100000], range_y=[25,90])
    fig.show()
    
  ![image](/assets/images/banners/V3-1.png)

    import pandas as pd
    
    file_path = "/content/bloodpressure.csv"
    bpdf = pd.read_csv(file_path)
    
    df.head()

  ![image](/assets/images/banners/V3-2.png)

    fig = px.scatter(bpdf, x="Mean systolic blood pressure (mmHg)", y="Mean diastolic blood pressure (mmHg)", animation_frame="Year", animation_group="Country/Region/World",
                color="Sex", hover_name="Country/Region/World",
               log_x=True, size_max=45, range_x=[100,200], range_y=[50,150])
    fig.show()

  ![image](/assets/images/banners/V3-3.png)

    df["BP_Status"] = np.where(df['SBP'] >= 130, 'High', 'Low')
    
    import plotly.express as px
    
    fig = px.choropleth(df, locations="ISO",
                        color="SBP", # lifeExp is a column of gapminder
                        hover_name="Country", # column to add to hover information
                        color_continuous_scale=px.colors.sequential.Plasma)
    fig.show()
    
    hdf = df[df['BP_Status']=='High']
    fig = px.choropleth(hdf, locations="ISO",
                        color="SBP", # lifeExp is a column of gapminder
                        hover_name="Country", # column to add to hover information
                        color_continuous_scale=px.colors.sequential.Plasma)
    fig.show()
    
    fig = px.bar(hdf, x='Country', y='DBP')
    fig.show()
    
    import plotly.graph_objects as go
    
    
    fig = go.Figure(data=[
        go.Bar(name='SBP', x=hdf['Country'], y=hdf['SBP']),
        go.Bar(name='DBP', x=hdf['Country'], y=hdf['DBP'])
    ])
    
    fig.update_layout(barmode='group')
    fig.show()
    
    import plotly.express as px
    # This dataframe has 244 lines, but 4 distinct values for `day`
    
    fig = px.pie(df, values='SBP', names='BP_Status')
    fig.show()

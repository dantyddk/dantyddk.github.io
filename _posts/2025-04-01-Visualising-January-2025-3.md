---
layout: post
title: UoE - Visualising Data January 2025 - ML Regression in Python
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## ML Regression in Python
---
### Ordinary Least Square (OLS) with plotly.express
    
    import plotly.express as px

    df = px.data.tips()
    fig = px.scatter(
        df, x='total_bill', y='tip', opacity=0.65,
        trendline='ols', trendline_color_override='grey'
    )
    fig.show()
    
  ![image](/assets/images/banners/V2-1.png)

### Linear Regression with scikit-learn

    import numpy as np
    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.linear_model import LinearRegression
    
    df = px.data.tips()
    X = df.total_bill.values.reshape(-1, 1)
    
    model = LinearRegression()
    model.fit(X, df.tip)
    
    x_range = np.linspace(X.min(), X.max(), 100)
    y_range = model.predict(x_range.reshape(-1, 1))
    
    fig = px.scatter(df, x='total_bill', y='tip', opacity=0.65)
    fig.add_traces(go.Scatter(x=x_range, y=y_range, name='Regression Fit'))
    fig.show()
 
  ![image](/assets/images/banners/V2-2.png)

### ML Regression in Dash

    !pip install dash
    
    from dash import Dash, dcc, html, Input, Output
    from sklearn.model_selection import train_test_split
    from sklearn import linear_model, tree, neighbors
    import plotly.graph_objects as go
    import plotly.express as px
    import numpy as np
    
    app = Dash(__name__)
    
    models = {'Regression': linear_model.LinearRegression,
              'Decision Tree': tree.DecisionTreeRegressor,
              'k-NN': neighbors.KNeighborsRegressor}
    
    app.layout = html.Div([
        html.H4("Predicting restaurant's revenue"),
        html.P("Select model:"),
        dcc.Dropdown(
            id='dropdown',
            options=["Regression", "Decision Tree", "k-NN"],
            value='Decision Tree',
            clearable=False
        ),
        dcc.Graph(id="graph"),
    ])
    
    
    @app.callback(
        Output("graph", "figure"),
        Input('dropdown', "value"))
    def train_and_display(name):
        df = px.data.tips() # replace with your own data source
        X = df.total_bill.values[:, None]
        X_train, X_test, y_train, y_test = train_test_split(
            X, df.tip, random_state=42)
    
        model = models[name]()
        model.fit(X_train, y_train)
    
        x_range = np.linspace(X.min(), X.max(), 100)
        y_range = model.predict(x_range.reshape(-1, 1))
    
        fig = go.Figure([
            go.Scatter(x=X_train.squeeze(), y=y_train,
                       name='train', mode='markers'),
            go.Scatter(x=X_test.squeeze(), y=y_test,
                       name='test', mode='markers'),
            go.Scatter(x=x_range, y=y_range,
                       name='prediction')
        ])
        return fig
    
    app.run(debug=True)

### Model generalization on unseen data

    import numpy as np
    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.linear_model import LinearRegression
    from sklearn.model_selection import train_test_split
    
    df = px.data.tips()
    X = df.total_bill.to_numpy()[:, None]
    X_train, X_test, y_train, y_test = train_test_split(X, df.tip, random_state=0)
    
    model = LinearRegression()
    model.fit(X_train, y_train)
    
    x_range = np.linspace(X.min(), X.max(), 100)
    y_range = model.predict(x_range.reshape(-1, 1))
    
    fig = go.Figure([
        go.Scatter(x=X_train.squeeze(), y=y_train, name='train', mode='markers'),
        go.Scatter(x=X_test.squeeze(), y=y_test, name='test', mode='markers'),
        go.Scatter(x=x_range, y=y_range, name='prediction')
    ])
    fig.show()

  ![image](/assets/images/banners/V2-3.png)

### Comparing different kNN models parameters

    import numpy as np
    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.neighbors import KNeighborsRegressor
    
    df = px.data.tips()
    X = df.total_bill.values.reshape(-1, 1)
    x_range = np.linspace(X.min(), X.max(), 100)
    
    # Model #1
    knn_dist = KNeighborsRegressor(10, weights='distance')
    knn_dist.fit(X, df.tip)
    y_dist = knn_dist.predict(x_range.reshape(-1, 1))
    
    # Model #2
    knn_uni = KNeighborsRegressor(10, weights='uniform')
    knn_uni.fit(X, df.tip)
    y_uni = knn_uni.predict(x_range.reshape(-1, 1))
    
    fig = px.scatter(df, x='total_bill', y='tip', color='sex', opacity=0.65)
    fig.add_traces(go.Scatter(x=x_range, y=y_uni, name='Weights: Uniform'))
    fig.add_traces(go.Scatter(x=x_range, y=y_dist, name='Weights: Distance'))
    fig.show()

  ![image](/assets/images/banners/V2-4.png)

### Displaying PolynomialFeatures using $\LaTeX$

    import numpy as np
    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.linear_model import LinearRegression
    from sklearn.preprocessing import PolynomialFeatures
    
    def format_coefs(coefs):
        equation_list = [f"{coef}x^{i}" for i, coef in enumerate(coefs)]
        equation = "$" +  " + ".join(equation_list) + "$"
    
        replace_map = {"x^0": "", "x^1": "x", '+ -': '- '}
        for old, new in replace_map.items():
            equation = equation.replace(old, new)
    
        return equation
    
    df = px.data.tips()
    X = df.total_bill.values.reshape(-1, 1)
    x_range = np.linspace(X.min(), X.max(), 100).reshape(-1, 1)
    
    fig = px.scatter(df, x='total_bill', y='tip', opacity=0.65)
    for degree in [1, 2, 3, 4]:
        poly = PolynomialFeatures(degree)
        poly.fit(X)
        X_poly = poly.transform(X)
        x_range_poly = poly.transform(x_range)
    
        model = LinearRegression(fit_intercept=False)
        model.fit(X_poly, df.tip)
        y_poly = model.predict(x_range_poly)
    
        equation = format_coefs(model.coef_.round(2))
        fig.add_traces(go.Scatter(x=x_range.squeeze(), y=y_poly, name=equation))
    
    fig.show()
    
  ![image](/assets/images/banners/V2-5.png)

### 3D regression surface with px.scatter_3d and go.Surface

    import numpy as np
    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.svm import SVR
    
    mesh_size = .02
    margin = 0
    
    df = px.data.iris()
    
    X = df[['sepal_width', 'sepal_length']]
    y = df['petal_width']
    
    # Condition the model on sepal width and length, predict the petal width
    model = SVR(C=1.)
    model.fit(X, y)
    
    # Create a mesh grid on which we will run our model
    x_min, x_max = X.sepal_width.min() - margin, X.sepal_width.max() + margin
    y_min, y_max = X.sepal_length.min() - margin, X.sepal_length.max() + margin
    xrange = np.arange(x_min, x_max, mesh_size)
    yrange = np.arange(y_min, y_max, mesh_size)
    xx, yy = np.meshgrid(xrange, yrange)
    
    # Run model
    pred = model.predict(np.c_[xx.ravel(), yy.ravel()])
    pred = pred.reshape(xx.shape)
    
    # Generate the plot
    fig = px.scatter_3d(df, x='sepal_width', y='sepal_length', z='petal_width')
    fig.update_traces(marker=dict(size=5))
    fig.add_traces(go.Surface(x=xrange, y=yrange, z=pred, name='pred_surface'))
    fig.show()

  ![image](/assets/images/banners/V2-6.png)

### Visualizing coefficients for multiple linear regression (MLR)

    import pandas as pd
    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.linear_model import LinearRegression
    
    df = px.data.iris()
    
    X = df.drop(columns=['petal_width', 'species_id'])
    X = pd.get_dummies(X, columns=['species'], prefix_sep='=')
    y = df['petal_width']
    
    model = LinearRegression()
    model.fit(X, y)
    
    colors = ['Positive' if c > 0 else 'Negative' for c in model.coef_]
    
    fig = px.bar(
        x=X.columns, y=model.coef_, color=colors,
        color_discrete_sequence=['red', 'blue'],
        labels=dict(x='Feature', y='Linear coefficient'),
        title='Weight of each feature for predicting petal width'
    )
    fig.show()

  ![image](/assets/images/banners/V2-7.png)

### Simple actual vs predicted plot

    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.linear_model import LinearRegression
    
    df = px.data.iris()
    X = df[['sepal_width', 'sepal_length']]
    y = df['petal_width']

### Condition the model on sepal width and length, predict the petal width
    
    model = LinearRegression()
    model.fit(X, y)
    y_pred = model.predict(X)
    
    fig = px.scatter(x=y, y=y_pred, labels={'x': 'ground truth', 'y': 'prediction'})
    fig.add_shape(
        type="line", line=dict(dash='dash'),
        x0=y.min(), y0=y.min(),
        x1=y.max(), y1=y.max()
    )
    fig.show()

 ![image](/assets/images/banners/V2-8.png)

### Enhanced prediction error analysis using plotly.express

    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.linear_model import LinearRegression
    from sklearn.model_selection import train_test_split
    
    df = px.data.iris()

### Split data into training and test splits

    train_idx, test_idx = train_test_split(df.index, test_size=.25, random_state=0)
    df['split'] = 'train'
    df.loc[test_idx, 'split'] = 'test'
    
    X = df[['sepal_width', 'sepal_length']]
    y = df['petal_width']
    X_train = df.loc[train_idx, ['sepal_width', 'sepal_length']]
    y_train = df.loc[train_idx, 'petal_width']

### Condition the model on sepal width and length, predict the petal width

    model = LinearRegression()
    model.fit(X_train, y_train)
    df['prediction'] = model.predict(X)
    
    fig = px.scatter(
        df, x='petal_width', y='prediction',
        marginal_x='histogram', marginal_y='histogram',
        color='split', trendline='ols'
    )
    fig.update_traces(histnorm='probability', selector={'type':'histogram'})
    fig.add_shape(
        type="line", line=dict(dash='dash'),
        x0=y.min(), y0=y.min(),
        x1=y.max(), y1=y.max()
    )
    
    fig.show()

 ![image](/assets/images/banners/V2-9.png)

### Residual plots

    import numpy as np
    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.linear_model import LinearRegression
    from sklearn.model_selection import train_test_split
    
    df = px.data.iris()

### Split data into training and test splits
    
    train_idx, test_idx = train_test_split(df.index, test_size=.25, random_state=0)
    df['split'] = 'train'
    df.loc[test_idx, 'split'] = 'test'
    
    X = df[['sepal_width', 'sepal_length']]
    X_train = df.loc[train_idx, ['sepal_width', 'sepal_length']]
    y_train = df.loc[train_idx, 'petal_width']

### Condition the model on sepal width and length, predict the petal width
  
    model = LinearRegression()
    model.fit(X_train, y_train)
    df['prediction'] = model.predict(X)
    df['residual'] = df['prediction'] - df['petal_width']
    
    fig = px.scatter(
        df, x='prediction', y='residual',
        marginal_y='violin',
        color='split', trendline='ols'
    )
    fig.show()

 ![image](/assets/images/banners/V2-10.png)

### Visualize regularization across cross-validation folds

    import numpy as np
    import pandas as pd
    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.linear_model import LassoCV
    from sklearn.preprocessing import StandardScaler
    
    N_FOLD = 6

### Load and preprocess the data

    df = px.data.gapminder()
    X = df.drop(columns=['lifeExp', 'iso_num'])
    X = pd.get_dummies(X, columns=['country', 'continent', 'iso_alpha'])
    y = df['lifeExp']

### Normalize the data
    
    scaler = StandardScaler()
    X_scaled = scaler.fit_transform(X)

### Train model to predict life expectancy
    
    model = LassoCV(cv=N_FOLD)
    model.fit(X_scaled, y)
    mean_alphas = model.mse_path_.mean(axis=-1)
    
    fig = go.Figure([
        go.Scatter(
            x=model.alphas_, y=model.mse_path_[:, i],
            name=f"Fold: {i+1}", opacity=.5, line=dict(dash='dash'),
            hovertemplate="alpha: %{x} <br>MSE: %{y}"
        )
        for i in range(N_FOLD)
    ])
    fig.add_traces(go.Scatter(
        x=model.alphas_, y=mean_alphas,
        name='Mean', line=dict(color='black', width=3),
        hovertemplate="alpha: %{x} <br>MSE: %{y}",
    ))
    
    fig.add_shape(
        type="line", line=dict(dash='dash'),
        x0=model.alpha_, y0=0,
        x1=model.alpha_, y1=1,
        yref='paper'
    )
    
    fig.update_layout(
        xaxis=dict(
            title=dict(
                text='alpha'
            ),
            type='log'
        ),
        yaxis=dict(
            title=dict(
                text='Mean Square Error (MSE)'
            )
        ),
    )
    fig.show()

 ![image](/assets/images/banners/V2-11.png)

### Grid search visualization using px.density_heatmap and px.box

    import numpy as np
    import pandas as pd
    import plotly.express as px
    import plotly.graph_objects as go
    from sklearn.model_selection import GridSearchCV
    from sklearn.tree import DecisionTreeRegressor
    
    N_FOLD = 6

### Load and shuffle dataframe

    df = px.data.iris()
    df = df.sample(frac=1, random_state=0)
    
    X = df[['sepal_width', 'sepal_length']]
    y = df['petal_width']

### Define and fit the grid

    model = DecisionTreeRegressor()
    param_grid = {
        'criterion': ['mse', 'friedman_mse', 'mae'],
        'max_depth': range(2, 5)
    }
    grid = GridSearchCV(model, param_grid, cv=N_FOLD)
    grid.fit(X, y)
    grid_df = pd.DataFrame(grid.cv_results_)

### Convert the wide format of the grid into the long format
#### accepted by plotly.express

    melted = (
        grid_df
        .rename(columns=lambda col: col.replace('param_', ''))
        .melt(
            value_vars=[f'split{i}_test_score' for i in range(N_FOLD)],
            id_vars=['mean_test_score', 'mean_fit_time', 'criterion', 'max_depth'],
            var_name="cv_split",
            value_name="r_squared"
        )
    )

### Format the variable names for simplicity

    melted['cv_split'] = (
        melted['cv_split']
        .str.replace('_test_score', '')
        .str.replace('split', '')
    )

### Single function call to plot each figure

    fig_hmap = px.density_heatmap(
        melted, x="max_depth", y='criterion',
        histfunc="sum", z="r_squared",
        title='Grid search results on individual fold',
        hover_data=['mean_fit_time'],
        facet_col="cv_split", facet_col_wrap=3,
        labels={'mean_test_score': "mean_r_squared"}
    )
    
    fig_box = px.box(
        melted, x='max_depth', y='r_squared',
        title='Grid search results ',
        hover_data=['mean_fit_time'],
        points='all',
        color="criterion",
        hover_name='cv_split',
        labels={'mean_test_score': "mean_r_squared"}
    )

### Display

    fig_hmap.show()
    fig_box.show()

 ![image](/assets/images/banners/V2-12.png)
 ![image](/assets/images/banners/V2-13.png)

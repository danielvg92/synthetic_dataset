## Requirements

```
bokeh >= 1.4.0
numpy >= 1.17.4
plotly >= 4.3.0
scikit-learn >= 0.21.3
```

## Usage

Generate complex synthetic dataset. 

- Data generator functions are in soydata.data
- Visualization functions are in soydata.visualize. These functions uses Bokeh >= 1.4.0 and Plotly >= 4.3.0

```python
from soydata.data import *
from soydata.visualize import *
```

### Two moon

```python
from soydata.data.classification import make_moons
from soydata.visualize import scatterplot

X, labels = make_moons(n_samples=500, xy_ratio=2.0, x_gap=-0.2, y_gap=0.2, noise=0.1)
p = scatterplot(X, labels=labels, height=400, width=400, title='Two moon')
```

<img src="./figures/soydata_two_moon.png" width="400" height="400">

### Spiral

```python
from soydata.data.classification import make_spiral
from soydata.visualize import scatterplot

X, labels = make_spiral(n_samples_per_class=500, n_classes=3,
    n_rotations=2.5, gap_between_spiral=0.1, noise=0.2,
    gap_between_start_point=0.1, equal_interval=True)
p = scatterplot(X, labels=labels, title='Spiral')
```

<img src="./figures/soydata_spiral.png" width="400" height="400">

### Swiss roll

```python
from soydata.data.clustering import make_swiss_roll
from soydata.visualize import scatterplot3d

X, colors = make_swiss_roll(n_samples=3000, n_rotations=3, 
    gap=0.5, thickness=0.0, width=10.0, discretize=True)
fig = scatterplot3d(X, colors)
```

<img src="./figures/soydata_swissroll.png" width="400" height="400">

### Radial

```python
from soydata.data import make_radial
from soydata.visualize import scatterplot

X, labels = make_radial(n_samples_per_cluster=100, n_classes=2, 
    n_clusters_per_class=3, gap=0.1, equal_proportion=True,
    radius_min=0.1, radius_scale=1.0, radius_variance=0.5)
p = scatterplot(X, labels=labels, title='Radial')
```

<img src="./figures/soydata_radal.png" width="400" height="400">

### Two layer radial

```python
from soydata.data.classification import make_two_layer_radial
from soydata.visualize import scatterplot

X, labels = make_two_layer_radial(n_samples_per_cluster=100, n_classes=2, 
    n_clusters_per_class=3, gap=0.0, equal_proportion=True)
p = scatterplot(X, labels=labels, title='Two-layer radial')
```

<img src="./figures/soydata_two_layer_radial.png" width="400" height="400">

### Rectangular

```python
from soydata.data import make_rectangular
from soydata.visualize import scatterplot

X = make_rectangular(n_samples=500, x_min=0, x_max=10, y_min=0, y_max=10)
p = scatterplot(X, title='Rectangular', size=3)
```

<img src="./figures/soydata_rectangular.png" width="400" height="400">

### Triangular

Upper triangular

```python
from soydata.data import make_triangular
from soydata.visualize import scatterplot

X = make_triangular(n_samples=500, upper=True, x_min=0, x_max=10, y_min=0, y_max=10)
p = scatterplot(X, title='Upper triangular', size=3)
```

<img src="./figures/soydata_upper_triangular.png" width="400" height="400">

Lower triangular

```python
X = make_triangular(n_samples=500, upper=False, x_min=0, x_max=10, y_min=0, y_max=10)
p = scatterplot(X, title='Lower triangular', size=3)
```

<img src="./figures/soydata_lower_triangular.png" width="400" height="400">

Lower triangular with negative direction

```python
X = make_triangular(n_samples=500, upper=False, positive_direction=False,
    x_min=0, x_max=10, y_min=0, y_max=10)
p = scatterplot(X, title='Lower triangular with negative direction', size=3)
```

<img src="./figures/soydata_lower_triangular_nd.png" width="400" height="400">

### Decision Tree dataset 1

```python
from soydata.data.classification import make_predefined_data
from soydata.visualize import scatterplot

X, labels = make_predefined_data('decision-tree-1', n_samples=2000)
p = scatterplot(X, labels=labels, size=3, title='decision-tree-1')
```

<img src="./figures/soydata_decision_tree1.png" width="400" height="400">

### Decision Tree dataset 2

```python
X, labels = make_predefined_data('decision-tree-2', n_samples=2000)
p = scatterplot(X, labels=labels, size=3, title='decision-tree-2')
```

<img src="./figures/soydata_decision_tree2.png" width="400" height="400">

### Composition of rectangulars

```python
from soydata.data.supervised import make_complex_rectangulars
from soydata.visualize import scatterplot

X, labels = make_complex_rectangulars(n_samples=3000, n_classes=3,
    n_rectangulars=20, volume=0.5, seed=0)
p = scatterplot(X, labels=labels, title='Complex rectangulars (3 classes)', size=3)
```

<img src="./figures/soydata_complex_rectangulars.png" width="400" height="400">


### Simple clusters

```python
from soydata.data.clustering import make_rectangular_clusters
from soydata.visualize import scatterplot

X, labels = make_rectangular_clusters(n_clusters=8,
    min_size=10, max_size=15, volume=0.2, seed=0)
scatterplot(X, labels=labels, title='Simple clusters')
```

<img src="./figures/soydata_simple_clusters.png" width="400" height="400">

### Linear regression

```python
from soydata.data.regression import make_linear_regression_data
from soydata.visualize import lineplot

x, y, y_true = make_linear_regression_data(n_samples=300, x_range=(-1,1), noise=0.5)
p = lineplot(x, y, show_inline=False, line_width=2, title='linear regression')
# overlay true line
p = lineplot(x, y_true, p=p, line_color='red')
```

<img src="./figures/soydata_linear_regression.png" width="400" height="400">

### Polynomial linear regression

```python
x, y, y_true = make_polynomial_regression_data(degree=5, noise=0.2, seed=11, x_range=(-1.5, 1.5))
p = lineplot(x, y, show_inline=False, line_width=2, title='Polynomial regression')
p = lineplot(x, y_true, p=p, line_color='red')
```

<img src="./figures/soydata_polynomial_linear_regression.png" width="400" height="400">

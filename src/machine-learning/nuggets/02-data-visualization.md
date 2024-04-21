# Data Visualization

## Building Blocks

### Aesthetics

Aesthetics refer to a quantifiable set of features that are mapped to the data in a graphic. They describe every aspect of a given graphic element.

Some aesthetics like position, size, color, and line width work for both `continuous` and `discrete` data, while others (shape & line type) work for only discrete data.

### Scales

You have data, and you have aesthetics. You need some sort of mapping between the two, which is nothing but the `legend` that you plot in your plot.

`Scales` are the mapping between data values and aesthetics values.

Taking an example of a 2D plot, it doesn't mean you can only use two scales. Sometimes you can expand your visualization to five scales (as an example) in the same plot. In this case, it is like providing 5 dimensions in a 2-dimensional figure.

Of all the scales, the most common scales are:

1. Position scale - most commonly uses [Cartesian coordinate system](https://en.wikipedia.org/wiki/Cartesian_coordinate_system). It is ok to use different `aspect ratios` (spacing between grids) across dimensions, unless you're using the same dimension on both the axes.
2. Nonlinear scale (Logarithmic scale) - most commonly used for Nonlinear Axes. This is where you tend to use skewed data because of very different orders of magnitude. This scale is helpful when you're drawing proportions/representing ratios.
3. Color scale - used to distinguish groups of data, or represent data values, or as a tool to highlight

### Types of plots

Most commonly, the kinds of things you're trying to plot are:

* Amounts
* Distributions
* Proportions
* X-Y relationships
* Uncertainty - esp important for A/B tests

Sometimes ordering representation on an axis helps better represent the findings.

### Visualizing distributions

* **Histograms** - when making histograms, always explore multiple bin widths
* **Kernel density plots** - if the values are too small, you instead try to fit a curve to the data through a function, solving the optimization problem (also called curve fitting). To visualize several distributions at once, kernel density plots work better than histograms.
    * Different kernels include Gaussian, Rectangular, etc.
    * Each kernel is parameterized by bandwidth
* Multiple distributions can be represented on `Box plot` (minimum 5 points), or `Violin plot` (also captures density of the points unlike box plot)

For highly skewed distributions, you can still use log of values in visualization to get better representation and information about the data.

### Visualizing proportions

* **Pie charts** - help visually emphasize simple fractions
* **Stacked bars** - preferred when there are only two quantities to compare over time.
    * Stacked density plots can be used to visualize how proportions change in response to a continuous variable.
* **Side-by-side bars** - help visualize easily changing proportions over time

### Visualizing X-Y relationships

When you want to understand relationships between more than one column.

* Scatter plots
* Bubble plots
* Scatterplot matrix - you'll see this a lot in research papers
* Correlograms - uses correlation coefficient

### Visualizing uncertainty

Used a lot in A/B testing. Another example is election polls.

* Probability distribution
* Confidence intervals
* Comparing parameter estimates

In machine learning, the gold standard for launching anything in production, is an A/B test.

## References

* Book: [Fundamentals of Data Visualization](https://learning.oreilly.com/library/view/fundamentals-of-data/9781492031079/), Claus O. Wilke, 2019
    * [Online book](https://clauswilke.com/dataviz/)
    * [GitHub code](https://github.com/clauswilke/dataviz)

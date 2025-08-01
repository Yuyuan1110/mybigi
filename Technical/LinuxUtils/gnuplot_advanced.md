---
tags: Linux, Utils, gnuplot, graphing, plotting
alias: []
created: 2025-08-01
updated:
source:
---

# `gnuplot` Advanced Usage

This note covers more advanced `gnuplot` features. For a basic introduction, see [[gnuplot]].

## Customizing Plots

`gnuplot` offers many options for customizing the appearance of your plots.

- **`set title`**: Adds a title to the plot.
- **`set xlabel` / `set ylabel`**: Sets labels for the x and y axes.
- **`set xrange` / `set yrange`**: Sets the range for the axes.
- **`set grid`**: Adds a grid to the plot.
- **`set key`**: Customizes the plot legend.

### Advanced Example Script (`custom_plot.gp`)

```gnuplot
# Set the output format and file name
set terminal pngcairo size 800,600 enhanced font 'Verdana,10'
set output 'custom_plot.png'

# Set plot titles and labels
set title "Sine and Cosine Functions"
set xlabel "X-axis"
set ylabel "Y-axis"

# Set the axis ranges
set xrange [-pi:pi]
set yrange [-1.5:1.5]

# Add a grid
set grid

# Customize the legend
set key top left

# Plot the functions with custom titles and styles
plot sin(x) title 'Sine' with lines linewidth 2, \
     cos(x) title 'Cosine' with points pointtype 7
```

Run the script:
```bash
gnuplot custom_plot.gp
```

## 3D Plotting

Use the `splot` command for 3D plots.

**Example:**
```gnuplot
# Set the output for a 3D plot
set terminal png
set output '3d_plot.png'

# Plot a 3D surface
splot x**2 + y**2
```

## Fitting Functions to Data

`gnuplot` can fit a function to a set of data points.

**1. Create a data file (`noisy_data.txt`):**
```
# X Y
0.0 0.1
1.0 0.9
2.0 2.2
3.0 2.8
4.0 4.1
```

**2. Create a fit script (`fit.gp`):**
```gnuplot
# Define the function to fit (a line)
f(x) = m*x + c

# Fit the function to the data
fit f(x) 'noisy_data.txt' via m, c

# Set the output
set terminal png
set output 'fit_plot.png'

# Plot the original data and the fitted function
plot 'noisy_data.txt' with points, f(x) with lines
```

Run the script:
```bash
gnuplot fit.gp
```
This will plot the original data points along with the best-fit line.

---
tags: Linux, Utils, gnuplot, graphing, plotting
alias: []
created: 2025-08-01
updated:
source:
---

# `gnuplot` Note

`gnuplot` is a command-line driven graphing utility. It can be used to plot functions and data points in both 2D and 3D.

For more advanced usage, see [[gnuplot_advanced]].

## Basic Usage: Plotting Functions

You can run `gnuplot` in interactive mode or by passing it a script file.

### Interactive Mode

1.  Run `gnuplot` in your terminal.
2.  Use the `plot` command to graph a function.

**Example:**
```gnuplot
# Start gnuplot
gnuplot

# Plot the sine function
plot sin(x)

# Plot multiple functions
plot sin(x), cos(x)
```

### From a Script

1.  Create a file with gnuplot commands (e.g., `plot.gp`).
2.  Run `gnuplot plot.gp`.

**Example `plot.gp` file:**
```gnuplot
# Set the output format and file name
set terminal png
set output 'sine_wave.png'

# Plot the sine function
plot sin(x)
```

Run the script:
```bash
gnuplot plot.gp
```
This will create a file named `sine_wave.png` with the plot.

## Plotting Data Files

`gnuplot` can also plot data from files.

**1. Create a data file (`data.txt`):**
```
# X Y
1 1
2 4
3 9
4 16
```

**2. Plot the data:**

In interactive mode or in a script:
```gnuplot
# Plot the data from the file
plot 'data.txt'

# Plot with lines and points
plot 'data.txt' with linespoints
```

# Investigation: downsample.rate Parameter in CoveragePlot Function

## Summary

The `downsample.rate` parameter was introduced in the `CoveragePlot()` function in **commit f5a84118508d2f0d6b04bd7fd28ad7f3576de461** as part of **version 1.16.0** of the Signac package.

## Commit Details

- **Commit SHA**: f5a84118508d2f0d6b04bd7fd28ad7f3576de461
- **Author**: timoast <4591688+timoast@users.noreply.github.com>
- **Date**: Friday, October 10, 2025 at 16:45:50 +0800
- **Message**: 1.16.0

## Parameter Location

The `downsample.rate` parameter can be found in the file:
- **File**: `R/visualization.R`
- **Function**: `CoveragePlot()`

## Parameter Documentation

From the function documentation in the commit:

```r
#' @param downsample.rate Fraction of positions to retain when downsampling.
#' Retaining more positions can give a higher-resolution plot but can make the
#' number of points large, resulting in larger file sizes when saving the plot
#' and a longer period of time needed to draw the plot.
```

## Default Value

The parameter has a default value of `0.1` (10% of positions retained).

## Usage in Code

The parameter is used in conjunction with `max.downsample` to determine the sampling rate for plotting:

```r
sampling <- ceiling(x = max(max.downsample, window.size * downsample.rate))
```

This ensures that:
1. At minimum, `max.downsample` positions are included
2. The number of positions scales with the window size
3. Downsampling helps manage plot file sizes and rendering time

## Verification

The parameter did not exist in any commits prior to f5a8411, confirming this as the initial introduction.

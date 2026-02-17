# Assignment 3 – India Air Quality Analysis (NO₂)

## Dataset
India Air Quality Data (Kaggle) — NO₂ column extracted for analysis.

## Data Transformation
The raw NO₂ values (`x`) are transformed into a new signal `z` using a student-ID-seeded sinusoidal perturbation:

```
z = x + a_r * sin(b_r * x)
```

where `a_r` and `b_r` are derived from the student registration number `r = 102303491`.

## Graph: Histogram of z and Learned PDF

The single plot in this notebook overlays two things:

1. **Histogram (bars)** — shows the empirical frequency distribution of the transformed NO₂ values (`z`), normalized to probability density. The distribution is right-skewed with the bulk of values concentrated at low NO₂ levels.

2. **Gaussian PDF curve (line)** — a Normal distribution fitted to `z` using its sample mean (μ ≈ 25.81) and standard deviation. The curve is defined as:

   ```
   PDF(z) = c · exp(−λ · (z − μ)²)
   ```

   | Parameter | Value |
   |-----------|-------|
   | μ (mean)  | 25.81 |
   | λ         | 0.00146 |
   | c         | 0.02156 |

The graph confirms that the fitted Gaussian approximates the central mass of the data but underestimates the long right tail — a common characteristic of real-world pollution data.

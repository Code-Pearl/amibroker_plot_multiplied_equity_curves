# Manual Multi-Strategy Portfolio for AmiBroker

A clean and flexible AmiBroker AFL solution to combine multiple trading strategies into a single equal-weighted portfolio equity curve.

## Overview

This repository contains two ready-to-use AFL scripts:

- **Manual 12-Strategy Portfolio** – Full version supporting up to 12 strategies
- **2-Strategy Example** – Simplified starter version with just 2 strategies (ideal for testing and learning)

Both scripts:
- Load equity curves from composite symbols (`~~~Equity_StratX`)
- Forward-fill gaps (Null values)
- Normalize each strategy to the same starting capital
- Calculate an **equal-weighted combined portfolio**
- Plot individual strategies + the final portfolio curve

Perfect for portfolio analysis, strategy allocation, and visual performance comparison.

## Features

- Automatic forward filling of equity curves
- Proper normalization to starting capital (`$100,000` default)
- Equal-weighted averaging
- Clean visualization:
  - Thin grey lines for individual strategies (12-strategy version)
  - Colored lines in the 2-strategy example
  - **Thick lavender/white line** for the combined portfolio
- Final portfolio value shown in chart title
- Easy to customize (add/remove strategies, change colors, rename symbols)

## Files

| File                              | Description                                      |
|-----------------------------------|--------------------------------------------------|
| `Manual-12-Strategy-Portfolio.afl` | Full version – supports 1 to 12 strategies      |
| `2-Strategy-Example.afl`           | Simple version with 2 strategies (recommended for beginners) |

## How It Works

### Step-by-step logic (same in both scripts):

1. **Data Loading**  
   Loads equity curves using `Foreign("~~~Equity_StratX", "C")`

2. **Forward Filling**  
   Replaces Null values by carrying forward the previous equity value

3. **Normalization**  
   Scales every strategy so it starts at `StartCash` (default = 100000)

4. **Combined Portfolio**  
   Simple average: `(e1 + e2 + ... + e12) / 12` (or `/ 2` for the example)

5. **Plotting**  
   Individual strategies + highlighted combined curve

## Usage Instructions

1. Run each of your individual strategies and save their equity curves as composites:
   - `~~~Equity_Strat1`, `~~~Equity_Strat2`, ..., `~~~Equity_Strat12`

2. Open a new chart and apply one of the formulas:
   - Use `Manual-12-Strategy-Portfolio.afl` for up to 12 strategies
   - Use `2-Strategy-Example.afl` to test with just two

3. Customize strategy names or number of strategies as needed.

## Customization Tips

- Change `StartCash` to your preferred starting capital
- Rename the `Foreign()` symbols to match your composites
- Modify plot colors and styles
- Easily scale between 2 and 12 strategies by copying the pattern

### Example: 2-Strategy Version

The `2-Strategy-Example.afl` uses clear variable names (`eq1`, `eq2`) and colored lines (Blue + Bright Green) making it perfect for understanding the logic before scaling up to 12 strategies.

## Requirements

- **AmiBroker** (any recent version)
- Pre-computed equity curves saved as composite symbols starting with `~~~Equity_`

## Why Use This Approach?

- Full transparency and control
- No external portfolio manager required
- Easy to audit and modify
- Excellent for visual comparison of strategy contribution and correlation
- Great for robustness testing and multi-strategy development

## License

MIT License – Free to use and modify.

---

**Built for traders who want simple, transparent, and effective multi-strategy portfolio construction.**

Happy trading! 

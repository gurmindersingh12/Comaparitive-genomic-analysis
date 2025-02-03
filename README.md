# Comparative Heatmap Visualization

## Overview
This repository contains a Python script for generating a comparative heatmap of identity percentages across different wheat genotypes. The heatmap is designed to be visually appealing, colorblind-friendly, and formatted for high-quality publication.

## Files in this Repository
- **heatmap_plot.py**: The Python script for generating the heatmap.
- **Comparative_Heatmap.svg**: The output heatmap saved in high-resolution SVG format.

## Purpose of the Heatmap
The goal of this visualization is to compare identity percentages of genes from different wheat genotypes with Kronos genes. This is particularly useful for analyzing genetic similarity and variability.

## Features and Customizations
### 1. **Data Input**
- The script reads a CSV file (`Comparative.csv`).
- Ensure the file is structured properly, with **Kronos genes as row labels** and **wheat genotypes as column headers**.

### 2. **Color Scheme**
- The colors are chosen to be **colorblind-friendly** and visually distinct:
  - **Light Grey (#B0B0B0)** for **0% identity**
  - **Deep Blue (#1F77B4)** for **97 - 98% identity**
  - **Vivid Orange (#FF7F0E)** for **98 - 99% identity**
  - **Rich Green (#2CA02C)** for **99 - 99.9% identity**
  - **Lighter Red (#FF9999)** for **100% identity**
- These colors can be modified in the script (`final_color_palette`).

### 3. **Legend Customization**
- The legend explains the identity percentages.
- The title is bold and slightly larger (`% Identity`).
- The position is set **at the center-right** (`bbox_to_anchor=(1.05, 0.5)`).
- The legend marker sizes are adjusted for better readability.

### 4. **Gridlines and Formatting**
- **Light grey gridlines** (`linewidths=0.3, linecolor='lightgrey'`).
- **X-axis labels rotated** at **45 degrees** for readability.
- **Y-axis labels italicized** (Kronos genes appear in *italic* format).
- **All fonts are black** to maintain consistency.

### 5. **Output Format**
- The figure is **saved as an SVG file** (`600 dpi resolution`) for high-quality visuals.
- Modify `plt.savefig("Comparative_Heatmap.svg", format="svg", dpi=600, bbox_inches="tight")` to change resolution or file format (e.g., PNG, PDF).

## How to Use This Script
### **Step 1: Install Dependencies**
Ensure you have the required Python libraries installed:
```sh
pip install matplotlib seaborn pandas
```

### **Step 2: Run the Script**
Run the script using:
```sh
python heatmap_plot.py
```

### **Step 3: View or Modify the Output**
- The script generates and saves **Comparative_Heatmap.svg**.
- Open the file in **any vector graphic viewer** or **edit it using Inkscape or Illustrator**.

## Customization Guide
### **Change Color Palette**
Modify the `final_color_palette` dictionary inside `heatmap_plot.py` to adjust colors:
```python
final_color_palette = {
    0: "#B0B0B0",   # Light Grey
    97: "#1F77B4",  # Deep Blue
    98: "#FF7F0E",  # Vivid Orange
    99: "#2CA02C",  # Rich Green
    100: "#FF9999"  # Lighter Red
}
```

### **Adjust Gridline Thickness**
- To make gridlines **thicker**, increase `linewidths` in:
```python
sns.heatmap(df, linewidths=0.5, linecolor='lightgrey')
```
- To **remove gridlines**, set `linewidths=0`.

### **Change X-axis Label Rotation**
Modify the `rotation` angle in:
```python
plt.xticks(rotation=45, ha="right")
```
- Change `rotation=90` for **vertical labels**.

### **Move the Legend**
Adjust the `bbox_to_anchor` values in:
```python
plt.legend(bbox_to_anchor=(1.05, 0.5), loc='center left')
```
- `bbox_to_anchor=(1.05, 1)` moves the legend **higher**.
- `bbox_to_anchor=(1.05, 0)` moves it **lower**.

## Conclusion
This repository provides a **fully customizable** script for generating **publication-ready comparative heatmaps**. Use this guide to tweak the figure as needed!

For questions or modifications, refer to the inline comments in `heatmap_plot.py`.


import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
from matplotlib.patches import Patch
from matplotlib.colors import ListedColormap

# Load the dataset (Modify the file path if needed)
file_path = "Comparative.csv"  # Change this to your file location
df = pd.read_csv(file_path)

# Set 'Kronos' column as the index to use it as row labels
df.set_index("Kronos", inplace=True)

# Define a refined color palette for a visually appealing, colorblind-friendly heatmap
final_color_palette = {
    0: "#B0B0B0",   # Light Grey for 0%
    97: "#1F77B4",  # Deep Blue for 97 - 98%
    98: "#FF7F0E",  # Vivid Orange for 98 - 99%
    99: "#2CA02C",  # Rich Green for 99 - 99.9%
    100: "#FF9999"  # Lighter Red for 100%
}

# Create a custom colormap using the defined color palette
cmap = ListedColormap([final_color_palette[val] for val in sorted(final_color_palette.keys())])

# Define value ranges for colors
bounds = [0, 97, 98, 99, 100, 101]  # Ranges correspond to defined color categories
norm = plt.cm.colors.BoundaryNorm(bounds, cmap.N)

# Initialize figure with appropriate size
plt.figure(figsize=(10, 8))

# Create heatmap
ax = sns.heatmap(df, cmap=cmap, norm=norm, linewidths=0.3, linecolor='lightgrey', cbar=False)

# Define legend labels
updated_legend_labels = {
    0: "0%",
    97: "97 - 98%",
    98: "98 - 99%",
    99: "99 - 99.9%",
    100: "100%"
}

# Create a custom legend with formatted labels and increased size
legend_patches = [Patch(color=final_color_palette[val], label=updated_legend_labels[val], linewidth=2)
                   for val in sorted(updated_legend_labels.keys())]
legend = plt.legend(
    handles=legend_patches, title="% Identity", bbox_to_anchor=(1.05, 0.5), loc='center left',
    fontsize=14, handleheight=2.5, handlelength=3  # Adjust marker sizes for readability
)
legend.get_title().set_fontsize(16)  # Increase title font size
legend.get_title().set_fontweight("bold")  # Make the legend title bold

# Customize axis labels
plt.xlabel("Wheat Genotypes", fontsize=14, fontweight='bold', color='black', labelpad=10)
plt.ylabel("Kronos Genes", fontsize=14, fontweight='bold', color='black', labelpad=10)  # Add spacing

# Italicize y-axis labels (Kronos gene names)
ax.set_yticklabels([f'$\\it{{{label}}}$' for label in df.index], color='black')

# Rotate x-axis labels for better readability
plt.xticks(rotation=45, ha="right", color='black')

# Set tick parameters to ensure all fonts remain black
ax.tick_params(axis='both', colors='black')

# Save the figure as a high-quality SVG file (600 dpi)
plt.savefig("Comparative_Heatmap.svg", format="svg", dpi=600, bbox_inches="tight")

# Display the plot
plt.show()

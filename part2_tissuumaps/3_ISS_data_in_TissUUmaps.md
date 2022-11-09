# Using TissUUmaps for exploring ISS data
By Christophe Avenel

## Data
- Folder: `dataset_2_iss_data/`
- DAPI Image: `6_Base_1_stitched-1.tif`
- Markers: `Cell types.csv` and `Gene Counts.csv`
- Color dictionary: `color_dict.json`

## Gene counts
1. Load the DAPI image 6_Base_1_stitched-1.tif into TissUUmaps. You can do it by dragging and dropping the .tif image file into TissUUmaps space, or using the File > Open menu.
1. Inspect the `Gene Counts.csv` marker file in Excel to understand its structure. It contains three columns: X, Y and Gene (resp. X and Y coordinates of each point on the DAPI image, and its corresponding gene name).

    ![](images/gene_counts_excel.png?raw=true "Gene counts in excel")
1. Load the `Gene Counts.csv` marker file into TissUUmaps, either by drag and drop again, or through the Markers tab in TissUUmaps, using the `[+]` button.
1. Give a new name to the created Tab (for example: `"Gene Counts"`) and select X and Y columns as coordinates.
1. You can already display your markers by clicking on **[Update view]**. All markers will have the same color and be in one group named “All”.
1. In **Render Options**, group markers by Gene name, by selecting the Gene column as Key.
1. In **Advanced Options**, change the marker size factor to 0.1, to make all gene markers smaller.
1. Click **[Update view]** again, to see how markers are divided into different gene names, with different colors and shapes.
1. Hover your mouse on the ![](images/eye.png?raw=true "Eye") icon in the marker list to display one gene at a time, or select multiple genes using the checkboxes ![](images/checkbox.png?raw=true "Checkbox") on the left.

## Cell types
1. Load the Cell types.csv marker file into a new tab, either by drag and drop again, or using the [+] button.
1. Give a new name to the created Tab (for example: Cell types) and select X and Y columns as coordinates.
1. In **Render options**, group markers by Cell type, by selecting the Gene column as Key.
1. To use pre-selected colors, check the option “Use color from dictionary” in `Render Options > Color options`, and copy paste the content of the file 
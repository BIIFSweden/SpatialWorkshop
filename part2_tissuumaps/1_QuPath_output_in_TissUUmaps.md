# Using TissUUmaps for exploring QuPath output and cell-cell interactions
By Andrea Behanova

## Data
- Images: 10 channels of one image core (TMA core, .tif)
- Markers: GT from Lina, classification from QuPath (.csv)
- Regions: Geojson masks from QuPath  (.json)

In case something is not clear you can always search for help in our documentation: https://tissuumaps.github.io/TissUUmaps-docs/.

## General
1. Install TissUUmaps: https://tissuumaps.github.io/download/.
1. Load all 10 image channels into TissUUmaps. You can do it by dragging and dropping 10 individual .tif image files into TissUUmaps space. They will be listed in the tab Image layers.
1. Now load the output .csv file from QuPath by clicking on tab Markers, clicking the plus sign, selecting the desired file from your computer under the section File and coordinates - Choose file.
1. You can change the Tab name to any desired name, then you need to select the column names from the .csv file corresponding to the X and Y coordinates.
1. In the section Render options, you can define a key to group by, that is a column from the .csv file which will be used to display the dataset grouped by different colors and shapes of the marker.
1. Click the *Update View* button.
1. Now you can explore the classification results in form of the markers in the spatial view, you can zoom in or zoom out, select which groups should be displayed, etc.
1. To load the segmentation results from QuPath, you need to go to the tab Regions and press Import -> Choose File -> select the desired file from your computer and press the button Import.
1. All the segmentation regions are displayed on top of the image and you can fill them by clicking the check box next to the regions, or you can just fill all regions by clicking the button Fill all regions. Selected regions can also be analyzed by clicking the button Analyze group meaning displaying a list of all the marker keys with their counts inside that region (expression).
1. In order to present further TissUUmaps functions, we first need to install the plugins.
1. Open the menu Plugins -> Add plugin, check the boxes in front of the plugins ClassV&QC and InteractionV&QC, click Install, and re-start TissUUmaps.

## Classification comparison:
1. Open TissUUmaps.
1. Load all 10 image channels into TissUUmaps. You can do it by dragging and dropping 10 individual .tif image files into TissUUmaps space. They will be listed in the tab Image layers.
1. Now load the output .csv file from QuPath by clicking on tab Markers, clicking the plus sign, selecting the desired file from your computer under the section File and coordinates - Choose file.
1. You can change the Tab name to any desired name, then you need to select the column names from the .csv file corresponding to the X and Y coordinates.
1. In the section Render options, you can define a key to group by, that is a column from the .csv file which will be used to display the dataset grouped by different colors and shapes of the marker.
1. Click the Update View button.
1. Now repeat steps 3-6 but for the ground truth file (file name) containing manual annotations.
1. Save the project as a .tmap file by opening the menu File -> Save project. In order to save the project together with the .csv file, it is necessary to generate a button first. A warning window appears and you need to generate the button. The path to the .csv file needs to be relative to the path of the image.
1. Then you select a suitable directory to save the project and write the project file name, i.e. My_project**.tmap**, and the project is saved.
1. Open the plugin ClassV&QC by clicking the menu Plugins -> ClassQC.
1. In the plugin’s pop-up menu Select marker Dataset 1 - select the ground truth dataset, in the pop-up menu Select column of Dataset 1 - select the column of Dataset 1 containing the classification results, in the pop-up menu Select marker Dataset 2 - select the dataset resulting from QuPath, in the pop-up menu Select column of Dataset 2 - select the column of Dataset 2 containing the classification results.
1. Click the Display button and explore misclassification from the spatial point of view. You can click on the cells and see the cropped patches from all 10 channels. The size of the displayed patches can be adjusted in the settings Figure size.

## Interaction:
1. Open TissUUmaps.
1. Load DAPI image. You can do it by dragging and dropping the .tif image file into TissUUmaps space.
1. Now load the.csv file of one classification marker dataset by clicking on tab Markers, clicking the plus sign, selecting the desired file from your computer under the section File and coordinates - Choose file.
1. You can change the Tab name to any desired name, then you need to select the column names from the .csv file corresponding to the X and Y coordinates.
1. In the section Render options, you can define a key to group by, what is a column from the .csv file which will be used to display the dataset grouped by different colors and shapes of the marker.
1. Click the Update View button.
1. Save the project as a .tmap file by opening the menu File -> Save project. In order to save the project together with the .csv file, it is necessary to generate a button first. A warning window appears and you need to generate the button. The path to the .csv file needs to be relative to the path of the image.
1. Then you select a suitable directory to save the project and write the project file name, i.e. My_project**.tmap**, and the project is saved.
1. Open the plugin InteractionV&QC by clicking the menu Plugins -> InteractionQC.
1. Next, we want to calculate the neighborhood enrichment test (NET) and save the results as a .csv file: Open the following Google Colab link: https://colab.research.google.com/drive/1KN9hkFp_ZpJcB4jQxajHlHNHbMe0Ts4N?usp=sharing and copy the notebook to your drive by clicking File -> Save a copy in Drive. Now the notebook has been copied to your Google Drive.
1. Load the .csv file which will be analyzed by clicking the icon of a folder (![](images/folder.png?raw=true "Folder")) saying Files on the left panel -> then clicking icon ![](images/upload.png?raw=true "Upload") saying Upload to session storage and choose the .csv file from your computer which will be subsequently loaded.
1. Define the file name at:
    ```python
    #define which file_name to load:
    file_name = '5_10_B.csv'
    ```
1. Define the column names of X, Y coordinates and the classification results at: 
    ```python
    #define column name containing X coordinates:
    X_name = 'X'
    #define column name containing X coordinates:
    Y_name = 'Y'
    # define column name containing classification results:
    Classification = 'Cell_type'
    ```
1. Run the notebook, start by pressing the symbol play ![](images/play.png?raw=true "Play") in the first notebook element, then click on the second element and click on the tab Runtime -> Run after. This will result in saving the output matrix from NET and a .csv file named Neighborhood_enrichment_test_file_name_squidpy.csv in the local session. Download this file to your computer by left click on the file and selecting Download. (The result will be lost if the notebook is closed).
1. Now we can go back to the TissUUmaps software.
1. Open plugin InteractionV&QC by clicking the menu Plugins -> InteractionQC.
1. In the pop-up menu Select marker dataset - select the marker dataset which will be used for the interactive visualization of the NET matrix, 
1. In the menu Select file - select the .csv file from the computer which was downloaded from the Google Colab notebook.
1. Then click the button Display Neighborhood Enrichment Test - to load the .csv file and displays an interactive matrix where you can click on the elements and see the corresponding 2 cell types on top of the displayed image in the spatial viewport.
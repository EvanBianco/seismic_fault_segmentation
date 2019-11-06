# Seismic Fault Segmentation

This repo provides codes to generate 2D images (PNG) from a seismic data volume to be used in some machine-learning image segmentation challenges.

## Data generation
The seismic data used in this exercise is from the Kerry 3D data set (1 GB) offshore New Zealand: https://dataunderground.org/dataset/kerry. The notebook entitled, `Image_slices_from_3d_seismic.ipynb` uses that data set. The inline and crossline parameters are not correctly placed in the SEGY file, so that notebook demonstrates how to read the Textual File Header to figure out the shape of the data and reshape the data into a 3D cube.

## Fault segmentation picking and annotation
A series of image tiles are generated from this volume and exported to be used in Microsoft's Visual Object Tagging Tool, https://github.com/microsoft/VoTT. 

![VoTT picking example](https://raw.githubusercontent.com//EvanBianco/seismic_fault_segmentation/blob/master/images/VoTT_seismic_fault_pick.PNG)

## Model generation
After using VoTT to manually pick and tag fault regions within the images, one of the options to export the regions for is a JSON formatted file. The notebook entiteled `Fault_Polygon_masks.ipynb` takes this JSON file as input, and then creates PNG images of the polygons using masks. These fault mask images match the corresponding seismic data images so they can be inserted into a neural network architecture.
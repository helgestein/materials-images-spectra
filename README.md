# MaterialsImages
This repository contains code for handling the materials images and spectra dataset that is the largest expermental materials science dataset containign composition, images, UV-Vis spectra and processing information for about 180.000 compositions.
The stand alone dataset can be found [here](https://data.caltech.edu/records/1152) and is published under the creative commons [cc-by](https://creativecommons.org/licenses/by/4.0/) license. The data was aquired at the [Joint Center for Artificial Photosynthesis](https://solarfuelshub.org/thrust-2) at Caltech.
## Installation
You'll need to install h5py and tqdm in a python >=3.6 environment via
```
pip install h5py tqdm
```
## Usage
During the first run the script will try to download the dataset to the current work directory. To use this script simply run
```python
from MaterialsImages import MaterialsImages
```
depending on your internet connection this might take a while.
If you want to know which attributes to this dataset are available run this code that will also tell you the shape of each attribute
```python
m = MaterialsImages()
m.show_datasets()
```
There are come convenience functions build in like get spectrum that will return a spectrum (here number 1337)
```python
spectrum = m.get_spectrum(1337)
```
The same functions exist for image and loading.
A special function is get_composition_string which will return a materialsproject compatible composition spring. Please note that we do not know the actual Oxygen content so that the string does not contain Oxygen.
```python
composition_string = m.get_composition_string(1337)
```
If you have sufficient RAM (ca. 16GB should suffice) you can also load al spectra,images etc. into memory by calling
```python
m.load_all_spectra_to_memory()
m.load_all_compositions_to_memory()
m.load_all_images_to_memory() #this will take a while
```
The images and spectra are then accessibile (faster) by calling m.spectra[1337] etc.

## Citation
When using this data for a scientific publication please consider citing the data descriptor published in Scientific Data:
```
Stein, H.S., Soedarmadji, E., Newhouse, P.F., Guevarra, D., Gregoire, J.M., Synthesis, optical imaging, and absorption spectroscopy data for 179072 metal oxides
```
This dataset was first used in our [publication on variational and generative autoencoders to use materials image embeddings for spectrum prediction and vice versa](https://doi.org/10.1039/C8SC03077D). Please consider citing:
```
Stein, H.S., Guevarra, D., Newhouse, P.F., Soedarmadji, E., Gregoire, J.M., Machine learning of optical properties of materials
– predicting spectra from images and images from spectra Chemical Science, 2019, 10, 47 DOI: 10.1039/c8sc03077d
```

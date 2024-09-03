# LISA mbhb-catalogs
Data release supporting:

- _Stars or gas? Constraining the hardening processes of massive black-hole binaries with LISA_. Alice Spadaro, Riccardo Buscicchio, David Izquerdo-Villalba, Antoine Klein, Geraint Pratten, Davide Gerosa. [arXiv:2409.XXYY](https://arxiv.org/abs/2409.XXYY).

## Credits

You are welcome to use this dataset in your research. We kindly ask you to cite the paper above. 
If you want to cite this data release specifically, the DOI code is: [![DOI](https://zenodo.org/badge/DOI/XX.YYYY/zenodo.XXYYWWZ.svg)](https://doi.org/XX.YYYY/zenodo.XXYYWWZ).


## Data

Data need to be downloaded from the [github release page](https://github.com/RiccardoBuscicchio/lisa-mbhb-catalogs/releases). 
The total size is ~450MB.

We provide 1000 simulated LISA realizations (referred to as catalogs), named `LisaCatalog_*.h5`. 

- Each catalog contains a variable number of sources: it can be loaded in a single panda dataframe using the snippet in the accompanying Jupyter notebook (with a few example lines to access binary systems parameters).
# LISA mbhb-cats-and-samps 🐈‍⬛ & 🌽

Data release supporting:
- _Stars or gas? Constraining the hardening processes of massive black-hole binaries with LISA_. 
(**EDIT WITH FINAL AUTHORSHIP**)
Alice Spadaro, Riccardo Buscicchio, David Izquerdo-Villalba, Davide Gerosa, Antoine Klein, Geraint Pratten. [arXiv:2409.XXYY](https://arxiv.org/abs/2409.XXYY).

## Credits

You are welcome to use this dataset in your research. We kindly ask you to cite the paper above. 
If you want to cite this data release specifically, the DOI code is: [![DOI](https://zenodo.org/badge/DOI/XX.YYYY/zenodo.XXYYWWZ.svg)](https://doi.org/XX.YYYY/zenodo.XXYYWWZ).


## Data

Data need to be downloaded from the [github release page](https://github.com/RiccardoBuscicchio/lisa-mbhb-catalogs/releases). 
The total size is ~XYZMB in total: ~450MB for the catalogs, ~XYZ for the posterior samples of the reference catalog.
We provide 1000 simulated LISA realizations, in `catalogs/LisaCatalogFrame_*.h5`.
Similarly, posterior samples for each event analyzed are in `samples/source_*.h5`.
  

## Requirements
To read catalogs and samples you just need the [pandas](https://pandas.pydata.org/) python package. 

## LISA Catalogs

Reading a catalog is as simple as 

```python
import pandas as pd
# Read the catalog
catalog_number = 1
cat = pd.read_hdf(f'catalogs/LisaCatalogFrame_{catalog_number}.h5', key='events')
# Inspect events in the catalog
print(cat.head())
``` 

If you want to open TheCatalog, as we refer to it in the publication, use `catalog_number=713`.

## Units and conventions

Catalog columns are source parameters used for injection, `f_cut`,`Gas fraction`, `SNR`, `Detection`.

Units for source parameters, `f_cut`, `Gas fraction`, are specified in the dictionary below:
```python
dimensionsdict = {
 'DimensionlessSpin1': 'dimensionless',
 'DimensionlessSpin2': 'dimensionless',
 'EclipticLongitude': 'radian',
 'Gas fraction': 'dimensionless',
 'InitialOrbitalPhase': 'radian',
 'LuminosityDistance': 'parsec',
 'Mass ratio': 'dimensionless',
 'MergerTimeOrInitialOrbitalFrequency': 'second',
 'Polarization': 'dimensionless',
 'Redshift': 'dimensionless',
 'RedshiftedMass1': 'dimensionless',
 'RedshiftedMass2': 'solar mass',
 'SNR': 'solar mass',
 'cosInclination': 'dimensionless',
 'f_cut': 'Hz',
 'sinEclipticLatitude': 'dimensionless',
 }
 ```
 for their definitions, please refer to the paper. 
The only exception: `f_cut`, which corresponds exactly to `5*f_isco`, the latter being defined in the paper. 

 SNR is either a float or `NaN`, for the reason specified in the `Detection` string:
 - `Yes`: Source is detectable
 - `LowSNR`: Source is not detectable, given the SNR threshold
 - `LowMassRatio`: Source has too low mass-ratio, for the waveform to be used confidently
 - `OutOfBand`: the source is undetectable because its signal is outside the LISA sensitivity band


## TheCatalog event posterior samples

Reading posterior samples from an event of TheCatalog is as simple as 

```python
import pandas as pd
event_number = 1
# Read the samples from the first event 
samples = pd.read_hdf(f'TheCatalog_samples/source_{event_number}.h5', key='samples')
# Inspect the samples
samples.head()
```

Units and conventions are the same as for the Catalog, with the addition of the (unnormalized) log-likelihood column `logL`.

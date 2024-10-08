# Frilement 📂

Frilement is a Python librairy to split large data files like `csv` files into multiple little files, inside folders (clusters) or not.

## Available file formats 📃
### Input ↩️

- CSV
- Parquet

### Output ↪️

- CSV

## How to use 💯
### Create the configuration 📈

To begin you'll need to fill the config object.
```py
from frilement import FrilementConfig

CONFIG: FrilementConfig = FrilementConfig(
    "./output",  # Path to the output folder
    250e6,  # Max amount of datas loaded in memory at a time
    250_000,  # Max size of a result file
    True,  # Determins if file clustering is enabled
    20,  # Max amount of file by cluster
    8192  # Size of datas loaded for CSV delimiter analyzer
)
```
> NB : Here I have specified defaults values, but your free to adjust them.

### Usage 📘

To use it you have two main ways to operate. You can fragment from one or multiple file source.
```py
from frilement import FrilementConfig, FrilementService, FileFormat

CONFIG: FrilementConfig = FrilementConfig(
    "./output",  # Path to the output folder
    250e6,  # Max amount of datas loaded in memory at a time
    250_000,  # Max size of a result file
    True,  # Determins if file clustering is enabled
    20,  # Max amount of file by cluster
    8192  # Size of datas loaded for CSV delimiter analyzer
)

FrilementService.frilement("./my_single_csv.csv", CONFIG, FileFormat.CSV)  # Here the output file format is optionnal
FrilementService.frilements(["./my_csv.csv", "./my_other_csv.csv"], CONFIG, FileFormat.CSV)
```
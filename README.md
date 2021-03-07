# The trackintel Framework


[![PyPI version](https://badge.fury.io/py/trackintel.svg)](https://badge.fury.io/py/trackintel)
[![Build Status](https://travis-ci.org/mie-lab/trackintel.svg?branch=master)](https://travis-ci.org/mie-lab/trackintel)
[![Documentation Status](https://readthedocs.org/projects/trackintel/badge/?version=latest)](https://trackintel.readthedocs.io/en/latest/?badge=latest)
[![codecov.io](https://codecov.io/gh/mie-lab/trackintel/coverage.svg?branch=master)](https://codecov.io/gh/mie-lab/trackintel)
          
*trackintel* is a library for the analysis of spatio-temporal tracking data with a focus on human mobility. The core of *trackintel* is the hierachical data model for movement data that is used in transport planning [[1]](#1). We provide functionalities for the full life-cycle of human mobility data analysis: import and export of tracking data of different types (e.g, trackpoints, check-ins, trajectories), preprocessing, data quality assessment, semantic enrichment, quantitative analysis and mining tasks, and visualization of data and results.
Trackintel is based on [Pandas](https://pandas.pydata.org/) and [GeoPandas](https://geopandas.org/#)

You can find the documentation on the [trackintel documentation page](https://trackintel.readthedocs.io/en/latest).

Try *trackintel* online in a MyBinder notebook: [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/mie-lab/trackintel/master?filepath=%2Fexamples%2Fexample_geolife%2FTrackintel_introduction.ipynb)

## Data model

An overview of the data model of *trackintel*:
* **positionfixes** (Raw tracking points, e.g., GPS recordings or check-ins)
* **staypoints** (Locations where a user spent time without moving, e.g., aggregations of positionfixes or check-ins)
* **activities** (Staypoints with a purpose and a semantic label, e.g., meeting to drink a coffee as opposed to waiting for the bus)
* **locations** (Important places that are visited more than once, e.g., home or work location)
* **triplegs** (or stages) (Continuous movement without changing mode, vehicle or stopping for too long, e.g., a taxi trip between pick-up and drop-off)
* **trips** (The sequence of all triplegs between two consecutive activities)
* **tours** (A collection of sequential trips that return to the same location)

An example plot showing the hierarchy of the *trackintel* data model can be found below:

<p align="center">
  <img width="492" height="390" src="/docs/assets/hierarchy.png">
</p>

The image below explicitly shows the definition of **locations** as clustered **staypoints**, generated by one or several users.

<p align="center">
  <img width="720" height="405" src="/docs/assets/locations_with_pfs.png">
</p>

You can enter the *trackintel* framework if your data corresponds to any of the above mentioned movement data representation. Here are some of the functionalities that we provide: 

* **Import**: Import from the following data formats is supported: `geopandas dataframes` (recommended), `csv files` in a specified format, `postGIS` databases. We also provide specific dataset readers for popular public datasets (e.g, geolife).
* **Aggregation**: We provide functionalities to aggregate into the next level of our data model. E.g., positionfixes->staypoints; positionfixes->triplegs; staypoints->locations; staypoints+triplegs->trips; trips->tours
* **Enrichment**: Activity semantics for staypoints; Mode of transport semantics for triplegs; High level semantics for locations

## Installation and Usage
*trackintel* is on [pypi.org](https://pypi.org/project/trackintel/), you can install it in a `GeoPandas` available environment using: 
```{python}
pip install trackintel
```

You should then be able to run the examples in the `examples` folder or import trackintel using:
```{python}
import trackintel
```

## Development
You can find the development roadmap under `ROADMAP.md` and further development guidelines under `CONTRIBUTING.md`.

## Contributors

*trackintel* is primarily maintained by the Mobility Information Engineering Lab at ETH Zurich ([mie-lab.ethz.ch](http://mie-lab.ethz.ch)).
If you want to contribute, send a pull request and put yourself in the `AUTHORS.md` file.

## References
<a id="1">[1]</a>
[Axhausen, K. W. (2007). Definition Of Movement and Activity For Transport Modelling. In Handbook of Transport Modelling. Emerald Group Publishing Limited.](
https://www.researchgate.net/publication/251791517_Definition_of_movement_and_activity_for_transport_modelling)

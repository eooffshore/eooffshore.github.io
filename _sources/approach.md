# Approach

## Objectives

The objectives of this work are: 

1. Investigate use of open data to increase wind measurement coverage of the [Irish Continental Shelf (ICS)](https://www.marine.ie/Home/site-area/irelands-marine-resource/real-map-ireland) region, for renewable energy assessment of offshore Areas Of Interest (AOIs).
2. Scalable data processing for offshore wind analysis, for example wind speed extrapolation and power density estimation.
3. Prototype wind atlas service, demonstrating interactive offshore AOI wind and power density maps.


## Project Activities

The following activities were undertaken:

1. **EOOffshore data catalog:** wind products were retrieved from multiple data providers, preprocessed, and persisted to chunked, compressed [Zarr](https://zarr.readthedocs.io/en/stable/) stores, which provide a cloud-optimised format suitable for multi-dimensional arrays. All EOOffshore data sets are accessible using the EOOffshore [Intake](https://intake.readthedocs.io/en/latest/) catalog. Each [catalog](https://intake.readthedocs.io/en/latest/catalog.html) entry provides a description and metadata associated with the corresponding data set, defined in a [YAML configuration file](https://intake.readthedocs.io/en/latest/catalog.html#yaml-format). The EOOffshore catalog configuration was originally influenced by the [Pangeo Cloud Data Store atmosphere.yaml catalog configuration](https://github.com/pangeo-data/pangeo-datastore/blob/master/intake-catalogs/atmosphere.yaml). Catalog details, including Jupyter notebooks describing data set creation, are provided [here](datasets).

2. **Scalable catalog processing:** Zarr data sets in the EOOffshore catalog are loaded and processed using [xarray](https://docs.xarray.dev/en/stable/index.html), a library for processing N-D labeled arrays and datasets. As xarray labels take the form of dimensions, coordinates and attributes on top of [NumPy](https://numpy.org/)-like arrays, it is particularly suited to the catalog data sets whose variables feature latitude/longitude grid coordinates. To enable support for potentially large data sets, processing of the underlying variable arrays involves [Dask](https://docs.dask.org/en/latest/), a parallel, out-of-core computing library. Zarr data set variables are loaded into [Dask arrays](https://docs.dask.org/en/latest/array.html), which are processed in parallel as [chunks](https://docs.dask.org/en/latest/array.html) during subsequent computation. This approach results in a scalable solution that can be applied to data sets of arbitrary sizes (related to heterogeneous spatial and temporal resolutions). Further details may be found in the [Offshore Wind in Irish Areas Of Interest](./Offshore_Wind_AOI) and [Comparison of Offshore Wind Speed Extrapolation and Power Density Estimation](./Comparison_Wind_Power) notebooks. All notebooks were executed using the [base Docker image for Pangeo JupyterHubs and BinderHubs](https://github.com/pangeo-data/pangeo-docker-images/tree/master/base-image).

3. **Interactive wind atlas prototype:** a prototype wind atlas has been developed, using an interactive dashboard. This features a power density map highlighting AOIs, and plots and tables similar to those provided in the [Offshore Wind in Irish Areas Of Interest](./Offshore_Wind_AOI) and [Comparison of Offshore Wind Speed Extrapolation and Power Density Estimation](./Comparison_Wind_Power) notebooks. It operates on the EOOffshore catalog, and is implemented using [Bokeh](https://bokeh.org/) and [HoloViz](https://holoviz.org/) libraries, including [HoloViews](https://holoviews.org/), [GeoViews](http://geoviews.org/), [hvPlot](https://hvplot.holoviz.org/), [Panel](https://panel.holoviz.org/) and [Datashader](https://datashader.org/). The current prototype is described in the [MÉRA-based Wind Atlas for Irish Continental Shelf region](./MERA_ICS_Wind_Atlas) notebook.

This approach has been inspired by:

1. [Pangeo Gallery](https://gallery.pangeo.io/), for example, the [NASA CCMP Winds Gallery](https://gallery.pangeo.io/repos/cgentemann/pangeo_ccmp)   
1. [Pangeo Showcase Webinar Series](https://pangeo.io/pangeo-showcase.html), for example:
   * Gentemann, C.: [Accessing Sea Surface Temperature Data on the Cloud](https://discourse.pangeo.io/t/may-19-2021-accessing-sea-surface-temperature-data-on-the-cloud/1503), Pangeo Showcase, 19 May 2021, [https://doi.org/10.5281/zenodo.4783039](https://doi.org/10.5281/zenodo.4783039) [![https://doi.org/10.5281/zenodo.4783039](https://zenodo.org/badge/DOI/10.5281/zenodo.4783039.svg)](https://doi.org/10.5281/zenodo.4783039)
   * Kellndorfer, J.: [The new era of SAR time series: Tackling big EO data analysis and visualization with Pangeo tools](https://discourse.pangeo.io/t/may-12-2021-the-new-era-of-sar-time-series-tackling-big-eo-data-analysis-and-visualization-with-pangeo-tools/1475), Pangeo Showcase, 12 May 2021, [https://doi.org/10.5281/zenodo.4756696](https://doi.org/10.5281/zenodo.4756696) [![https://doi.org/10.5281/zenodo.4756696](https://zenodo.org/badge/DOI/10.5281/zenodo.4756696.svg)](https://doi.org/10.5281/zenodo.4756696)
1. Discussion in [Pangeo Discourse](https://discourse.pangeo.io/) and [Pangeo GitHub issues](https://github.com/pangeo-data).
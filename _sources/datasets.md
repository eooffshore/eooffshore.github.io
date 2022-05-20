# Irish Continental Shelf Data Sets

The EOOffshore project has involved the creation of a new wind data catalog, consisting of a collection of analysis-ready, cloud-optimized (ARCO) data sets, 
which features up to 21 years of available in situ, reanalysis, and satellite observation wind data products for the [Irish Continental Shelf](https://www.marine.ie/Home/site-area/irelands-marine-resource/real-map-ireland) region.

| ![Irish Continental Shelf](images/ics.png) |
| :--: |
|  | 

The [Intake library](https://intake.readthedocs.io/en/latest/) is used to manage this catalog, where ARCO datasets have been generated using the [Zarr](https://zarr.readthedocs.io/en/stable/) format, enabling subsequent scalable processing with [xarray](https://zarr.readthedocs.io/en/stable/) and [Dask](https://dask.org/). 

| Data | Provider | Time | # Products | Products Size (GB) | Zarr (GB) |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| [ASCAT Near Real Time L3 Sea Winds](https://resources.marine.copernicus.eu/product-detail/WIND_GLO_WIND_L3_NRT_OBSERVATIONS_012_002) | [Copernicus Marine Service](https://marine.copernicus.eu/) | 2016-01 to 2021-09 | 324 | 16 | 11 |
| [ASCAT Reprocessed L3 Sea Winds](https://resources.marine.copernicus.eu/product-detail/WIND_GLO_WIND_L3_REP_OBSERVATIONS_012_005) | [Copernicus Marine Service](https://marine.copernicus.eu/) | 2007-01 to 2021-07 | 412 | 21 | 14 |
| [CCMP Wind V2.1 NRT](http://www.remss.com/measurements/ccmp/) | [Remote Sensing Systems](http://www.remss.com) | 2015-01 to 2021-09 | 2,436 | 109 | 0.5 |
| [ERA5 Hourly Single Level](https://cds.climate.copernicus.eu/cdsapp##!/dataset/reanalysis-era5-single-levels) | [Copernicus Climate Change Service](https://climate.copernicus.eu/) | 2001-01 to 2021-09 | 249 | 10 | 16 |
| [Met Éireann Re-Analysis (MÉRA)](https://www.met.ie/climate/available-data/mera) | [Met Éireann](https://www.met.ie/about-us) | 2001-01 to 2016-12 | 1,920 | 226 | 196 |
| [Sentinel-1 L2 OCN](https://sentinel.esa.int/web/sentinel/technical-guides/sentinel-1-sar/products-algorithms/level-2-algorithms) | [Copernicus Open Access Hub](https://scihub.copernicus.eu/); [Alaska Satellite Facility](https://asf.alaska.edu/) | 2015-06 to 2021-09 | 17,698 | 241 | 12 |
| [Irish Weather Buoy Network](http://www.marine.ie/Home/site-area/data-services/real-time-observations/irish-weather-buoy-network-imos) | [Marine Institute](https://www.marine.ie/Home/home) | 2001-05 to 2021-09 | 1 | 0.08 | n/a |

Overviews of the catalog data sets are provided in the following notebooks:

1. [Advanced SCATterometer (ASCAT) Sea Surface Winds](ASCAT_ICS_Wind_Data)
1. [Cross-Calibrated Multi-Platform (CCMP) Wind Vector Analysis](CCMP_ICS_Wind_Data)
1. [ERA5 Hourly Single Level Wind](ERA5_ICS_Wind_Data)
1. [Met Éireann Re-Analysis (MÉRA) Wind](MERA_ICS_Wind_Data)
1. [New European Wind Atlas (NEWA)](NEWA_ICS_Wind_Data)
1. [Sentinel-1 Ocean (OCN) Wind](Sentinel-1_ICS_Wind_Data)

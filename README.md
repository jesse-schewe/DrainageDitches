# DrainageDitches
**This repository is simultaneously me learning github and working on a new project regarding drainage in Minnesota.**

Start with finding what drainage basins in Minnesota are already defined.\
Resources:\
[USGS Hydrologic Unit Codes (HUCs) Explained](https://nas.er.usgs.gov/hucs.aspx)\
[Minnesota's watershed basins](https://www.dnr.state.mn.us/watersheds/map.html)\
[National Map Downloader](https://apps.nationalmap.gov/downloader/#/)\
\
Aim for units that have an area ~100km<sup>2</sup>\
3rd level hydrologic unit, basi, 6 digit code, are too big\
\
**Collecting Data**\
[Access National Hydrography Products](https://www.usgs.gov/national-hydrography/access-national-hydrography-products)\
Click [Download the NHDPlus HR by 4-digit Hydrologic Unit (HU4) for CONUS or by 8-digit Hydrologic Unit (HU8) for Alaska](https://prd-tnm.s3.amazonaws.com/index.html?prefix=StagedProducts/Hydrography/NHDPlusHR/)\
Click National/\
Click GDB/\
Click NHDPlus_H_National_Release_1_GDB.zip\
After opening in QGIS, this appears to have lots of data but the HUCs are too large for my purposes\
\
In the same download website, I went up a level to select WBD/\
Click National/\
Click GDB/\
This gdb had trouble displaying in QGIS on Ubuntu. Filezilla'd the gdb to Windows and was able to successfully open in ArcGIS Pro. The data contain columns that include which states they are a part of --nice. \
\
[The Watershed Boundary Dataset (WBD)](https://www.usgs.gov/media/images/wbd-v231-model-poster-12202021) is what I should have been looking at to start with, but the USGS website didn't make it super easy for me to figure out what was what.\
WBDHU8 has sizes from 1,590.16 skm to 84,944.11 sqkm with the median at 5,121.81 sqkm.\
WBDHU10 has sizes from 102 sqkm to 82,002.48 sqkm with the median at 624.18 sqkm.\
The max is so large because of the Lake Superior unit\
\
In ArcGIS Pro, exported features with states column containing MN from WBDHU10 as WBDHU10_MN\
Shipped exported shapefiles over to Ubuntu to work in Jupyter Notebooks\
Downloaded N44W094.hgt dem tile of MN from from [Shuttle Radar Topography Mission](https://dwtkns.com/srtm30m/) for testing\
\
After a fair amount of [prototyping](https://github.com/jesse-schewe/DrainageDitches/blob/main/HUC.ipynb) I was able to come up with [HUC_Func](https://github.com/jesse-schewe/DrainageDitches/blob/main/HUC_Func.ipynb) as a semi ready to go script to parse out pieces of a raster based on collection of polygons


---
date: 2024-12-15
title: Creating a GeoColor image from GOES-West/GOES-East L2 data using SatPy
---

After a significant amount of trial and error, I figured out how to use SatPy to create a GeoColor image from GOES satellites. I tried doing the same with Himawari L1 data, but the process kept running out of memory and crashing. Not sure why.

## Installation

```bash
pip install satpy[all]
# in case that did not install everything:
pip install satpy[geotiff]
pip install satpy[rayleigh]
pip install satpy[generic_image]
```

## Data download

If using L2 data, it needs to be `ABI-L2-MCMIPC` for CONUS, or equivalent for other regions. For example, navigate to https://noaa-goes16.s3.amazonaws.com/index.html#ABI-L2-MCMIPC/2024/350/15/ and download [this file](https://noaa-goes16.s3.amazonaws.com/ABI-L2-MCMIPC/2024/350/15/OR_ABI-L2-MCMIPC-M6_G16_s20243501531173_e20243501533558_c20243501534081.nc).

## Generation

Having placed the file in, say, `/home/user/abi`, the following Python code should generate a GeoColor GeoTIFF image:

```python
from satpy import Scene, find_files_and_readers

files = find_files_and_readers(base_dir="/home/user/abi",reader="abi_l2_nc")
scn = Scene(filenames=files)
scn.available_composite_names()
scn.load(scn.available_dataset_names())
scn.load(["geo_color"])
new_scn = scn.resample(scn["C01"].attrs["area"],resampler="nearest",reduce_data=False)
new_scn.save_dataset("geo_color",filename="geocolor.tif")
```

In theory, to reduce RAM usage, the following can be executed before generating the GeoColor image, but it didn't seem to help anything in my case:

```python
import dask

dask.config.set(num_workers=2)
dask.config.set({"array.chunk-size": "32MiB"})
```

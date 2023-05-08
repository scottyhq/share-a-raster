# share-a-raster

template repository for sharing a COG via github pages

This can be a convenient way to share a collection of COGs with someone for troubleshooting. 

1. Click the green `Use This Template` button
2. Enable [GitHub Pages for your repository](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow)
3. Add COGs to the cogs/ folder


## Example
We use this [Landsat COG from MS Planetary Computer](https://planetarycomputer.microsoft.com/dataset/landsat-c2-l2) as an example:
`https://landsateuwest.blob.core.windows.net/landsat-c2/level-2/standard/oli-tirs/2021/046/027/LC08_L2SP_046027_20210725_20210803_02_T1/LC08_L2SP_046027_20210725_20210803_02_T1_SR_B5.TIF`

It's copied into cogs/, so it's accessible publicly without authentication:
`gdalinfo https://scottyhq.github.io/share-a-raster/LC08_L2SP_046027_20210725_20210803_02_T1_SR_B5.TIF`

Or you can point somebody to a tiler endpoint, using developmentseed's fantastic [TiTiler](https://developmentseed.org/titiler/)! 

https://titiler.xyz/cog/viewer?url=https://scottyhq.github.io/share-a-raster/LC08_L2SP_046027_20210725_20210803_02_T1_SR_B5.TIF

Or open with rioxarray
```python
import xarray as xr
URL = 'https://scottyhq.github.io/share-a-raster/LC08_faux.tif'
da = xr.open_dataset(URL, engine='rasterio')
da
```


## Propriety data

Consider sharing a file that is obscured rather than setting up complicated authentication! https://github.com/cogeotiff/rio-faux

`rio faux LC08_L2SP_046027_20210725_20210803_02_T1_SR_B5.TIF LC08_faux.tif`


## Limitations

GitHub isn't really designed for sharing data, so this is best for small COGs (<100MB) to share among colleagues. If you want long-term storage that is high performance look into options like cloud object storage (AWS S3 etc).

Check out https://github.com/scottyhq/zarrdata for a similar example with Zarr instead of COG

Or use a service list Felt https://felt.com/blog/raster-imagery-and-geotiffs-in-felt

# Mars_DEMs
Mars DEM list and footprint shapefile for visualizing available DEMs 

[THIS IS A COPY OF THE README FILE ARCHIVED WITH THE NASA PDS]

Title: Digital Elevation Models derived from HiRISE and CTX stereo image pairs 
Version: 1
Updated: January 2023
Citation: Day, M., E. Kim, M. Sullivan, T. Goudge, and D. Paige, High Resolution DEMs for Mars: A repository of paired HiRISE and CTX DEMs. 6th Planetary Data Workshop, 2023, Flagstaff, Arizona. 
PDS DOI: 10.17189/ervc-mr85
For questions about this archive, contact Mackenzie Day: daym@epss.ucla.edu 

**Summary Description:**
Digital elevation models (DEMs) provide three-dimensional information about outcrops and landscapes that facilitate a range of scientific analyses not possible with imaging alone. For example, DEMs enable measurements of layer thickness and orientation that are critical to understanding local stratigraphy. On Mars, DEMs are currently available at a range of scales, and can be generated from stereo-pairs of images taken at different viewing angles. High resolution images produce high resolution DEMs, but not all stereo image pairs have been processed into three-dimensional products. This archive aims to bridge some of the gap between the available stereo imaging and the available DEMs. Roughly 2600 DEMs are included in this archive, half created using images from the High Resolution Imaging Science Experiment (HiRISE) and half using images from the Context Camera (CTX) aboard the Mars Reconnaissance Orbiter. CTX DEMs in this archive overlap one of the HiRISE DEMs, providing three-dimensional context, but at lower resolution, for the 1 m/px HiRISE DEMs. DEMs locations were chosen from HiRISE targeted for collection in stereo, suggesting an existing scientific interest by the community. 

This archive includes 1,353 HiRISE DEMs, 1,353 CTX DEMs that overlap the HiRISE DEMs, orthoimages associated with each, and pixel masks to show the quality of each stereo correlation. 

**Data generation process:**  
The process of generating DEMs from overlapping images collected at dissimilar geometries (stereo images) is reviewed in the literature (Bemis et al., 2014; Shean et al., 2016), with several works providing guidance specifically for planetary data analysis (e.g., Öhman, 2013). We briefly review the steps taken in to generate the products in this archive.
DEMs in this archive were generated using the open source Ames Stereo Pipeline (ASP; Shean et al., 2016; Beyer et al., 2018), which interfaces with the freely available Integrated Software for Imagers and Spectrometers (ISIS3) developed by the USGS (Edmundson et al., 2012; Sides et al., 2017). EDR files for each image in the stereo pair are downloaded and ingested through ISIS3. For HiRISE, EDRs are processed into a single mosaic using ASP. The images are then projected to the same reference frame (local sinusoidal projection), and then the ASP stereo correlation is run on the two projected images. This results in an orthoimage (digitally rectified graphic; DRG) and a point cloud of elevations. 
The point cloud is then tied to a lower-resolution elevation dataset. Elevation point clouds generated from CTX images are tied to elevations from the Mars Orbiter Laser Altimeter (MOLA; Smith et al., 2001), and point clouds generated from HiRISE are tied to the associated CTX point cloud (e.g., Mayer and Kite, 2016; Goudge et al., 2018). 
Point clouds are then converted into DEMs and saved as GeoTIFF files. Associated XML files are added to the DEMs and DRGs per PDS4 standard guidelines. 

**Data product coverage and accessibility:** 
_Selection criteria:_ The DEMs created for this work met the following criteria: 
1) HiRISE images were collected intentionally in stereo, meaning overlapping images were captured at geometries well-suited for generating DEMs using photogrammetry 
2) CTX images overlapping the HiRISE stereo pair were collected during the same orbit and at similar geometries (i.e., “ride along” observations with the original HiRISE), such that the HiRISE image pair and associated CTX image pair have similar relative geometries. 
3) The center latitudes of the HiRISE image pair are equatorial of 65 degrees latitude 
A total of 1,353 HiRISE stereo pairs meeting these criteria were successfully turned into DEMs archived in this bundle. Each HiRISE DEM is associated with an orthoimage (DRG), overlapping CTX DEM and DRG covering a larger area than the HiRISE DEM, and pixel masks that show the quality of the stereo correlation. 

_Searching the archive for specific DEMs:_ The top-level documentation includes an index which can be used to search the available DEMs within this dataset. This index (dem_index_.csv) includes the center latitude and longitude of the HiRISE image pair and the Image IDs of each HiRISE image used in the pair, along with the CTX image IDs of the associated CTX DEM. 

**As a secondary method of viewing the spatial distribution of coverage, a shapefile of the DEM footprints is archived on the PI’s GitHub page at: 
https://github.com/GALE-Lab/Mars_DEMs**

**Data structure and naming convention:** 
This archive contains top-level documentation including this document (readme.pdf), a product index (dem_index.csv), and (collection_data.csv). and paired HiRISE and CTX DEMs in separate folders within the archive. 

_Contents of this archive:_
  readme.pdf – Overview and guidance for using these data
  dem_index.csv – Searchable index of products including the HiRISE and CTX image IDs used to create the associated HiRISE and CTX DEMs, the number that identifies each set of paired DEMs, and the center latitude and longitude of the first HiRISE image ID in each set. The SetID is used to determine the location of the DEMs and associated data products in the file structure. The column headers of this index are: 
	SetID	HiRISE1   HiRISE2   CTX1   CTX2   CenterLat   CenterLon
  collection_data.csv – List of the PDS identifiers of every file in this archive. 
  hirise_###-### - Folders that contain the DEM sets and associated data products. There are a total of 1353 DEM sets included in this archive and they are binned into groups of 100, identified with a number in the dem_index.csv top level file. Each folder includes ~100 sets of paired HiRISE and CTX DEMs with their orthoimages and Good Pixel Map quality evaluation pixel mask products. Within a folder the files are arranged alphabetically, but a given set includes: 
	1 HiRISE DEM file (HiRISE1_HiRISE2_tied-DEM.tif)
	1 HiRISE orthoimage file (HiRISE1_HiRISE2_tied-DRG.tif) 
	1 Good Pixel Map for the HiRISE DEM (HiRISE1_HiRISE2-GoodPixelMap.png) 
	1 CTX DEM file (CTX1_CTX2_tied-DEM.tif) 
	1 CTX orthoimage file (CTX1_CTX2_tied-DRG.tif) 
	1 Good Pixel Map for the CTX DEM (CTX1_CTX2- GoodPixelMap.png) 
	XML files matching with each of the above 
  
_Example:_  “esp_049629_1375_esp_049563_1375_tied-dem.tif”
For the example above, the product was generated from two HiRISE images:  ESP_049629_1375 and ESP_049563_1375. The file name begins with the two image IDs, and ends with the type of product: in this case, a DEM already tied to the associated CTX. To find the associated CTX DEM, one could search for either HiRISE ID in the top level index (dem_index.csv) and find that this HiRISE DEM is associated with CTX imaqes J12_049629_1376_XN_42S158W and J12_049563_1376_XN_42S158W. The index would also provide the center latitude and longitude of ESP_049629_1375 and the SetID# for this group of data products. In the folder indicated by that number, one could find the CTX DEM overlapping the HiRISE DEM and would expect it to have filename:   
j12_049629_1376_xn_42s158w_j12_049563_1376_xn_42s158w_tied-dem.tif

**Data quality and limitations:**
_Resolution:_ HiRISE DEMs have a post-spacing of 1 m and CTX DEMs a post-spacing of 18 m. The associated orthoimages have the same resolution (HiRISE and CTX at 1 m/px and 18 m/px, respectively).  

_Quality evaluation and null values:_ Each DEM-orthoimage set is accompanied by a PNG file of the same naming convention, but appended with “Good Pixel Map”. This standard product is used to evaluate the quality of the stereo correlation (see additional explanation in Beyer et al. (2018) and Öhman T. (2013)). The Good Pixel Map is a pixel mask showing regions where the stereo correlation as successful (grey) and regions where it was not (red). 
Rather than interpolate across zones where the image correlation was unsuccessful, the data in this archive instead leave these regions blank and leave it to the user to interpolate via whatever method they wish. Regions of poor correlation are stored as null values and appear as “NoData” when viewed by GIS software. 
Projection information: The orthoimages and DEMs are projected to the Mars aeroid using the GCS_Mars_2000_Sphere georeferencing standard and the IAU D_MARS datum. 
 
Figure 1: Example of paired CTX and HiRISE DEMs in this archive. Colorized elevation DEM overlain on orthoimages (DRGs). The extent of both DEMs is shown in (a) with a zoomed view in (b) to show the difference in resolution of the CTX and HiRISE orthoimages (18 m/px and 1 m/px, respectively).
 
Figure 2: Coverage of the data products in this archive as footprints over a MOLA colorized elevation basemap. See appendix for zoomed-in panels. 
Funding and Acknowledgements: 
	This work was funded by the NASA Planetary Data Archiving, Restoration, and Tools program under grant 80NSSC21K1049. 

**References:** 
Bemis, S.P., Micklethwaite, S., Turner, D., James, M.R., Akciz, S., Thiele, S.T., and Bangash, H.A., 2014, Ground-based and UAV-Based photogrammetry: A multi-scale, high-resolution mapping tool for structural geology and paleoseismology: Journal of structural geology, v. 69, p. 163–178.
Beyer, R.A., Alexandrov, O., and McMichael, S., 2018, The Ames Stereo Pipeline: NASA’s open source software for deriving and processing terrain data: Earth and Space Science, v. 5, p. 537–548.
Edmundson, K.L., Cook, D.A., Thomas, O.H., Archinal, B.A., and Kirk, R.L., 2012, Jigsaw: The ISIS3 bundle adjustment for extraterrestrial photogrammetry: ISPRS Ann. Photogramm. Remote Sens. Spat. Inf. Sci, v. 1, p. 203–208.
Goudge, T.A., Mohrig, D., Cardenas, B.T., Hughes, C.M., and Fassett, C.I., 2018, Stratigraphy and paleohydrology of delta channel deposits, Jezero crater, Mars: Icarus, v. 301, p. 58–75.
Mayer, D.P., and Kite, E.S., 2016, An integrated workflow for producing digital terrain models of Mars from CTX and HiRISE stereo data using the NASA Ames Stereo Pipeline: LPI, p. 1241.
Öhman T., 2013, A beginner’s guide to stereo-derived DEM production and analysis using ISIS, ASP, and ArcMap. Lunar and Planetary Institute, internal report, 30 pp., doi: 10.13140/RG.2.1.1743.7609. Available online at: http://www.lpi.usra.edu/lunar/tools/dems/Ohman_2013_ISIS-ASPArcMap_workflow.pdf
Shean, D.E., Alexandrov, O., Moratto, Z.M., Smith, B.E., Joughin, I.R., Porter, C., and Morin, P., 2016, An automated, open-source pipeline for mass production of digital elevation models (DEMs) from very-high-resolution commercial stereo satellite imagery: ISPRS Journal of Photogrammetry and Remote Sensing, v. 116, p. 101–117.
Sides, S.C., Becker, T.L., Becker, K.J., Edmundson, K.L., Backer, J.W., Wilson, T.J., Weller, L.A., Humphrey, I.R., Berry, K.L., and Shepherd, M.R., 2017, The USGS Integrated Software for Imagers and Spectrometers (ISIS 3) Instrument Support, New Capabilities, and Releases, in Lunar and Planetary Science Conference, v. 48.
Smith, D.E., Zuber, M.T., Frey, H. V, Garvin, J.B., Head, J.W., Muhleman, D.O., Pettengill, G.H., Phillips, R.J., Solomon, S.C., and Zwally, H.J., 2001, Mars Orbiter Laser Altimeter: Experiment summary after the first year of global mapping of Mars: Journal of Geophysical Research: Planets, v. 106, p. 23689–23722.

 
Appendix A: Additional coverage maps 
Included below are zoomed-in visualizations of the spatial distribution of CTX and HiRISE DEMs. These maps are included to support quick determination as to whether a DEM is available in an area of interest. 
 
Figire A0: Global map of coverage (same as Fig. 2) with the subsequent figures labeled.  
Figire A1: Coverage map of CTX (grey) and HiRISE (pink) DEMs  
Figire A2: Coverage map of CTX (grey) and HiRISE (pink) DEMs  
Figire A3: Coverage map of CTX (grey) and HiRISE (pink) DEMs  
Figire A4: Coverage map of CTX (grey) and HiRISE (pink) DEMs  
Figire A5: Coverage map of CTX (grey) and HiRISE (pink) DEMs  
Figire A6: Coverage map of CTX (grey) and HiRISE (pink) DEMs  
Figire A7: Coverage map of CTX (grey) and HiRISE (pink) DEMs  
Figire A8: Coverage map of CTX (grey) and HiRISE (pink) DEMs

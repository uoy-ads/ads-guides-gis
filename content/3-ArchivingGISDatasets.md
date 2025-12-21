---
authors:
  - name: null
---

# 3 Archiving GIS Datasets

## 3.1 Preparing to Archive: Files and Formats

As GIS data often incorporates data from a variety of sources the formats that are safest for digital preservation vary with the type of information contained within a file. In this section, recommendations are given for formatting of GIS files, databases, images, documentation, and metadata.

__Significant Properties__

Any archiving of GIS files should aim to preserve the following properties:

* Coordinate reference system information
* Geometry (e.g. point, polygon, line)
* Attribute fields
* For rasters - source elevation model, bit-type, colourmap, pixel type

Strictly speaking, colour is not seen as a significant property of GIS data. This tailoring of data is stored in the project file (see below) and not in the digital object itself. If data creators require that colour/styling of original data should be recorded then this should be supplied as documentation in the form of a document or image. This documentation can then be stored with the data.

### 3.1.1 GIS Files

As highlighted in a 2009 DPC Technology Watch Report, "Attempts at defining a universal data model for geospatial data have been made (for example the Spatial Data Transfer Standard (SDTS)...but have not achieved widespread adoption. As a consequence, it is not possible to speak of - geospatial data - as a single type of information that can be handled by multiple, functionally equivalent applications and formats." [@mcgarva2009technology]. As with other data types discussed in these Guides, where the original source data (e.g. raw survey data) cannot be archived outside of the GIS environment, the most suitable files to use for archiving GIS data fall into the categories of open formats (e.g. GML and KML) and widely used standards (e.g. ESRI Shapefiles). This approach is further supported by the wide range of import and export functions often supported by the majority of GIS applications as well as third-party libraries such as the open source [GDAL library](https://gdal.org/en/stable/) (raster geospatial data formats) and the related OGR library (vector data).

General considerations, as outlined in the Guide-wide section on [Planning for the Creation of Digital Data](https://doi.org/10.5284/h0p2-5584) include ensuring that data, where possible, is not encoded or compressed.

__Project Files__

In many GIS applications, project files - such as .apr or .mxd. - can be created to hold data in a tailored manner that involves classification, symbolization, and annotation based upon the data content. These data views typically appear as maps, charts, or tables, or some combination thereof. In order for an end user to render this content it is necessary not only to have the project file, but also the software that supports it, the related components (possibly including software add-ons or extensions), as well as the actual data. The required use of specific software, the complexity of the project file formats, and the tenuous links to the actual data, which is often simply pointed to, put these project files at high risk for failure over time. It is therefor recommended that project files are not archived or at least are not used to hold key information relating to the associated datasets.

__File Formats__

Generally speaking, GIS data falls into two main categories, geo-referenced vector and gei-referenced raster data formats. Unlike other simpler data types, GIS files may consist of more than one physical file/object. This is well illustrated by the case of ESRI Shapefiles where a single 'file' may be made up of a collect of up to eight separate files. When archiving GIS data it is essential that all relevant files are stored. The tables below outline a number of common GIS formats for both raster and vector data however, in summary, it is recommended that where possible vector data is archived in the __GML__ format and raster data as __GeoTIFF__ files.

```{list-table} Geo-referenced Vector
:header-rows: 1


* - Format
  - Description
* - ArcInfo Interchange (.e00)
  - An ESRI format developed to move coverages, INFO data files, text files such as ARC Macro Language (AML) files, and other ArcInfo files between machines not connected by a file sharing network. Interchange files contain all coverage information and appropriate INFO data file information in a fixed-length ASCII format. The ESRI E00 interchange data format combines spatial and descriptive information for vectors and rasters in a single ASCII file. It is mainly used to exchange files between different versions of ArcInfo, but can also be read by many other GIS programs. This can be used as a preservation format.
* - ESRI Shapefile (.shp, .shx, .dbf, .sbn and .sbx, .fbn and .fbx, .ain and .aih, .prj and .xml)
  - Shapefile is an openly published format and is actually a collection of files the number and combination of which depends upon the type of data stored in the file. Shapefiles store nontopological geometry and must be accompanied by in index file (.shx) and a dBASE file that holds the attributes of the shapes in the shp file. Shapefiles contain the following files: 
    * SHP - the file that stores the feature geometry. Required. 
    * SHX - the file that stores the index of the feature geometry. Required. 
    * DBF - the dBASE file that stores the attribute information of features. Required. 
    * SBN, SBX - the files that store the spatial index of the features. Optional. 
    * FBN, FBX - the files that store the spatial index of the features for shapefiles that are read-only. Optional. 
    * AIN, AIH - the files that store the attribute index of the active fields in a table or a theme's attribute table. Optional. 
    * PRJ - the file that stores the coordinate system information. Optional. 
    * XML - metadata. Optional.
* - Geographic Markup Language (.gml)
  - GML utilises XML to express geographical features. It can serve as a modelling language for geographic systems as well as an open interchange format for geographic data. It is an ISO standard (ISO 19136) and is built on a number of other ISO standards collectively known as the 19100 family. GML is defined by the Open Geospatial Consortium. In being an XML based schema and an ISO standard. GML is very suitable as a preservation format and recommended for GIS data.
* - Keyhole Markup Language (KML)
  - An XML based format initially developed for use with the Google Earth application but now an international standard of the Open Geospatial Consortium.
* - MOSS export
  - An export format from the MOSS GIS software, it can be problematic to import into other applications and is not a preferred format.
* - MapInfo Interchange Format (.mif & .mid)
  - MapInfo is a commonly used GIS software package. Where the .mif file contains the grahics, the .mid component contains any attribute data as delimited text and is optional. The format is a standard format and most other GIS programs can also read it. This format is ASCII based and open and thus a possible preservation format although MapInfo products provide support for GML which is even more suited to preservation.
* - National Transfer Format (NTF)
  - The NTF format has been mostly used in the past by the UK Ordnance Survey. The format is widely supported for conversion into other formats and is supported (read access) by the OGR Library.
* - Spatial Data transfer standard (.ddf)
  - The Spatial Data Transfer Standard (SDTS) is a data exchange format for transfering different databases between disimilar computing systems, preserving meaning and minimizing the amount of external information needed to describe the data. It can only be used for certain types of feature point, arc and grid data. One coverage would produce many files all with extension .ddf.
* - Vector product Format (.vpf)
  - Vector Product Format (VPF) is a U.S. Department of Defense Standard. The National Imagery and Mapping Agency (NIMA) is using VPF for digital vector products developed at a variety of scales. VPF has also been adopted into an international spatial standard as the Digital Geographic Information Exchange Standard (DIGEST). Vector Product Format (VPF) coverages and tables can be translated into ARC/INFO coverages and INFO tables.
```

```{list-table} Geo-referenced Raster
:header-rows: 1

* - Format
  - Description
* - Geo-referenced TIF Image/GeoTIFF .tif (.rrd,.aux .xml)
  - GeoTIFF is a metadata format, which provides geographic information associated with the image data. The TIFF file structure allows both the metadata and the image data to be encoded into the same file. GeoTIFF files embed information about the projection within tags in the file and will import automatically with correct georegistration. Whereas images saved using GeoTIFF require only one file with a .tiff or .tif file extension it is important not to confuse GeoTIFF with a different format using .tif files called the "TFW" format. This format uses two files, a .tif file and a .tfw "world" file to provide georeferencing information. TFW is not the same as GeoTIFF. Adding to the confusion is that some packages will create both a GeoTIFF file as well as a .tfw "world" file. The .tfw file provided in such cases is not part of the GeoTIFF standard. GeoTIFF is a preferred format to Tif World files.
* - ESRI GRID (.adf, .asc, .grd)
  - An [ESRI GRID](https://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html#//009t0000000w000000) is a raster GIS file format developed by Esri, which has two formats. The first is a proprietary binary format with the extension .adf and is also known as an ARC/INFO GRID, ARC GRID and many other variations. See ESRI documentation on the binary version. The second is a non-proprietary ASCII format, also known as an ARC/INFO ASCII GRID with the file extension .asc, but recent versions of ESRI software also recognize the extension .grd. Both types are well documented online.
* - JPG World .jpg & jgw (.rrd,.aux,.xml)
  - As with TIFF world files (described above) these files consist of a standard JPG file accompanied by a world file containing the georeferencing information.
```

__Database Files__

If you have external databases connected to your GIS system, for example a database containing your attribute data, then you may want to archive these as well. Details on how best to archive database data is covered in the [Databases and Spreadsheets](https://doi.org/10.5284/are0-mn51) guide.

__Image Files__

It is __NOT__ necessary to archive images of every single coverage in your GIS, nor is it necessary to archive images showing all of the ways you used the GIS to play with that data. Occasionally an image may have proven useful to you in a research project and, in order to document the research that you did, archiving that image might be worth more than 1,000 words of documentation. One example is an image showing lithic flakes scattered across a house floor in a pattern that you argued demonstrates lithic production was taking place on site - that single image might be well worth including.

Further information on archiving raster images can be found in the [Raster Images](https://doi.org/10.5284/mtgj-7130) guide.

### 3.1.2 Documentation and Metadata to accompany your GIS, database, or image files

Your data set - the GIS files, database files, and image files - will need to be accompanied by detailed documentation as described in Sections [3.2](archivinggisdatasets#id-3-2-project-level-metadata) and [3.3](archivinggisdatasets#id-3-3-data-specific-documentation-and-metadata). These are general guidelines and certain archives may have specific requirements for the format and content of the metadata that accompanies GIS and spatial datasets e.g. some archive may request that it is supplied as documents along with the data whereas others, e.g. tDAR, utilise interactive web forms to help users create metadata for resources they deposit.

## 3.2 Project-level Metadata

As discussed in [Section 2.8](creatingandusinggisdata#id-2-8-why-document-your-data), the documentation which accompanies a data set should enable a third party to make sense of the data. In addition to the specific documentation suggested in [Section 2.8](creatingandusinggisdata#id-2-8-why-document-your-data), in particular the Dublin Core elements described in [Section 2.8.4](creatingandusinggisdata#id-2-8-4-dublin-core-metadata) and in the general [Project Metadata](https://doi.org/10.5284/h0p2-5584) section, the table below outlines a set of project-level metadata that should be completed for GIS datasets.

```{list-table}
:header-rows: 1


* - Project Title
  - 
* - History of the Originating Project
  - * the purpose of the project 
    * topic(s) of research
    * geographic and temporal limits
    * other relevant information
* - Information about Methods
  - * methods used to create the data set
    * methods used to georeference data
    * consistency checks
    * error corrections
    * sampling strategies employed
    * other relevant information
* - Details of source materials used to create the data set
  - * archives interrogated for desktop assessments
    * maps used to georeference site grids or surveys
    * previous excavations/evaluations of the site
    * data selection or sampling procedures
    * procedures for updating, combining, or enhancing source data
    * description of any known copyrights held on source material
* - Content and structure of data set
  - * list of filenames and description of contents
    * description of identification numbers assigned
    * list of codes used, and what they mean
    * description of any known errors
    * indications of any known areas of weakness
    * details of derived variables or coverages
    * data dictionaries, if available
    * documentation of record conversion to new systems and formats
    * description of the record-keeping system used to document the data set
    * names of primary project staff
    * history of format changes to data set
    * history of how the data set has been used
    * other relevant information
* - Details of how the data set relates to other archives and publications
  - * bibliographic references to any publications about the site or project
    * information about any archives, museums, SMRs, NMRs, etc. which hold material related to the data set
    * information about any non-public material relating to the data set
```

## 3.3 Data-specific Documentation and Metadata

The sections below summarise the additional documentation and metadata recommended for specific datatypes and processes as outlined in [Section 2](creatingandusinggisdata). Data creators are advised to see the relevant pages under said section of this guide.


### 3.3.1 The Vector model

The following information should always be recorded when assembling, compiling and utilising vector data:

* The data type, Point, Line or Polygon
* Type of topology which the file contains
* Details of any automatic vector processing applied to the theme
* State of the topology in the file
* Projection system
* Co-ordinate system

### 3.3.2 The Raster model

The following information should always be recorded when assembling, compiling and utilising raster data:

* grid size (number of rows and columns)
* grid resolution
* georeferencing information, e.g. corner co-ordinates, source projection.

### 3.3.3 Attribute Data Models

When attempting to structure and organise a flexible attribute database the following factors are of critical importance:

* Naming conventions
* Key fields
* Character field definitions
* Grid references
* Validation
* Numeric data
* Data entry control
* Confidence values
* Consistency
* Documentation
* Dates

### 3.3.4 Data Capture using a Scanner

* Details of the scanning device used, software driver and version
* All parameters chosen in the scanning process, such as the resolution setting of the device, the number of bits per pixel used
* Details of any pre-processing undertaken on the source mapsheet. This may include a range of options provided by the specific scanning software used
* Details of any post-processing undertaken on the data, such as noise reduction or sharpening with convolution filters, histogram equalisation, contrast adjustment

### 3.3.5 Data Capture using a Digitiser

* Detail of the digitising device used, software driver and version
* The precision, usually specified as a quoted resolution or as lpi
* Details of any automatic vector processing applied to the theme (such as snap-to-nearest-node)
* Details of control points used to manage conversion from digitiser to real-world planar co-ordinate systems
* Errors incurred in the above transformation process (e.g. quoted RMS)

### 3.3.6 Data Capture using a Scanning-digitising Hybrid

In the case of using both a scanner and a digitiser to capture data, for example during 'heads-up digitising', the full information above for both the digitising and scanning procedures should be recorded.

### 3.3.7 Common Sources of Spatial Data

* Maps and Plans
* Textual and numeric data
* Purchased or downloaded digital data
* Aerial photography
* Satellite and airborne remotely sensed images
* Terrestrial Survey data
* Satellite-based (GPS) data

### 3.3.8 Common Sources of Attribute Data

Below are some likely sources of attribute data which you may come across, and wish to re-use:

* paper based card indexes
* archaeological site and survey archives (including paper based records, finds databases)
* qualitative report texts and articles published in journals (paper based or on the Internet)
* microfiche archives
* geophysical interpretation data derived from interpreted geophysics plots
* aerial photograph interpretations which may include morphological analysis attribute data and photo source information
* typological databases or artefact type series
* data generated at a regional level for integrated large scale historic landscape studies, such as the English Heritage Open Fields Project
* local level archaeological databases (e.g. Sites and Monuments Records or Urban Archaeological Databases where they are held separately from SMRs)
* local museum site and finds databases
* local Record Offices
* national archaeological databases (e.g. such as the various UK National Monument Records or English Heritage's database of Scheduled Ancient Monuments)
* Gardens Trust surveys
* historic buildings surveys and databases maintained by local authorities
* metadata relating to data sets

### 3.3.9 Maps and Plans

In general the following information should always be recorded:

* Publisher __and__ copyright owner
* The map medium
* Scale of source map
* Name of the map and the map series
* Claimed accuracy for any specific map components
* All details of the map projection and co-ordinate system employed

### 3.3.10 Textual and Numeric Data

When integrating textual and numeric data the following information should be recorded:

* The data source
* The precision of the quoted co-ordinates
* Have the quoted locations been verified and how
* Projection system/co-ordinate origin
* If derived from a source map, record details of the map-base used
* If derived from a survey programme, record details of the survey procedure

### 3.3.11 Purchased or Downloaded Digital Data

Several standard formats and standards are of interest.

* British Standard 7567 (NTF: National Transfer Format), the format used by Ordnance Survey for the supply and transfer of digital products
* The recommendations of the National Geospatial Data Framework (NGDF)
* SDTS (Spatial Data Transfer Standard), a United States Federal Information Processing Standard (FIPS)
* DLG (Digital Line Graph) format, used by the USGS for supply of vector information
* DRG (Digital Raster Graphics), is the description that the USGS gives for the distribution of scanned map sheets
* DXF (Digital eXchange Format) format, commonly used for transferring drawings between CAD (Computer Aided Design) systems

### 3.3.12 Aerial Photography

To incorporate scanned and rectified aerial photographs into GIS databases the following information should be recorded:

* Full Photographic details
* Details of the scanning process
* Details of the rectification method(s) used
* The software employed including, where possible, specific parameters chosen
* Details regarding the ground control points (GCPs) used during the procedure
* Details of any post-processing undertaken on the data

### 3.3.13 Satellite and Airborne Remotely Sensed Images

To incorporate remotely sensed data into GIS databases the following information should be recorded:

* Data source
* Date image was captured
* Data resolution
* Details of any post-processing undertaken on the data
* Details of the rectification method(s) used
* The software employed including, where possible, specific parameters chosen
* Details regarding the ground control points (GCPs) used during the procedure

### 3.3.14 Terrestrial Survey

When integrating data themes which are derived from survey data, the following should be recorded:

* The source and estimated error of survey base station co-ordinates
* Details of the survey, including date time and purpose
* Details of the thematic organisation of the survey
* Make and model of instrument used
* Type of survey (contour, feature etc.)
* Estimated error terms for the co-ordinate pairs and (if appropriate) the z-co-ordinate
* Georeferencing information, overall accuracy of the survey data

### 3.3.15 Satellite-based Survey (GPS)

In integrating GPS data the following information should be recorded:

* The method used to locate stations: C/A or P code pseudorange measurements, carrier phase measurements and whether a single measurement or averaging (include time period) was used
* The software used for any co-ordinate transformation and associated error estimate
* The satellites used in obtaining fix and observed GDOP (Geometric Dilution of Precision)
* The nature of any differential correction undertaken + error estimates
* The broadcast differential: name of the service provider and the name and location of base station
* The local base station: instrument details, location (including error estimate) of base station
* Post-processing: the software used and the source of correction data

### 3.3.16 Creating a GIS Database

When combining and integrating information from a variety of sources the following points should be kept in mind:

* All spatial data must be recorded in the same co-ordinate system. Data which are recorded to some other system must be transformed/projected to the required co-ordinate system.
* All spatial data should be to the *same spatial* resolution, or scale. It is not possible to get meaningful results from the combination of spatial data recorded to a *scale* of 1:250, as might be the case for an excavation site plan, with road alignments recorded to a scale of 1:250,000. Spatial data recorded to *scales* of greater than around 1:10000 involve considerable generalisation of alignments to avoid features conflicting.
* Non-spatial information to be combined, or integrated, must use the same field definitions, encoding regimes, etc. Where different schemes are used it will be necessary to convert or translate the data to the required scheme.

### 3.3.17 Documenting the Dataset

Information about where the data you use are acquired from is one of the most important things you can record whilst constructing and using a GIS. The following comprises a *non-exhaustive list* of the information you might wish to record during your everyday creation, collection, and use of data:

* Computer hardware used
* Computer software used
* Date the data were captured/purchased/whatever
* Who did the work
* Data source ('bought from Ordnance Survey', etc.)
* Scale/resolution of data capture
* Scale/resolution at which data are currently stored
* Root Mean Squared error or other assessments of data quality
* Purpose of data set creation, where known
* Method of original data capture (Total Station Survey, etc.)
* Purpose for which *you* acquired the data (might differ from the previous information where the data were *created* by someone else for one purpose, and bought from them by you for another)
* Complete history of data ownership/rights.
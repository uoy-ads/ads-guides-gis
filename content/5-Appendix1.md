---
authors:
  - name: null
---

# Appendix 1: Case Study - Depositing a GIS Dataset

## Introduction to the Case Study

As discussed in the previous sections, data deposited for archiving should be accompanied by appropriate documentation. To illustrate this process, a simple case study based on data from a real archaeological project is provided.

Data prepared for deposit consisted mainly of Arc/Info export files and some postscript images showing key coverages in the GIS. The importance of documentation becomes immediately clear - imagine if you were given this data, and the only thing you knew about it was that it consisted mainly of Arc/Info export files!

## Documentation

Luckily the depositor, Dr Julian Richards of the University of York, provided a WordPerfect text file in addition to his export files. The [original WordPerfect file](./attachments/cottam.doc) can be viewed by those of you with access to this software. As not everyone can read WordPerfect files, the documentation was migrated into HTML:

## Background Information about Cottam Project, by Julian Richards

%%( background-color: #ddd; border: 1px dotted black; padding: 1em; )
The presence of a settlement site of the 8th - 10th centuries AD in the parish of Cottam and Cowlam, East Yorkshire, was first indicated by the distribution of over 200 metal objects discovered from 1987 onwards by metal detector users working fields to the west of Burrow House Farm. The majority of the metal finds were published in the Yorkshire Archaeological Journal [@haldenby1990anglian; -@haldenby1992anglian; -@haldenby1994anglian], although at that stage the location of the site was not revealed because of the dangers of unauthorised metal detecting. The original group of metal detector users had recorded the approximate location of each of their finds and their distribution was shown to correspond with a sub-rectangular crop mark enclosure. Rural sites which can be assigned to the Anglian and Anglo-Scandinavian period are rare in England and it was decided to carry out an archaeological evaluation of the site, using field walking, geophysics and trial excavation [@richards1994cottam]. Three seasons of excavation were carried out, between 1993-96, sponsored by the Department of Archaeology, University of York, Earthwatch, and the British Academy. The aims of the evaluation were to:

* 1. examine the relationship between the crop marks and the 8th-10th century finds
* 2. characterise the nature of the settlement activity
* 3. assess the extent of plough damage and the survival of occupation layers
* 4. recover artefactual and environmental samples

The role of the GIS was in the integration of the different categories of evidence and to help understand the spatial development of the site both internally and within its wider landscape setting [@richards1996putting]. It is believed that this question is critical for our understanding of the development of early medieval settlement patterns in Northumbria. Within ARC/INFO coverages were defined for several classes of data, including:

* 1. the distribution of metal artefacts recorded by the metal-detectorists;
* 2. the aerial photographic coverage;
* 3. data collected in two seasons of field walking;
* 4. magnetometer and resistivity survey data;
* 5. evidence from the trial excavation. 

This data incorporates point, line and polygon information. Associated attribute tables include detailed finds information which enable the development of artefact distribution patterns, incorporating those finds recovered by the metal detector users, and during the controlled excavations. The final excavation report is in preparation [@richards1999cottam].

## Data and Metadata

This background documentation about the project accompanied the actual data sets. Only the image files will be discussed in the remainder of this case study.

An original image file showing the main aerial photograph interpretation for Cottam was deposited as a [postscript file](./attachments/ap.eps). For ease of viewing a web-formatted version is included here:

```{figure} ../images/gis_ap.gif
:alt: Cottam AP image
```

Metadata supplied at the time of deposit gives useful background information about this image:

```{list-table}
:header-rows: 1

* - 
  - Dublin Core Metadata for Image
* - Title
  - Cottam B Enclosure aerial photograph transcription
* - Creator
  - John Duffy interpreted and transcribed image
* - Subject
  - settlement, excavation, survey, aerial photography, Anglo-Saxon
* - Description
  - This aerial photograph interpretation was created during the post-excavation analysis of the Cottam B Project directed by Julian Richards. Image was imported into Arc/Info from Autocad. This Anglo-Saxon settlement is located in Yorkshire on the Wolds east of York.
* - Publisher
  - The image is licensed for distribution by the Archaeology Data Service
* - Date
  - 1998
* - Type
  - image
* - Format
  - postscript (eps) and gif
* - Identifier
  - http://ads.ahds.ac.uk/images/ap.gif
* - Source
  - Aerial photograph held by the Royal Commission on the Historical Monuments of England
* - Language
  - English
* - Relation
  - Derived from a larger GIS data set held by Julian Richards, Department of Archaeology, University of York. Data is from site 6865 in the Humberside Sites and Monuments Record. Site is called "Burrow House Farm, Cottam" in the RCHME National Excavation Index for England.
* - Coverage - Spatial
  - 4976 4667
* - Coverage - Temporal
  - Early Medieval - this term is derived from a controlled MIDAS list (RCHME 1998)
* - Rights
  - Image is freely accessible to registered Archaeology Data Service users.
```

There was also an image file showing the trench locations for the Cottam excavation. The [postscript format](./attachments/cot-tren.eps) is available as is an image formatted for web browsers:

```{figure} ../images/gis_trench2.gif
:alt: cottam trench locations
```

Metadata supplied at the time of deposit gives useful background information about this image:

```{list-table}
:header-rows: 1

* - 
  - Dublin Core Metadata for Image
* - Title
  - Cottam 1993 excavation trench outlines
* - Creator
  - Julian Richards
* - Subject
  - settlement, excavation, Anglo-Saxon
* - Description
  - The location of excavation trenches for the 1993 Cottam excavation are shown in this image. Data was collected using an EDM, and then downloaded into Arc/Info. This Anglo-Saxon settlement is located in Yorkshire on the Wolds east of York.
* - Publisher
  - The image is licensed for distribution by the Archaeology Data Service
* - Date
  - 1995
* - Type
  - image
* - Format
  - postscript (eps) and gif
* - Identifier
  - http://ads.ahds.ac.uk/images/trench2.gif
* - Source
  - EDM survey
* - Language
  - English
* - Relation
  - Derived from a larger GIS data set held by Julian Richards, Department of Archaeology, University of York. Data is from site 6865 in the Humberside Sites and Monuments Record. Site is called "Burrow House Farm, Cottam" in the RCHME National Excavation Index for England.
* - Coverage - Spatial
  - 4976 4667
* - Coverage - Temporal
  - Early Medieval - this term is derived from a controlled MIDAS list (RCHME 1998)
* - Rights
  - Image is freely accessible to registered Archaeology Data Service users.
```

The third and final original image file showed the location of metal artefacts found at Cottam. It is available as a [postscript file](./attachments/metal-de.eps) and a web-browsable version is included here:

```{figure} ../images/gis_metal-de.gif
:alt: cottam metal locations
```


Metadata supplied at the time of deposit again gives useful background information about this image:

```{list-table}
:header-rows: 1

* - 
  - Dublin Core Metadata for Image
* - Title
  - Cottam B metal detector finds
* - Creator
  - Dave Haldenby conducted the survey, Tony Austin entered data, and Julian Richards managed the GIS
* - Subject
  - settlement, excavation, survey, metal objects, coins, Anglo-Saxon
* - Description
  - The metal objects found by metal detector were plotted as part of the post-excavation analysis of the Cottam B Project, directed by Julian Richards. Data was entered into a Paradox database and then exported to Arc/Info. Cottam is an Anglo-Saxon settlement located in Yorkshire on the Wolds east of York.
* - Publisher
  - The image is licensed for distribution by the Archaeology Data Service
* - Date
  - 1995
* - Type
  - image
* - Format
  - postscript (eps) and gif
* - Identifier
  - http://ads.ahds.ac.uk/images/metal-de.gif
* - Source
  - Metal detector survey
* - Language
  - English
* - Relation
  - Derived from a larger GIS data set held by Julian Richards, Department of Archaeology, University of York. Data is from site 6865 in the Humberside Sites and Monuments Record. Site is called "Burrow House Farm, Cottam" in the RCHME National Excavation Index for England.
* - Coverage - Spatial
  - 4976 4667
* - Coverage - Temporal
  - Early Medieval - this term is derived from a controlled MIDAS list (RCHME 1998)
* - Rights
  - Image is freely accessible to registered Archaeology Data Service users.
```

As mentioned in section 6.3, tools are being developed by the ADS to assist in the creation of metadata. This will facilitate the creation of standard, structured metadata rather than free-text entries for each of the fields - important when using metadata to enable searching for data sets.

## Too much work?

If you were considering deposit of an __entire__ GIS data set you might not want to create such detailed metadata records for every single layer. There is a high degree of overlap in the metadata for these three images, and this points to another possible option -- creating a single metadata record describing the contents of the __entire__ GIS data set that you wished to archive. In this case it would be important to use enough subject keyword terms to identify themes within the GIS data set.
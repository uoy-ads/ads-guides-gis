---
authors:
  - name: null
---

# 2 Creating and Using GIS data

## 2.1 Data types: Vector and Raster models

Spatial data can be most simply defined as information that describes the distribution of things upon the surface of the earth. In effect any information concerning the location, shape of, and relationships among, geographic features [@walker1993agi; @demers1997fundamentals]. In archaeology we routinely deal with an enormous amount of spatial data, varying in scale from the relative locations of archaeological sites upon a continental landmass down to the positions of individual artefacts within an excavated context. The first half of this section highlights the most important issues that need to be considered in incorporating common sources of spatial data within a GIS database. It comprises a short review of the particular issues that relate to obtaining and integrating spatial data within the GIS database. This concentrates on generic concerns such as projections, precision, accuracy and scale and is followed by a consideration of more source-specific issues. Throughout, the emphasis is upon the importance of carefully recording information about the various data themes.

There are two principal GIS data-models in widespread use, which are termed vector and raster. They differ in how they conceptualise, store and represent the spatial locations of objects.

It should be noted that, to date, the principal applications of GIS within archaeology have been restricted to 2-dimensional models, and at best 2.5 dimensional representations. The latter are a result of the inability of currently available analysis and display tools to adequately deal with truly 3-dimensional data. As a direct result, the issues we will be discussing here are concerned solely with the integration, management, analysis and archiving of representations of 2/2.5-dimensional space.

### 2.1.1 The Vector Model

In the vector model, the spatial locations of features are defined on the basis of co-ordinate pairs. These can be discrete, taking the form of points (POINT or NODE data); linked together to form discrete sections of line (ARC or LINE data); linked together to form closed boundaries encompassing an area (AREA or POLYGON data). Attribute data pertaining to the individual spatial features is maintained in an external database.

```{figure} ../images/vector.gif
:alt: Figure 1


__Figure 1:__ Vector and Raster Data. Cottam Project geophysics data displayed as a raster background and overlaid with an aerial photograph interpretation (blue line data), coins (red point data), and metal artefacts (black point data).
```

In dealing with vector data an important concept is that of topology. Topology, derived from geometrical mathematics, is concerned with order, contiguity and relative position rather than with actual linear dimensions. A good illustration of a topological map is that of the London Underground metro system. This well-known map is a precise representation of the stations (points or nodes) and the routes (arcs or lines) between them, yet provides only a very approximate indication of their relative locations and no indication of distances between them.

Topology is useful in GIS because many spatial modelling operations do not require co-ordinate locations, only topological information - for example to find an optimal path between two points requires a list of the arcs or lines that connect to each other and the cost to traverse them in each direction. It is also possible to perform the same spatial modelling and interrogation processes without using stored topology, by processing the geometrical data directly, as in such GIS as ArcMap and MapInfo, or by generating topology *on the fly*, as and when it is required. The latter is the approach taken by Intergraph, amongst other major GIS suppliers.

For a detailed discussion of the vector model see @aronoff1989geographic and @burrough1986principles.

__Important information to record about vector files__

The following information should always be recorded when assembling, compiling and utilising vector data:

* The data type: Point, Line or Polygon
* Type of topology which the file contains, such as line, network, closed area or arc-node
* Details of any automatic vector processing applied to the theme (such as snap-to-nearest-node)
* State of the topology in the file, particularly whether it is 'clean' (topologically consistent) or contains inconsistencies that may require further intervention or processing. This is particularly important where arc-node data is concerned
* Projection system
* Co-ordinate system

### 2.1.2 The Raster Model

Here the spatial representation of an object and its related non-spatial attribute are merged into a unified data file. In practice the area under study is covered by a fine mesh, or matrix, of grid cells and the particular ground surface attribute value of interest occurring at the centre of each cell point is recorded as the value for that cell. It should be noted that whilst some raster models support the assignment of values to multiple attributes per discrete cell, others adhere strictly to a single attribute per cell structure.

Within this model spatial data is not continuous but is divided into discrete units. In terms of recording where individual cells are located in space, each is referenced according to its row and column position within the overall grid. To fix the relative spatial position of the overall grid, i.e. to geo-reference it, the four corners are assigned planar co-ordinates. An important concept concerns the size of the component grid cells and is referred to as grid-resolution. The finer the resolution the more detailed and potentially closer to ground truth a raster representation becomes.

Unlike the vector model there are no implicit topological relationships in the data, we are after all not recording individual spatial features but instead the behaviour of attributes in space. For a detailed discussion of the raster model see @aronoff1989geographic and @burrough1986principles.

__Important information to record about raster files__

The following information should always be recorded when assembling, compiling and utilising raster data:

* grid size (number of rows and columns)
* grid resolution
* georeferencing information, e.g. corner co-ordinates, source projection.

### 2.1.3 Choice of Vector, Raster or Combined Forms of Spatial Database

The choice of vector, raster, or combined, forms for the spatial database may be determined by the GIS software in use and its ability to manipulate certain types of data.

Vector means of managing and manipulating the data are to be preferred for handling information relating to discrete points, delimited boundaries, alignment of linear features, etc. Thus a vector model would be used for storing, and manipulating, an excavation plan.

Raster means of managing and manipulating the data are to be preferred for handling continuous information such as altitude (see Digital Elevation Models, below), vegetation, etc., and are the digital form in which information from Geophysical Survey, Aerial Photography, and other forms of Remote Sensing and non-invasive survey, are delivered.

Where both data types are required to be used *together* a GIS capable of manipulating both is required. When combining and integrating information from a variety of sources the following points should be kept in mind:

* All spatial data must be recorded in the same co-ordinate system. Data which are recorded to some other system must be transformed/projected to the required co-ordinate system.
* All spatial data should be to the same *spatial resolution*, or *scale*. It is not possible to get meaningful results from the combination of spatial data recorded to a scale of 1:250, as might be the case for an excavation site plan, with road alignments recorded to a scale of 1:250,000. In the former example 1mm represents 25cm, and in the latter example represents 250m. Spatial data recorded to *scales* of greater than around 1:10000 involve considerable generalisation of alignments to avoid features conflicting. This is especially true of *paper* maps drawn to such scales.
* Non-spatial information to be combined, or integrated, must use the same field definitions, encoding regimes, etc. Where different schemes are used it will be necessary to convert or translate the data to the required scheme.

### 2.1.4 Layers and Themes

The terms *layer* and *theme* are used almost interchangeably by many people - archaeologists and GIS practitioners included - yet are given very distinct meanings by some software suppliers and in some specific disciplines, for example in Computer Aided Design (CAD). For the purposes of this guide these terms will be used as follows. A __theme__ is a collection of like objects, for example 'pottery', 'Iron Age sites', etc. A __layer__ is a group of specific objects within a *theme* - for example, 'Stamford Ware' within the pottery theme or 'Hillforts' in the Iron Age site theme. In order to avoid confusion, it is important that the names given to such themes and layers are both descriptive and free from ambiguity.

```{figure} ../images/gis_theme.gif
:alt: Figure 2


__Figure 2:__ Layers and themes. Two layers from the Cottam Project GIS (red layer with coin findspots and black layer with metal artefact findspots) are combined to represent the metal object theme. Two other themes are illustrated in this image, one for aerial photograph interpretations (line data) and another for geophysical survey data (raster image).
```

The purpose of the theme/layer approach is to provide a framework for collecting together objects of similar nature - in terms of either representation and/or descriptive type. Thus, different Iron Age site types might be gathered together because they are related in terms of both the representational type - a line or point object - and because of their nature or purpose - delineation of the landscape location selected for settlements in the Iron Age. In the same way, a database of finds of pottery might be defined in locational terms as a collection of points, each of which might relate to an individual object, or closely related group of objects.

## 2.2 Precision and Accuracy, Scale and Resolution

### 2.2.1 Precision and Accuracy

In incorporating any spatial data source it is crucially important to consider the issues of *precision* and *accuracy*.

"Precision implies that the degree of measurement of an attribute is refined; accuracy that the measurement taken is correct within the degree of precision indicated" (@richards1985data: 20).

This can best be illustrated with respect to the example of a highly detailed topographical survey undertaken using a total-station survey instrument and based upon reference points taken from a 1:2500 scale base-map. This is an example of a potentially very __precise__ method using potentially very __inaccurate__ data. This is because the source data, i.e. the fixed point locations derived from the map, are not sufficiently accurate to justify the precision employed in the method. To summarise, accuracy relates to the correctness of a result, whereas precision is essentially a measure of the units used.

As an aside, such issues of precision and accuracy are of particular interest in the context of GPS, where the quoted accuracy of co-ordinates varies commonly from sub-centimetre to around ±50 or so metres. Although this varies according to where on the globe you are referring, one second is approximately equal to thirty metres, yet, in terms of decimal degrees, is represented by a value of 0.0002777778. Thus a typical GPS readout in decimal degrees of, say, 52.005N is only within about 500 metres - making the general GPS error rate of ±50 metres trivial!

There is a temptation to believe the apparent accuracy with which computer-based GIS report the co-ordinate locations of objects. This information is, however, only as good as the initial data source, and errors made at this stage can be perpetuated through the lifetime of the data set.

### 2.2.2 Scale and Resolution

Scale is the ratio of the distance measured on a map to that measured on the ground between the same two points. For example a quoted scale of 1:50,000 implies that a distance of 1 cm on the map translates to a distance of 50,000 cm (or 500 metres) on the ground. Often, the difference between large and small map scales is confused. The larger the ratio, the smaller the map scale. Therefore, a map of the world would have a very small scale, whereas a map of a town centre will have a large scale.

Resolution is the smallest distance that can be usefully distinguished on a map with a given scale, for example on a 1:10,000 scale map the smallest distinguishable distance is 0.5 mm which equates to a distance of 5 m on the ground. It is worth noting that the accuracy of a map cannot be 'better' than its resolution, but it can often be much 'worse'.

The larger the map scale, the higher the possible resolution. It is very important to be aware of the scale of a given spatial data source as the degree of simplification and reduction involved in the representation of spatial features tends to increase as scale decreases. As map scale decreases, resolution diminishes and feature boundaries must be smoothed, simplified, or not shown at all. This process is referred to as generalisation. To give an arbitrary example, a map of an area of rural Greece produced at a scale of 1:5000 may show villages and towns as discrete areas, whereas at a scale of 1:500,000 they will be portrayed as little more than dots.

It should also be noted that the wider usability of any co-ordinate system is partly a function of the resolution in which it is quoted. For example, in the UK, the widely used six figure OSGB grid references are only valid within the hundred kilometre grid square for which they are quoted - they repeat in every other hundred kilometre grid square and they also only address to the nearest kilometre, even though the OSGB National Grid per se can support references to the nearest metre (or even sub-metre, if given as a decimal number).

In a GIS where spatial data sets from a range of sources are integrated and the spatial resolution of a given data set can be altered at will, it is vitally important to be aware of such issues and not to analyse spatial information at a scale greater than that of the data source (see @demers1997fundamentals: 56 for discussion).

## 2.3 Attribute Data and Databases

Information commonly stored, or manipulated, using a GIS tends to have two main components - the *spatial* and the *descriptive* attributes. For many users, and with many software products, these two data types may appear to be a seamless unit. There are, however, some data management issues which are peculiar to whether you are working with spatial or attribute data, and certain general issues which are common to either form of information.

*Attributes* are data that describe the properties of a point, line, or polygon record in a Geographic Information System. For example, imagine a GIS coverage in which points represent sites on a landscape. The attribute data that accompanied this coverage would record more detailed information about each site. Attribute information might include an indication of the time period in which the site was occupied (e.g. Neolithic, Iron Age, Medieval), full descriptions of the archaeological deposits excavated from each site, and an indication of the class of artefacts found on the surface at each site.

Archaeological attribute data already exists in myriad forms. These can range from simple card indexes - for example the results of a graveyard survey undertaken using the Council for British Archaeology guidelines - through to complex digital databases recording a wealth of detailed information. Such databases sometime include descriptions about all the archaeological sites in a country or county and sometimes contain very detailed site-specific information such as stratigraphic records. This diversity is on the increase as the use of computers grows in archaeology.

In archaeological GIS you will often be linking and combining attribute information collected by others, and turning this information to new purposes.

### 2.3.1 Common Sources of Attribute Data

Below are some likely sources of attribute data which you may come across, and wish to re-use:

* paper based card indexes
* archaeological site and survey archives (including paper based records, finds databases)
* qualitative report texts and articles published in journals (paper based or on the Internet)
* microfiche archives
* geophysical interpretation data derived from interpreted geophysics plots
* aerial photograph interpretations which may include morphological analysis, attribute data and photo source information
* typological databases or artefact type series
* data generated at a regional level for integrated large scale historic landscape studies
* local level archaeological databases (e.g. Sites and Monuments Records or Urban Archaeological Databases where they are held separately)
* local museum site and finds databases
* local Record Offices
* national archaeological databases (such as the various National Monument Records or English Heritage's database of Scheduled Ancient Monuments)
* Gardens Trust surveys
* historic buildings surveys and databases maintained by local authorities
* metadata relating to data sets

### 2.3.2 Designing a New Attribute Database

Whether you are using pre-existing attribute data or actually collecting new information yourself, you will need to think carefully about the design of your new attribute database. A great deal of literature exists on this complicated topic - it is quite literally a topic which has launched a thousand PhD research projects! Some good sources of basic information can be found in @batini1991conceptual, @date1995introduction, @ryan1995database, and @whittington1988database.

Archaeologists should also be aware of [MIDAS Heritage](https://heritage-standards.org.uk/midas-heritage/), the Monument Inventory Data Standard [-@rchme1998midas]. This standard is designed for those establishing a new attribute database in which to manage archaeological information or for those who have been working with archaeological attribute databases for a long time.

__The principal types of database structure__

Database systems should be efficient tools for the storage, analysis and reporting of your data. As a result, the choice of database package and data structure used in a given project should be dictated by the requirements of each organisation or project. It is not within the scope of this guide to enter into a discussion of the merits and failings of software packages. Instead a short overview of the types of database data models is presented.

Data structures currently fall into four major types: *flat file*, *hierarchical*, *relational*, and *object oriented*. More detailed discussion of these can be found in *Fundamentals of Spatial Information Systems* [@laurini1996fundamentals], especially pages 620-38 on object oriented databases.

__Flat file data structures__

In this simplest form of data structure, data are arranged in concurrent horizontal rows, with attributes stored in vertical columns. One row stores all attributes for a single entry (object) on the database. If many of the objects on the database have the same attributes they must be entered many times, leading to data redundancy and often to empty fields. A common example is the card index.

__Hierarchical data structures__

Hierarchical data structures have useful applications within archaeology as they arrange the objects in a database in a related tree of linked parent and child records. This can be used to model the breakdown of the historic environment into 'monuments within monuments' and allows flexible searching across the hierarchy. The most common applications for these database structures are in cultural resource management environments such as HERs and national databases which contain large amounts of data and need efficient, speedy, searches.

__Relational data structures__

Currently the most common type of database used is based on the relational data model. If you imagine a series of tables similar to small flat file databases, with links or relationships between specific unique fields that allow complex queries of different data sets, you have the essence of the relational structure. One table could be of pottery types, another of contexts, a third of scientific dates and with easily structured queries it will be possible to construct chronologies based on pottery typology or scientific dating.

__Object oriented data structures__

The newest form of data structure, there are currently a limited number of GIS packages using the object oriented approach (e.g. Smallworld). While the relational data structure deals with an object's description by tearing it apart into single rows, and holding those rows in many discrete but linked tables of similarly grouped attributes, the object oriented approach to data structure allows the descriptive attributes of an object (e.g. a monument) to be encapsulated digitally in one place, allowing a more realistic model of the 'real world' to be assembled. The geographic location of the object is then just another characteristic of the object, just as function, date and period of existence are.

### 2.3.3 Issues to Consider When Structuring and Organising a Flexible Attribute Database

When attempting to structure and organise a flexible attribute database the following factors are of critical importance. In the following section each of these issues will be looked at in turn.

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

__Naming conventions__

Try to keep field names descriptive rather than cryptic. The crib sheet for decoding cryptic names may easily get lost, and your fields are likely to be too numerous for you to remember their contents easily.  __Also be aware that some GISs (particularly ArcMap) have limits on the number of characters in field names, so truncation may occur.__

__Key fields__

Key fields are the most important fields in your attribute database and are the fields that will be used for primary searching of the database and/or for linking tables within your database. It is essential that the same data definitions are used for all instances of the key field in your database and that the same codes are used in each.

__Character field definitions__

Take care with character field definitions. Most databases require character data to be stored in a fixed length form and so, inevitably, this means that every record must contain enough space for the largest expected, even where this is not required for the vast majority of records. As an example, there is no point in defining a location name field large enough to store the longest name in Monmouthshire, *Llanvihangel-Ystern-Llewern*, if the name *Monmouth* happens to be the longest in the data set!

__Grid references__

Store grid references in an appropriate notation for easy transition to a GIS or conversion to an appropriate map projection (e.g. British National Grid references are commonly held as alphanumeric attributes in a single column which require some processing before points can be mapped on a GIS, a more appropriate form of notation would be in two numerical columns e.g. **4**56344 / **2**67833 for __SP__ 5634467833).

__Validation__

Get in the habit of ensuring that the data entered into any field in your attribute database makes sense. For example, check that you haven't typed the letter 'O' instead of '0' (zero). Another tip is to check that numeric values are within range - for example that a slip of the old typing fingers hasn't moved your Norman site from 1066 to 2066. It's often helpful to have someone else validate data that you have entered as typos are more easily detected by a fresh pair of eyes. If your data input tools allow you to define validation checks, use them, but remember that - like spelling checkers - they cannot catch all possible input errors.

__Numeric data__

It is best to use numeric field types rather than text fields if you have numeric data. This can have three benefits. First, confusing characters - such as that familiar O (letter) instead of 0 (zero) problem - cannot be stored in the wrong field type. Second, in many computer-based databases numeric information is stored more efficiently than text and occupies less space. This means that your GIS data set will be leaner and meaner. Third, when data is held in numeric form the data can more readily be manipulated with the arithmetic operators.

If you are using numeric data, also ensure that you use the most appropriate numeric type - integer or floating point. Integer types are used for storing whole numbers and floating point numbers are used for storing numbers which have, or may have, a fractional part.

__Data entry control__

Where possible the fields should be set up to use dictionaries or thesauri to ensure that typing errors are kept to a minimum and restricted to free text fields, and that terms used to describe real world objects are used accurately and consistently. Adhere to established appropriate project data standards (e.g. the RCHME/English Heritage Urban Archaeological Database Data Standards). If no project standards exist, adhere to the data standards of the digital archive for your data. Remember that your data will need a home if it is to remain a useful and accessible resource in the future, and it is your responsibility to ensure its compatibility with other data sets of a similar spatial or temporal resolution.

__Confidence values__

These indicate the level of certainty that is associated with an entry in the attribute database. For example, your certainty that the location, identification, dating, etc. of the object is accurate. It is very good practice to maintain this information at all times.

__Consistency__

Try to ensure that the codes used to record your attribute data are consistent. Ensuring consistency is especially difficult when data entry is performed by more than one person, or if data entry is carried out incrementally over time. The use of thesauri and documentation standards can be helpful in ensuring consistency within your database and between your database and others.

__Dates__

Calendar dates should be recorded in a date field-type rather than character field-type to avoid the loss of crucial data when transferring into different software packages. Be aware some software will not prompt you if you are about to lose data due to incompatible field types.

__Documentation__

The most important thing of all is to document the way you have organised your database and entered information into it! It is essential that source-specific information is recorded as and when data is generated, as this task becomes increasingly difficult retrospectively. Where did the source data originate from, what was the scale at which it was prepared, if based on others' work where can this be found, and what are the copyright restrictions involved in its use by a third party? What levels of accuracy were accepted and what errors were recorded during digitization etc? What data standards were adhered to (dated if possible, as revisions will occur) and what naming conventions have been adopted.

### 2.3.4 Combining and Integrating Attribute Databases

__Data standards__

Successful database integration relies on the implementation of data standards. These aim to facilitate the production of a common frame of reference for archaeologists, endorsed by the profession as a whole and implemented in a widely compatible national network of databases and digital archives.

Many core data standards have been defined for many fields of archaeology, from portable items such as MDA Archaeological Object Thesaurus [-@mda1998archaeological] and the International Guidelines for Museum Object Information, produced by the International Committee for Documentation [CIDOC](https://cidoc.mini.icom.museum/wp-content/uploads/sites/6/2020/03/guidelines1995.pdf), to the draft data standards for SMRs and revisions of the RCHME Thesauri of Architectural Types, Monument Types, and Building Materials. Another useful resource is MIDAS Heritage. Outside of the profession, essential standards have been set for such data sets as British postal addresses (BS7666), and international naming conventions for countries (ISO3166).

The basic process involved in the integration of data from external databases relies on compatible field structure. This means that complementary fields in both the source and target databases must be of a compatible type (Integer, Floating Point, Date, a Character field of an appropriate length etc.) to avoid the loss of data during the integration process.

Some features of certain databases (e.g. DBASE memo fields) are difficult to export to other systems and may require specialist advice to avoid their loss. The new data should be date stamped digitally by the computer operator and a record kept of its source and ownership.

__Integrating paper records__

Data can be extracted from documents and typed manually into an existing database, or whole reports can be captured speedily using a commercially available optical character scanning suite. These convert scanned text into digital characters which can be saved into a variety of word processor formats. The character interpretation is never 100% effective and will require spell-checking and proof-reading before it is used, but this method can save a great deal of time, especially when capturing printed table data. Most often, the integration of paper-records will involve some form of manual input, often involving a number of separate individuals over a considerable period of time. Here the importance of adherence to existing standards and guidelines cannot be over-stressed. Such a process often involves a great number of decisions that directly affect the quality of the source data sets, as often very descriptive information is broken down into the discrete thematic field structure of the database. To ensure that the resultant database is usable it is important to record such decisions and ensure that a degree of consistency is adopted throughout the process.

## 2.4 Projections and Coordinate Systems

These matter because at some point there is a need to integrate information from different projects in order to study the results together or in the context of something new.  Projections are increasingly important because of the widespread availability of affordable satellite navigation devices that enable one or more locations to be accurately recorded and the data retrieved for later use.  Coordinate systems are important because these provide the means of specifying a location.  This section aims to introduce these topics but cannot be a replacement for the excellent texts on the subjects, to which reference is made in the text and where the necessary detail will be found.

### 2.4.1 Why do we need Projections?

Our planet Earth is not in fact a sphere, although it is often most convenient to treat it as such, as indeed is done by the various satellite positioning systems.  Even if the Earth were a perfect sphere, there would remain a problem, because spheres make rather inconvenient notebooks or publication media.  Imagine a set of paper maps replaced with set of balls or curved plates!  Unfortunately it is not possible to accurately and completely represent the surface of a sphere on any other type of surface: for example, having peeled an orange, the peel only joins up again when back in the orange shape.  The process of rendering the surface of a sphere onto another type of surface is likened to placing a light source within the sphere and *projecting* the surface as an image onto the destination medium as though that were a screen.  How this works is a matter for the textbooks; however, because the process inevitably introduces elements of distortion into the result, because the result is not on the surface of a sphere, it is necessary to understand something of the implications.

There is an additional complication: not only is the Earth not a sphere, it is not actually a regular geometric shape: it is flattened at the poles and over the oceans and bulges at the Equator and over the continents.  Sometimes this shape is treated as an ellipsoid or an oblate spheroid, but the term most generally used is *Geoid* - which simply means *Earth-shaped*.  As a result, there is no single elegant solution but many alternatives, as different parts of the Earth's surface require different types of solution.  Sadly, the choice of the wrong projection for a particular purpose or location can have very serious consequences.

There are four key characteristics of any representation of a three dimensional phenomenon or of a planimetric representation: shape, scale, direction and area.  These are also characteristics of projections but, with the source being a transformation from the curved surface of the Geoid, it is not possible to preserve all four - except on the Geoid.  The loss of one or more of these characteristics means that the result is a compromise between fidelity to the surface of the Earth and the flat represntation on paper or the computer screen.  This also means that there are different types of projection for different applications.

### 2.4.2 Properties and Types of Projection

There are four classes of projection properties and three classes of type.  It is theoretically possible for there to be projections of each type and property, and combinations of up to three of each of the properties but there are combinations that are uncommon.  This guide can only explore some of the most common types of projection, the literature must be consulted for others.

__Conformal projections__

Conformal projections preserve *shape*.  However, especially where the coordinate system is Cartesian, *area* will be distorted; it is only possible to preserve shape for small parts of the Earth's surface and no projection can preserve shape at a regional or global scale.

__Equal-area projections__

Equal-area projections preserve the *area* of the represented part of the Earth's surface but at the expense of distortion to shape and possibly angle and or scale.  For very small areas of the Earth's surface, the extent of distortion to shape may be difficult to measure.  Some equal-area projections do not yield Cartesian coordinate systems.

__Equidistant projections__

Equidistant projections maintain correct scaled distance between selected points but, as with all other projections, no projection can preserve true distance everywhere on the map.

__Azimuthal projections__

Azimuthal projections preserve direction between all points represented and are sometimes called *true-direction* projections.  Azimuthal projections are typically used for maps used to support navigation.

__Conic projections__

Conic projections work as though a cone of paper has been placed on the Earth.  Conic projections where the cone only touches the surface along a single circle are said to have *one standard parallel*, whilst those which intersect the surface are said to have two.  The simplest conic projections *sit* on a pole, *polar conic* projections, with the others are termed *oblique*.  In conic projections, the meridians, lines of longitude, meet at the tip of the cone and the parallels, lines of latitude, are parallel to each other, but not necessarily equally spaced.  The cone is generally opened out along the line opposite the *central meridian*.  Conic projections are sometimes used for polar regions, but are more often used for regions that have a large horizontal, East to West, extent: the *Lambert Conic Conformal* projection is often used for representing the co-terminal states of the USA.

__Cylindrical projections__

Cylindrical projections can be envisaged as a sheet of paper wrapped around the Earth to form a cylinder.  In cylindrical projections, the meridians are all parallel and equally spaced and the parallels intersect the meridians at right angles but need not be equally spaced.   In *Normal* cylindrical projections, the paper is wrapped around the equator and is open at the poles.  In *Transverse* cylindrical projections, the paper is wrapped around the poles and open at two sides to the Equator.   The well known *Mercator* projection is a *normal cylindrical* projection, whilst the *Transverse Mercator* projection is the *transverse* form.  The British National Grid system, introduced in 1936, is a *Transverse Mercator* projection, as are UTM (which is widely used in the US) and the *Gauss Conformal*' or *Gauss-Krüger* projection widely used in mainland Europe.  The *Cassini* projection, used for the early *County Series* mapping of Great Britain, is also a *transverse cylindrical* projection and is well suited for mapping regions that have limited horizontal extent but extend considerably North to South.

__Planar projections__

Planar projections work as though a flat piece of paper is placed tangential to the Earth's surface and can take *polar*, where the point of tangency is a pole, *equatorial*, where the point of tangency is on the Equator,  or *oblique* forms.  The *polar* form is the most common planar projection, in *azimuthal* form being often used for mapping polar regions.

__Geographic projection__

The literature also often refers to a concept of a *geographic* projection yet, properly, this is not a projection at all.  In the *geographic* projection position is represented by spherical coordinates of angles relative to the centre of the Earth, degrees of *Latitude*, and angles around the Equator relative to a reference *Meridian*, degrees of *Longitude*.  The reference, *prime*, meridian, zero degrees, is arbitrarily chosen to be the Greenwich Meridian.  There is usually no geoid associated with this concept, thus it is not possible to measure distance or area but it is possible to estimate direction.   When assoicated with the *WGS84* spheroid, this equates to the positioning system used by satellite navigation systems.

### 2.4.3 Coordinate Systems

Coordinate systems provide a means of communicating the location of some feature represented on a map in terms of that map representation.  The most commonly used are termed *Cartesian*, after Descartes, and comprise a regular grid relative to two or three axes at right angles to each other, as in a graph or chessboard.  There are many types of Cartesian coordinate systems, from mixtures of letters and digits, as with a chessboard, to numeric offsets from an origin, as with a graph.  It is not strictly necessary for a Cartesian coordinate system to use the same units or unit interval on each axis, although using different units or intervals for the horizontal axes is liable to lead to considerable confusion for anyone seeking to *read* the map or plan.  Some of the impacts on end users of the choice of projection and coordinate system are discussed by @monmonier1996lie.

__Cartesian coordinates__

These are familiar to most people and are those used in archaeological site grids, comprising a set of measurements along axes set at right angles to each other.  Typically these measurements are *in metres*, as in the British National Grid, but *feet* are used in the USA.

__Spherical coordinates__

These are measurements of angles relative to the centre of a sphere and relative to a central *prime meridian*.  The *Greenwich Meridian*, the meridian passing through Greenwich, in south west London and as measured by Sir George Airy in 1851 was adopted internationally in 1884.  More recently and based on measurements from satellite observation, an *International Earth Rotation and Reference Systems*  meridian, the *IERS Reference Meridian (IRM)*, was established for use by satellite navigation systems.  The IRM is very slightly to the East of Airy's Greenwich Meridian.

__Other coordinate systems__

Postal codes provide a means of referencing the location of properties, or small groups of properties, and have given rise to a geography based on these references.  In the UK, Postcodes are widely used for social science applications, such as Census work and the unit is also used by emergency services and planners.

### 2.4.4 Datums

Every projection requires a *Datum*, which provides the reference grounding to the Earth's surface.  The datum provides the reference parameters for the coordinate system to *lock* it to the surface of the Earth.  All datums define the geoid to be used for approximating the shape of the Earth when calculating position and it is critically important to use the correct datum, or positional calculations can become wildly inaccurate.  The datum also defines the zero point for measuring altitude or depth.  Ordnance Survey define a number of datums for use for Great Britain, based on the Airy Spheroid; the choice of datum is dependent on scale and location within Great Britain and there is a general purpose datum for use with small scale mapping, eg 1:50000.

### 2.4.5 Further Reading

This guide is not the place to teach map projections, coordinate systems or datums.  Some of the following publications assume the reader to have some understanding of the topics concerned, although @kennedy2000understanding, @monmonier1996lie and @snyder1987map all provide at least some introductory material. @snyder1987map is the key authority, especially should formulae for individual projections be required. @bugayevskiy1995map and @yang2000map also include discussions and formulae relating to mapping in Russia and the former USSR and the Peoples Republic of China respectively.

## 2.5 Sources of Data

In undertaking any GIS-based work the most common sources of spatial data will comprise one or more of the following:

* mapsheets and plans
* raw co-ordinate lists, derived from field survey or extracted from existing site records such as those held within national and regional monument records
* aerial photographs and remotely sensed images
* digital data products, such as the United States Geological Survey topographical data.

__Derived Data__

You will often be using data derived from other sources when creating or managing a GIS data set. There are often important considerations in documenting derived data sets, as discussed in [Section 2.8](creatingandusinggisdata#id-2-8-why-document-your-data). __When deriving data from another source, or when making use of derived data, it is the responsibility of the data user to ensure that any intellectual property rights belonging to the initial data creator(s) are respected__. In some cases this may simply be a requirement to acknowledge the originating source, in other cases a royalty payment may be due for some part of the data to be used. Be sure to check out the situation in advance.

### 2.5.1 Maps and Plans

Mapsheets comprise one of the most widely available and familiar sources of spatial data. In incorporating spatial data derived from mapsheets it is important to be aware of a number of issues. The first of these concern the map itself. The medium of the map itself is highly important. While maps originated on specially stable plastic films, such as mylar, are reasonably stable, paper maps can stretch and distort over time. In addition, where the map is a copy rather than an original a number of distortions may be present as a result of the specific copying process used. In general the following information should always be recorded:

* Publisher and copyright owner, which will often (but not always) be the same. For Ordnance Survey mapping, the copyright holder is the Crown.
* The map medium.
* Scale of source map, given as a ratio, and the original scale (where the source map is an enlargement or generalisation from another map).
* Name of the map and the map series (where appropriate).
* Claimed accuracy for any specific map components: map makers will often provide an estimated precision for contour lines or other sub-components of a map.
* All details of the map projection and co-ordinate system employed. This information is usually printed on the mapsheet or else should be sought from the map source.

__Integrating map data__

There are three methods for integrating map data into a GIS database and these are based upon two discrete techniques. Where information to be recorded is indicated, this should be considered as being in addition to the generic information required for all mapsheets, as described above.

__Scanning__

Paper mapping can be scanned, with a flatbed or drum scanner, to generate raster GIS data themes. Scanning devices vary considerably in accuracy and resolution, with flatbed and drum scanners normally providing a resolution between 100 and 1200 dots per inch (dpi). The more expensive drum scanners claim resolutions of between 3-5000 dpi. In all cases care should be taken to distinguish between the true optical resolution of a given scanner and that obtained through interpolation procedures. If scanned, then there is likely to be a single raster file data product.

There are a very wide variety of image formats for holding raster data (see the [Raster Images](https://doi.org/10.5284/mtgj-7130) guide), the majority of which are designed for photographic images and not spatially referenced data. Several GIS provide proprietary raster data structures and record spatial referencing information (e.g. IDRISI, Arc/Info GRID, SPANS raster, GRASS raster), they also provide tools for importing data from other common raster formats. The Tagged Interchange File Format (TIFF) graphics standard has also been extended to provide georeferencing and spatial data in a format called 'GeoTIFF'. Details of the GeoTIFF standard, including the official specification of Geotiff 1.0 can be obtained from the [Geotiff website](https://trac.osgeo.org/geotiff/).

It should be noted that the scanning process can result in some very large raster images and this can be compounded by the software used to integrate and study the raster layers which may require increased colour depth.

For products that have been generated by scanning paper originals, the following additional information to the core mapsheet data should be recorded for each raster file generated. It should be noted that to retrieve some of this information will involve careful checking of the respective hardware and software documentation:

* Details of the scanning device used, such as the make and model, software driver and version
* Parameters chosen in the scanning process, such as the resolution setting of the device, the number of bits per pixel used
* Details of any pre-processing undertaken on the source mapsheet. This may include a range of options provided by the specific scanning software used
* Details of any post-processing undertaken on the data, such as noise reduction or sharpening with convolution filters, histogram equalisation, contrast adjustment

__Digitising__

Maps and plans may also be geometrically described, using a digitising tablet, to provide vector data. Digitising tablets generally offer finite resolution in both x and y directions. This can be expressed as a quoted resolution, for example 0.02 inches or 0.001 inches, or as lines per inch (lpi), e.g. 200 lpi or 1000 lpi. This information can be found within the digitiser manual. Unlike the scanning process, where a scanned map generates a single raster GIS image, digitising a single paper map may form the basis of a large number of discrete, thematic vector data layers.

When digitising mapsheets the following additional information should be recorded. As with the scanning process this may involve careful checking of hardware and software documentation, for example to determine the resolution of the digitiser.

* Detail of the digitising device used, such as the make and model, software driver and version
* The precision, usually specified as a quoted resolution or as lpi
* Details of any automatic vector processing applied to the theme (such as snap-to-nearest-node)
* Details of control points used to manage conversion from digitiser to real-world planar co-ordinate systems
* Errors incurred in the above transformation process (e.g. quoted RMS)

__Scanning-digitising hybrid__

A third option is to scan the source document but then use the scanned product as the basis for 'on screen digitising', using a graphics workstation and pointing device to create vector data themes. This is often referred to as 'heads-up digitising' and is an attractive option where a digitising tablet is not available, or where raster data from a third party can be obtained.

The basis of heads-up digitising is to use the mouse pointer to trace around the image to be digitised, recording the coordinates as it moves - in much the same manner as moving the puck on a digitising table or tablet. With the image displayed on the computer screen, however, it is easy to zoom in on an area of complexity in a way that is hardly possible on the digitising table or tablet. Indeed, with the scanned image, the only limit to this enlargement is the point at which the individual cells, representing the marks on the original, are distinguishable as squares and rectangles. Where the scan is at 300 pixels per inch, typical of many desktop scanners, each of these cells represents approximately 0.085mm square; with higher resolution scanners the size of these cells is proportionately smaller! In addition to this facility, because registration is effectively performed when the map/plan is scanned, it is much easier to undertake the digitisation in much smaller time-chunks, thus minimising errors resulting from fatigue, etc.

There are a number of software tools available to assist in obtaining vector data from a scanned image of a map or plan. These include very sophisticated, semi-automatic, tracing tools which, for an ideal image, can often vectorise perhaps 70-80% of the data without intervention and which automatically request intervention when a problem cannot be resolved. Examples of this type of tool include Vtrack, from Laserscan, and ArcScan, from ESRI. Tools such as these can manipulate output from high (over 3000 pixels per inch) resolution drum scanners, as well as the output from a desktop flatbed scanner. Such software tends to be expensive, although sometimes available to non-profit research and educational institutions at discounted rates. There are also, at the other end of the price/sophistication range a number of cheap/shareware tools for running on a PC. These may have limitations in terms of the maximum scan resolution they can handle, or the maximum size or complexity of the image. Note that none of these tools can be guaranteed to be able to vectorise 100% of a scanned map/plan without intervention. The degree of intervention required will always be a function of the sophistication of the vectorising/tracing tool, the quality of the scan, and the nature of the original.

### 2.5.2 Textual and Numeric Data

Often spatial data will be encoded in the form of co-ordinate lists, for example those commonly found within regional and national monument registers. Where co-ordinates are expressed they should conform to the standard Surveying notation of Easting, Northing, elevation (x, y, z) though this may not be consistently applied in proprietary systems and particularly in hand-written records.

It is important to determine how the co-ordinates were derived, for example are they reckoned from a base-map or determined through field survey? In addition, it is also important to determine the precision of the co-ordinates as quoted. For example, within regional monument registers in the UK it is not uncommon to find the locations of archaeological sites quoted to the nearest 100 metres (what is referred to as a 6 figure grid reference). If this data is to be integrated into a GIS database comprising spatial data originated at one metre resolution, these co-ordinates will have to be rounded up, leading to a spurious level of accuracy.

One important point to realise when using co-ordinate references is that even when a discrete point reference is quoted it is in actuality indicating the lower left-hand corner of a bounding box. The size of this bounding box is dictated by the resolution of the reference. To return to the example of a UK sites and monuments register, far from indicating the precise location of a site on the ground, the six figure reference actually serves to locate the bottom left-hand corner of a 100 x 100 metre bounding box, somewhere within which the site is located.

__Integrating Textual and Numeric Data__

When integrating textual and numeric data it is important to understand the co-ordinate system to which the quoted co-ordinate locations relate. Although co-ordinates will most commonly reference a national or international system, such as the Great Britain National Grid, or UTM, occasionally they may relate to a site-grid. This is a contingent rectangular co-ordinate system with its datum at a fixed point, that has been established for a specific purpose. Perhaps the most common examples are geophysical survey grids and excavation grids, established to facilitate the spatial recording of features within excavated contexts. Until the location of grids has been surveyed or 'fixed' with respect to a larger or more generic co-ordinate system, such as those mentioned above, it can be thought of as 'divorced' or 'floating' and whilst internally consistent is impossible to relate it spatially to features beyond the confines of the grid. Needless to say, the geo-referencing status of grids must carefully be considered when archiving data for potential future re-use as this can seriously affect the overall accuracy of the quoted co-ordinates. For a detailed discussion of these issues undertaken in the context of geophysical survey, practitioners are referred to the guide on [Geophysical Data in Archaeology](https://doi.org/10.5284/vrs7-8149).

When integrating textual and numeric data the following information should be recorded:

* The data source
* The precision of the quoted co-ordinates
* Have the quoted locations been verified and how?
* Projection system/co-ordinate origin
* If derived from a source map, where possible record details of the map-base used (see the paragraph on map data for details of the information required)
* If derived from a survey programme, where possible record details of the survey procedure (see the paragraph on Survey data for details of the information required)

### 2.5.3 Purchased or Downloaded Digital Data

Spatial data which is already in digital form may be purchased from mapping agencies (such as the Ordnance Survey or public utilities). Many agencies supply both raster and vector data, depending on the requirements of the user. An increasing amount of spatial information can also be downloaded from the Internet, again in both vector and raster formats.

__A Note on the Integration of digital data sources__

Looking to the information that it is important to record, it must be realised that such data is often derived from another medium, for example a scanned or digitised map or a scanned image of a geophysical survey. As a result, similar information to that required for these data sources should also be recorded for digital data products. This information will be obtainable directly from the supplier and should be requested if not supplied.

As discussed previously, vector data may take the form of simple points or lines, often with associated attributes, or more complex topological themes such as arc-node data. Because of the variety of data structures used in different GIS, particularly for arc-node data, there is currently no platform-independent standard file format for spatial data. Several standard formats are of interest, however, and may be used in particular circumstances.

* British Standard 7567 (the National Transfer Format) is the format used by Ordnance Survey for the supply and transfer of digital products. It allows both spatially referenced raster and vector products to be stored in ASCII coded form. A useful guide to the OS implementation of BS 7567 (NTF 2.0) may be obtained from the Ordnance Survey

* Users and those involved in the archiving of spatial vector and raster data in the United Kingdom should also be aware of the National Geospatial Data Framework (NGDF), which is "a national forum of data providers and data users seeking to facilitate and encourage widespread use of geospatial data which is 'fit for purpose'. Its objectives are to facilitate and encourage collaboration in the collection, provision and use of geospatial data; to facilitate and encourage the use of standards and best practice in the collection, provision and use of geospatial data and to facilitate and widen access to geospatial data"

* SDTS (Spatial Data Transfer Standard) is a United States Federal Information Processing Standard (FIPS) which was developed to accommodate different data models to allow users to encode spatial data in a standard format, accompany data with description and provide machine and platform independence. SDTS is the responsibility of the Federal Geographic Data Committee (FGDC). SDTS is not an exchange format for data, rather it is a standard set of guidelines which will describe and preserve a database design and its underlying model.

* DLG (Digital Line Graph) format is used by the United States Geologic Survey for supply of vector information, while DRG (Digital Raster Graphics) is the description that the USGS gives for the distribution of scanned map sheets. Details of these standards may be obtained from the USGS WWW site.

* DXF (Digital eXchange Format) format is commonly used for transferring drawings between Computer Aided Design systems. It is also however very widely (mis)used as a *de facto* standard for the transfer of digital spatial data [@walker1993agi]. A detailed discussion of DXF is undertaken in the CAD Guide to Good Practice.

### 2.5.4 Aerial Photography

Aerial photographs may reveal archaeological sites directly, where they are extant, or as crop, soil or other surface indications where the site is buried. As a result, archaeology has a long history of using aerial photographs for recording existing site morphology, and prospecting for new ones.

Two types of aerial photograph are widely used in archaeology: vertical photographs and oblique photographs. In either case, the image will pass through at least two stages before it can be included in a GIS database i.e. it will need to be first rectified and then georeferenced. For a detailed bibliography and for a full and comprehensive discussion of the issues and techniques involved, including more advanced techniques such as photogrammetry, please refer to the guide on [Aerial Survey for Archaeology](https://doi.org/10.5284/g02y-6y14).

To incorporate scanned and rectified aerial photographs into GIS databases the following information should be recorded:

* Full Photographic details
* Details of the scanning process __if employed__ (see the paragraph on map scanning for details of the information that should be recorded)
* Details of the rectification method(s) used
* The software employed including, where possible, specific parameters chosen
* Details regarding the ground control points (GCPs) used during the procedure
* Details of any post-processing undertaken on the data, such as noise reduction or sharpening with convolution filters, histogram equalisation, contrast adjustment etc.

### 2.5.5 Satellite and Airborne Remote Sensed Images

Airborne remote sensing refers to situations in which an aircraft carries an electronic sensor that records information directly to digital format. In recent years, increasing use of remote sensing satellites has been made with images being available at reasonable cost. For a detailed bibliography and for a full and comprehensive discussion of the issues and techniques involved please refer to the guide on [Aerial Survey for Archaeology](https://doi.org/10.5284/g02y-6y14).

Looking to the information that needs to be recorded, many of the issues which arise when using scanned aerial photography will also be relevant to the integration of airborne remote sensed data. For example, they will normally require rectification in the same way as scanned photographic material. Once again, comprehensive details can be found in the guide on [Aerial Survey for Archaeology](https://doi.org/10.5284/g02y-6y14).

* Data source
* Date image was captured
* Data resolution
* Details of any post-processing undertaken on the data, such as noise reduction or sharpening with convolution filters, histogram equalisation, contrast adjustment etc.
* Details of the rectification method(s) used
* The software employed including, where possible, specific parameters chosen
* Details regarding the ground control points (GCPs) used during the procedure

### 2.5.6 Primary Survey Data

__Terrestrial Survey__

Data from older optical instruments will normally have been recorded and even processed entirely by hand. Most modern total-station and satellite-based instruments (using either US 'Navstar' Global Positioning System (GPS) or the Russian GLONASS) have internal data stores and processors, or are used with a separate data logging device, typically a hand-held or laptop computer.

Data may be obtained directly from these survey instruments, usually in the form of co-ordinate pairs (or 3D triples) often with attached attribute(s). It may be exported either to proprietary data file formats, or to ASCII files which can be imported directly to GIS databases. In many cases, there is unlikely to be a complex thematic arrangement of data, although this is changing with the increasing use of advanced data logging software that provides direct GIS or CAD input in the field.

Commonly, however, survey data will be in the form of CAD drawings, which may have thematic (layer) structure or complex block-attribute structure themselves. Here, the source and derivation of the data used to construct each layer must be documented. Readers should consult the CAD Guide to Good Practice to familiarise themselves with CAD systems.

Whatever the source of the data, it is essential to understand the sources of errors and to record details of any instruments, software and methods used to derive the co-ordinates used in GIS layers. Whilst modern semi-automated survey instruments and methods may be easier to use and reduce the possibility of simple transcription and mis-calculation errors, they are still subject to many sources of error. For terrestrial survey methods, these include the reliability of locations used as survey base stations as well as individual and cumulative measurement errors introduced by the instrument and its operators [@clancy1991site].

__Integrating Terrestrial Survey Data__

Survey information may well be in the form of angle and distance measurements. Although there are GIS which can store and manipulate such geometric measurements, they are most often processed to derive Cartesian co-ordinates. Much in the same way as for quoted co-ordinate lists and textual data, when incorporating terrestrial survey data into a GIS database it is critically important to understand fully the co-ordinate system to which the quoted co-ordinate locations relate. Most surveys begin their lives divorced or floating, i.e. quoting co-ordinates with respect to a highly contingent rectangular co-ordinate system. These divorced surveys are internally consistent and commonly employ very precise technology, for example total-station survey instruments, capable of recording locations to the nearest millimetre and beyond. Before the results of such surveys can be more widely employed they have, however, to be integrated within a larger or more generic co-ordinate system, such as a national survey grid or UTM. Despite the high precision of such surveys, this process of geo-referencing can severely affect the overall accuracy as often the divorced survey grid is 'fixed' with respect to points derived from base-maps which themselves may only, at best, have been located to the nearest metre. The more accurate the points utilised to fix the divorced survey grid within a larger co-ordinate system, for example the use of triangulation pillars or high precision GPS, the greater the accuracy of the resultant survey data resource.

When integrating data themes which are derived from survey data, the following should be recorded:

* The source (paper/digital map, GPS, data from mapping agency) and estimated error of survey base station co-ordinates
* Details of the survey, including date time and purpose
* Details of the thematic organisation of the survey
* Make and model of instrument used
* Type of survey (contour, feature etc.)
* Estimated error terms for the co-ordinate pairs and (if appropriate) the z-co-ordinate
* Georeferencing information, overall accuracy of the survey data

__Satellite-based (GPS) Survey__

Satellite-based survey data is complicated by the variety of possible methods used by receivers to produce a position fix, and by differential techniques used to improve the accuracy of fixes. Whilst a single fix from a simple hand-held device intended for navigational purposes may only be accurate to within 100m, differential correction may improve this to 10-15m, or better. On the other hand, under favourable circumstances, the best survey instruments may achieve sub-centimetre accuracy.

The accuracy of fixes from the same equipment varies through time as the relative positions of satellites and receiver change. Careful 'mission planning' is essential to avoid times when the satellites offer a poor configuration for triangulation or when a reduced number of satellites are visible from the observation site. Fortunately, many data logging packages include satellite prediction facilities that can be used to determine the optimum observation times. @sickle1996gps and @wells1986guide provide useful introductions to satellite surveying, whilst @leick1995gps gives a thorough coverage of the underlying technology and mathematics.

__Integrating GPS data__

As discussed earlier, satellite systems measure the relative positions of receiver and satellites using an ECEF Cartesian co-ordinate system. Whilst positions expressed in ECEF x,y,z co-ordinates are ideal for locating satellites and receivers in 3D space, they are rather less suitable for terrestrial mapping. Fortunately, most receivers will output co-ordinates expressed in latitude and longitude relative to the WGS 84 ellipsoid, and many will also generate positions relative to other ellipsoids and in other co-ordinate systems such as UTM or the various national grids. If the only co-ordinates available are relative to WGS 84 or some other system, these will require transformation to the system used for the base mapping in the GIS. This conversion requires both a transformation between ellipsoids and a datum shift. Numerous datums have been used for mapping around the world. For details, see @snyder1987map; [-@snyder1989album]. Each datum is defined in terms of a common reference ellipsoid together with x,y,z offsets that take account of differences in the origins of the ellipsoids and local deviations of the earth's surface from the ideal ellipsoid.

For mapping in the UK, the Ordnance Survey publishes two booklets [-@os1995ellipsoid; -@os1996geodetic] giving details of transformations between ECEF, WGS 84, Latitude/Longitude, and the National Grid. Similar transformations are used to derive UTM co-ordinates.

Some GIS provide suitable datum transformation functions and several purpose-written programs are also available for this task. It is important to realise, however, that the results produced by many transformation methods are only approximations that may degrade the accuracy of the original position. For example, the methods described in @os1996geodetic produce National Grid co-ordinates that are only correct to within 2 metres. The programs and methods used in any transformation must therefore be recorded as part of the history of the data.

In integrating satellite data the following information should be recorded:

* The method used to locate stations: C/A or P code pseudorange measurements, carrier phase measurements and whether a single measurement or averaging (include time period) was used
* The software used for any co-ordinate transformation and associated error estimate
* The satellites used in obtaining fix and observed GDOP (Geometric Dilution of Precision, a measure of the quality of the fix indicating the suitability of satellite positions for triangulation)
* The nature of any differential correction undertaken together with error estimates
* The broadcast differential: name of the service provider and the name and location of base station
* The local base station: instrument details, location (including error estimate) of base station
* Post-processing: the software used and the source of correction data

__Preferred and Accepted Formats for GPS Data__

GPS or GLONASS data will often have been recorded using data logging equipment and then transferred to other systems using a simple ASCII text, DXF or proprietary GIS or CAD format. For most purposes, one of these formats, particularly if it includes associated attribute data, will be preferred.

The direct output of many of these receivers is usually in one of the following formats:

* NMEA 0183: an ASCII protocol devised by the US National Maritime Electronics Association for marine navigation equipment [@nmea1995standard]
* RINEX version 2: Receiver INdependent EXchange format [@gurtner1990rinex; @gurtner1994rinex]
* A proprietary ASCII or binary format such as Trimble Standard Interface Protocol (TSIP)

Of these, RINEX is widely used and is not tied to a particular device or class of device. It also has a provision for recording comments and events, such as movement to a new survey point and the start of a new point occupation. Where raw satellite data forms part of a data set, it is the currently preferred format.

## 2.6 Digital Elevation Models

Digital Elevation Models, also referred to as Digital Terrain Models (DTM) or Digital Surface Models (DSM) record a raster representation of ground surface elevation; almost invariably the raster cell is square.  Unlike contours, DEMs deliver an elevation measurement for every cell in the raster, so there are no intermediate points for which interpolatiion is necessary.  DEMs are used for a wide variety of purposes, including studying visibility and intervisibility, exposure, hydrology, ease of access and, using high resolution data, minor surface variations that may indicate the presence of buried features.  This section first discusses some readily available DEM data for Great Britain and then sources for other areas.  It then discusses some of the potential uses in an achaeological context.

### 2.6.1 DEMs for Great Britain

The primary provider of spatial data for Great Britain is the Ordnance Survey of Great Britain (OSGB).  At the time of writing, OSGB offer two DEM products, both of which are available to users whose institutions are registered for the JISC Digimap service:
* Landform Panorama. This product is derived from 1:50000 contour mapping to generate a DEM with a 50m cell size and an integer (whole number) elevation value. This product gives a generalised surface model but which is unsuited for hydrological studies. It is good for general visibility and landscape studies.
* Landfrom Profile. This product includes material derived from 1:10000 contour mapping and spot height control for interpolating between contours and has a cell size of 10m and integer elevation value. It is better than Landform Panorama for hydrological studies but will not necessarily yield a hydrologically correct model. It is suitable for similar studies to those using Landform Panaorama but reqquiring greater detail. Users of DEM products derived from contours should be aware of significant potential artefacts that are directly related to the contour source. These are fully described in Jo Wood's PhD thesis [-@wood1996geomorphological].

There are a number of DEMs for Great Britain which are derived from Remote Sensing methodologies.  These include:
* Shuttle RaDAR Topography Mission (SRTM).  These data were aquired by NASA using a Synthetic Aperture Radar (SAR) instrument mounted on the Space Shuttle.  Details of the coverage and product options are discussed in connection with other geographic areas, below, however 3ArcSecond SRTM data for the British Isles (including Ireland) are available from the JISC Landmap service for academic and other users permitted access to this service.  These SRTM data have a cell size of 75m and a vertical resolution of 10m.  SRTM data are suitable for larger scale landscape studies and for visibility, intravisibility and exposure studies; they are not suitable for hydrological studies.  Whilst generally of good quality, SAR data suffer from a problem termed 'loss of phase coherence', where the radar signal cannot be effectively processed and which can lead to 'holes' in these data.  Such 'holes' are rare and are most common over water; they can also occur where the direction of the radar beam is the same as the slope of the ground.  The data available for download from the Landmap service are projected onto the British and Irish National Grids respectively.
* Landmap ifSAR DEM.  This product, with a 25m cell size is derived from European Space Agency European Radar Satellite (ERS) data using a process with similarities to the photgrammetric process used with stereoscopic aerial photography called *interferometry*.  This product gives a surface representation that include man-made objects, such as the upper surface of ambankments, bridges, etc.  These data are more detailed than the SRTM materials and generally have a better vertical resolution.  There are similar processing artefacts as the source instruments are similar.  Whilst unsuited to use in hydrological applications, these are good data for landscale level work and for visibility, inter-visibility and exposure studies.  These data are projected to the British and Irish National Grids respectively.
* Bluesky DTM.  This commercial DTM has a cell size of 5m and an integer elevation value which has been rounded to the nearest metre.  These data are photogrammetrically  interpolated from stereoscopic aerial photography and adjusted to record the ground surface elevation: a separate, Building Heights, dataset is available which records the difference between the measured and surface elevations.  At the time of writing, these data are available for England and Wales from the JISC Landmap service for academic and those users eleigible for access to this facility.  These data, registered to the British National Grid, are suitable for more detailed landscape, visibility, inter-visibility and exposure studies; they are also of a suitable resolution for larger scale hydrological studies, generalised flooding models, etc.  The cell size means that some larger archaeological features may be discernable from these data.
* LiDAR (Light Direction and Ranging).  These highly detailed products are generated from airborne laser instruments and can deliver ground cell sizes down to 25cm and a sub-centimetre vertical resolution.  Expensive to collect and store, these very high resolution data are primarily collected in the UK for flood risk modelling and monitoring and so tend to be collected for 'at risk' urban environments.  These data are capable of yielding highly accurate hydrological models and are capable of supporting study of buried structures that result in variations in ground surface elevation, such as archaeological remains.  UK data are collected by the Environment Agency and the Geoinformation Group: data from the GeoInformation Group product range are available through the JISC Landmap service for eligible users.  These Landmap service datahave a cell size of 1m, a vertical resolution of 15cm and coverage at the time of writing for Birmingham, Edinburgh, Glasgow, Liverpool, London, Manchester and Newcastle-upon-Tyne.

__A Note of Caution__

With raster data, such as these, an increase in horizontal detail is accompanied by a significant increase in the volume of the data.  For example, going from a cell size of 30m to 15m will quadruple the data volume.  These data are, therefore, very large: the Bluesky DEM for England and Wales, as delivered, occupies around 50Gb of disk storage.  Some software packages and / or computer operating systems may impose limits on the maximum dataset size that can be manipulated or stored.  It is beyond the scope of this guide to provide details or advice on dealing with issues relating to dataset size.

### 2.6.2 Rest of the World

This list is in no way complete: there are data products for nations and regions which cannot be listed here.  Listed here are some easily accessible datasets with near global coverage and some pointers for looking for more detailed products.
* SRTM.  The Shuttle RaDAR Topography Mission covers landmasses between 60 degrees North and 56 degrees South.  The mission was flown in February 2000 as a joint international venture.  The most detailed SRTM products are restricted to military users; 1ArcSecond, approximately 30m cell size, data are available within the USA to USA users for the co-terminus USA.  3ArcSecond data, which varies in cell size depending on the location of the study area on the surface of the earth, 90m on the Equator, is available for download for any location within the data collection limits; there is also a 30ArcSecond, or approximately 1km, product and a range of related imagery products.  The vertical resolution of published SRTM data are 10m.   These data are available for download from [USGS](https://www.usgs.gov/centers/eros#/Find_Data/Products_and_Data_Available/Elevation_Products) and a number of other servers.
* ASTER GDEM.  The product of a joint Japanese Ministry of Environment, Trade and Industry and NASA initiative, these data are produced from mesurements collected by a Japanese instrument on board the 'terra' satellite.  Data have been collected since 2000 for landmasses between 83 degrees North and South.  These data have a cell size of 30m and a vertical resolution between 7 and 14m.  The ASTER instrument operates in the visible light spectrum, so no data can be collected from areas of the Earth subject to continuous cloud cover.  ASTER data are supplied in 1 degree tiles and are available for download from [ASTER GDEM](https://asterweb.jpl.nasa.gov/gdem.asp).
* SPOT DEM.  The French SPOT Earth observation satellite series are capable of collecting stereoscopic imagery, which can be processed photogrammetically, like stereoscopic aerial photography, to generate a DEM.  These data can deliver a planimetric accuracy of 15m and a vertical accuracy of 10m and are supplied as either 1ArcSecond or 20m datasets.  This is a commercial service delivered by SPOT Image and details can be found on the SPOT Image website.
* National services.  There are national and commercial services supplying DEM data in many countries and beyond the scope of this guide to deliver a detailed list.  LiDAR data, as well as photogrammetic DEMs are increasingly available and local sources must be consulted for details.

### 2.6.3 Uses of DEM Data

Surface topography has a direct impact on many natural and human processes, in addition to providing evidence of past or present natural or human activities.  In high latitudes, the angle and direction of slope can be the controling factor in snow melt; shallow slopes and the similarity of surface elevation to river level are factors in assessing flood risk; and the elevation of one location relative to another is a major factor in controlling whether the one location is visible from the other.

### 2.6.4 Working with DEM Data

The nature of DEM data is such that it is necessary to employ a GIS or Remote Sensing package in order to use these data.  Although similar to image data, DEM data have values from the lowest elevation, which may be below sea level and thus negative, to the highest and, as a result, are not suited to processing with general purpose image processing packages, such as Photoshop or the GIMP.  Most GIS packages, including Open Source products, include at least some basic tools for computing hillshade and visibility, direction and angle of slope and to be able to associate specified locations with the elevation at those points.  In combination, these basic tools enable a wide range of study opportunities.  In archaeological terms, such tools *support* an interpretive analysis: they are not deterministic in themselves.

__Visibility and Exposure__

These approaches concern whether one location is visible from another (visibility), the extent to which an area is visible from elsewhere and the extent to which an area is exposed to the sun, wind directions, etc (exposure).  These can be measured using similar tools.  Most GIS packages offer a hillshading tool: this is designed to model light shone from a light source and illuminate those parts that are not in shadow.  By adjusting the location and elevation of the light source, it is possible to determine the field of view, or *viewshed*, from a given location and, thus, the area exposed to that location.  In a similar manner the light source can be programmed to follow the passage of the sun and to identify areas illuminated or in shadow, or their *exposure*: obviously in an extreme climate, exposure to the sun or shade that prevents the sun penetrating to a location may have a significant impact on the behaviour of natural and human phenomena.

Some packages have tools to support the determination of the visibility of individual and specific locations from another.  An example might be a chalk-covered barrow or for a more defensive purpose.  This is the type of work referred to here as  inter-visibility.  Where such tools are not included, a similar effect can be achieved by reversing the viewshed analysis, to determine whether the specified location is in view from the target.

__Surface Topography__

The surface morphology of a landscape can also have a controlling impact on natural and human phenomena: flood risk is one example, as might also be the availability of suitable land for some actrivity.  These are usually measured in terms of slope, the angle of slope, and aspect, the direction in which the ground slopes.  Areas to which the ground slopes from all adjacent cells may, for example, be damp hollows; the combination of slope, aspect and elevation may determine the practicality of some activity, such as the growing of some crop.  There are many tools for studying landscape morphology, but these are outside the scope of this guide.

## 2.7 Copyright issues - an example from the Ordnance Survey

The following notes were based upon OS information current at the time of writing and are intended as a guide. The most recent OS documents should always be consulted for the definitive conditions.

All derived data that you may use in your GIS will be copyright by someone whether this is you, your organisation, or someone else entirely. It's very important to keep careful track of who owns the copyright on each piece of information you incorporate into your GIS data set as this will affect how you can publish your data and who else can use it. An example of the complexities of copyright comes from the Ordnance Survey of Great Britain.

### 2.7.1 Requesting Permission

The Ordnance Survey (OS) requests that users of their information ask permission before any procedure requiring copyright clearance is undertaken. As OS data is copyright by the Crown, especially rigorous regulations are applicable which makes it particularly important to understand their copyright requirements __before__ undertaking a GIS analysis.

The Copyright, Designs and Patents Act 1988 [@hmso1988copyright] defines Crown copyright and states that it would be infringed if any person or organisation reproduced a copy of Crown copyright information without first having permission. Copyright is infringed when:

* the copying is by hand or by mechanical means
* the copying is direct or through a fresh drawing in whole or in part, or from a map or document based on Ordnance Survey material. 

One exception to this need for permission is a 'fair dealing' clause, which generally means that you do not need permission to make up to four A4 size copies of a map that you own for private study, research, criticism or review. The OS define 'educational purposes' in terms of paper map extracts for the purposes of teaching map reading and interpretation, etc., and for related assessment of a student's progress. Research usage is limited to 'university research projects only'. This generally excludes research supported by 'external' sponsors including higher education funding councils.

Another exception is the use of OS material in connection with any proceedings on parliamentary, judicial, Royal Commission, or statutory inquiry matters. In these cases OS material may be used without permission but cannot be used in a publication [@os1996copyright4].

### 2.7.2 Citation

Whether or not you need advance permission to use OS material, you __must__ cite the fact that you are using their information.

With OS material that is out of copyright, you must __include__ the statement 'Reproduced from the (year of publication) Ordnance Survey map' [@os1996copyright4].

### 2.7.3 Are all OS maps copyright?

Strictly speaking, __all__ legitimate use of OS material will carry with it an appropriate citation together with the phrase 'Crown Copyright Reserved'. The OS encourages you to seek confirmation from them directly whether or not material which does not bear this inscription is subject to their copyright.

### 2.7.4 Publishing

The OS define 'publishing' as 'selling or giving away any publication which contains our material. By publication, we mean sheet maps, books, journals, brochures, leaflets, catalogues, and so on' [@os1996copyright4].

Generally royalties are not charged on publications of academic research that are not intended to make a profit, but you will need to get OS permission before publishing and you will need to acknowledge OS copyright in the publication. There are various scales of royalty charges for publishers of things other than academic research and discounts are offered for registered charities, etc. The scale of royalties depend in part upon both the proportion of OS material in the product and the OS perceived 'usefulness' of the final product. OS Copyright Leaflet 4, dated April 1996, defines all these provisions.

Generally the OS do not allow any of their material to be published on the World Wide Web [@os1996copyright4].

### 2.7.5 The National Grid

Believe it or not, the UK national grid is even covered by Crown Copyright on Ordnance Survey maps. Generally you can copy the national grid without having to pay a charge, but you must print the following acknowledgement:

"The grid on this map is the National Grid taken from the Ordnance Survey map with the permission of the Controller of Her Majesty's Stationery Office." [@os1996copyright4].

It's not the national grid, *per se*, that is copyright. The national grid is a standard Transverse Mercator map projection, using the Airey Spheroid and a false origin to the south west of the Isles of Scilly. Since it is a mathematical transformation, determined by people long since dead, it is not of itself copyrightable.

However, the OS __usage__ of the national grid - displaying grid co-ordinates with two letter codes for the 100km squares - __is__ Crown Copyright. The OS claim 'ownership' of any national grid reference (NGR) which is given in the 'NY 123 456' form. It is our understanding that the OS have been successful in obtaining injunctions against commercial use of this form where no royalties were paid to the OS.

This means that the example reference, NY 123 456, given above __is__ OS Copyright whilst its numeric form, 312300 445600, isn't.

### 2.7.6 Use of OS Data (paper maps and digital data)

The general case is that everything conveyed within an OS product is Crown Copyright. Clearly, the OS cannot claim copyright of the name of a settlement, for example, but they can claim ownership of anything relating to their survey effort that delineates the extent of that settlement. Also, equally clearly, any errors in their data are OS Copyright. This may seem strange, but error matching is one of the mechanisms that the OS uses to determine whether or not someone has violated their copyright.

### 2.7.7 Ground control points and OS maps

Taking ground control points from OS maps is a restricted right under Copyright Law. Restricted rights are not covered under the standard licence granted by Ordnance Survey, and instead are only granted on a case by case basis. A charge is almost always made.

Using OS data (maps, digital data) to specify position of other data (maps, images, etc.) gives the OS an intellectual property right in the resultant data, map, etc. Indeed, the OS claim that they __own__ the positional content of the new data. It is thus an offence to pass this information on to a third party without the explicit, and prior, permission of the OS. The OS will seek a royalty for any information which they consider to be a commercial product, or to have commercial potential. 'You risk breaking Crown Copyright if you try to capture your own data which has been fixed from Ordnance Survey material.' [@os1996copyright4].

Of course, if the data are surveyed in from a GPS  point, for example, and the co-ordinates are specified in full numeric form (e.g. 312300 445600 from the above example) the OS are not involved. The numeric form is far more useful in relation to digital data anyway, so this is a good habit to get into! Differential GPS, with a potential precision from less than a cm up to a metre or two is readily available now. It can be hired cheaply, is already in wide use, and thus may already be accessible to you. It's a good idea to keep accurate field records about GPS use in order to prove your exemption from OS claims.

### 2.7.8 Digitising OS Maps

The OS do not generally grant permission to digitise any OS copyright material for which there is an existing digital equivalent. Now that the whole OS production system is digital, that means that you will need to argue a very specific case to get permission. Wanting to digitise a map at a scale of 1:25000 when an OS digital map is available at 1:1250, will probably not gain you permission. When the OS do grant digitising permission there is generally a data capture royalty to be paid.

### 2.7.9 The Worst Case Scenario

Copyright law is a serious matter, and it is best to seek the proper permissions in advance. According to the OS:

"If you reproduce our maps or use our digital data without our permission, this is known legally as an infringement of the Copyright, Designs and Patents Act 1988. If you do this you are stealing the results of our work and we will take legal action. We will decide if you must pay damages and if you must destroy the copies. Our minimum damages will be the same as the royalty fees which apply at the time we discover the infringement, plus 25%." [@os1996copyright4]. 

### 2.7.10 Other Issues in Using Data Derived from the OS

Whilst the OS claim their data to be complete they do not claim 100% positional accuracy. Indeed, there is a residual error which relates to the early County Series to National Grid transition which the OS currently estimate needs an investment of over 40m pounds to resolve. Their present approach to this problem is to ask customers to notify them of corrections so that they get a piece-meal update ... for free! City centres are least affected by these errors.

The biggest issue is that of OS claiming intellectual property rights in 'knowing where you are'. This means that much existing data, whilst free from liability as long as it remains solely with its collector, may become liable to copyright royalties the moment it passes to another person. It also implies that the use of GPS technology for 'fixing' position for __all__ future field data collection work should be seriously costed - by this means the collected data would become free of OS claims.

### 2.7.11 Would you like more Information?

Additional useful information can be found on the OS Web pages.


## 2.8 Why document your data?

Working with your Geographic Information System on a regular basis as you do, you probably have a pretty good idea about what it contains, the area of the country it covers, and what its major strengths and weaknesses are likely to be. You know, for example, that your data cover the city of York, that period information is only stored to the nearest century, and that the aerial photographic interpretation to the south–west of the city is a bit dubious.

Data offered to a digital archive, however, may potentially be used by researchers from many different parts of the planet, and with widely varied levels of expertise. *They* have no way of knowing anything at all about your data unless you tell them.

In order to make sure that the maximum amount of information is delivered to the user whilst involving you, the depositor, in minimal effort, these Guides suggest a number of procedures to standardise and simplify the documentation process.

__Documentation for you__

Some form of record about your data — and about what you've done to it — is also, of course, undoubtedly useful within your own organisation. Even using data every day, it is still possible to forget about where *some* of it came from, or how the data you currently used were originally compiled from various sources.

This section introduces the issues relevant to both types of documentation, as well as discussing the detail relevant to one or the other.

### 2.8.1 Levels of Documentation

In documenting something so complicated as a Geographic Information System, it is possible to enter into great detail, and record everything from the data sets comprising the GIS to the sequence in which individual commands were applied to the data in order to produce your current system.

As with most things, there are situations in which great detail is required, and others where a more slimmed–down level of recording might be more appropriate. It is generally up to you as creator, maintainer, and primary user of your data to decide how much documentation is justified, and to select a suitable level for the language of your documentation; is 'cleaned coverage' appropriate, for example, or is your situation such that the more expressive:


*Using the Arc/Info clean command, tidied up the new pottery layer in order to remove errors introduced whilst digitising from the paper map. The command was* 

*clean pottery # # # poly*


is more suitable? The former has implications for decreasing the interpretability of your documentation, whilst the latter has implications for the effort required in producing this level of detail.

In documenting data which are to be made available to others, it is often necessary to describe things more clearly — and with a greater degree of contextualisation — than is normally the case for internal use.

### 2.8.2 'Documentation' versus 'Metadata'

Metadata is discussed in detail in the general section '[Metadata](https://doi.org/10.5284/h0p2-5584)'. Several definitions are offered for metadata, but one which might usefully be given here is that metadata is the means by which your *data* are transformed into *information*, interpretable to and re-usable by those other than yourself. In other words, metadata is a label for the extra details associated with any data set which enable someone else to place them into some form of context. Metadata might include information on the computer format in which the data are stored, the area of the country they relate to, etc.

Metadata in its widest sense may be considered *all* of the documentation conceivably associated with GIS data, but this guide simplifies things somewhat by using the metadata label only to apply to metadata used for *resource discovery*. As such, information suitable for entry into a digital archive catalogue itself, and which can be used to facilitate the discovery of your data by others, can be thought of as metadata, whilst the information you provide which helps people to use your data after they have accessed it may be thought of as ancillary documentation.

__So... how much is enough?__

Well, it depends... If you are documenting data for your own internal use, you are of course free to use as much or as little of what is recommended here as you like.

If, however, you are preparing data for deposit with a particular archive e.g. the ADS or tDAR, then you will need to comply with certain archive-specific guidelines to enable the ingest and re–use of your data. Where your data are particularly complicated, archives may recommend other — specialised — documentation to accompany them, and will hope to enter into dialogue with you at an early stage in order to define this.

### 2.8.3 Information to be Recorded

It is generally a good idea to start recording information about your data as early as possible, and ideally you should begin recording as soon as you start using or creating the data. If you wait until just before depositing to start creating metadata and documentation, it will be difficult for you to provide some pieces of information at all, and far harder to write most of the rest than it would have been at the time you were actually *doing* it.

Assuming that you choose to record relevant details as you go along, it might be useful for you to start a formal __log book__ of some kind. This way, it will be easier to find information later, rather than having to rifle through various old envelopes, scrap paper, and whatever else you scribbled on at the time.

Within this log book, it is normal to record such general details as the software you are using, the versions thereof, and the type of computer and operating system (e.g. Windows PC, Mac, Sun workstation, etc.) you are running it on. As time passes, people discover problems with earlier versions of software, and if someone finds out that *SuperGIS* version 23.7 displaced all green lines on maps by 3mm, then it is undoubtedly useful for you to be able to look back through the log book and find that all your maps displaying public rights of way were created three years ago using *SuperGIS* 23.7. Knowing there is a problem, you can do something about retrospectively fixing it with adequate documentation.

__Sources of Data__

Information about where the data you use are acquired from is one of the most important things you can record whilst constructing and using a GIS.

Data are acquired from numerous sources, auch as mapping agencies (e.g. Ordnance Survey, USGS), local authorities, special interest groups, etc., and are gathered and displayed at a wide variety of — often different — scales or resolutions.

Each of these sources are of value for a different set of purposes, and each brings with it a different set of problems; data acquired at 1:50,000 scale, for example, may be ideally suited for plotting maps of artefact distributions, but wholly improper for recording the layout of individual excavation trenches (1 centimetre on a 1:50,000 map, after all, is equivalent to 50,000 centimetres, or 500 metres, on the ground).

In order to aid the user in deciding how best to incorporate your data within their own work, it is desirable to provide them with information such as the scale or resolution of the original survey, scale or resolution at which that survey was digitised into the computer, assumed errors from the data capture process (often expressed as a Root Mean Square, or RMS, error on printed maps), and the method by which the data were originally acquired (although both ultimately plotted at a scale of 1:100, a user will presumably be interested to know that one topographic data set was constructed by survey with measuring tapes and dumpy level, whilst the other is the result of a detailed survey by state of the art Total Station Theodolite).

Ownership of data is also an important attribute to record about any data set, and may well prove quite complex. Data owned by the Ordnance Survey, for example, might be used by North Yorkshire County Council to derive a new data set, 'owned' by the County Council. This, in turn, is used by York Archaeological Trust to derive a new data set, now 'owned' by them. Although little, if any, of the original Ordnance Survey resource may survive in this latest incarnation of the data, Ordnance Survey in reality continue to hold intellectual property rights which should be recognised and which may well affect the ease with which, for example, York Archaeological Trust could later *legally* sell 'their' data to Yorkshire Water.

Complicated *data trails* such as this are extremely common with digital data, and it makes life easier for everyone if the evolution of every data set is tracked through every reincarnation.

In short, then, a *non–exhaustive* list of the information you might wish to record during your everyday creation, collection, and use of data includes:

* Computer hardware used
* Computer software used
* Date the data were captured/purchased/whatever
* Who did the work
* Data source ('bought from Ordnance Survey', etc.)
* Scale/resolution of data capture
* Scale/resolution at which data are currently stored
* Root Mean Square error or other assessments of data quality
* Purpose of data set creation, where known
* Method of original data capture (Total Station Survey, etc.)
* Purpose for which *you* acquired the data (might differ from the previous information where the data were *created* by someone else for one purpose, and bought from them by you for another)
* Complete history of data ownership/rights.

__Processes applied__

As well as recording information such as that suggested above, most of which will probably only need recording once when you start work with a data set, it is also extremely valuable to log the manner in which data are manipulated and modified. Not only does this allow you to keep track of — and back–track from, if necessary — changes you make to the data, but it also allows you and others to work out how data you lifted from your local Sites & Monuments Record, for example, and incorporated into your own GIS differs from those same records still residing in the SMR. How many records have you enhanced? For how many have you had to re–enter the grid references, as you discovered that those provided by the SMR actually placed sites in the North Sea?

The sorts of information you may wish to consider logging for these purposes include:

* The date of any change/modification
* The reason for any change/modification
* The record numbers affected by the change
* Relationships to other resources; where, for example, you derive a new GIS data set by passing a mathematical filter or some other modification through an existing data set, you may wish to record the relationship formally between the original data and the new set

Where you edit an existing data set to correct spelling in text fields, or some similar operation, it makes more sense to simply record this as 'Corrected spelling throughout data set' and give the numbers of those records altered if relevant, rather than to list every single correction made to every single record. For processes such as converting an elevation matrix to a Triangulated Irregular Network (TIN) or an equally drastic data set-wide modification, it is worth recording the parameters you used in undertaking this process so that you — and others — may repeat or undo it in the future.

### 2.8.4 Dublin Core Metadata

Much of the information recommended for you to record is most useful when it comes to actually *using* your data, and as such will probably only be downloaded by a potential user at the same time as they access your data. Certain pieces of information, though, are key in aiding the user in *finding* your data in the first place, and it is these that are explored in this section.

Many organisations around the world advocate the use of the *Dublin Core* for recording the information that helps potential users to find - and simply evaluate - your data. This information is known as 'resource discovery metadata'; information about your data (the 'resource') that helps people discover it.

Through more than three years of international development, the Dublin Core has evolved to become a series of fifteen broad categories, or elements. Each of these elements is *optional*, may be *repeated* as many times as required, and may be *refined* through the use of a developing set of sub–elements. The use of the Dublin Core within archives such as the Archaeology Data Service and tDAR is discussed in the general [Project Metadata](https://doi.org/10.5284/h0p2-5584) section.

__...and how to create it__

With complex collections of computer files such as those present in most archaeological GIS, it is extremely difficult to draw up simple rules defining what you should create metadata records *for* (the GIS as a whole, every 'layer', every original data source, etc.). As a basic guide, it is sensible for you to create one record describing the GIS as a whole, plus one subsidiary record for each major resource 'type' stored in the system. If, for example, you created a GIS for a specific region which recorded Neolithic burial monuments and Roman settlement patterns (well — you *might*!), it would seem sensible to create one record for the whole, one for the Neolithic part, and one for the Roman part, giving three records of which one (the whole GIS) is the 'parent' and two are 'children'. If in doubt, contact the digital archive for advice.

An important factor in ensuring that a user can sensibly compare records you create with those provided by others is the use of relevant standardised terminologies and modes of expression. The Dublin Core system allows users to identify a 'SCHEME' which controls the terms stored in any one occurrence of a Dublin Core element. Thus, a user could identify the *Thesaurus of Monument Types* [@rchme1995thesaurus] as a SCHEME for the Dublin Core Subject element, and describe their resource using terms drawn from this thesaurus. As all of the Dublin Core elements are repeatable, the user could then — if they wanted to — repeat the Subject element and define the Getty's *Art & Architecture Thesaurus* as their SCHEME. Importantly, each use of a Dublin Core element should only include terms drawn from *one* SCHEME. Where absolutely necessary, it is possible to enter information as 'free text', not qualified by any SCHEME, but such use of free text makes it far harder for users to search across resources meaningfully, and should thus be avoided.

### 2.8.5 Ancillary Documentation: What to Supply and Why

Possibly the single most important piece of information you can provide above and beyond the Dublin Core catalogue entries discussed above is an idea of your data model.

This model enables potential users to discover relatively quickly what sorts of information your GIS will probably hold, and allows them to work out how the whole thing is tied together.

For a typical archaeological GIS, the information that might usefully be represented in a data model includes:

* a list of field names (and definitions) for your database \\e.g. __Address__: The postal address of the archaeological intervention being described. 
* a diagram depicting the relationships between database tables (similar to Figure 3), if relevant
* a list of map/coverage/'layer' names (and definitions) \\e.g. __modernyork__: The modern streetplan for the study area, extracted from Ordnance Survey 1:1,250 scale digital mapping.

Other than the data model itself, much of the information this section advocates for entry into your project log book can usefully be passed on to the digital archive in digital form, as it is equally useful to *others* trying to make use of your data as it was to you.
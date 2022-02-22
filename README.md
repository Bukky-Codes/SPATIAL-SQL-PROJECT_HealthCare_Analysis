# GOA_HEALTH_FINAL

Introduction

The goal of this geospatial application is to identify and visualize medical resource allocation in the State of Goa, India. This is accomplished by plotting the locations of the medical facilties for the entire state and creating buffers around them. More specifically, these buffers are actually "isochrones"- polygons that represent equal driving distances around a given point. Two distances were chosen for each isochrone- a smaller and a larger one- to represent two levels of the facility's availability to nearby residents. The distances selected for these isochrones are somewhat arbitrary, but they can primarily be determined based on the size of the facility- The larger the facility, the greater its service area. Both for simplicity's sake and based on the categorizations of medical facilities in the data, the facilities are broken up into 3 tiers: the first tier includes major hospitals, the second tier includes smaller health centers, and the third tier contains medical clinics. Therefore, tier one facilities have the largest isochrones and tier three have the smallest. These isochrones are then overlayed on top of census tracts for the state in order to see how many people are served by a particular facility. This results in intersections of polygons (between census tracts and isochrones) and tells the user an estimate of the total population served. In addition, the application returns a popup window with other important information: the name of the facility, the type of facility, and the size of the isochrone around the facility (both large and small and the radius in km).

Structure

Limitations

Closing Thoughts

Tools

• Python 3 (the scripting language)
• PostgreSQL (the database language)
• QGIS (data inspection and shapefile manipulation)
• Postman (to test APIs)
VS Code (IDE/text editor)
Jupyter Notebooks (exploratory data analysis and ETL)

Extensions

Flask
PgRouting
PostGIS
Leaflet

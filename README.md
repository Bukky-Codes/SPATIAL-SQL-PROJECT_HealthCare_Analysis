# Epic Medical Planning System for Goa, India



![image](https://www.attainia.com/wp-content/uploads/2018/05/Healthcare-facility-hospital.jpg)





# Introduction

The goal of this geospatial application is to identify and visualize medical resource allocation in the State of Goa, India. This is accomplished by plotting the locations of the medical facilties for the entire state and creating buffers around them. More specifically, these buffers are actually "isochrones"- polygons that represent equal driving distances around a given point. The user can select a specific facility and two isochrones will be created around it.

Two distances were chosen for each isochrone- a smaller and a larger one- to represent two levels of the facility's availability to nearby residents. The distances selected for these isochrones are somewhat arbitrary, but they can primarily be determined based on the size of the facility- The larger the facility, the greater its service area. Both for simplicity's sake and based on the categorizations of medical facilities in the data, the facilities are broken up into 3 tiers: the first tier includes major hospitals, the second tier includes smaller health centers, and the third tier contains medical clinics. Therefore, tier one facilities have the largest isochrones and tier three have the smallest.

These isochrones are then overlayed on top of census tracts for the state in order to see how many people are served by a particular facility. This results in intersections of polygons (between census tracts and isochrones) and tells the user an estimate of the total population served. In addition, the application returns a popup window with other important information: the name of the facility, the type of facility, and the size of the isochrone around the facility (identifying large and small and the radius in km).

## Structure

### How to Install
1. Download OpenStreetMap network data where you need to calculate isochrones. Download .osm.pbf files from http://download.geofabrik.de/.
2. In PgAdmin, create a new database and install PgRouting and PostGIS extensions.
3. With osmconvert, turn the pbf file into osm and, optionally, clip to the extent of your study area. You can use a shapefile for this purpose or coordinates of a bounding box.
4. Use osm2pgrouting to your osm file into your new database. You also need a configuration file based on how you want to create the network (for cars, walking etc.). There are some basic ones found in the PostgreSQL installation folder. Use your username, password, host, and port to send it to your new database.
5. This will create two tables in your database- the network and the network nodes- which are the basis for the routing calculations.

### How to Run
1. Create a new environment and install all dependencies.
2.
3.

## Limitations
- Intersections are based on percentage of area of the census tracts covered by isochrones, which is not accurate because people may or may not live in that area

- Isochrones are based on PgRouting driving distance which actually only calculates distances, but still uses nodes of a road network which we retrieved from OpenStreetMap; we have no way of knowing which method of transportation people may actually be using or if bike paths, walking paths etc. match closely or do not match at all with the existing road network

-  Using nodes of the road network to create isochrones can be especially problematic in rural areas where small clinics may be at quite a distance from established roads or highways; thus, the population served is almost certainly less accurate in these areas

-  Data is static; it is only retrieved at a moment in time that most likely does not accurately refelect the situtation as it is now

## Food for Thought

Accurate and up-to-date data is a major concern for an application like this. In a future release, it would be very useful to have recent data that automatically retrieves at a given interval- say monthly or yearly. 

It would also be very worthwile to have users categorized into either the general public or medical planners and have the app have a dual purpose- with different functionality depending on the type of end user. For the general public, we would have liked to add a functionality where you could click on any spot in Goa (presumably matching the user's location), and it would calculate the distance to the nearest medical facility and give you other important attributes about it (as it does in the current version). For medical planners, it would be really useful for them to be able to click on any spot in Goa and for it to draw isochrones with a estimate of the population served for that location- allowing new facilities to be built in underserved areas.

We think that this app provides pretty useful information that could be used by a variety of people for different purposes. Within the scope of this project and with the limited time that we had, we were able to show how medical resources are distributed in Goa. The app could easily be expanded to include more types of data with different parameters for any area.

### Tools

- Python 3 (the scripting language)
- PostgreSQL (the database language)
- HTML5 (the website language)
- QGIS (data inspection and shapefile manipulation)
- Postman (to test APIs)
- VS Code (IDE/text editor)
- Jupyter Notebooks (exploratory data analysis and ETL)

### Extensions

- Flask
- PgRouting
- PostGIS
- Leaflet
- CSS-Bootstrap

# Project 2: Generating Synthetic Populations

## Part 1
- Import de facto settlement boundaries from project 1
- Import synthetic households and persons from project 2
- Create voronoi tessellations
- Introduce gravity model

## Project 3 deliverables : 
- Please upload and provide a link from your GitHub index to a 3 to 4 page project report that analyzes migration and movement at your selected location. Include analysis that addresses the following.
  -  Provide a written description of the analysis you conducted of the gravity model for London.  Additionally, incorporate the Garcia et al. paper into your description while introducing your the migration data for your selected country.  Supplement your introduction with spatial plots that describe in/out migration by adminsitrative subdivision.
  - Produce an origin-destination matrix and include a portion of it as an exhibit in your write-up.  Be sure to identify the number of rows in your data frame while also including the following.
    - Names of origin and destination administrative subdivisions
    - Distances between all locations
    - Migration flows between all locations
    - An additional variable that describes all origin and destinations to be used for further specification of a gravity model (one option you could use is to select night-time lights from WorldPop)
    - Geometric description of all origin and destination center points
  - Describe your OD matrix and how it is used to model migration across the administrative subdivisions that comprise your selected location.
  - Produce an animation of migration and elaborate on how your OD matrix and gravity model could be integrated with your simulation.
    - How would you modify the number of points departing from each origin?
    - How would you modify the time variable? What scale is the temporal dimension at this level?
    - How would the gravity model update these attributes in order to produce a different simulation of migration that more closely approximates reality?
  - At the level of your selected, higher resolution administrative subdivision (where you produced de facto descriptions of settlements), use the center points of each settlement to produce a tesselation of voronoi polygons.  Similar to your analysis of the higher level administrative subdivisions, address the following.
    - How would you produce an OD matrix of these higher resolution entities?  Which variables would you include?  Are you lacking any data that would improve upon your model results?
    - How would you modify the number of points departing from each origin? How would you determine each points destination?
    - How would you modify the time variable? What scale is the temporal dimension at this level?
    - How would the gravity model update these attributes in order to produce a different simulation of migration?
    - How would you go about integrating migration and transport activities at the differing geospatial and temporal scales of these hierarchical levels?



---
tags:
  - hawthorneGeneralConstruction
  - public
---
## Objective
Send a direct mailer marketing touch to a desirable area around a job site.
## Procedure
1. Determine if the neighborhood area is a good target. [[What our ideal roof jobs look like]]
2. Determine the target of the neighborhood area. [[How to determine a neighborhood area]]
3. Open qgis. [[Installing, opening, and basic use tips for qgis]]
4. Prepare the workspace. [[How to start a new project in qgis]]
5. Zoom to the starting address. [[How to zoom to an address in qgis]]
6. Zoom out so the target area is framed in the map extent. Try using `cmd -` for major zooms. The scroll wheel on the mouse is a little fussy in qgis but is good for smaller increments. ![[Screen Shot 2024-02-22 at 2.22.51 PM.jpg]]
7. Draw a polygon of the target neighborhood area. [[How to draw a polygon in qgis]]
8. Extract house numbers from OSM map extent. [[How to extract house number data from OpenStreetMap map extent in qgis]] 
   ![[Screen Shot 2024-02-22 at 2.57.43 PM.jpg]]
9. Limit the address to those intersecting the drawn polygon. [[How to select intersecting buildings with polygon in qgis]]
10. Export the addresses to a .csv file. [[How to export address data from qgis shapefile]]
11. Open [Stannp](https://www.stannp.com/). Create a new group and import the file.
12. Send Mailer in Stannp. Use the [[Send direct mail to neighbors]] for the design, the [[Neighborhood Mailer Copy]] for copy, and input via [[Manual Use of Stannp Online Platform]]
---
tags:
  - hawthorneGeneralConstruction
  - public
---
1. Open the attribute table of the buildings that intersect with the drawn polygon.
   
   ![[Screen Shot 2024-02-09 at 8.20.33 AM.jpg]]
   
2. Scroll through and do a quick data validity check. It should look like addresses. This one looks good.
   
   ![[Screen Shot 2024-02-09 at 8.22.34 AM.jpg]]

3. Open the field calculator.
   
   ![[Screen Shot 2024-02-09 at 8.43.26 AM.jpg]]
 
4. Create a new field named `state`. OSM data doesn’t come with it and Stannp will want it. Make sure this menu looks the same as what you’re putting in! Set the name to the appropriate state. Click OK.
   
   ![[Screen Shot 2024-02-09 at 9.27.37 AM.jpg]]

5. Open field calculator again. Concatenate the house number and the street, set as "address", (It says address 3 because this is just my 3rd attempt in my effort to blaze a path for you.) Make sure the menu looks the same! Click ok.
   
   ![[Screen Shot 2024-02-09 at 9.10.19 AM.jpg]]

6. Export by right clicking on the the layer Export > Save Features As…
   
   ![[Screen Shot 2024-02-09 at 8.27.48 AM.jpg]]

5. Select a folder and name the file.
   
   ![[Screen Shot 2024-02-09 at 8.31.33 AM.jpg]]
   
   ![[Screen Shot 2024-02-09 at 8.31.11 AM.jpg]]

6. Save only the address columns, **be sure to check the created "address" and "state" columns.**
   
   ![[Screen Shot 2024-02-09 at 8.29.32 AM.jpg]]
   
7. Select No Geometry.
   
   ![[Screen Shot 2024-02-09 at 8.30.11 AM.jpg]]
   
8. Click Save.
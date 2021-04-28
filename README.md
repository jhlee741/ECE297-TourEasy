![Banner](/images/toureasy.png)
# TourEasy
![Language Stats](/images/languageStats.png)<br/>
A map application that shows important information for different cities around the world. Written using C++, retrieves data using the OpenStreetMap Database API, and draws graphics using GTK.<br/>

NOTE: This project was made for the course ECE297 at the University of Toronto, and therefore, the source code is not available to the public.

## Main Features
* Use buttons to move around and zoom in/out
* Dropdown menu to select maps for different cities
* Display streets, street names, parks, rivers, lakes, buildings, etc...
* Display subway stations, points of interest
* Search bar to search up intersections
* Find optimal path between two intersections
* Display easy-to-follow driving instructions to get from one point to another
* Dark Mode

## Algorithms
### Setting up a Graph data structure
Our map represents the information retrieved from the OSM Database as a directed, weighted graph. The nodes of the graph represent city intersections, and the edges represent street segments that connect two intersections together. The weight of each edge represents the travel time to get from one intersection to another, which was calculated from the length of the street divided by the speed limit. 

### Pathfinding using A* Search Algorithm
Our map implements the A* Search algorithm to search for the shortest path between two intersections. Since we know the travel time to get from one intersection to another, our algorithm uses a greedy approach to always travel to the next intersection with the lowest time cost. Also, our algorithm takes into account a heuristic (which is the Euclidean distance between the start,end intersection, divided by the maximum speed limit in the city) to find the next intersection. This allows our algorithm to favor routes that get us closer to the destination, which allows us to find the shortest path much more quickly. 

### Traveling Salesman Problem 

![Banner](/images/toureasy.png)
# TourEasy
![Language Stats](/images/languageStats.png)<br/>
TourEasy is a tourist-friendly map application that shows important information for different cities around the world. Written using C++, retrieves data using the OpenStreetMap Database API, and draws graphics using GTK.<br/>

NOTE: This project was made for the course ECE297 at the University of Toronto, and therefore, the source code is not available to the public.

## Main Features
* Use buttons to move around and zoom in/out
* Dropdown menu to select maps for different cities
* Display streets, street names, parks, rivers, lakes, buildings, etc...
* Display subway stations, points of interest
* Click POI's or intersections to view more information
* Search bar to search up intersections
* Find optimal path between two intersections
* Display easy-to-follow driving instructions to get from one point to another
* Dark Mode
* Help Box

## Algorithms
### Setting up a Graph data structure
Our map represents the information retrieved from the OSM Database as a directed, weighted graph. The nodes of the graph represent city intersections, and the edges represent street segments that connect two intersections together. The weight of each edge represents the travel time to get from one intersection to another, which was calculated from the length of the street divided by the speed limit. 

### Pathfinding using A* Search Algorithm
Our map implements the A* Search algorithm to search for the shortest path between two intersections. Since we know the travel time to get from one intersection to another, our algorithm uses a greedy approach to always travel to the next intersection with the lowest time cost. Also, our algorithm takes into account a heuristic (which is the Euclidean distance between the start,end intersection, divided by the maximum speed limit in the city) to find the next intersection. This allows our algorithm to favor routes that get us closer to the destination, which allows us to find the shortest path much more quickly. 

### Traveling Salesman/Courier Problem - NP Hard Problem
Given a set of dropoff/pickup points, and a set of start/end intersections, our algorithm attempts to find the optimal path that reaches all the intersections. Since this type of problem is an example of a NP Hard problem, our algorithm finds a few "mediocre" solutions, then continues to make improvements until we end up with a relatively optimal path in a reasonable amount of time. 

For our initial "baseline" solution, we try starting at every possible depot(start point), and use a greedy algorithm to always travel to the next closest pickup or dropoff point from the current location. Then, using the best "baseline" solution, we try swapping the order of two random intersections continuously to look for a more optimal path until we run out of time which we set as a hard limit of 50 seconds. 

## Screenshots
| Main Screen  | Changing maps |
| ------------- | ------------- |
| ![Loading Screen](/images/mainScreen.png)  | ![Map Selection](/images/changeMap.gif) |

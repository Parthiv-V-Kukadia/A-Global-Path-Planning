# A* Path Finding with B-spline Smoothing
This project implements the A* path finding algorithm to navigate a 2D binary map containing obstacles. It further refines the generated path using a B-Spline smoothing algorithm to create a smoother, more natural trajectory.

## Overview

The project consists of the following functionalities:

1.  **A* Path Finding Algorithm:**
    * Finds the shortest path between a start and a goal point on a grid-based map.
    * Considers 8-connectivity (allows diagonal movements).
    * Uses the Euclidean distance as the heuristic function to estimate the cost to the goal.
    * Maintains open and closed lists to efficiently explore the search space.

2.  **B-Spline Smoothing Algorithm:**
    * Takes the path generated by the A* algorithm as input.
    * Applies B-Spline interpolation to create a smooth curve that follows the general direction of the A* path.
    * Includes a collision check to ensure the smoothed path remains in the free space (does not intersect obstacles). If a collision is detected, the smoothed path is discarded for that simulation.

3.  **Simulation Environment:**
    * Loads a binary map from a `.mat` file (`Map.mat`). On this map, `0` represents free space and `1` represents an obstacle.
    * Allows running multiple simulations with randomly generated start and goal points.
    * Includes checks to ensure that the randomly generated start and goal points are not located within obstacle areas.
    * Visualizes the map, obstacles, the A* generated path, the B-Spline smoothed path (if collision-free), and the start and goal points for each simulation.

## Files Included

* `AStar_BSpline_Navigation.m`: The main MATLAB script containing the implementation of the A* algorithm, B-Spline smoothing, and the simulation environment.
* `Map.mat`: A MATLAB data file containing the binary map representing the environment with obstacles. You will need to provide your own `Map.mat` file for the script to run.

## How to Use

1.  **Ensure `Map.mat` exists:** Make sure you have a MATLAB data file named `Map.mat` in the same directory as the `AStar_BSpline_Navigation.m` script. This file should contain a 2D binary matrix representing your environment.
2.  **Open MATLAB:** Launch the MATLAB environment.
3.  **Navigate to the directory:** In the MATLAB command window, navigate to the directory where you saved the `AStar_BSpline_Navigation.m` and `Map.mat` files.
4.  **Run the script:** Execute the script by typing `AStar_BSpline_Navigation` in the command window and pressing Enter.
5.  **Configure the number of simulations:** Inside the `AStar_BSpline_Navigation.m` script, you can change the value of the `num` variable at the beginning of the script to control the number of path finding simulations that will be run.

    ```matlab
    num = 4;  % Number of simulations to run
    ```

## Function Descriptions

* **`AStar(Map, start, goal)`:** Implements the A* path finding algorithm. Takes the map, start coordinates, and goal coordinates as input and returns the shortest path as a list of coordinates.
* **`AStarPath(node)`:** Helper function for `AStar` to reconstruct the path from the goal node back to the start node using the parent information.
* **`heuristic_cost(node, goal)`:** Calculates the Euclidean distance between two points, used as the heuristic in the A* algorithm.
* **`BSplineAlgo(Map, path)`:** Implements the B-Spline smoothing algorithm. Takes the map and the A* generated path as input and returns a smoothed path (if collision-free) as a list of coordinates.
* **`Simulations(Map, numSimulations)`:** Runs multiple A* path finding simulations with random start and goal points on the given map. It then attempts to smooth the generated path using the B-Spline algorithm and visualizes the results for each simulation.

## Visual Output

For each simulation, the script will display a figure showing:

* The binary map with obstacles (black) and free space (white).
* The randomly generated start point (blue star).
* The randomly generated goal point (red star).
* The path found by the A* algorithm (red line with circles).
* The B-Spline smoothed path (blue dashed line with circles), if it is collision-free.

The MATLAB command window will also display information about each simulation, including whether a path was found and if the smoothed path was collision-free.

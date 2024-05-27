About The Project: 
The objective of this project is to create a C++ application that leverages kd-trees for the purpose of efficiently searching for points within a polygon. Kd-trees are used for managing multi-dimensional point sets, facilitating swift search operations. The project makes use of the Approximate Nearest Neighbor (ANN) library to build a kd-tree from a collection of n two-dimensional points denoted as P = {p1, p2, ..., pn}.

Features
Kd-Tree Construction: Utilizes the ANN library to build a kd-tree from a set of 2D points, allowing for efficient spatial queries.
Polygon Range Queries: Supports two primary types of queries:
Count Query: Returns the number of points located within a specified polygon.
Report Query: Retrieves the indices of all points inside the specified polygon.
Robust Geometric Functions: Includes implementations of point-in-polygon test (using the ray-casting algorithm) and bounding box calculations to optimize query performance.
Input/Output in JSON Format: Facilitates easy data interchange and testing through JSON formatted input and output.
Automated Testing Setup: Comes with a framework for automated testing, allowing users to easily validate the correctness and performance of the range searching functionalities with provided test cases.


What is KD tree?
A k-d tree, short for k-dimensional tree, is a specialized structure for managing points in a space with k dimensions. It excels at fast search operations like identifying the closest point to a given location or searching within a certain range. This tree structure segments the space by recursively cutting it into overlapping subspaces, where each node corresponds to a distinct area determined by a point in k-dimensional space. The tree splits the space based on one dimension at a time, which builds a tiered system of divisions, streamlining the search process. K-d trees are widely applied in fields such as computer graphics, computer vision, and machine learning, where they help with efficient spatial organization and quick retrieval of nearest neighbors.


System Requirements
Compiler: C++17 compatible compiler such as GCC or Clang.
Libraries: ANN library, nlohmann/json (included in the project repository).
Operating System: Compatible with Unix-like operating systems including Linux and macOS.


Project Repository Stucture: 
 Below is an outline of the project's directory and file structure along with descriptions for each component:

Project-Repository-Structure/
│
├── ann/                                    # Directory for ANN (Approximate Nearest Neighbor) Library
│   ├── bin/                                # Directory for Executable Files
│   │   ├── ann_sample                      # Executable for Demonstrating ANN Usage
│   │   └── ann_test                        # Executable for Testing ANN Functionality
│   │
│   ├── lib/                                # Directory for Library Files
│   │   └── libANN.a                        # Archive File Containing the Static ANN Library
│   │
│   ├── include/                            # Directory for Header Files of ANN
│   │   └── ann/                            # Subdirectory for ANN-Specific Header Files
│   │       ├── ANN.h                       # Primary Header for the ANN Library
│   │       ├── ANNperf.h                   # Headers for Performance Metrics within ANN
│   │       └── ANNx.h                      # Headers for Extended Features and Definitions in ANN
│   │
│   └── src/                                # Source Code Directory for ANN
│       ├── ANN.cpp                         # Implementation of Basic Functions in ANN
│       ├── brute.cpp                       # Implementation of Brute-force Nearest Neighbor Search
│       ├── kd_fix_rad_search.cpp           # Implementation of Fixed-Radius Search in Kd-trees
│       ├── kd_pr_search.cpp                # Implementation of Priority Search in Kd-trees
│       ├── kd_range_search.cpp             # Implementations of Range Search in Kd-trees
│       ├── kd_range_search.h               # Header File for Kd-tree Range Search Functions
│       ├── kd_search.cpp                   # Core Kd-tree Search Function Implementations
│       ├── kd_split.cpp                    # Functions Handling Splits in Kd-trees
│       ├── kd_tree.cpp                     # Functions for Constructing and Managing Kd-trees
│       ├── kd_util.cpp                     # Utility Functions Supporting Kd-tree Operations
│       ├── Point.cpp                       # Implementation of the Point Class
│       ├── Polygon.cpp                     # Implementation of the Polygon Class
│       └── pr_queue.h                      # Definitions for a Priority Queue Structure
│
├── json.hpp                                # Single-Header File for JSON Manipulation by nlohmann/json
│
├── main.cpp                                # The Main Driver Program File
│
└── test_case_01/                           # Directory for the First Test Case
    ├── input_points.json                   # JSON File Containing Input Points for the First Test
    ├── input_query.json                    # JSON File Containing Query Polygon for the First Test
    ├── output_count.json                   # JSON File with Expected Count Results for the First Test
    ├── output_report.json                  # JSON File with Expected Points Report for the First Test
    ├── output_result_count.json            # JSON File with Actual Count Results After Test Execution
    └── output_result_report.json           # JSON File with Actual Points Report After Test Execution



# How to compile and run the project on linprog: 

 First open the terminal from the project folder and execute below given commands:
     1) make clean
     2) make
     3) ./bin/rangesearch

Here's what each command accomplishes:

1) make clean:
   This command clears the build environment by deleting all old compiled object files and executables associated with the project. It's a preparatory step that ensures a fresh start for the build process, free from any artifacts that might disrupt the current compilation.
2) make:
   Following the cleanup, the 'make' command is issued to compile the project. It refers to the 'Makefile', a script with build directives, to transform the source code into an executable file. If this command finishes without any errors, the compilation is deemed successful. While warnings might appear, they are generally minor and shouldn't impede the compilation, although they should be reviewed to avoid potential problems.
3) ./bin/rangesearch:
   After compilation, this command runs the executable. The './' indicates that the file is located in the current directory, with 'bin/rangesearch' pointing to the executable's location. This action activates the range searching algorithm that works with the kd-tree structure.

Once the './bin/rangesearch' command is executed, the program follows its logic and creates an 'output.json' file. 
This file includes the results of the range search, listing the data points that lie within or on the boundary of the specified query polygon Q, according to the algorithm's design.


# Guide for Running Custom Test Scenarios:

1. Start by uploading a folder that includes four designated JSON files. 
   - For instance, name your folder 'test_case_01'. [Reminder: For adding more folders, continue the sequence with names like 'test_case_02', 'test_case_03', etc.]

2. This folder must contain these four JSON files:
   - 'input_points.json' - Contains the input points needed to begin the first test.
   - 'input_query.json' - Holds the query polygon data for the first test.
   - 'output_count.json' - Provides the expected number of results for the first test.
   - 'output_report.json' - Details the expected points report for the first test.

3. After the test runs, two output files will be produced in the same directory:
   - 'output_result_count.json' - Delivers the actual count of results from the test.
   - 'output_result_report.json' - Offers the actual report of points from the test.

The output files will be created within the same folder as the test case you provided.
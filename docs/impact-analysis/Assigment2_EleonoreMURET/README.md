# Assignment 2 — Impact Analysis — Eleonore

## Component analyzed 
File: `scripts/at.lua`  
This module manages the classification of Austrian railway routes in the Transitous system.  
It uses a mapping table (`route_type_map`) to associate route types with MOTIS classes and target route types.  
The function `process_route(route)` applies this logic to each route.

## Created graph — Program Dependency Graph 
Type: Program Dependency Graph  
Diagram: see `GRAPH_ASS2.png`  
Components:
- `motis.lua`: provides the constants used (`HIGHSPEED_RAIL`, etc.)
- `at.lua`: main module
- `process_route(route)`: application function
- `route_type_map`: mapping table

Color coding:
-  Red: external dependency
-  Blue: analyzed module
-  Green: internal elements

## Impact and insights 
- **Critical dependency on `motis.lua`**: any modification of constants breaks the classification logic.  
- **Rigid structure**: mappings are hard-coded → difficult to maintain.  
- **Single but central function**: `process_route(route)` is likely called elsewhere in the project.  
- **Refactoring opportunity**: externalize `route_type_map` into a configuration file.  
- **Low coupling**: `at.lua` is autonomous → changes are low risk if properly tested.  

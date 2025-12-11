# Fault-Tree-Statistic

This project focuses on fault tree analysis and provides tools for generating, analyzing, and optimizing fault trees.

## Data Directories

### data_ft

The `data_ft` directory contains fault tree data files in a custom format. Each file represents a single fault tree with the following structure:

- **File Naming Convention**: `ftX.dat` where X is an integer identifier (e.g., ft0.dat, ft1.dat, etc.)
- **File Format**: 
  - Each file starts with `[ftX]` where X is the fault tree identifier
  - Each node is defined in the format: `{nodeID|operator|probability|[childNode1,childNode2,...]}`
  
  Where:
  - `nodeID`: Unique identifier for the node (e.g., node0, node1, eNode123)
  - `operator`: Logic gate type
    - `*`: AND gate
    - `+`: OR gate
    - `N`: K-out-of-N gate (where N is an integer)
    - `.`: Basic event (leaf node)
  - `probability`: Failure probability in scientific notation (e.g., 1.000000e+00)
  - `childNode1,childNode2,...`: List of child node IDs (empty for basic events)

**Example Node Definition:**
{node116|*|1.000000e+00|[node6,node164,eNode543,node385,eNode673,node139]}

This represents an AND gate (node116) with 5 child nodes and a probability of 1.0.

### data_statistic

The `data_statistic` directory contains computational cost statistics for fault trees analyzed with different node ordering strategies. Each file corresponds to a fault tree from the `data_ft` directory.

- **File Naming Convention**: `ftX_statistic.txt` where X matches the fault tree identifier
- **File Format**: Each line contains three fields separated by the `|` delimiter:
  - Node ordering sequence (comma-separated list of node IDs)
  - Number of operations (integer)
  - Computational time (float)

**Example Line:**
node123,node456,node789|125|0.003456
This represents a node ordering that required 125 operations and took 0.003456 seconds to compute.



### Analysis Approach
The project aims to optimize node ordering in fault tree analysis to minimize computational cost. 

## Usage

The project includes tools for:
- Generating fault trees with specified parameters
- Analyzing fault trees using different node ordering strategies
- Measuring computational performance of different approaches
- Training machine learning models to predict optimal node orderings

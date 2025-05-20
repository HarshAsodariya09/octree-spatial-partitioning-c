# DSA Project: Octree Data Structure and Range Queries

## Table of Contents

1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Detailed File Descriptions](#detailed-file-descriptions)

   * [Core Octree Implementation](#core-octree-implementation)
   * [Driver Programs](#driver-programs)
   * [Sample Input and Outputs](#sample-input-and-outputs)
   * [Configuration Files](#configuration-files)
4. [Build and Compilation](#build-and-compilation)
5. [Usage Instructions](#usage-instructions)
6. [Contributing](#contributing)
7. [License](#license)

---

## Project Overview

This repository demonstrates an **octree** data structure for 3D point storage and **range query** operations, accompanied by two driver programs. Implemented in **C**, the project:

* Builds an octree by inserting 3D points dynamically.
* Supports querying all points within a specified axis-aligned cube.
* Outputs tree structure and query results to text logs.

---

## Repository Structure

```
DSA/
├── octree.h              # Octree node and function prototypes
├── octree.c              # Octree implementation (insertion, traversal, range query)
├── main.c                # Driver 1: build tree and dump structure
├── main2.c               # Driver 2: perform range queries on built tree
├── random.txt            # (Optional) Input file for main.c (list of 3D points)
├── random1.txt           # Input file for main2.c (list of 3D points)
├── Octree.txt            # Sample output: printed octree structure
├── RangeQuery.txt        # Sample output: points found in range queries
├── main.o                # Object file for main.c
├── main2.o               # Object file for main2.c
├── octree.o              # Object file for octree.c
├── program.exe           # Compiled executable of main.c (Windows)
├── program2.exe          # Compiled executable of main2.c (Windows)
└── .vscode/              # VSCode configurations (tasks, launch settings)
```

---

## Detailed File Descriptions

### Core Octree Implementation

* **`octree.h`**

  * Defines the `OctreeNode` struct with:

    * Bounding cube center and half-dimension.
    * Pointers to up to 8 child octants.
    * Storage for a small number of points before subdivision.
  * Declares functions:

    * `createNode(...)`, `insertPoint(...)`, `rangeQuery(...)`, `printOctree(...)`, and `freeOctree(...)`.

* **`octree.c`**

  * Implements octree logic:

    * **Node Creation**: initializes a node with given center and half-dimension.
    * **Insertion**: places points in appropriate child octant, subdividing when capacity exceeded.
    * **Range Query**: traverses nodes whose bounds intersect the query cube, collecting points.
    * **Printing**: recursively prints node depth and contained points to a text file.
    * **Memory Cleanup**: frees all allocated nodes.

### Driver Programs

* **`main.c`**

  * Reads 3D points from `random.txt` (format: `x y z` per line).
  * Constructs an octree covering the data extents.
  * Prints the full tree structure to `Octree.txt`.

* **`main2.c`**

  * Reads 3D points from `random1.txt` to build the same octree.
  * Performs multiple range queries (hardcoded or via `RangeQuery.txt` parameters).
  * Appends each query result (points within cube) to `RangeQuery.txt`.

### Sample Input and Outputs

* **`random.txt` / `random1.txt`**

  * Contain lines of random 3D coordinates (e.g., `12 45 -8`).

* **`Octree.txt`**

  * Shows each node's depth and points when leaf, e.g.:

    ```
    Leaf Node at depth 0 with 2 points:
      Point: (1.00, 1.00, 1.00)
      Point: (100.00, 100.00, 100.00)
    ```

* **`RangeQuery.txt`**

  * Lists points found within each query cube:

    ```
    Point within cube: (-74.00, -72.00, -88.00)
    Point within cube: (-78.00, -39.00, -94.00)
    ```

### Configuration Files

* **`.vscode/tasks.json`**, **`launch.json`**, **`c_cpp_properties.json`**, **`settings.json`**

  * Provide build and debug setups in Visual Studio Code:

    * Compilation tasks for `main.c` and `main2.c`.
    * Debug configurations pointing to generated executables.

---

## Build and Compilation

1. **Prerequisites**:

   * GCC or Clang supporting C99.
2. **Clone and navigate**:

   ```bash
   git clone https://github.com/yourusername/DSA.git
   cd DSA
   ```
3. **Compile sources**:

   ```bash
   gcc -std=c99 -O2 -c octree.c -o octree.o
   gcc -std=c99 -O2 -c main.c   -o main.o
   gcc -std=c99 -O2 -c main2.c  -o main2.o
   gcc octree.o main.o -o program
   gcc octree.o main2.o -o program2
   ```

---

## Usage Instructions

* **Build the tree and print structure**:

  ```bash
  ./program random.txt
  # Output in Octree.txt
  ```

* **Perform range queries**:

  ```bash
  ./program2 random1.txt
  # Results appended to RangeQuery.txt
  ```

---

## Contributing

Feel free to open issues or pull requests for:

* Adding dynamic query input.
* Improving balance heuristics or capacity thresholds.
* Integrating visualization of the octree.

---

## License

Licensed under MIT. See [LICENSE](LICENSE) for details.

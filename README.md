#Octree Spatial Partitioning in C
A lightweight and modular implementation of a 3D Octree in C, designed for efficient spatial partitioning, point queries, and live interaction via a game-loop-style demo.

Features
Point insertion, search, and deletion

Automatic subdivision and merging of nodes

3D range queries using axis-aligned bounding cubes

Live simulation loop with point movement and trespass detection

Project Structure
bash
Copy
Edit
DSA/
├── .vscode/            # VS Code build/debug configuration
│   ├── c_cpp_properties.json
│   ├── launch.json
│   ├── settings.json
│   └── tasks.json
├── octree.h            # Octree data structures and function declarations
├── octree.c            # Core implementation of the Octree
├── main.c              # Main demo with interactive point movement
├── main2.c             # Optional secondary demo or testbed
├── Octree.txt          # Notes on design and logic
├── RangeQuery.txt      # Details for implementing 3D range queries
├── random.txt          # Sample point dataset
├── random1.txt         # Additional sample dataset
└── README.md           # Project documentation (this file)
Requirements
A C Compiler (gcc, MinGW, etc.)

(Optional) Visual Studio Code with C extension for streamlined builds

Build Instructions
Compile and Run via Terminal
bash
Copy
Edit
# Compile octree logic
gcc -c octree.c -o octree.o

# Build main demo program
gcc main.c octree.o -o program

# Optional: Build secondary demo
gcc main2.c octree.o -o program2
Run the Demo
bash
Copy
Edit
./program
Loads 3D points from random.txt

Prompts you to select a point: x y z

Move the point using keys:

w = +Y, s = -Y

a = -X, d = +X

e = +Z, f = -Z

A cube forms around the point

If another point enters the cube:

java
Copy
Edit
You are trespassing at point (X, Y, Z)!
Press q to exit loop and perform a 3D range query

Octree API (from octree.h)
c
Copy
Edit
typedef struct { float x, y, z; } Point;
typedef struct OctreeNode OctreeNode;

OctreeNode *createNode(Point center, float size, int depth);
void insertPoint(OctreeNode *root, Point *p);
OctreeNode *search(OctreeNode *root, Point *p);
void deletePoint(OctreeNode *root, Point *p);
void printTree(OctreeNode *root);
void rangeQuery(OctreeNode *root, Point *min, Point *max);
File Descriptions
octree.c/h: Core logic – insertion, subdivision, deletion, and queries

main.c: Game-style interaction demo with live trespass detection

main2.c: Alternate testing/demo logic

Octree.txt: Notes and decisions regarding Octree implementation

RangeQuery.txt: Breakdown of range query techniques

random.txt, random1.txt: Sample input files with point data

.vscode/: Tasks and launch configs for easy use in VS Code

Sample Input Format (random.txt)
python-repl
Copy
Edit
1.2 3.4 5.6
7.8 9.0 1.2
...
Each line: X Y Z (space-separated 3D coordinates)

Concepts Demonstrated
Recursive data structures (Octree)

Dynamic memory allocation

Point-in-cube detection

Node subdivision and merging

Real-time spatial interaction in C

Axis-aligned bounding cube queries

To-Do (Optional Enhancements)
 Add graphical visualization via Python/OpenGL

 Enable saving/loading Octree to/from files

 Implement collision detection between moving entities

 Add point update without delete-insert

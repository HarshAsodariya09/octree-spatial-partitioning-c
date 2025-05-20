# Octree Spatial Partitioning in C

A straightforward C implementation of a **3D Octree** data structure, featuring:

- ✅ Point insertion, search, and deletion  
- ✅ Automatic node subdivision and merging  
- ✅ 3D range queries using axis-aligned cubes  
- ✅ Demo “game loop” to move points and detect trespassing  

---

## ⚙️ Requirements

- C Compiler (`gcc`, MinGW, etc.)
- (Optional) Visual Studio Code for easier build/debug via `.vscode`

---

## 🛠️ Build Instructions

```bash
# Compile the octree implementation
gcc -c octree.c -o octree.o

# Build main demo program
gcc main.c octree.o -o program

# (Optional) Build the alternate demo
gcc main2.c octree.o -o program2
💡 VS Code users: Press Ctrl+Shift+B or run Terminal → Run Task → build (preconfigured)

🚀 How to Run
bash
Copy
Edit
./program
Loads 3D points from random.txt

Prompts you to select a point (x y z)

Move the point using:

w = +Y, s = -Y

a = -X, d = +X

e = +Z, f = -Z

A 3D bounding cube forms around the point

If any other point enters, it prints:

java
Copy
Edit
You are trespassing at point (X, Y, Z)!
Press q to stop and then perform a range query:

yaml
Copy
Edit
Enter minimum corner:  x y z
Enter maximum corner:  x y z
🔧 Octree API (in octree.h)
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
📄 Description of Files
octree.c & octree.h – Implements the Octree logic: inserting, subdividing, merging, searching, deletion, and querying.

main.c – Game-style demo with point movement and live trespass detection.

main2.c – Optional test/demo entry point.

Octree.txt – Your design and logic explanations for Octree structure.

RangeQuery.txt – Details on implementing 3D range search.

random.txt, random1.txt – Sample input files with 3D coordinates.

.vscode/ – Launch and build configurations for VS Code.

📌 Sample Input Format (random.txt)
python-repl
Copy
Edit
1.2 3.4 5.6
7.8 9.0 1.2
...
Each line contains a 3D point in the format:
X Y Z (separated by spaces)

🧠 Concepts Demonstrated
Recursive data structures (Octree)

Dynamic memory allocation in C

Point-in-cube detection

Subdivision and merge operations

Real-time 3D interaction via console

Range searching in 3D space

✅ To-Do (Optional Enhancements)
 Visualize octree using Python/OpenGL

 Support saving/loading octree to file

 Collision detection for moving entities

 Add point update (move without delete + insert)


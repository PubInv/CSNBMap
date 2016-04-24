# VestaReady

This is an incomplete to provide semi-automatic creation Constant-Scale Natural Boundary (CSNB) maps.

You can play with our [limited progess](http://robertlread.github.io/VestaReady/).

The basic toolchain and process is:

* Start with a .STL 3D file. In this case, we are using an STL providing by [neurothing](http://www.thingiverse.com/thing:42888)
of Thingiverse, created from NASA data.
* Looking at a 3D view of this object, select "nodes" which correspond to the interesting natural features used by CSNB. The GUI
for doing this is primitive, you just have to select a vertex or enter 3-space coordinates directly. At present it demands precisely
three points to be chosen, but of course that would be expanded in future work.
* These points form a primitive "tree" which is a network.  It is provided in an "unzipped" form in a network editor. In theory
this network editor would support all of the "Elbow" and "hinging" operations described by Clark and Clark in their research papers.
In actually I have selected an unzipping topology and you can't control it.
* You can, however, position the nodes in 2-space, which really DOES create the 2-space shape of the final map (in this case, 
quadrilateral.)  Real CSNB mapping must use polylines but at present only straight lines are allowed.
* The resulting "map", or what would become a map, is then presented.  I render ONLY the control points on this in color
representing the feature of interest (distance from the centroid in this example.) The point of CSNB mapping is of course to map all 
points, but I did not complete that in the 48 hours I had.

Looking on the bright side, this project demonstrates how a number of technologies can be used to create an online tool,
which may not have been obvious. Those are:
* three.js for the photorealistic rendering (and many math functions that will be needed for doing the projection/mappping),
* three.js STL loading to load arbitrary 3D shapes,
* vis.js for the network editing, which potentially would allow "node splitting" and unzipping and rejoining. It currently
demonstrates dragging.
* d3.js for and svg canvas for rendering the final map.

Much work remains to be done to make this workable.  Although in a sense it does a very, very minimal form of mapping, it
needs:
* The completion of the mapping. I believe this can be done by using map (mostly provided by three.js) to implement the following algorithm:
** Iterate over each feature/facet of the 3D model,
** for each feature, determine to which boundary segment it is closest by a distance from the plane of project associated with.
** I believe the 3-space feature paths MUST be flattend in a segment wise fashion, though the size of the segments may vary.
** Having chosen the closest segment, compute the closest point and the angle which to "shoot out" the feature from the
projection plan OF THAT SEGMENT in 3Space,
** Shoot parametrically along that angle in the map space, computing distance relative to the encounterable edge of the map.
** Note that closeness to a boundary is a directional condition; you have to check that you are on the "correct" side of the 
boundary. This can be done by comparing against the plane projected from the flattened segment to centroid.
** Complete all features.

This is not a formal specification; there is a fair amount of math left unspecified about how this can actually be done.
However, I do believe it CAN be fully automated, and that the human can apply creativity in desiging the boundaries, leaving
all mapping to the algorithm.

It is unclear to me if this is worth continuing.  If you have an opinion or could benefit from the completion of this work, please 
contact me.




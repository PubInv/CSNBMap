# My Current Plan

## Build an toolbench

I am going to build an actual toolbench that lets you interactively go from any 3D STL file to a 2D map.
Although this will be very general, I am going to focus on the Constant Scale Natural Boundary Mapping
idea, as that is the motivting factor.

My basic approach will be to use Cannon.js to provide "springines" to allow maniuplation of flexible objects
as if they were rubber sheets.

We will upload an STL file, "rubberize" it, then allow operations:

1) Stretching
2) Cutting (with preservation of centroid)
3) Projection about point (such as centroid)
3) Joining along node points.

In this way we want to show that we can create a CSNB of an object with these primitive operations.

Note that we need to use three.js and cannon to get the physicality.  After the projection to two space, it is not
clear that these are the best tools, but possibly we can still work with these things.  We can provide
cutting and joing in 2 space as well somehow.

Unfortunately, the mousepick functionality of the current system works with version 68, and does not directly work
with version 76.  I will no doubt have to debug and fix that if I carry on.

But let me try to get the testrahedral spike working.
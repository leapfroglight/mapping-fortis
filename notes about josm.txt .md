opening a geojson file containing polygons in JOSM

and saving it from JOSM

changes the polygons into LineStrings again

update(17 july 2026 01:36)
https://josm.openstreetmap.de/ticket/18902?cversion=0&cnum_hist=1

https://josm.openstreetmap.de/ticket/17453

does not solve the issue, but explains it

(Although there might be a preference which if set, would force all closed LineStrings to be Polygons)

..

for now, manually changing LineStrings to Polygons in the geojson code/text

"LineString" to "Polygon"

and wrap/enclose the coordinates with an extra set of square brackets [ ]



---

Features wished for in JOSM

either by core features or with a plugin

..

(writing this 16 july 2026 - calendar date 17 july 2026 00:58)

You have updated the building outline
and selected it

now want to remove all the other features so that you can save a 
copy of a geojson file with just the newly updated building outline


..

generalised description of the use case:

You want to save one or a select few features as a separate file

A way to attempt this is by Selecting the features of choice,
then click on Selection -> Invert Selection

Now all the other features are selected

delete

The problem is, deleting the other features will delete the Points in those features too

And if the features being deleted share some points with the features you want to keep,
those shared points/nodes will get deleted too
and as a result - modifying the features you want to keep (deleting some nodes of the feature)
or
possibly entirely deleting the feature (when all nodes are shared with inverted selection and are deleted)


...

so, solving it like this now:

give a unique/easily identifiable tag for the new feature/features

open the geojson files in a code editor

and either cut+paste or copy+paste the features of choice to a new geojson file


Wished for feature:

Delete all the unselected features while preserving all nodes of selected features (even if nodes are shared)

or

Select one or a few features
and
save them as a new or separate layer

or move them to another existing layer

UPDATE:
(17 july 01:24)

Found how to do it

Step 1:
If want to move to a new layer, create a new layer first

If you want to add to an already existing layer, skip this step

Step 2:

select the features of choice
Edit -> Merge Selection 

and select an existing layer or the newly created and now existing layer

the selected features are moved to the selected layer of choice


---



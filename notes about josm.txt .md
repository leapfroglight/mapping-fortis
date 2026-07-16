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


17 july 02:45

Moved a few features to a separate layer

Now, wanted to delete those features in the previous layer


(
exact thing I was trying to do:

the elevator shaft area and the staircase footprint areas were part of 
Polygons layer Areas file

since the elevator shaft areas and staircase footprint areas are common to whole building in this case
and therefore can be reused across all floors

whereas other areas might differ between floors

Wanted to extract those areas to a separate file

)

So, I selected and used the 
Edit->Merge Selection
feature to move these to a new feature

But it does not remove those features (LineString)(closed LineString) from the previous layer

We have to remove them

deleting those features from JOSM also deletes all the nodes and segments in the feature entirely

in case some of these nodes or segments were shared by other features in the file,

all those other features get modified and removed of the nodes and segments that are in the feature you want to delete


..

Therefore,

the solution i could think of now is to again do manual editing in geojson code

find and delete those features in the geojson code manually

..

If we anyways, have to manually do this,

there's not much benefit gained from using the "Edit -> Merge Selection" feature


the "Edit -> Merge Selection" functionality would be useful when we want to Copy+Paste features into other layers or a new layer

When we want to Cut+Paste a feature from one layer(A) to another layer(B),

then doing manual cutting from A.geojson file and pasting into B.geojson file

would be the same work as doing

"Edit -> Merge Selection" to paste it into B file
and manually removing/deleting those features in the A.geojson file's json text/code


..

So, this still leaves the folowing functionality to be desired in JOSM

Ability to delete a LineString or Polygon feature while preserving the nodes and segments wherever they are being used by other features

EDIT:REALISING AS I TYPE THIS

I MISUNDERSTOOD

JOSM ACTUALLY DOES NOT DELETE NODES THAT ARE SHARED BY OTHER FEATURES WHEN DELETING A LINESTRING

BUT IF YOU DELETE A NODE, IT WILL GET DELETED REGARDLESS OF HOW OTHER FEATURES THAT INCLUDE THIS NODE MIGHT GET 
MODIFIED

# Groom_Exporter_To_Unreal
HDA exports groom from houdini to Unreal on ABC

Inside the HairGen node, create the HDA (groomexporterabc) and connect it just below the OUTPUT called HAIRS.
The HDA allows alembic export both as a single frame pose and the entire frange range in scene.

-Scale:

By definition it is set to 100 which is the value that Unreal uses, if you need to use the Houdini scale, please set the scale to 1.

-Random Delete:

It is disabled but allows you to set a random percentage of hair that will be removed.

-Rop Alembic:

We can choose between current frame and frame range, choose where it is saved and we would only need to save to disk.

IMPORTANT NOTE: Both for a single frame and for several frames, do not save the file with $F4, since we only need a single file.

# Groom_Exporter_To_Unreal
### HDA exports groom from houdini to Unreal on ABC

In Houdini:

  Inside the HairGen node, create the HDA (groomexporterabc) and connect it just below the OUTPUT called HAIRS.
  The HDA allows alembic export both as a single frame pose and the entire frange range in scene.

  - Scale:

  By definition it is set to 100 which is the value that Unreal uses, if you need to use the Houdini scale, please set the scale to 1.

  - Random Delete:

  It is disabled but allows you to set a random percentage of hair that will be removed.

  - *Rop Alembic*:

  We can choose between current frame and frame range, choose where it is saved and we would only need to save to disk.

  > [!WARNING]
  > Both for a single frame and for several frames, do not save the file with $F4, since we only need a single file.
  
In Unreal:

Edit>Plugings>Activate Alembic Groom Importer and Groom.

We create a folder for Groom and add the created file, this will open a tab named "Groom Import Options".

Change the following parameters:

Rotation: 90,0,0

Scale: 1,-1,1

Groom Cache: Activate Import Groom Cache and Import Groom Asset. (Only for Frame Range Exports)

Finally Import.

In the case of having exported a single frame, it will result in a single file, in the case of having exported in frange range, it will return three files (Groom, GuidesCache and StrandsCache).

How to view our groom in viewport?

Case 1(Single Frame):

  -We drag our file (Groom) to the viewport and in Details>Translation (0,0,0)
  
  -Double click on the imported file to set the Width

  -Right click on the hair file>Create Bindings>Select where we want to attach it.

  -Finally we need to replace the groom and bindings files in our target geometry>Groom.

Case 2(Frame Range):

  -We drag our file (Groom) to the viewport. 

  -In the Details section of the file added to the Viewport, we find Groom cache, there we will add the file (StrandsCache). Finally, we need to create a Level Sequence.

  -With the hair selected and in the Sequence tab, click +Track>Actor To Sequencer>Add. This will create a file just below, we need to click + and select GroomCache.

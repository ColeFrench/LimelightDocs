Complete NetworkTables API
============================

"Best" Contour information:

Use the following code:

.. tabs::
	
	.. tab:: Java

		.. code-block:: java

			NetworkTableInstance.getDefault().getTable("limelight").getEntry("<variablename>").getDouble(0);

	.. tab:: LabView

			.. image:: img/Labview_ReadData.png

	.. tab:: C++

		.. code-block:: c++

			nt::NetworkTableInstance::GetDefault().GetTable("limelight")->GetNumber("<variablename>",0.0);
			
	.. tab:: Python

		.. code-block:: python

			NetworkTables.getTable("limelight").getNumber('<variablename>');

		    


to retrieve this data:


====== =====================================================================================
tv 		Whether the limelight has any valid targets (0 or 1)
------ -------------------------------------------------------------------------------------
tx		Horizontal Offset From Crosshair To Target (-27 degrees to 27 degrees)
------ -------------------------------------------------------------------------------------
ty		Vertical Offset From Crosshair To Target (-20.5 degrees to 20.5 degrees)
------ -------------------------------------------------------------------------------------
ta		Target Area (0% of image to 100% of image)								
------ -------------------------------------------------------------------------------------
ts		Skew or rotation (-90 degrees to 0 degrees)
------ -------------------------------------------------------------------------------------
tl 		The pipeline's latency contribution (ms) Add at least 11ms for image capture latency.
------ -------------------------------------------------------------------------------------
tshort		Sidelength of shortest side of the fitted bounding box (pixels)
------ -------------------------------------------------------------------------------------
tlong 		Sidelength of longest side of the fitted bounding box (pixels)
------ -------------------------------------------------------------------------------------
thoriz		Horizontal sidelength of the rough bounding box (0 - 320 pixels)
------ -------------------------------------------------------------------------------------
tvert 		Vertical sidelength of the rough bounding box (0 - 320 pixels)
====== =====================================================================================


Camera Controls:

Use the following code:

.. tabs::
	
	.. tab:: Java

		.. code-block:: java

			NetworkTableInstance.getDefault().getTable("limelight").getEntry("<variablename>").setNumber(<value>);

	.. tab:: LabView

			.. image:: img/Labview_WriteData.png

	.. tab:: C++

		.. code-block:: c++

			nt::NetworkTableInstance::GetDefault().GetTable("limelight")->PutNumber("<variablename>",<value>);
			
	.. tab:: Python

		.. code-block:: python

		    	NetworkTables.getTable("limelight").putNumber('<variablename>',<value>);


to set this data:

=========== =====================================================================================
ledMode		Sets limelight's LED state
----------- -------------------------------------------------------------------------------------
0	 	use the LED Mode set in the current pipeline
----------- -------------------------------------------------------------------------------------
1 		force off
----------- -------------------------------------------------------------------------------------
2 		force blink
----------- -------------------------------------------------------------------------------------
3 		force on
=========== =====================================================================================


=========== =====================================================================================
camMode		Sets limelight's operation mode
----------- -------------------------------------------------------------------------------------
0	 	Vision processor
----------- -------------------------------------------------------------------------------------
1 		Driver Camera (Increases exposure, disables vision processing)
=========== =====================================================================================


=========== =====================================================================================
pipeline	Sets limelight's current pipeline
----------- -------------------------------------------------------------------------------------
0 .. 9		Select pipeline 0..9
=========== =====================================================================================


=========== =====================================================================================
stream		Sets limelight's streaming mode
----------- -------------------------------------------------------------------------------------
0	 	Standard - Side-by-side streams if a webcam is attached to Limelight
----------- -------------------------------------------------------------------------------------
1 		PiP Main - The secondary camera stream is placed in the lower-right corner of the primary camera stream
----------- -------------------------------------------------------------------------------------
2	 	PiP Secondary - The primary camera stream is placed in the lower-right corner of the secondary camera stream
=========== =====================================================================================

=========== =====================================================================================
snapshot		Allows users to take snapshots during a match
----------- -------------------------------------------------------------------------------------
0	 	Stop taking snapshots
----------- -------------------------------------------------------------------------------------
1 		Take two snapshots per second
=========== =====================================================================================

Advanced Usage with Raw Contours
-------------------------------------------------

Raw Targets:

Limelight posts three raw contours to NetworkTables that are not influenced by your grouping mode. That is, they are filtered with your pipeline parameters, but never grouped. X and Y are returned in normalized screen space (-1 to 1) rather than degrees.

=========== =====================================================================================
tx0		Raw Screenspace X
----------- -------------------------------------------------------------------------------------
ty0		Raw Screenspace Y
----------- -------------------------------------------------------------------------------------
ta0		Area (0% of image to 100% of image)	
----------- -------------------------------------------------------------------------------------
ts0		Skew or rotation (-90 degrees to 0 degrees)
----------- -------------------------------------------------------------------------------------
tx1		Raw Screenspace X
----------- -------------------------------------------------------------------------------------
ty1		Raw Screenspace Y
----------- -------------------------------------------------------------------------------------
ta1		Area (0% of image to 100% of image)	
----------- -------------------------------------------------------------------------------------
ts1		Skew or rotation (-90 degrees to 0 degrees)
----------- -------------------------------------------------------------------------------------
tx2		Raw Screenspace X
----------- -------------------------------------------------------------------------------------
ty2		Raw Screenspace Y
----------- -------------------------------------------------------------------------------------
ta2		Area (0% of image to 100% of image)	
----------- -------------------------------------------------------------------------------------
ts2		Skew or rotation (-90 degrees to 0 degrees)
=========== =====================================================================================


-------------------------------------------------

Raw Crosshairs:

If you are using raw targeting data, you can still utilize your calibrated crosshairs:

=========== =====================================================================================
cx0		Crosshair A X in normalized screen space
----------- -------------------------------------------------------------------------------------
cy0		Crosshair A Y in normalized screen space
----------- -------------------------------------------------------------------------------------
cx1		Crosshair B X in normalized screen space
----------- -------------------------------------------------------------------------------------
cy1		Crosshair B Y in normalized screen space
=========== =====================================================================================

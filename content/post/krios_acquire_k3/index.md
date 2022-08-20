---
authors:
- admin
categories: []
date: "2022-08-16T00:00:00Z"
draft: false
featured: true
image:
  caption: 'Titan Krios Data Acquisition Setup'
  focal_point: "top"
  preview_only: false
lastmod: "2022-08-16T00:00:00Z"
projects: [Outreach]
title: 'Cryo-EM Data Acquisition with a K3 detector and EPU (CDS Mode)'
subtitle: 'Quick Reference for cryo-EM data acquisition using EPU on the Titan Krios  :snowflake:'
summary: Quick Reference for cryo-EM data acquisition using EPU on the Titan Krios
tags:
- Cryo-EM
- Instructions
- Protocols
- Featured
---

## Overview

Setting up data collection can be divided into these main steps:
<ol>
	<li>GIF Tuning</li>
	<li>Non-CDS Gain Reference Collection</li>
	<li>Image Shift Calibration</li>
	<li>Atlas Generation</li>
	<li>Set Up the EPU Session</li>
	<li>CDS Gain Reference Collection</li>
	<li>Manual ZLP Centering</li>
	<li>Perform Direct Alignments</li>
	<li>Final Touches</li>
</ol>

<hr style='margin:35px 0'>

## Step 1 - Tune the GIF (optional)
<ol>
	<li>Using the microscope computer, set the <code>Condenser Aperature</code> to 150.</li>
	<li>If needed, the position of the slit can be moved manually. To do so, activate the camera <code>View</code>, click on the Gatan Filter Control Window (<code>Gatan >> Windows >> Filter Control</code>), and use the keyboard arrow keys to adjust.</li>
	<li><code>Stop View</code></li>
	<li>Set the spot size to 2 using the microscope control pad.</li>
	<li>Insert the screen, center the beam using the track ball, and adjust the beam size and intesity to be approximately 1.5 times the size of the green circle. Retract the screen when finished.</li>
	<li>The tuning needs to be performed in both linear and counted modes. Begin with the Gatan set to <code>linear</code>.
	<li>On the Gatan computer <code>Tune GIF >> Quick Tune</code>. This will also center the ZLP.</li>
	<li>When the GIF tuning is complete, an assement image will pop up on the Gatan computer. It should look fairly flat with muddy colors. If the GIF tuning fails completely or if the image is very colorful, it may be due to a beam intensity that is is too low. Reinsert the screen, increase the intensity, and try again.</li>
</ol>

<hr style='margin:35px 0'>

## Step 2 - Non-CDS Gain Reference Collection (optional)
<div style='background:pink; color:darkred'><B>CRITICAL:</B>  For Gain Reference Collection, Data Acquisition parameters must already be set and the ZLP should be centered. ZLP centering is performed as part of the GIF tuning protocol, so the ZLP is likely already centered.<BR><BR>Also note that during the automatic ZLP centering, the Gatan camera is taken out of CDS mode (if it was previously in CDS mode). For the initial gain references, you DO NOT want to be in CDS mode.</div>

<p style='margin-bottom:15px'></p>

<ol>
	<li>Navigate to an empty grid square.</li>
	<li>Check that the acquisiton parameters in EPU are reasonable. <code>Preparation >> Data Acquisition >> Preview</code></li>
	<li>On the microscope computer, set the <code>Aperature</code> to 150.</li>
	<li>Using the microscope control panel, set the spot size to 2.</li>
	<li>On the microscope computer, insert the screen and check for fringes. If fringes are present, adjust the beam intensity using the control panel knobs and the beam position using the track ball.</li>
	<li>Gain references will need to be collected in both counted and linear modes. Adjust the Gatan camera settings to be <code>Low Dose</code>, <code>Counted</code>, <code>0.5x</code>. Note:  If the camera is set to <code>Counted</code> then the gain reference acquisition will automatically advance from counted to linear mode. If the camera is set to <code>Linear</code>, only the linear gain references will be collected. That is not what you want.</li>
	<li>Prepare gain references on the Gatan Computer. <code>Camera >>  Prepare Gain Reference</code>.</li>
	<li>Follow the instructions when prompted by the Gatan Computer. You will need to adjust the beam intensity. Use the numbers on the Gatan display and adjust to the required value.</li>
	<li>Manually check the beam centering by inserting the screen. If needed, adjust the beam center postion by selecting <code>Direct Alignments >> Beamshift Center</code> on the microscope computer and adjusting the beam position with multifunction X and multifunction Y on the control pad. Center on the green circle.</li>
	<li>After the first set (linear) of gain references have been collected, make sure the <code>Data Acquisition</code> settings display for EPU. Click <code>Set</code>. Note:  The spot size should change back to 5 and the objective aperature should automatically change to 100 um if it was not already at 100 um.</li>
	<li>After the linear gain references have been collected, the counted mode gain reference collection window will appear. Check <code>Expert Mode</code> and make sure the <code>Dose Rate</code> is set to 10.0 and the <code>Gain Ref Electron</code> is at 3000. Click <code>OK</code>.</li>
	<li>Follow the instructions when prompted by the Gatan Computer (similar to before). You will need to adjust the beam intensity. Use the numbers on the Gatan display and adjust to the required value.</li>
	<li>When the gain reference is completed, open the Gatan camera. <code>View</code>.
	<li>Set the view to <code>1x</code>.</li>
	<li>Also activate the FFT window.</li>
	<li>Both the main window and the FFT should be decently flat however with the latest acquisition setups the gain reference is not applied. Any imperfections in the image should be reflected by a similar pattern in the gain reference.</li>
	<li>Set the <code>Data Acquisition</code> parameters by clicking <code>Set</code>.</li>
</ol>

<hr style='margin:35px 0'>

## Step 3 - Image Shift Calibration

<div style='background:pink; color:darkred'><B>CRITICAL:</B>  For the Image Shift Calibration, it is obligatory that all Preparation modes (Atlas at 175x, Grid Square, Hole/Eucentric Height, Data Acquisition/Auto Focus) are already set.</div>

### Part 1 - Grid Square Selection
<div style='background:lemonchiffon; color:goldenrod'>Note:  This square will take a fair amount of radiation damage, so it is important that it is not a square that you plan to use for data acqusition. A square that has a few empty holes and some interestingly-shaped contamination is ideal.</div>

### Part 2 - Locate and Navigate to a Landmark
<ol>
	<li>Navigate to <code>Preparation >> Atlas</code>.</li>
	<li>Select a grid square that has an obvious landmark. Usually a piece of contaimination with a distinctive shape is desirable. If collecting on Lacey carbon grids, contamination near to an interesting carbon pattern is even better. Move the stage to that grid square and landmark. <code>(Right click) Move stage here</code>.</li>
	<li>Check the grid square. <code>Preparation >> Grid Square >> Preview</code>.</li>
	<li>Determine the eucentric height  <code>Auto Functions >> Hole/Eucentric Height >> Auto-eucentric by beam tilt.</code></li>
	<li>Set the microscope parameters to match the Data Acqusition settings. <code>Preparation >> Data Acquisition >> Set</code>.</li>
	<li>Sequentially center the stage position on the landmark at each magnification setting, ending with <code>Data Acquisition</code>.</li>
</ol>

### Part 3 - Perform Image Shift Calibration
<ol>
	<li>Select <code>Preparation >> Tasks >> Calibrate Image Shifts >> Start Calibration</code>.</li>
	<li>The Image Shift Calibration module will walk through the calibration. To continue, click <code>Proceed</code>.</li>
	<li>When a new setting is applied and an image is generated, adjust the calibration center by double-clicking on the corresponding spot on the right image panel. It is advisable to re-acquire this image before moving on. When satisfied, click <code>Proceeed</code>. This will walk through each magnification setting, beginning from <code>Data Acquisition</code> and continuing through to <code>Atlas</code>.</li>
</ol>

<hr style='margin:35px 0'>

## Step 4 - Generate the Atlas

<ol>
	<li>Select <code>Atlas >> Session Setup</code>.</li>
	<li>Enter a path for the data (the folder will be created automatically). Images should be saved as <code>MRC</code> format.</li>
	<li>Double-check the Atlas acquisition parameters <code>Preparation > Atlas</code>. For screening, a magnification 135x of is used to increase speed. For data collection atlases, a magnification of 175x is preferred.</li>
	<li>Select the grid to be atlased.</li>
	<li>Ensure that the objective aperature it out.</li>
	<li>Begin the atlas acquisition by clicking <code>Start</code>.</li>
</ol>

<hr style='margin:35px 0'>

## Step 5 - Set up the EPU Session

<ol>
	<li>Select <code>EPU >> Session Setup</code>.</li>
	<li>Enter the setup parameters. Enter a path for the data (the folder will be created automatically). Image format should be saved as <code>MRC</code> format. The Dose fraction output should be <code>Tiff Lzw Non-gain normalized</code>.  Make sure that the acqusition type is <code>Manual</code> and <code>Faster</code>. Make sure to select the correct grid type and indicate the hole paramters (if applicable).</li>
	<li>Still in the EPU window, use the <code>Atlas</code> tab to select a reasonable grid square.</li>
	<li>Determine the eucentric height. Select <code>Preparation >> Hole/Eucentric Height >> Auto Eucentric Height by beam tilt</code>.  Note: Our microscope has a slight systematic error of about 2.5 um for the typical parameters.  Manually adjust the Z height using the microscope computer <code>Stage >> Set >> Z (subtract 2.5 microns) >> Go To</code>.</li>
	<li>It can be useful to take an image of an empty hole in the grid for subsequent determination of approximate ice thickness. This can be done by centering on the empty hole, then selecting <code>Preparation >> Data Acquisition >> Acquire</code>. Note the dose (lower right window).</li>
	<li>Check the grid square quality. Move to a hole that could be potenially useful for collection. Then collect an image <code>Preparation >> Data Acquisition >> Acquire</code>.</li>
	<li>If the ice thickness is appropriate (usually ~80% of the empty hole dose is desireable), this square can be used for data collection. <code>EPU >> Atlas >> (Right Click on Grid Square) Add Square</code>.</li>
	<li>Generate the pattern of images to be collected. <code>EPU >> Hole Selection >> Generate Pattern</code>. Use the brush too to manually remove i) empty holes/regions, ii) significant contamination, iii) thick ice near the edges of each grid square. Some of this can be automated using the controls in the top and right panels.  Note: If you intend on using the automatic hole selection (recommended), be very stringent in setting the cutoff values in the histogram!</li>
	<li>Add the collection and focus parameters. Defocus values that are typically used begin around -2.2 microns and continue to -0.8 microns. To add these, enter the desired defocus value and click on the :page_facing_up: icon next to the entry field. It should now be present in the defocus values list above. Valeus can be removed by selecting them and clicking on the :wastebasket: icon. Be sure to double check these and ensure that the values are negative!</li>
	<li>Set the following parameters for Lacey carbon grids:
		<ul>
			<li>Delay after Image Shift = 1.5 seconds</li>
			<li>Delay after Stage Shift = 15 seconds</li>
			<li>Recurrance = After Distance = 10 microns</li>
			<li>Focus = Objective lens</li>
		</ul>
	</li>
	<li>Alternatively, set the following parameters for Quantifoil grids:
		<ul>
			<li>Delay after Image Shift = 1.5 seconds</li>
			<li>Delay after Stage Shift = 1 second</li>
			<li>Recurrance = After Distance = 10 um</li>
			<li>Focus = Objective lens</li>
		</ul>
	</li>
	<li>If collecting from Lacey grids, use the <code>EPU >> Generate Template</code> to tile the grid square. Use a spacing of 1.2 um.</li>
	<li>If collecting from Quantifoil grids, beam shift collection can dramatically speed up acquisiton. Use the <code>EPU >> Generate Template</code> to set this up. Be sure to include one shot for Autofocus. If you are unsure how to make an appropriate template, ask the Facility Manager.</li>
	<li>Return to the <code>EPU >> Atlas</code> view. The grid square should now display the eucentric height determined earlier and the number of images to be collected should be indicated in the right-most panel.</li>
	<li>Option 1 - Automatic (preferred):  Return to the Atlas view (<code>EPU >> Preparation >> Square Selection</code>) select more squares that look good for acquisition.  Once finished, go to <code>EPU >> Preparation >> Hole Selection >> Prepare All Squares</code>.</li>
	<li>Option 2 - Manual:  Repeat this process beginning at item 3. It is not necessary to re-enter the collection  (item 9) as these should be preserved from earlier, but remember to update the Z-height after determining the eucentric height for each square.  Continue adding more grid squares until there are enough for the desired collection time.</li>
</ol>

<hr style='margin:35px 0'>

## Step 6 - Manual Centering of the ZLP (optional)
<div style='background:pink; color:darkred'><B>IMPORTANT:</B>  Centering the ZLP will disable CDS mode without notification. If centering the ZLP, make sure to double-check that CDS mode is enabled afterward.</div>

<p style='margin-bottom:15px'></p>

<ol>
	<li>On the Gatan computer open the <code>Filter Control</code> window.</li>
	<li>Adjust the Gatan camera settings to be <code>Low Dose</code>, <code>Linear</code>, <code>1x</code>.</li>
	<li>Make sure the camera is active by clicking <code>View</code>. 
	<li>Using the arrow keys (up and down), adjust the ZLP position. Make sure to count how many times you click in a given direction.</li>
	<li>Move in the up direction. You should eventually find the edge of the ZLP as the camera image will have aberrations. This is usually 10-14 clicks.</li>
	<li>Now navigate using the down arrow key back into the slit and to the bottom edge (while counting).</li>
	<li>Navigate back up into the slit to make up half of the distance. Example:  If it took 24 clicks from the 'top' edge of the slit to the 'bottom' edge of the slit, navigate back 12 times to center the slit.</li>
	<li>Click the <code>O</code> button to the left of the adjustment text box to set this current slit position to 0.</li>
</ol>

<hr style='margin:35px 0'>

## Step 7 - CDS Mode Gain Reference Collection

<div style='background:pink; color:darkred'><B>CRITICAL:</B>  For Gain Reference Collection, Data Acquisition parameters must already be set and the ZLP should be centered. <BR>This time, do NOT center the ZLP using the automatic ZLP centering function on the Gatan computer. Doing so will cause the camera to come out of CDS mode. If you accidentally center the ZLP this way, make sure to reactivate CDS mode as described above.</div>

<p style='margin-bottom:15px'></p>

<ol>
	<li>Make sure the Gatan is set to CDS mode <code>Technique Manager >> Low Dose >> EF-CCD Camera >> Gear Icon (to the right of "View").</code>  Make sure to set <code>Corrections: Unprocessed</code>, <code>Correct defects: Checked</code>, <code>CDS Mode: Checked</code></li>
	<li>Navigate to an empty grid square.</li>
	<li>Check that the acquisiton parameters in EPU are reasonable. <code>Preparation >> Data Acquisition >> Preview</code></li>
	<li>On the microscope computer, set the <code>Aperature</code> to 150.</li>
	<li>Using the microscope control panel, set the spot size to 2.</li>
	<li>On the microscope computer, insert the screen and check for fringes. If fringes are present, adjust the beam intensity using the control panel knobs and the beam position using the track ball.</li>
	<li>Gain references will need to be collected in both counted and linear modes. Adjust the Gatan camera settings to be <code>Low Dose</code>, <code>Counted</code>, <code>0.5x</code>. Note:  If the camera is set to <code>Counted</code> then the gain reference acquisition will automatically advance from counted to linear mode. If the camera is set to <code>Linear</code>, only the linear gain references will be collected. That is not what you want.</li>
	<li>Prepare gain references on the Gatan Computer. <code>Camera >>  Prepare Gain Reference</code>.</li>
	<li>Follow the instructions when prompted by the Gatan Computer. You will need to adjust the beam intensity. Use the numbers on the Gatan display and adjust to the required value.</li>
	<li>Manually check the beam centering by inserting the screen. If needed, adjust the beam center postion by selecting <code>Direct Alignments >> Beamshift Center</code> on the microscope computer and adjusting the beam position with multifunction X and multifunction Y on the control pad. Center on the green circle.</li>
	<li>After the first set (linear) of gain references have been collected, make sure the <code>Data Acquisition</code> settings display for EPU. Click <code>Set</code>. Note:  The spot size should change back to 5 and the objective aperature should automatically change to 100 um if it was not already at 100 um.</li>
	<li>After the linear gain references have been collected, the counted mode gain reference collection window will appear. Check <code>Expert Mode</code> and make sure the <code>Dose Rate</code> is set to 10.0 and the <code>Gain Ref Electron</code> is at 3000. Click <code>OK</code>.</li>
	<li>Follow the instructions when prompted by the Gatan Computer (similar to before). You will need to adjust the beam intensity. Use the numbers on the Gatan display and adjust to the required value.</li>
	<li>Set the <code>Data Acquisition</code> parameters by clicking <code>Set</code>.</li>
	<li>When the gain reference is completed, open the Gatan camera. <code>View</code>.
	<li>Set the view to <code>1x</code>.</li>
	<li>Also activate the FFT window.</li>
	<li>Both the main window and the FFT should be decently flat however with the latest acquisition setups the gain reference is not applied. Any imperfections in the image should be reflected by a similar pattern in the gain reference.</li>
	<li>Bin and export the CDS gain reference. Navigate to <code>C:/ProgramData/Gatan/ReferenceImages/</code>code>. There should be two sets of gain references. One set for non-CDS (i.e. 'normal') mode that are rather stable. The other set are for CDS mode and include the ones you just collected. Open the image, then rebin it. <code>Process >> Re-bin by Two >> Save As...</code>. Make sure NOT to overwrite the original. Change the name following the convention CDSbinnedgainrefMMDDYY.mrc. Save it in the DoseFractions folder.</li>
	<li>Set the <code>Data Acquisition</code> parameters by clicking <code>Set</code>.</li><li>Activate the Gatan camera (<code>View</code>), check that the empty image quality is reasonable (although keep in mind that it is not gain corrected), and record the empty dose. This should be something around 14 electrons/pixel/second.</li>
</ol>

<hr style='margin:35px 0'>

## Step 8 - Perform Direct Alignments

### Part 1 - Grid Square Selection
<div style='background:lemonchiffon; color:goldenrod'>Note:  As with the Image Shift Calibration, this square will take a fair amount of radiation damage, so it is important that it is not a square that you plan to use for data acqusition. A square that has a few empty holes and some interestingly-shaped contamination is ideal.</div>

<p style='margin-bottom:15px'></p>

<ol>
	<li>Use EPU to navigate to a new grid square. Move to an empty hole for best contrast.</li>
	<li>Determine the eucentric height. <code>Auto functions >> Hole Eucentric >> Eucentric Height by Beam Tilt</code></li>
	<li>Position the beam on the edge of an empty hole. This can be done using the EPU controls or by using the joystick on the control panel if the screen is inserted.</li>
</ol>

### Part 2 - Initial Focus Determination
Overview:  This part of the protocol will serve to tune the eucentric height and find focus. It will be refined in Part 5.
<ol>
	<li>Insert the screen</li>
	<li>Set the eucentric height manually
		<ol type="a">
			<li>Set the microscope optics to the Data Acquisition setting. <code>Preparation >> Data Acquisition >> SET</code></li>
			<li>Use the control panel joystick to move to an area where you can see the edge of the hole and some carbon.</li>
			<li>Set the alpha angle to +/- 20 degrees. This command can be found on the microscope computer under the Stage menu (lower right corner) in the Control tab. You will need to activate the popout extension from the Stage parameters menu to adjust the alpha angle. The stage should rotate. The goal is to adjust the Z-height of the stage such that changing alpha +/- 20 degrees keeps the center of the image in place. Z-height can be adjusted using the control panel (rightmost buttons).</li>
			<li>When adjusting the height, it is likely necessary to toggle between alpha=0 and alpha=20.</li>
			<li>When satisfied with the Z-height adjustment, make sure to set alpha back to 0 degrees.</li>
		</ol>
	</li>
	<li>Use the control panel joystick to move the beam over some carbon.</li>
	<li>Find focus using the Gatan computer
		<ol type="a">
			<li>Retract the screen</li>
			<li>Check the Gatan camera parameters. The <code>exposure time</code> should be 1x. The mode should be <code>counted</code>.
			<li>Activate the Gatan camera. <code>View</code></li>
			<li>Using the FFT window, find focus. Use the defocus knob on the control panel and adjust until no Thon rings are apparent.</li>
			<li>Reset the defocus to 0 using the control panel.</li>
			<li>Deactivate the Gatan camera. <code>Stop View</code></li>
		</ol>
	</li>
</ol>

### Part 3 - Initialize Direct Alignments
<ol>
	<li>Insert the screen.</li>
	<li>Activate the direct aligments menu (bottom right).</li>
	<li>Sequentially adjust the alignments:
		<ol type="a">
			<li>nP beam tilt ppX (use multifunction X to minimize movement)</li>
			<li>nP beam tilt ppY (use multifunction X to minimize movement)</li>
			<li>beamshift center (use both knobs; center on the green circle)</li>
			<li>rotation center (minimize movement; use both knobs)</li>
		</ol>
	</li>
	<li>Click <code>Done</code> when finished.</li>
	<li>Retract the screen.</li>
</ol>

### Part 4 - Initial Astigmatism Correction and Coma-Free Alignment
<ol>
	<li>Open the Sherpa window. If Sherpa is not already running, it can be launched from <code>Microscope Software Launcher >> Tools >> Sherpa</code>.</li>
	<li>Use the control panel to dial in approximately -0.9 um defocus (note: this may vary depending on the magnification being used)</li>
	<li>Check and/or set the following parameters:</li>
		<ul>Type: EF-CCD</ul>
		<ul>Exposure time [s]: 2.0</ul>
		<ul>Binning: 2</ul>
		<ul>Readout area: Full</ul>
		<ul>Electron counting: checked</ul>
		<ul>Autofocus to [um]: -0.9, checked</ul>
	<li>Measure the objective stigmation. <code>Measure</code></li>
	<li>Correct the objective stigmation. <code>Correct</code></li>
</ol>

### Part 5 - Focus Determination
<ol>
	<li>Activate the Gatan camera. <code>View</code></li>
	<li>Determine the correction from Sherpa (the defocus used is in the Sherpa window; the set defocus is listed in the current optics parameters on the microscope computer)</li>
	<li>Adjust the current defocus by the amount calculated above. This should get you very close to focus.</li>
	<li>Check for focus using the FFT window. It should be quite good. Make fine adjustments if needed using the defocus knob on control panel.</li>
	<li>If the defocus setting at focus is more than 0.2 microns from what is expected, return to Part 3 - Initialize Direct Alignments and try again.</li>
	<li>Reset the defocus to 0 using the control panel</li>
	<li>Deactivate the Gatan camera. <code>Stop View</code></li>
</ol>

### Part 6 - Final Astigmatism Correction and ComaFree Alignment
<ol>
	<li>Open the Sherpa window</li>
	<li>Use the control panel to dial in approximately -0.9 um defocus (note: this may vary depending on the magnification being used)</li>
	<li>Measure the objective stigmation. <code>Measure</code></li>
	<li>Correct the objective stigmation. <code>Correct</code></li>
	<li>Correct the coma. <code>Correct</code></li>
	<li>Measure the objective stigmation. <code>Measure</code>. Correct if needed.</li>
	<li>Cycle between the objective stigmation and coma-free alignment until both are accurate and the errors are small.</li>
	<li>The last step should be measurement of the objective stigmation with the astigmatism measuring 1 nm or less.</li>
</ol>

### <div style='background:pink; color:darkred'>Part 7 - Import Settings to EPU - CRITICAL!</div>
<ol>
	<li>Set the Data Acquisition optics parameters. <code>EPU >> Preparation >> Data Acquisition >> GET</code></li>
	<li>Set the Autofocus optics parameters. <code>EPU >> Preparation >> Autofocus >> GET</code></li>
	<li>Write down or photograph the current Hole Eucentric optics paramters. Once you have written them down, <code>EPU >> Preparation >> Hole Eucentric >> GET</code>. Then manually repopulate the Hole Eucentric parameters.
</ol>

<hr style='margin:35px 0'>

## Step 9 - Final Touches and Start
<ol>
	<li><div style='background:pink; color:darkred'><B>CRITICAL - Double Check the Following:</B>
		<ul>Microscope computer - The stage rotation (alpha) is set to zero. Stage >> Popout >> alpha</ul>
		<ul>Microscope computer - The Turbo pump is OFF.</ul>
		<ul>Microscope computer - The 100 um objective aperature is inserted.<BR>Note:  If the objective was not inserted, it is necessary to redo the direct alignments.</ul>
		<ul>Gatan computer - The camera mode is Counted.</ul>
	</div></li>
	<li>Start the automated acquisition <code>EPU >> Automated Acquistion >> Start Run!</code></li>
</ol>

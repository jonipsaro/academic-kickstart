---
authors:
- admin
categories: []
date: "2019-08-21T00:00:00Z"
draft: false
featured: false
image:
  caption: 'Titan Krios Data Acquisition Setup'
  focal_point: "top"
  preview_only: false
lastmod: "2019-11-19T00:00:00Z"
projects: [Outreach]
title: 'Cryo-EM Data Acquisition with EPU'
subtitle: 'Quick Reference for cryo-EM data acquisition using EPU on the Titan Krios  :snowflake:'
summary: Quick Reference for cryo-EM data acquisition using EPU on the Titan Krios
tags:
- Cryo-EM
- Instructions
- Protocols
---

## Overview

Setting up data collection can be divided into these main steps:
<ol>
	<li>Run Setup - Gain Reference Collection and GIF Tuning</li>
	<li>Image Shift Calibration</li>
	<li>Atlas Generation</li>
	<li>Set Up the EPU Session</li>
	<li>Perform Direct Alignments</li>
	<li>Final Touches</li>
</ol>

<hr>

## Step 0 - Run Setup
### Part 1 - Gain Reference Collection --- THIS PART IS NOT YET COMPLETE
<div style='background:pink; color:darkred'><B>CRITICAL:</B>  For Gain Reference Collection, Data Acquisition parameters must already be set.</div>
<ol>
	<li>Navigate to an empty grid square.</li>
	<li>Check that the acquisiton parameters in EPU are reasonable.  <code>Preparation >> Data Acquisition >> Preview</code></li>
	<li>On the microscope computer, set the <code>Aperature</code> to 150.</li>
	<li>Using the microscope control panel, set the spot size (4 for 200 kV; 3 for 300 kV).</li>
	<li>Prepare gain references on the Gatan Computer.  <code>Camera >>  Prepare Gain References</code>.  Click <code>OK</code></li>
	<li>On the microscope computer, lift the screen and check for fringes.  If fringes are present, adjust the beam intensity using the control panel knobs.</li>
	<li>Insert the screen.</li>
	<li>Follow the instructions when prompted by the Gatan Computer.  You will need to adjust the beam intensity.  Use the numbers on the Gatan display and adjust to the required value.</li>
	<li>Additionally, collect a dark reference.  When doing this <code>Close column valves</code>.</li>
	<li>When the gain reference if completed, open the Gatan camera.  <code>View</code></li>
	<li>Also activate the FFT window.</li>
	<li>Both the main window and the FFT should be flat, indicating the gain reference is correct.</li>
<ol>

### Part 2 - Tune the GIF
<ol>
	<li><code>Center ZLP</code>.</li>
	<li><code>View</code>.  This should again be flat.</li>
	<li><code>Stop View</code>.</li>
	<li>Using the microscope computer, put in the condenser aperature.  If needed, the position of the slit can be moved manually.  To do so, click on the Gatan Filter Control Window (<code>Gatan >> Windows >> FIlter Control</code>) and use the keyboard arrow keys to adjust.</li>
	<li><code>Stop View</code></li>
	<li>Set the spot size to 5 using the microscope control pad.</li>
	<li>On the Gatan computer <code>Tune GIF >> Full</code>.</li>
</ol>

## Step 1 - Image Shift Calibration
<div style='background:pink; color:darkred'><B>CRITICAL:</B>  For the Image Shift Calibration, it is obligatory that all Preparation modes (Atlas, Grid Square, Hole/Eucentric Height, Data Acquisition/Auto Focus) are already set.</div>

### Part 1 - Grid Square Selection
<div style='background:lemonchiffon; color:goldenrod'>Note:  This square will take a fair amount of radiation damage, so it is important that it is not a square that you plan to use for data acqusition.  A square that has a few empty holes and some interestingly-shaped contamination is ideal.</div>

### Part 2 - Locate and Navigate to a Landmark
<ol>
	<li>Navigate to <code>Preparation >> Atlas</code>.</li>
	<li>Select a grid square that has an obvious landmark.  Usually a piece of contaimination with a distinctive shape is desirable.  If collecting on Lacey carbon grids, contamination near to an interesting carbon pattern is even better.  Move the stage to that grid square and landmark. <code>(Right click) Move stage here</code>.</li>
	<li>Check the grid square.  <code>Preparation >> Grid Square >> Preview</code>.</li>
	<li>Determine the eucentric height  <code>Auto Functions >> Hole/Eucentric Height >> Auto-eucentric by beam tilt.</code></li>
	<li>Set the microscope parameters to match the Data Acqusition settings. <code>Preparation >> Data Acquisition >> Set</code>.</li>
	<li>Move to the microscope computer.  Lift the screen.  Use the control panel joystick to make fine manipulations onto the landmark.</li>
</ol>

### Part 3 - Perform Image Shift Calibration
<ol>
	<li>Select <code>Preparation >> Tasks >> Calibrate Image Shifts</code>.</li>
	<li>The Image Shift Calibration module will walk through the calibration.  To continue, click <code>Proceed</code>.</li>
	<li>When a new setting is applied and an image is generated, adjust the calibration center by double-clicking on the corresponding spot on the right image panel.  It is advisable to re-acquire this image before moving on.  When satisfied, click <code>Proceeed</code>.</li>
</ol>

<hr>

## Step 2 - Generate the Atlas

<ol>
	<li>Select <code>Atlas >> Session Setup</code>.</li>
	<li>Enter a path for the data (the folder will be created automatically).  Images should be saved as <code>MRC</code> format.</li>
	<li>Begin the atlas acquisition.</li>
</ol>

<hr>

## Step 3 - Set up the EPU Session

<ol>
	<li>Select <code>EPU >> Session Setup</code>.</li>
	<li>Enter the setup parameters.  Enter a path for the data (the folder will be created automatically).  Images should be saved as <code>Unnormalized Packed</code> and <code>MRC</code> format.  Make sure that the acqusition type is Manual.  Make sure to select the correct grid type and indicate the hole paramters (if applicable).</li>
	<li>Still in the EPU window, use the <code>Atlas</code> tab to select a grid square.</li>
	<li>Determine the eucentric height.  Select <code>Preparation >> Hole/Eucentric Height >> Auto Eucentric Height by beam tilt</code>.</li>
	<li>It can be useful to take an image of an empty hole in the grid for subsequent determination of approximate ice thickness.  This can be done by centering on the empty hole, then selecting <code>Preparation >> Data Acquisition >> Acquire</code>.  Note the dose (lower right window).</li>
	<li>Check the grid square quality.  Move to a hole that could be potenially useful for collection.  Then collect an image <code>Preparation >> Data Acquisition >> Acquire</code>.</li>
	<li>If the ice thickness is appropriate (usually ~80% of the empty hole dose is desireable), this square can be used for data collection.  <code>EPU >> Atlas >> (Right Click on Grid Square) Add Square</code>.</li>
	<li>Generate the pattern of images to be collected.  <code>EPU >> Hole Selection >> Generate Pattern</code>.  Use the brush too to manually remove i) empty holes/regions, ii) significant contamination, iii) thick ice near the edges of each grid square.  Some of this can be automated using the controls in the top and right panels.</li>
	<li>Add the collection and focus parameters.  Defocus values that are typically used begin around -3.2 microns and continue to -1.4 microns.  To add these, enter the desired defocus value and click on the :page_facing_up: icon next to the entry field.  It should now be present in the defocus values list above.  Valeus can be removed by selecting them and clicking on the :wastebasket: icon.  Be sure to double check these and ensure that the values are negative!</li>
	<li>Set the following parameters for Lacey carbon grids:
		<ul>
			<li>Spacing = 1 um</li>
			<li>Autofocus Recurrance = 5 um</li>
			<li>Delay after Stage Shift = 11 seconds</li>
		</ul>
	</li>
	<li>Alternatively, set the following parameters for Quantifoil grids:
		<ul>
			<li>Minimum Image Shift = 9 um</li>
			<li>Delay after Image Shift = 1.5 seconds</li>
			<li>Delay after Stage Shift = 2 seconds</li>
		</ul>
	</li>		
	<li>If collecting from Quantifoil grids, beam shift collection can dramatically speed up acquisiton.  Use the <code>EPU >> Generate Template</code> to set this up.  Be sure to include one shot for Autofocus.  If you are unsure how to make an appropriate template, ask the Facility Manager.</li>
	<li>Return to the <code>EPU >> Atlas</code> view.  The grid square should now display the eucentric height determined earlier and the number of images to be collected should be indicated in the right-most panel.</li>
	<li>Repeat this process beginning at item 3.  It is not necessary to re-enter the collection  (item 9) as these should be preserved from earlier.  Continue adding more grid squares until there are enough for the desired collection time.</li>
</ol>

<hr>

## Step 4 - Perform Direct Alignments

### Part 1 - Grid Square Selection
<div style='background:lemonchiffon; color:goldenrod'>Note:  As with the Image Shift Calibration, this square will take a fair amount of radiation damage, so it is important that it is not a square that you plan to use for data acqusition.  A square that has a few empty holes and some interestingly-shaped contamination is ideal.</div>
<ol>
	<li>Use EPU to navigate to a new grid square.  Move to an empty hole for best contrast.</li>
	<li>Determine the eucentric height. <code>Auto functions >> Hole Eucentric >> Eucentric Height by Beam Tilt</code></li>
</ol>

### Part 2 - Initial Focus Determination
Overview:  This part of the protocol will serve to tune the eucentric height and find focus.  It will be refined in Part 5.
<ol>
	<li>Lift the screen</li>
	<li>Set the eucentric height manually
		<ol type="a">
			<li>Set the microscope optics to the Data Acquisition setting. <code>Preparation >> Data Acquisition >> SET</code></li>
			<li>Use the control panel joystick to move to an area where you can see the edge of the hole and some carbon.</li>
			<li>Set the alpha angle to +/- 20 degrees.  The stage should rotate.  The goal is to adjust the Z-height of the stage such that changing alpha +/- 20 degrees keeps the center of the image in place.  Z-height can be adjusted using the control panel (rightmost buttons).</li>
			<li>When adjusting the height, it is likely necessary to toggle between alpha=0 and alpha=20.</li>
			<li>When satisfied with the Z-height adjustment, make sure to set alpha back to 0 degrees.</li>
		</ol>
	</li>
	<li>Use the control panel joystick to move the beam over some carbon.</li>
	<li>Find focus using the Gatan computer
		<ol type="a">
			<li>Insert the screen</li>
			<li>Activate the Gatan camera. <code>View</code></li>
			<li>Using the FFT window, find focus.  Use the defocus knob on the control panel and adjust until no Thon rings are apparent.</li>
			<li>Reset the defocus to 0 using the control panel</li>
			<li>Deactivate the Gatan camera. <code>Stop View</code></li>
		</ol>
	</li>
</ol>

### Part 3 - Initialize Direct Alignments
<ol>
	<li>Lift the screen</li>
	<li>Activate the direct aligments menu (bottom right)</li>
	<li>Sequentially adjust the alignments:
		<ol type="a">
			<li>nP beam tilt ppX (use multifunction X to minimize movement)</li>
			<li>nP beam tilt ppY (use multifunction X to minimize movement)</li>
			<li>beamshift center (use both knobs; center on the green circle)</li>
			<li>rotation center (minimize movement; use both knobs)</li>
		</ol>
	</li>
</ol>

### Part 4 - Initial Astigmatism Correction and Coma-Free Alignment
<ol>
	<li>Open the Sherpa window</li>
	<li>Use the control panel to dial in approximately -1.1 um defocus (note: this may vary depending on the magnification being used)</li>
	<li>Check and/or set the following parameters:</li>
		<ul>Type: EF-CCD</ul>
		<ul>Exposure time [s]: 3.0</ul>
		<ul>Binning: 2</ul>
		<ul>Readout area: Full</ul>
		<ul>Electron counting: checked</ul>
		<ul>Autofocus to [um]: -1.0, checked</ul>
	<li>Measure the objective stigmation. <code>Measure</code></li>
	<li>Correct the objective stigmation. <code>Correct</code></li>
</ol>

### Part 5 - Focus Determination
<ol>
	<li>Lift the screen</li>
	<li>Find/adjust focus using the Gatan computer
		<ol type="a">
			<li>Lift the screen</li>
			<li>Activate the Gatan camera. <code>View</code></li>
			<li>Determine the correction from Sherpa (the defocus used is in the Sherpa window; the set defocus is listed in the current optics parameters on the microscope computer)</li>
			<li>Adjust the current defocus by the amount calculated above.  This should get you very close to focus.</li>
			<li>Check for focus using the FFT window. It should be quite good.  Make fine adjustments if needed using the defocus knob on control panel.</li>
			<li>Reset the defocus to 0 using the control panel</li>
			<li>Deactivate the Gatan camera. <code>Stop View</code></li>
		</ol>
	</li>
</ol>

### Part 6 - Final Astigmatism Correction and ComaFree Alignment
<ol>
	<li>Open the Sherpa window</li>
	<li>Use the control panel to dial in approximately -1.1 um defocus (note: this may vary depending on the magnification being used)</li>
	<li>Measure the objective stigmation. <code>Measure</code></li>
	<li>Correct the objective stigmation. <code>Correct</code></li>
	<li>Correct the coma. <code>Correct</code></li>
	<li>Measure the objective stigmation. <code>Measure</code>.  Correct if needed.</li>
	<li>Cycle between the objective stigmation and coma-free alignment until both are accurate and the errors are small.</li>
	<li>The last step should correction of the objective stigmation.</li>
	<li>Insert the screen.</li>
</ol>

### <div style='background:pink; color:darkred'>Part VII - Import Settings to EPU - CRITICAL!</div>
<ol>
	<li>Set the Data Acquisition optics parameters. <code>EPU >> Preparation >> Data Acquisition >> GET</code></li>
	<li>Set the Autofocus optics parameters. <code>EPU >> Preparation >> Autofocus >> GET</code></li>
</ol>

<hr>

## Step 5 - Final Touches and Start
<ol>
	<li>Center the ZLP. <code>Gatan Window >> Center ZLP</code></li>
	<li>Start the automated acquisition <code>EPU >> Automated Acquistion >> GO!</code></li>
</ol>

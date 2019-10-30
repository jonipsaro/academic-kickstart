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
lastmod: "2019-10-30T00:00:00Z"
projects: [Outreach]
title: 'Cryo-EM Data Acquisition with EPU'
subtitle: 'Quick Reference for cryo-EM data acquisition using EPU on the Titan Krios  :snowflake:'
summary: Quick Reference for cryo-EM data acquisition using EPU on the Titan Krios
tags:
- Cryo-EM
- Instructions
- Protocols
---

## <div style='background:lemonchiffon; color:goldenrod'>IMPORTANT!  THESE NOTES ARE NOT YET COMPLETE, BUT THERE IS A LOT OF USEFUL STUFF HERE!</div>

### Part I - Grid Square Selection
Note:  This square will take a fair amount of radiation damage, so it is important that it is not a square that you plan to use for data acqusition.  A square that has a few empty holes and some interestingly-shaped contamination is ideal.
<ol>
	<li>Use EPU to navigate to a new grid square.  Move to an empty hole for best contrast.</li>
	<li>Determine the eucentric height. <code>Auto functions >> Hole Eucentric >> Eucentric Height by Beam Tilt</code></li>
</ol>

### Part II - Initial Focus Determination
Overview:  This part of the protocol will serve to tune the eucentric height and find focus.  It will be refined in Part V.
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
			<li>Lift the screen</li>
			<li>Activate the Gatan camera. <code>View</code></li>
			<li>Using the FFT window, find focus.  Use the defocus knob on the control panel and adjust until no Thon rings are apparent.</li>
			<li>Reset the defocus to 0 using the control panel</li>
			<li>Deactivate the Gatan camera. <code>Stop View</code></li>
		</ol>
	</li>
</ol>

### Part III - Initialize Direct Alignments
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

### Part IV - Initial Astigmatism Correction and Coma-Free Alignment
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

### Part V - Focus Determination
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

### Part VI - Final Astigmatism Correction and ComaFree Alignment
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
	<li>Set the Data Acquisition optics parameters. <code>EPU >> Preparation >> Data Acquisition >> GET</code>.</li>
	<li>Set the Autofocus optics parameters. <code>EPU >> Preparation >> Autofocus >> GET</code>.</li>
</ol>

### Part VIII - Final Touches and Start
<ol>
	<li>Center the ZLP. <code>Gatan Window >> Center ZLP</code></li>
	<li>Start the automated acquisition <code>EPU >> Automated Acquistion >> GO!</code></li>
</ol>

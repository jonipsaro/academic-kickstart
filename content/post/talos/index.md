---
authors:
- admin
categories: []
date: "2019-08-09T00:00:00Z"
draft: false
featured: false
image:
  caption: 'Protocol overview and tips for using the Talos for Negative Stain EM'
  focal_point: "top"
  preview_only: false
lastmod: "2019-08-09T00:00:00Z"
projects: [Outreach]
title: 'Negative Stain EM Imaging with the Talos'
subtitle: 'Step-by-step cheat sheet for working with the Talos  :microscope:'
summary: Step-by-step cheat sheet for working with the Talos
tags:
- TEM
- Instructions
- Protocols
---


### Overview
This protocol is to serve as a basic outline for collecting screening images on the Talos TEM.
Note that staining protocols have not yet been included.
Also note that advanced settings for collecting data with minimal dosage are not yet included.

### Initial Setup
<ol>
	<li>Before beginning, make sure that the column valve is closed.</li>
	<li>Set up the cold trap.<br><i>Note:  The dewar should be checked every 1-2 hours and refilled as needed.</i></li>
		<ol type="a">
			<li>Fill the small nitrogen dewar.</li>
			<li>Install the dewar and insert the copper bundle.  Be careful to avoid too much splashing.</li>
			<li>Cover the dewar with its foam cap.</li>
		</ol>
	<li>Turn on the filament. This takes ~10 minutes to warm up.  <code>Setup >> Filament</code>.</li>
	<li>Turn on the Turbo pump.  Wait until this finishes to proceed.  <code>Setup >> Turbo</code>.</li>
	<li>Make sure the cryobox (decontaminatior) is inserted.  <code>Vacuum >> [popout] >> Cryobox</code>.</li>
</ol>

### Sample Insertion
<ol>
	<li>Make sure the column valves are closed.</li>
	<li>Remove the sample holder wand.
		<ol type="a">
			<li>Pull the wand out until it stops.</li>
			<li>Rotate the wand clockwise so that the pin (originally at 12 o'clock) is at 5 o'clock.</li>
			<li>Pull the wand out fully and place it in the holding station.</li>
		</ol>
	</li>
	<li>Recover any currently-loaded grid and place the new grid in the holder.</li>
	<li>Insert the sample holder wand
		<ol type="a">
			<li>Insert the wand such that the pin is approximately at 2 o'clock.</li>
			<li>Rotate the wand clockwise smartly until it is at the 5 o'clock position.</li>
			<li>Immediately push the wand in approximately 1/4 inch until it stops.</li>
			<li>Wait for the air lock protocol to complete (this is automatic, check the <code>Setup >> Vacuum</code> menu for the countdown).</li>
			<li>Rotate the wand such that the pin will be at the 12 o'clock positon.</li>
			<li>Allow the vacuum to pull the wand into the instrument.  Provide gentle resistance to control the rate of insertion.</li>
			<li>Tap Tap (for good luck :four_leaf_clover:)</li>
		</ol>
	</li>
	<li>Wait until the vacuum has recovered.  This should only take a couple of moments.</li>
	<li>Confirm the specimen holder type (<code>Single Tilt</code>).</li>
</ol>

### Sample Screening
<ol>
	<li>Open the column valve.  <code>Setup >> (Col. Valve Closed)</code>.<br>
	Note:  The Turbo will automatically turn off when you open the column valve.</li>
	<li>Make sure that the user interface is set to Search mode.  <code>Low Dose >> Search</code>.</li>
	<li>Make sure that the screen is inserted.  <code>Flucam Viewer Window >> Insert Screen</code>.</li>
	<li>Use the control panel <code style='color:royalblue;background-color:#F6F6FF'>joystick</code> to inspect the grid while at low magnification (~500x).  The beam spread and position can be adjusted using the Intensity and Track Ball controls on the control panel, respectively.</li>
	<li>Use the control panel interface to set the <code style='color:royalblue;background-color:#F6F6FF'>Magnification</code> to SA 2600x.</li>
	<li>Set the eucentric height
		<ol type="a">
			<li>Check the eucentric height by alternating the tilt angle (alpha) from 0 to 20 degrees.  <code>Search >> [popout menu] >> Set Alpha</code>.</li>
			<li>Adjust as needed using the <code style='color:royalblue;background-color:#F6F6FF'>Z-axis adjustment buttons</code> on the control panel.  The goal is the center of the viewfinder to remain on the same spot when alternating between the tilt angles.</li>
		</ol>
	<li>Zoom in as needed (<code style='color:royalblue;background-color:#F6F6FF'>Magnification</code> on the control panel) and inspect for good regions of the grid.  <code>Low Dose >> Focus</code>.</li>
	<li>Find focus by using the TEM Imaging and Analysis window.
		<ol type="a">
			<li>Retract the screen (<code>Flucam Viewer Window >> (Insert Screen)</code>).</li>
			<li>Activate the CCD/TV Camera.  <code>Low Dose >> CCD/TV Camera >> [popout] >> Mode >> Continuous</code>.</li>
			<li>Turn on the FFT window.  <code>FFT/IFFT >> FFT</code>.</li>
			<li>Find focus using the <code style='color:royalblue;background-color:#F6F6FF'>Focus</code> knob until the presence of zeros in the FFT is at a minimum.</li>
			<li>Reset the defocus using the <code style='color:royalblue;background-color:#F6F6FF'>control panel shortcut (usually R2)</code>.</li>
			<li>Adjust to ~1 um defocus (-1.00 um) using the <code style='color:royalblue;background-color:#F6F6FF'>Focus</code> knob.</li>
			<li>Change the CCD Mode to Single.  <code>Low Dose >> CCD/TV Camera >> [popout] >> Mode >> Single</code>.</li>
			<li>Save the image by right-clicking and specifying the file name/path</li>
		</ol>
	<li>Low dosage tab default settings:
		<table>
			<tr><th>Mode</th>		<th>Zoom</th>		<th>Spot Size</th>	<th>Intensity</th>		<th>Other</th></tr>
			<tr><td>Search</td>		<td>2600x</td>		<td>6</td>			<td>80</td>				<td>x: 0.0 um; y: 0.0 um</td></tr>
			<tr><td>Focus</td>		<td>150000x</td>	<td>6</td>			<td>40</td>				<td>1.6 um; 90&deg;</td></tr>
			<tr><td>Exposure</td>	<td>150000x</td>	<td>6</td>			<td>40</td>				<td>1.0 seconds</td></tr>
		</table>
	</li>
	<li>Continue this process around the grid.  Eucentric height should be re-determined for each grid square, but only defocus needs to be re-determined for spots within a grid square.</li>
	<li>When finished with a grid, reset all settings.
		<ol type="a">
			<li>Reset the magnification.  <code>Low Dose >> Search</code>.</li>
			<li>Reset the holder position.  <code>Search >> Reset Holder</code>.</li>
			<li>Remove the screen.  <code>Flucam Viewer >> (Insert Screen)</code>.</li>
			<li>Close the column valve.  <code>Setup >> Col. Valve Closed</code>.</li>
			<li>If more grids are to be screened, activate the Turbo pump.  <code>Setup >> Turbo pump</code>.</li>
		</ol>
	<li>Repeat the Sample Insertion and Sample Screening steps for each grid.</li>
</ol>

### Shutdown
<ol>
	<li>Make sure the column valves are closed, the grid holder position is reset, and that the screen is out.</li>
	<li>If desired, remove the current grid using the <i>Sample Insertion</i> protocol above.  Replace the sample holder wand once the Turbo pump vaccum is restored.</li>
	<li>Turn off the Filament.  <code>Setup >> Filament</code></li>
	<li>Turn off the Turbo pump.  <code>Setup >> Turbo</code></li>
	<li>Remove the nitrogen dewar.</li>
	<li>Start the cryocycle.  <code>Cryo >> Vacuum >> [popout] >> Cryo >> Cryocycle</code>.<br>
		Note:  This will start the Turbo pump.  Some vacuum may be lost.  This is ok.
	</li>
</ol>
---
authors:
- admin
categories: []
date: "2019-08-21T00:00:00Z"
draft: false
featured: false
image:
  caption: 'Titan Krios - Changing Energy'
  focal_point: "top"
  preview_only: false
lastmod: "2019-11-19T00:00:00Z"
projects: [Outreach]
title: 'Cryo-EM Setup for Changing Energy'
subtitle: 'Quick Reference for Changing Energy on the Titan Krios  :snowflake:'
summary: Quick Reference for Changing Energy on the Titan Krios
tags:
- Cryo-EM
- Instructions
- Protocols
---

## Overview

There are three main places that energy settings must be imported:
<ol>
	<li>Microscope FEG Registry</li>
	<li>Microscope Alignments</li>
	<li>Gatan</li>
</ol>

<hr>

## Step 1 - Microscope Energ and FEG Registry
<ol>
	<li>Close the column valves.</li>
	<li>Close any instance of EPU that is running.</li>
	<li>Set the energy. <code>High Tension >> 200 kV</code>.  If you expand the High Tension tab, you will see the high tension move to 200 kV and stabilize.</li>
	<li>Set the FEG Controls.  <code>FEG Control >> Gun Lens</code>.  Set the gun lens (5 for 200 kV; 4 for 300 kV).  Confirm that the settings have been applied in the scope settings window.</li>
	<li>Load the FEG Registry.  <code>FEG Register</code>.  Select the appropriate registry (e.g. 200 kV nP for 200 kV settings).</li>
</ol>

## Step 2 - Load Alignments
<ol>
	<li>Open the <code>Alignments</code> tab.</li>
	<li>Select the appropriate alignments file (e.g. 200 kV_MC for 200 kV settings).</li>
	<li>Available settings will propagate in the "available" window.  Select all of them by clicking on one, then hitting <code>Ctrl+A</code>.  Click the <code><</code> arrow to move the selected parameters to thos ebeing used.</li>
	<li>Click <code>Apply</code>.</li>
	<li>Wait overnight for the microscope to stabilize before collecting data.  Some preliminary work can be done once the energy has stabilized.</li>
	<li>Perform a quick beam center.  Lift the screen.  <code>Direct Alignments >> Beam Center</code>, adjust with Multifunction X and Y on the control pad, then click <code>Done</code> on the Direct Aligments tab.
</ol>

## Step 3 - Setup Gatan Camera
<ol>
	<li>Activate the Filter Control Menu.
		<ol type="i">
			<li><code>Help >> User Mode >> Power User.</code></li>
			<li><code>Window >> Filter Control</code></li>
		</ol>
	</li>
	<li>Save the current settings.  Look for the :floppy_disk: icon near the bottom of the Gatan Filter Control window.</li>
	<li>Change the energy as appropriate.</li>
	<li>Load the settings (:open_file_folder: icon near the bottom of the Gatan Filter Control Window).</li>
	<li>Center the ZLP.</li>
</ol>



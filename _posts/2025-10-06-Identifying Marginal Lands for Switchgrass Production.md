---
title: "How to Run Daycent"
date: 2025-10-06
tags: [Switchgrass, Marginal Lands, GIS, DayCent, Bioenergy]
---

I am currently working on identifying marginal lands suitable for switchgrass production across Illinois. This project combines long-term cropland data, soil characteristics, and productivity indices to pinpoint areas with limited potential for conventional crops but strong suitability for perennial bioenergy grasses. The goal is to map and evaluate these sites as part of a broader sustainability assessment using the DayCent model. In future posts, I will share step-by-step details of the spatial workflow, data layers used, and how the results will be integrated into model simulations and economic analysis.

**How to get Daycent**

# How to run Daycent for individual site?"
Download DayCent [here](https://www.soilcarbonsolutionscenter.com/daycent)
[Download Daycent] (https://www.soilcarbonsolutionscenter.com/daycent)
**W1. The model executable**

This is the main DayCent program — the .exe file (daycent491.exe).
It’s the compiled binary that actually runs the model. Simply call it using a command (Below code). The .exe reads all input files and produces output files (daily, monthly, or yearly).

**2. The library (*.100) files**

These are core parameter files that define the biological and physical parameters used by DayCent for:

Crops (crop.100)
Fertilizers (fert.100)
Cultivation and tillage (cult.100)
Other management or ecological processes

They act like “lookup tables” for the model.
For example:

crop.100 defines species-specific properties like growth rates, carbon allocation, and phenology.
fert.100 defines fertilizer types and their N contents.
cult.100 defines tillage operations and soil disturbance depth.
These files don’t change by location — they’re shared across simulations and are stored in a library folder.

**3. Site-specific input files**

These define the unique environmental and management setup for each simulation site. They include:

{site}.100 — basic site parameters such as soil layer depths, texture, slope, latitude, and longitude.
Sometimes this information is divided into:
soils.in — soil physical and chemical properties
sitepar.in — site-level parameters (e.g., latitude, soil depth, elevation)
{weather}.wth — daily weather data (year, day, Tmax, Tmin, precipitation, etc.)
{schedule}.sch — the management schedule describing all planting, harvesting, fertilization, and tillage events for the simulation period.

Together, these files define the boundary conditions for a specific site.

**4. outfiles.in**

This tells DayCent which output variables to record and at what frequency (daily, monthly, yearly).
You can enable or disable certain output streams such as:

summary.out
harvest.out
soc.out
nflux.out

It’s useful for reducing unnecessary output files and speeding up simulations.

**5. File organization and calling the model**

There’s no single “correct” file structure, but the simplest setup is:

Copy all required files (exe, 100s, site, weather, sch, outfiles.in) into one folder per simulation.

Then run the model with a system command:

However, this becomes inefficient for regional simulations (hundreds of sites) because each folder would duplicate the same .exe and .100 library files.

To fix this, revision 491 (rev491) introduced the option:

daycent.exe -l {path_to_library_dir}


This lets us store shared .100 and .exe files in a central library folder and point to them during execution.
You can also define these paths in a configuration file, so your scripts can automatically call the correct paths.

**6. Directory structure for large-scale simulations**

When running many sites (e.g., across Illinois or the Midwest), a structured directory helps manage runs.
A typical setup (used by the DDcentutils R package) looks like this:
![Directory structure.png](Directory structure.png)

Each site folder reuses the same .100 and .exe files but contains its own soil, weather, and schedule.
Scripts then automate:

Running equilibrium (spin-up)
Running base historical (base)
Running experimental or scenario (exp)
Moving and renaming outputs so they don’t overwrite each other

7. Scaling up and automation (For detail visit regional analysis post).

For a few sites, this folder setup works fine.
For hundreds or thousands of sites, however:

need batch processing scripts (R, Python, or shell).

It is better to use a database-driven system to manage inputs and outputs (instead of individual folders). DDcent_utils can help automate creation of .sch files, manage runs, and extract outputs.

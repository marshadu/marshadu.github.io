---
title: "APEX Soil Generator Tool"
date: 2026-04-30
---

This web tool generates APEX soil (.SOL) files using SSURGO MUKEY values.

App: https://huggingface.co/spaces/marshadu2024/apex-soil-app

### How it works
- Enter MUKEY values or upload an Excel file (MUKEY column)
- The tool pulls soil properties (layer depth, bulk density, water content, texture, pH, organic matter) from SSURGO
- It formats the data into APEX-compatible .SOL files
- Output is downloadable as a ZIP file

### Interpolation option
- ✔ Checked: generates 10 soil layers using interpolation (smooth profile)
- ❌ Unchecked: uses original SSURGO layers (real data) and pads remaining layers

### What is fixed
- Uses dominant component (highest percentage) per MUKEY  
- Standard APEX structure (10 layers per variable)  
- Default values used for missing parameters  

### Limitations
- Only one soil component per MUKEY (no multi-component mixing)  
- Depends on SSURGO data availability  
- Interpolation may smooth real soil variability  
- Some APEX parameters are fixed/default (not site-specific)  

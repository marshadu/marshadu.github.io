---
title: "APEX Soil Generator Tool"
date: 2026-04-30
---

This tool generates APEX soil (.SOL) files from SSURGO data using MUKEY or coordinates.

<a href="https://huggingface.co/spaces/marshadu2024/apex-soil-app" target="_blank">
  <button style="padding:10px 20px; font-size:16px;">Open APEX Soil App</button>
</a>

App: https://huggingface.co/spaces/marshadu2024/apex-soil-app

### How it works
- Choose input type: **MUKEY or Coordinates**  
- MUKEY: enter values or upload Excel (MUKEY column)  
- Coordinates: enter Latitude/Longitude or upload Excel (LAT, LON columns)  
- Coordinates are automatically converted to MUKEY  
- Soil data is pulled from SSURGO and formatted into APEX .SOL files  
- Output is downloaded as a ZIP  

### Coordinate format

LAT LON  
31.25 -96.98  
30.26 -97.74  
29.76,-95.36

### Mukey format
365471,365472,365473

### Interpolation option
- ✔ Checked: creates 10 layers using interpolation (smooth profile)  
- ❌ Unchecked: uses actual SSURGO layers (real values) and fills remaining layers  

### Important notes
- Uses only the **dominant soil component** (highest % area) per MUKEY  
- Represents main soil, not mixed components  

### Data used
- **From SSURGO:** depth (Z), BD, WP, FC, sand, silt, pH, organic carbon, albedo, hydrologic group  
- **Fixed/default:** WN, SMB, CAC, CEC, TSLA, XIDS, RTN1, ZQT, etc.  

### Limitations
- No multi-component soil mixing  
- Some soil chemistry simplified  
- Interpolation may smooth variability  
- Depends on SSURGO data quality  

### Feedback
If you notice issues or incorrect data:  
**marshadu2024@gmail.com**  

Thank you — this helps improve and debug the tool.

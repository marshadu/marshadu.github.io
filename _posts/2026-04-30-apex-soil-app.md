---
title: "APEX Soil Generator Tool"
date: 2026-04-30
---

This tool generates APEX soil (.SOL) files from SSURGO MUKEY values.

<a href="https://huggingface.co/spaces/marshadu2024/apex-soil-app" target="_blank">
  <button style="padding:10px 20px; font-size:16px;">Open APEX Soil App</button>
</a>

App: https://huggingface.co/spaces/marshadu2024/apex-soil-app

### How it works
- Enter MUKEY(s) or upload an Excel file with a MUKEY column  
- Soil data is pulled from SSURGO (depth, bulk density, water content, texture, pH, organic matter)  
- Output is formatted into APEX .SOL files and downloaded as a ZIP  

### Interpolation option
- ✔ Checked: creates 10 layers using interpolation (smooth soil profile)  
- ❌ Unchecked: uses actual SSURGO layers (real values) and fills remaining layers  

### Important notes
- Each MUKEY can have multiple soil components; this tool uses **only the dominant component (highest % area)**  
- This means results represent the main soil, not all mixed soils in that MUKEY  

### Fixed vs data-driven parameters
- **Pulled from SSURGO (data-driven):**  
  depth (Z), bulk density (BD), wilting point (WP), field capacity (FC), sand (SAN), silt (SIL), pH, organic carbon (WOC), albedo, hydrologic group  

- **Fixed/default values:**  
  WN, SMB, CAC, CEC, and other chemical/biological parameters → set to 0 or standard defaults  
  TSLA, XIDS, RTN1, ZQT, etc. → fixed APEX constants  

👉 These defaults are used because SSURGO does not consistently provide them  

### Limitations
- Does not combine multiple soil components within a MUKEY  
- Some soil chemistry and biological parameters are simplified  
- Interpolation may smooth real soil variation  
- Output depends on SSURGO data quality and availability  

### Feedback
If you notice incorrect data or issues, please contact:  
**marshadu2024@gmail.com**  

Thank you — feedback will help improve and debug the tool.

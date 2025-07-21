# 🗺️ Parcel Mapping GIS Project

### *From Raster to Intelligent Cadastre*

**Author:** Yasser I. Barhoom
**Level:** Master's Degree GIS Course
**Software:** ArcGIS Pro
**Category:** Land Administration / Cadastral Mapping

---

## 🎯 Objective

This project aims to develop a **clean, topologically correct parcel map** from a scanned (raster) cadastral map. The final geodatabase integrates **parcels**, **roads**, **buildings**, and **ownership relationships**, following topology validation rules. This type of project supports **land registration, taxation, and urban planning**.

---

## 🧭 Workflow Overview

### 🔹 Step 1 – Georeferencing the Raster Map

* **Input:** Scanned parcel map
* **Tool Used:** ArcGIS Pro Georeferencing Tool
* **Output:** Aligned raster in UTM projection

---

### 🛣️ Step 2 – Digitizing Roads

* **Feature Class:** `Road`
* **Geometry:** Line
* **Method:** Manual tracing from raster
* **Topology Rules:**

  * Must Not Have Dangles
  * Must Not Have Pseudo-Nodes

---

### 🧱 Step 3 – Digitizing Parcels

* **Feature Class:** `Parcel`
* **Geometry:** Polygon
* **Method:** Manual tracing of parcel boundaries
* **Topology Rules:**

  * Must Not Have Gaps
  * Must Not Overlap

---

### 🏠 Step 4 – Digitizing Buildings

* **Feature Class:** `Buildings`
* **Geometry:** Polygon
* **Placement:** Inside parcels
* **Topology Rule:**

  * Must Be Covered By Parcel

---

### 🧩 Step 5 – Calculating Parcel Neighbors

* **Tool Used:** Spatial Join (Parcel ↔ Parcel)
* **Condition:** `"TARGET_FID" <> "JOIN_FID"`
* **Output:** New field with concatenated neighbor IDs for each parcel

---

### ✅ Step 6 – Topology Validation

* **Topology Layer:** `Parcels_Topology`
* **Validated With:** ArcGIS Pro Error Inspector
* **Applied Rules:**

  * **Roads:** No dangles / pseudo-nodes
  * **Parcels:** No gaps or overlaps
  * **Buildings:** Must be covered by parcels

---

## 📦 Final Outputs

* ✅ Clean, validated **parcel layer** with neighbor relationships
* 🏠 **Building layer** linked to parcels
* 🛣️ **Road network** free of topological errors
* 🗂️ Exported **multi-page parcel atlas**

---

## 📌 Conclusion & Applications

* ✅ Supports **land registration**, **taxation**, and **urban planning**
* 📐 Ready for integration into **Parcel Fabric**
* 🔧 *Future Work:* Integrate **ownership records**, **zoning info**, and **utility infrastructure**

---

### 👨‍💻 **Author**

* **Yasser I. Barhoom**
* **Geospatial Engineer**

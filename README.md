# 3D Airway Segmentation from Chest CT using 3D Slicer

An efficient workflow for extracting and visualizing a patient-specific 3D model of the human tracheobronchial tree from standard chest CT scans using semi-automatic segmentation techniques.

---

## 📌 Overview

This project isolates the primary airway anatomy from surrounding lung tissues by leveraging air-density Hounsfield Unit (HU) ranges. The final output generates a surface-smoothed 3D mesh overlay combined with semi-transparent volume rendering for diagnostic visualization, surgical planning, and 3D printing applications.

<img width="730" height="440" alt="image" src="https://github.com/user-attachments/assets/37cb5192-1343-4eab-8d1e-a424743152f2" />
<img width="730" height="440" alt="image" src="https://github.com/user-attachments/assets/9a78c3aa-324f-47ef-90b9-2f5fd277f2b0" />
<img width="730" height="440" alt="image" src="https://github.com/user-attachments/assets/1a44f03e-c8f0-47d3-8a1a-fda571d09ad8" />
<img width="730" height="440" alt="image" src="https://github.com/user-attachments/assets/85ef394f-90e7-431a-a879-5ae9a0f02699" />

---

## 🎯 Use Cases & Clinical Relevance

* **Procedure Planning:** Maps patient-specific airways for bronchoscopy and stent placement.
* **Diagnostics:** Detects airway narrowings (stenosis), obstructions, and structural anomalies.
* **Education & Communication:** Enhances medical training models and patient consultations.
* **3D Modeling & Simulation:** Exports clean surface geometry for custom 3D printing and CFD airflow simulations.

---

## 📋 Prerequisites & Hardware Requirements

* **Software:** [3D Slicer](https://www.slicer.org/) (v4.10 or newer)
* **Extensions:** `SegmentEditorExtraEffects` (required for Fast Marching)
* **Input Data:** Chest CT volume (DICOM, NRRD, or NIfTI format)
* **Hardware:** Standard workstation or laptop with GPU acceleration for 3D volume rendering

---

## 🛠️ Tools Used (3D Slicer)

* **Segment Editor Module:**
  * **Threshold:** Isolates the air intensity range (-1500 to -350 HU).
  * **Paint:** Places initial seed points inside the trachea.
  * **Fast Marching:** Semi-automatic region growing through connected airways.
  * **Scissors:** Trims non-target background structures.
  * **Smoothing:** Refines and smooths the final 3D surface mesh boundaries.
* **Volume Rendering Module:**
  * **CT-Air Preset:** Provides semi-transparent anatomical context around the segmented airway model.

---

## 🚀 Workflow Steps

1. **Import Volume:** Load the chest CT dataset into 3D Slicer.
2. **Set Threshold:** Open `Segment Editor`, select `Threshold`, and set the range to isolate air voxels (-1500 HU to -350 HU).
3. **Seed & Region Grow:** Use `Paint` to place a seed point inside the trachea, then apply `Fast Marching` to expand through the bronchial tree.
4. **Clean & Smooth:** Use `Scissors` to remove artifacts and apply `Smoothing` to achieve a clean 3D mesh.
5. **3D Context Rendering:** Enable `Volume Rendering` with the `CT-Air` preset for enhanced visualization.
6. **Export:** Export the final segment as an STL or OBJ file for 3D modeling or printing.

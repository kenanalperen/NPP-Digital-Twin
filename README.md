# NPP Digital Twin

![Multi-Robot Collaborative Teleoperation Demo](https://github.com/kenanalperen/NPP-Digital-Twin/raw/main/multi_robot.gif)

**A photorealistic Unity simulation of the Zwentendorf Nuclear Power Plant (NPP)**, developed as a testing and validation platform for autonomous robotic systems operating in hazardous environments.

This digital twin was built from real-world data collected during the [EnRicH 2025](https://enrich.european-robotics.eu/) robotics hackathon and is part of the open-source release of the **RAICAM EU Project**. It supports hardware-in-the-loop testing of UAV and UGV platforms, and multi-operator, multi-robot collaborative teleoperation research, without requiring access to a physical nuclear facility.

> **Associated Papers:**
> 1. *Low-Cost Rapid-Development Air-Ground Robotic Solution for Nuclear Power Plant Inspection*, presented at **IEEE SSRR 2025**. [IEEE Xplore →](https://ieeexplore.ieee.org/abstract/document/11391258)
> 2. *Design and Evaluation of a Collaborative Teleoperation Interface for Multi-Operator Multi-Robot Systems in Challenging Environments*, accepted at the **2026 IEEE Conference on Telepresence (TELE)**, Bristol, UK. [Zenodo →](https://zenodo.org/records/21740502)

---

## Overview

The simulation was constructed by combining:
- An approximate floor plan of the Zwentendorf engine area and turbine hall (provided by competition organisers)
- 3D point cloud data collected by LiDAR sensors mounted on both the UGV and UAV during field trials
- Video footage recorded inside the facility, used to identify objects, materials, and spatial dimensions

The result is a Unity environment that replicates the multi-level halls, steel piping, control consoles, machinery, and narrow passageways of the Zwentendorf NPP. It was originally used to tune control gains, test fail-safes, and validate the full ROS2 software stack before real-world deployment at EnRicH 2025, and has since been extended with mobile robots, a collaborative multi-operator interface, and disaster-response task scenarios for follow-on HRI research.

---

## Figures from the Simulation

1. **Ground Robot (UGV)**
   ![ROV POV](https://github.com/kenanalperen/NPP-Digital-Twin/raw/main/images/ROV_POV.png)
   *Point of view of the Ground Robot navigating the NPP interior*

2. **Aerial Robot (UAV)**
   ![UAV POV](https://github.com/kenanalperen/NPP-Digital-Twin/raw/main/images/UAV_POV_2.png)
   *Point of view of the Aerial Robot during indoor flight*

3. **Operator GUI**
   ![GUI](https://github.com/kenanalperen/NPP-Digital-Twin/raw/main/images/Screenshot%20from%202026-04-10%2011-16-59.png)
   *Four-screen operator GUI for simultaneous multi-operator UAV and UGV teleoperation and monitoring*

4. **Multi-Robot Teleoperation Conditions**
   ![Multi-Robot Conditions](https://github.com/kenanalperen/NPP-Digital-Twin/raw/main/Multi-Robot%20Conditions%20(1).jpg)
   *The three experimental conditions used to evaluate collaborative teleoperation: co-located shared interface, remote shared interface, and co-located individual interfaces*

---

## How to Open the Simulation

### Prerequisites
- [Unity Hub](https://unity.com/download) installed, the simulation was created using editor version 6.4.

---

### Step 1: Download the Unity Package

Download `npp_27_may.unitypackage` from the link below:

📦 **[Download Unity Package](https://uweacuk-my.sharepoint.com/:u:/g/personal/alperen_kenan_uwe_ac_uk/IQAzDemfW5iCRat51aQI4O8HAY1MBfwoaTTKCyvtPCEedw4?e=SP0WWR)**

Alternatively, `prototype_v1.unitypackage` and `Unity_enrich_export.unitypackage` are available directly in this repository via Git LFS.

---

### Step 2: Create a New Unity Project

1. Open **Unity Hub** and click **New Project**
2. Select the **3D (URP)** template
3. Name your project and click **Create**

> ⚠️ **Important:** Use the **3D (URP)** template.

---

### Step 3: Install Required Packages

Two packages are required before importing:

| Package | Purpose | Install Method |
|---|---|---|
| `com.unity.cloud.gltfast` | Import `.gltf` 3D model files | By technical name |
| `Flange` | Inverse kinematics for the robot manipulator | Git URL |

**Install `com.unity.cloud.gltfast`:**
> Window → Package Manager → **+** → *Install package by name*
> Enter: `com.unity.cloud.gltfast`

**Install `Flange` (IK):**
> Window → Package Manager → **+** → *Install package from Git URL*
> Enter: `https://github.com/Preliy/Flange.git#upm`

---

### Step 4: Import the Unity Package

1. In Unity, go to **Assets → Import Package → Custom Package...**
2. Select the downloaded `npp_27_may.unitypackage`
3. Click **Import All** when prompted

---

### Step 5: Open the Main Scene

In the **Project** window, navigate to the `Scenes/` folder and open the main **NPP scene**.

---

### Step 6: Explore the Simulation

Press ▶ **Play** to enter the simulation. You can:
- Switch between **UGV** and **UAV** viewpoints
- Interact with the **Zwentendorf NPP** digital twin
- Run single-operator or multi-operator collaborative teleoperation scenarios

---

### 📎 Additional Resources

| Resource | Description |
|---|---|
| `display_tutorial.mp4` | Video walkthrough of the UI |
| `multi_robot.gif` | Demo of the multi-robot collaborative teleoperation interface |
| `Control_Guidelines (1).pdf` | Robot control instructions |
| `Ground Floor Map of the Nuclear Plant.pdf` | Ground floor map of the NPP |
| `Task Scenario Details.pdf` | Details of the disaster-response task scenarios (radiation source deactivation, rescue dummy retrieval) |
| `Hypotheses (1).pdf` | Hypotheses tested in the collaborative teleoperation user study |
| `Multi-Robot Conditions (1).jpg` | Overview of the three multi-operator teleoperation conditions evaluated |

---

## Related Repositories

This simulation is part of a broader open-source release. The full system includes:

| Component | Repository |
|---|---|
| UAV Platform (Agipix V2) | <https://sasakuruppuarachchi.github.io/agipix/> |
| UGV Platform | <https://github.com/RAICAM-EU-Project/Enrich_UGV> |
| PX4 Onboard Control | <https://github.com/RAICAM-EU-Project/px4_onboard_control> |
| Radiation Sensor Module | <https://github.com/RAICAM-EU-Project/geiger_monitor> |
| **NPP Digital Twin (this repo)** | <https://github.com/kenanalperen/NPP-Digital-Twin> |

---

## Context: EnRicH 2025

The Zwentendorf NPP is a decommissioned nuclear facility in Austria used as a testbed for robotic inspection research. At EnRicH 2025 (June 30 – July 4, 2025), teams were challenged to perform 3D environment mapping, radiation hotspot localisation, valve manipulation, and search-and-rescue tasks within a 30-minute window — without GNSS and with severely attenuated wireless signals due to thick concrete and steel structures.

This digital twin was essential for pre-competition validation: the full ROS2 stack and PX4 SITL model of the drone were tested inside the simulation before any real-world deployment, enabling rapid iteration in a resource-constrained three-week development cycle. Following the competition, the environment was extended into a testbed for studying multi-operator, multi-robot collaborative teleoperation in simulated disaster-response scenarios.

---

## Citations

If you use this simulation in your research, please cite the relevant paper(s):

```bibtex
@inproceedings{tian2025npp,
  title     = {Low-Cost Rapid-Development Air-Ground Robotic Solution for Nuclear Power Plant Inspection},
  author    = {Tian, Changda and Kuruppu Arachchige, Sasanka and Li, Haichuan and
               Garc{\'\i}a C{\'a}rdenas, Juan Jos{\'e} and Raei, Hamidreza and
               Dincer, Enes and Kenan, Alperen and Bremner, Paul and
               Giuliani, Manuel and Neumann, Gerhard and Ajoudani, Arash and
               Tapus, Adriana and Westerlund, Tomi and K{\"a}m{\"a}r{\"a}inen, Joni-Kristian and
               Figueredo, Luis and Watson, Simon and Trahanias, Panos},
  booktitle = {IEEE International Symposium on Safety, Security, and Rescue Robotics (SSRR)},
  year      = {2025}
}
```

```bibtex
@inproceedings{kenan2026collaborative,
  title     = {Design and Evaluation of a Collaborative Teleoperation Interface for Multi-Operator Multi-Robot Systems in Challenging Environments},
  author    = {Kenan, Alperen and Garc{\'\i}a C{\'a}rdenas, Juan Jos{\'e} and
               Bremner, Paul and Giuliani, Manuel and Tapus, Adriana},
  booktitle = {2026 IEEE Conference on Telepresence (TELE)},
  address   = {Bristol, UK},
  year      = {2026},
  doi       = {10.5281/zenodo.21740502}
}
```

---

## Acknowledgements

This work was funded by the European Commission's HORIZON.1.2 Marie Skłodowska-Curie Actions (MSCA) under Grant Agreement No. **101072634**, project [RAICAM](https://raicam.eu/), and by **UK Research and Innovation (UKRI)** grant number **EP/X025004/1**.

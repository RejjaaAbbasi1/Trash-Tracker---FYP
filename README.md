**"Trash-Tracker: A Smart AI-Powered Waste Detection and Dispatching System"** is a Bachelor of Science in Software Engineering final year thesis report. Developed by **Ayesha Shafaqat**, **Rejjaa Qadeer Abbasi**, and **Khurram Bashir Raja** under the supervision of **Engr. Muhammad Awais Rathore** at the **University of Azad Jammu and Kashmir (UAJK), Muzaffarabad**, the project proposes an automated solution to tackle urban solid waste management issues.

Below is a detailed breakdown of the document's core aspects:

---

## 1. Executive Summary & Problem Addressed

* **The Core Problem:** Traditional municipal waste management relies heavily on manual inspections, static collection routes, and reactive public complaints, leading to long delays, unmonitored dump sites, and lack of accountability.


* **The Proposed Solution:** An autonomous, AI-driven waste detection and task-dispatching ecosystem that continuously scans urban areas using satellite imagery, detects waste accumulation automatically, and coordinates real-time cleanup through a structured field dispatch workflow.



---

## 2. Technical Framework & System Architecture

The platform uses a **3-Tier Client-Server Architecture** operating through four main components:

```
[ Google Earth Engine API ] ---> [ FastAPI Backend / YOLOv8 ] ---> [ MySQL Database / Cloud Storage ]
                                             |
                   +-------------------------+-------------------------+
                   |                                                   |
                   v                                                   v
         [ Admin Web Dashboard ]                            [ Worker Mobile App ]
           (React.js - Desktop)                              (Flutter - Mobile)
```[cite: 2]

1. **AI Inference & Detection Engine:**
   * Automatically pulls satellite imagery via the **Google Earth Engine (GEE) API**[cite: 2].
   * Processes high-resolution images (960px) using a custom-trained **YOLOv8** object detection model[cite: 2].
   * Translates detected pixel bounding boxes into precise real-world GPS coordinates (latitude/longitude)[cite: 2].
2. **Backend API (Logic Layer):**
   * Built with **FastAPI**, handling security via **JWT-based authentication** and coordinating data flow between the AI engine, database, and client applications[cite: 2].
3. **Admin Web Dashboard (React.js):**
   * Designed for supervisors to view live color-coded pins on an interactive map, assign tasks to workers, and review proof of completion[cite: 2].
4. **Field Worker Mobile Application (Flutter):**
   * Provides field sanitation workers with assigned job lists, embedded **Google Maps** navigation to exact site coordinates, and mandatory in-app camera capture for proof of cleanup[cite: 2].

---

## 3. Operational Workflow (State Machine)

To enforce strict accountability, every detected issue transitions through a 3-stage status pipeline[cite: 2]:

| State / Pin Color | Status Name | Trigger Event | Responsible Party |
| :--- | :--- | :--- | :--- |
| **Red Pin** | **Detected** | YOLOv8 detects waste accumulation on satellite imagery[cite: 2]. | AI Engine[cite: 2] |
| **Yellow Pin** | **Assigned** | Supervisor selects the hotspot and assigns it to a field worker[cite: 2]. | Admin / Supervisor[cite: 2] |
| **Green Pin** | **Remediated** | Field worker uploads proof photo, and admin approves the work[cite: 2]. | Field Worker & Admin[cite: 2] |

> **Accountability Rule:** Field workers are restricted from uploading photos from the gallery; live camera captures are required to prevent fraudulent submissions[cite: 2].

---

## 4. Key Academic & System Highlights

* **Software Lifecycle:** Developed following the **Agile/Scrum framework** through iterative cycles of planning, building, testing, and deployment[cite: 2].
* **Database Design:** Utilizes a relational **MySQL** schema for structured records (Users, Waste Hotspots, Tasks, Verification Logs) paired with a **Cloud Storage Bucket** for proof imagery archives[cite: 2].
* **Testing Levels:** Evaluated using unit, integration, and system testing methods aligned with the V-Model methodology[cite: 2].
* **Target Geographic Region:** Initial rollout focuses on **Muzaffarabad (e.g., Neelum Road)** and surrounding semi-urban sectors in Azad Kashmir[cite: 2].

---


```

# Ex.No.8 — Detect Hidden Data in Images Using StegExpose

## Aim
To detect hidden (steganographic) data in image files using the **StegExpose** tool and analyze its detection accuracy.

---

## Objective
1. Understand the concept of **steganography** and **steganalysis**.  
2. Learn how to use **StegExpose** to detect hidden data in image files.  
3. Analyze detection results using different images with and without embedded data.

---

## Requirements
- **Operating System:** Windows / Linux  
- **Software:** Java (JDK 8 or above)  
- **Tool:** StegExpose.jar  
- **Input Files:** A set of normal and steganographically modified image files (e.g., `.jpg`, `.png`)

---

## Theory
**Steganography** is the technique of hiding data within non-secret files such as images, audio, or videos.  
**Steganalysis** is the process of detecting such hidden information.

**StegExpose** is an open-source tool that uses multiple steganalysis techniques to detect hidden data in images.  
It combines several detectors such as:
- **Sample Pair Analysis (SPA)**
- **RS Analysis**
- **Chi-Square Attack**
- **Primary Sets**

These techniques analyze pixel patterns and statistical irregularities to determine whether an image contains hidden data.

---

## Algorithm / Procedure
1. **Download and Install StegExpose**
   - Download `StegExpose.jar` from GitHub.
   - Ensure Java Runtime Environment (JRE) or Java Development Kit (JDK) is installed.

2. **Prepare Image Files**
   - Collect two types of images:
     - Original images (no hidden data)
     - Steganographic images (data embedded using tools like OpenStego, SilentEye, etc.)

3. **Run StegExpose**
   - Open the Command Prompt or Terminal.
   - Navigate to the folder containing `StegExpose.jar` and images.
   - Run the following command:
     ```
     java -jar StegExpose.jar <image_folder_path> -t 0.2 -a
     ```
     Here:
     - `<image_folder_path>` = path to your image directory
     - `-t 0.2` = threshold value (default 0.2)
     - `-a` = analyze all images

4. **Observe the Output**
   - StegExpose generates a CSV report named `StegExposeResults.csv`.
   - The report shows:
     - File name
     - Suspiciousness score
     - Classification (Clean / Stego)

5. **Interpret Results**
   - If the suspicion level exceeds the threshold, the image is flagged as **Stego**.
   - Compare detection accuracy for different threshold values.

---

## Sample Command
```bash
java -jar StegExpose.jar C:\Images -t 0.3 -a

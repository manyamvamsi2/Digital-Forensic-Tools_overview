#  Ex No - 06: Use Sleuth Kit to Analyze Digital Evidence

## Description

The **Sleuth Kit (TSK)** is a powerful collection of command-line tools for digital forensics. It allows investigators to analyze disk images and recover digital evidence from various storage devices. This document provides a step-by-step guide to using Sleuth Kit on a Windows machine for a forensic analysis.

---

##  Step 1: Install Sleuth Kit

1.  **Download Sleuth Kit:**
    * Visit the official Sleuth Kit website or use the provided link: `https://drive.google.com/drive/u/1/folders/1ilSFY7Tqn2L7AjQGhq8yJ8kixc_xTU-v`
    * Download the latest stable version of Sleuth Kit compiled for Windows.
2.  **Install Sleuth Kit:**
    * Run the installer and follow the on-screen instructions to install TSK on your Windows machine.

---

##  Step 2: Acquire the Disk Image

Before analysis, a forensic disk image of the storage device (hard drive, memory card, etc.) is required.

1.  **Create Disk Image:**
    * Use a forensic imaging tool like **FTK Imager** or **`dd`** to create a bit-by-bit copy of the evidence.
    * Ensure the image is in a format supported by Sleuth Kit, such as **`.dd`**, **`.raw`**, **`.img`**, or **`.E01`**.
2.  **Download Evidence Files (for this exercise):**
    * Download the following sample files from the Google Drive link provided:
        * `4Dell Latitude CPi.E01`
        * `4Dell Latitude CPi.E02`

---

##  Step 3: Mount the Disk Image (Optional)

Mounting the image can simplify navigating the file system in a graphical environment.

* **Mount the Image:** Use a tool like **OSFMount** to mount the forensic image as a virtual, read-only drive on your Windows system.
* ***Note:*** *This step is optional but can make file system navigation easier.*

---

##  Step 4: Analyze the File System

Use the Sleuth Kit command-line tools to examine the file system structure and content.

1.  **Navigate to the Sleuth Kit Directory:**
    ```bash
    # Open Command Prompt (CMD) and change directory to the TSK installation path
    cd "C:\Program Files (x86)\sleuthkit-4.14.0-win32\bin"  
    ```
    <img width="1480" height="746" alt="image" src="https://github.com/user-attachments/assets/7a809110-3b57-447e-a19d-a65f14ecb3a2" />

2.  **Identify File System Type with `fsstat`:**
    ```bash
    fsstat.exe -o 63 "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01"
    ```
    <img width="1911" height="1036" alt="image" src="https://github.com/user-attachments/assets/f8579e3d-d40e-4b5d-94f9-e9a1e0e178d3" />

3.  **List Partitions with `mmls`:**
    ```bash
    mmls.exe "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01"
    ```
    <img width="1372" height="474" alt="image" src="https://github.com/user-attachments/assets/1f22d052-9ed1-4eb2-a6a1-f0ab5afe8f0b" />

    * *Purpose:* Lists the layout and addresses of all partitions within the disk image.
4.  **Analyze File System with `fls`:**
    ```bash
    fls.exe -r -o 63 "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01"
    ```
    <img width="1920" height="676" alt="image" src="https://github.com/user-attachments/assets/c8e24f54-5892-400b-b7ac-46a7f09d089e" />

    * *Purpose:* Recursively lists all files and directories in the file system, providing their metadata (inode) numbers.
5.  **Recover Deleted Files with `icat`:**
    ```css
    icat.exe -o 63  "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01" 11341 > C:\Users\Manya\Downloads\recovered_file_part1.jpg
    ```
    <img width="1388" height="732" alt="image" src="https://github.com/user-attachments/assets/f0fc9678-64b7-4b08-bdf5-37d33faa8f07" />

    * *Purpose:* Extracts a specific file by its **inode number** (found using `fls`) to recover both allocated and unallocated (deleted) files.

---

##  Step 5: Analyze Metadata

Extract and examine file metadata to gather crucial historical information.

* **View Metadata with `istat`:**
    ```css
    istat.exe -o 63  "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01" 11341 > C:\Users\Manya\Downloads\recovered_file_part2.txt
    ```
    <img width="1498" height="960" alt="image" src="https://github.com/user-attachments/assets/053a2308-b9c4-4729-9ba9-10c11e36e3b7" />

    * *Purpose:* Provides detailed information about a file or directory inode, including **MAC times** (Modified, Accessed, Changed), size, links, and allocation status.

---

##  Step 6: Timeline Analysis (Optional)

Constructing a timeline of file system activity is vital for reconstructing events.

1.  **Generate a Body File:**
    ```css
    fls.exe -m / -r -o 63 "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01" > C:\Users\Manya\Downloads\body.txt
    ```
    <img width="1911" height="1156" alt="image" src="https://github.com/user-attachments/assets/c7630900-1e89-42b0-bb75-3ae6ef15c8b4" />

    * *Purpose:* Creates a body file containing MAC times for all files, formatted for `mactime`.
2.  **Create the Timeline with `mactime`:**
    ```css
    mactime -b body.txt > timeline.txt
    ```
    * *Purpose:* Processes the body file to generate a chronologically ordered timeline of file activity.

---

##  Step 7: Generate a Report

Document the investigative findings in a structured report.

1.  **Compile the Data:** Gather all output files generated during the analysis (`filesystem_info.txt`, `partitions.txt`, `file_list.txt`, `metadata_info.txt`, `timeline.txt`).
2.  **Analyze and Document:** Review the data, highlight key evidence, and write a comprehensive report summarizing the investigative results, methods used, and conclusion.

---

##  Step 8: Finalize and Store Evidence

Ensure the integrity and secure storage of all evidence.

1.  **Archive Evidence:** Use a secure method (e.g., encryption and hashing) to archive the original disk image and the analysis results.
2.  **Store Securely:** Store the archived evidence in a secure location, strictly following the **Chain of Custody** procedures to maintain legal admissibility.

---


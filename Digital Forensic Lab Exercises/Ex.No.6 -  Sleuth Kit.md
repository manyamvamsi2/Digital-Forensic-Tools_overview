0##  Ex No - 06: Use Sleuth Kit to Analyze Digital Evidence

## **Aim:**
To use **The Sleuth Kit (TSK)** command-line tools to analyze a forensic disk image — identify partition layout, enumerate the file system, recover deleted or hidden files, extract file metadata (MAC times), build a timeline of activity, and produce artifacts and reports suitable for forensic investigation.

---
## **Procedure**
####  Step 1: Install Sleuth Kit
##### **Install Sleuth Kit:**

  Download and install **Sleuth Kit** from the official website:  
 [https://sleuthkit.org/download/](https://sleuthkit.org/download/)

---

####  Step 2: Acquire the Disk Image

Before analysis, a forensic disk image of the storage device (hard drive, memory card, etc.) is required.
#####  **Download Evidence Files (for this exercise):**
    * Download the following sample files from the Google Drive link provided:
        * `4Dell Latitude CPi.E01`
        * `4Dell Latitude CPi.E02`

---

####  Step 3: Mount the Disk Image (Optional)

Mounting the image can simplify navigating the file system in a graphical environment.

* **Mount the Image:** Use a tool like **OSFMount** to mount the forensic image as a virtual, read-only drive on your Windows system.
* ***Note:*** *This step is optional but can make file system navigation easier.*

---

####  Step 4: Analyze the File System

Use the Sleuth Kit command-line tools to examine the file system structure and content.

1.  **Navigate to the Sleuth Kit Directory:**
    ```bash
    # Open Command Prompt (CMD) and change directory to the TSK installation path
    cd "C:\Program Files (x86)\sleuthkit-4.14.0-win32\bin"  
    ```
    <img width="600"  alt="image" src="https://github.com/user-attachments/assets/7a809110-3b57-447e-a19d-a65f14ecb3a2" />

2.  **Identify File System Type with `fsstat`:**
    ```bash
    fsstat.exe -o 63 "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01"
    ```
    <img width="600"  alt="image" src="https://github.com/user-attachments/assets/f8579e3d-d40e-4b5d-94f9-e9a1e0e178d3" />

3.  **List Partitions with `mmls`:**
    ```bash
    mmls.exe "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01"
    ```
    <img width="600"  alt="image" src="https://github.com/user-attachments/assets/1f22d052-9ed1-4eb2-a6a1-f0ab5afe8f0b" />

    * *Purpose:* Lists the layout and addresses of all partitions within the disk image.
4.  **Analyze File System with `fls`:**
    ```bash
    fls.exe -r -o 63 "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01"
    ```
    <img width="600"  alt="image" src="https://github.com/user-attachments/assets/c8e24f54-5892-400b-b7ac-46a7f09d089e" />

    * *Purpose:* Recursively lists all files and directories in the file system, providing their metadata (inode) numbers.
5.  **Recover Deleted Files with `icat`:**
    ```css
    icat.exe -o 63  "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01" 11341 > C:\Users\Manya\Downloads\recovered_file_part1.jpg
    ```
    <img width="600" alt="image" src="https://github.com/user-attachments/assets/f0fc9678-64b7-4b08-bdf5-37d33faa8f07" />

    * *Purpose:* Extracts a specific file by its **inode number** (found using `fls`) to recover both allocated and unallocated (deleted) files.

---

####  Step 5: Analyze Metadata

Extract and examine file metadata to gather crucial historical information.

* **View Metadata with `istat`:**
    ```css
    istat.exe -o 63  "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01" 11341 > C:\Users\Manya\Downloads\recovered_file_part2.txt
    ```
    <img width="300"  alt="image" src="https://github.com/user-attachments/assets/053a2308-b9c4-4729-9ba9-10c11e36e3b7" />

    * *Purpose:* Provides detailed information about a file or directory inode, including **MAC times** (Modified, Accessed, Changed), size, links, and allocation status.

---

####  Step 6: Timeline Analysis (Optional)

Constructing a timeline of file system activity is vital for reconstructing events.

1.  **Generate a Body File:**
    ```css
    fls.exe -m / -r -o 63 "C:\Users\Manya\Downloads\4Dell Latitude CPi.E01" > C:\Users\Manya\Downloads\body.txt
    ```
    <img width="400"  alt="image" src="https://github.com/user-attachments/assets/c7630900-1e89-42b0-bb75-3ae6ef15c8b4" />

    
2.  **Create the Timeline with `mactime`:**
    ```css
    mactime -b body.txt > timeline.txt
    ```
   

---

####  Step 7: Generate a Report

Document the investigative findings in a structured report.

1.  **Compile the Data:** Gather all output files generated during the analysis (`filesystem_info.txt`, `partitions.txt`, `file_list.txt`, `metadata_info.txt`, `timeline.txt`).
2.  **Analyze and Document:** Review the data, highlight key evidence, and write a comprehensive report summarizing the investigative results, methods used, and conclusion.

---

####  Step 8: Finalize and Store Evidence

Ensure the integrity and secure storage of all evidence.

1.  **Archive Evidence:** Use a secure method (e.g., encryption and hashing) to archive the original disk image and the analysis results.
2.  **Store Securely:** Store the archived evidence in a secure location, strictly following the **Chain of Custody** procedures to maintain legal admissibility.

---
## Rubrics

| Criteria | Mark Allotted | Mark Awarded |
|---|---:|---:|
| 1. GitHub Activity & Submission Regularity | 3 | |
| 2. Application of Forensic Tools & Practical Execution | 3 | |
| 3. Documentation & Reporting | 2 | |
| 4. Engagement, Problem-Solving & Team Collaboration | 2 | |
| *Total* | *10* | |
## **Result:**
Using Sleuth Kit, the disk image was successfully examined. Key outcomes include:

- The partition table and file system type were identified.  
- A recursive file listing was produced (using `fls`/`mmls`).  
- Deleted/unallocated files were recovered by inode and exported (`icat`).  
- File metadata (MAC times, size, links, allocation status) was extracted using `istat`.  
- A body file was generated and processed with `mactime` to create a chronological timeline of file activity.  
- All outputs (file lists, recovered files, metadata, timeline) were compiled into a forensic report.  
- Evidence and results were archived and hashed to preserve integrity and chain-of-custody for further analysis or legal use.









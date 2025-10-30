<div style="border: 3px solid #4CAF50; border-radius: 12px; padding: 20px; background-color: #f9fff9;">

## Ex.No.1 FTK Imager: A Forensic Imaging Tool 
### Aim:
To acquire both **volatile memory (RAM)** and **non-volatile memory (disk image)** from a target system using **FTK Imager**, ensuring data integrity through proper forensic imaging procedures for further digital forensic analysis.

---
### Acquiring Volatile Memory (RAM) Using FTK Imager

#### Steps to Capture RAM Using FTK Imager
#### 1. Run as Administrator
- Open **FTK Imager** with administrative privileges.  
- Right-click the FTK Imager icon and select **Run as administrator**.


 <p align="center">
 <img width="300"  alt="image" src="https://github.com/user-attachments/assets/739f9871-3976-41c3-be50-b8a8da805b63" />
 </p>



#### 2. Initiate Memory Capture
- In the top menu bar, click **File → Capture Memory...** from the dropdown list.
  
  <p align="center">
  <img width="400"  alt="image" src="https://github.com/user-attachments/assets/8b6eead1-d327-43b7-be00-1b081822ebe5" />
  </p>


#### 3. Configure Destination
A dialog box will appear where you configure where and how the memory will be saved.

- **Destination Path:**  
  Click **Browse** to select a folder on an **external drive** (not the system drive).  

- **Destination Filename:**  
  You can keep the default `memdump.mem` or assign a more descriptive name.

- **Optional: Include pagefile.sys**  
  Check this box to capture `pagefile.sys`, which is virtual memory stored on the disk.  
  > Note: This may increase capture size and duration, but can contain valuable artifacts.

- **Optional: Create AD1 file**  
  Saves the memory dump in an AccessData-specific container file.  
  > Generally not necessary if using tools like **Volatility** for analysis.

 <p align="center">
 <img width="400"  alt="image" src="https://github.com/user-attachments/assets/37f79f46-b802-4028-a10e-659874ebc6e2" />
 </p>




#### 4. Start Capture
- Click the **Capture Memory** button to begin acquisition.


 <p align="center">
 <img width="400"  alt="image" src="https://github.com/user-attachments/assets/1194796f-767d-4e59-8e3a-5962823bdda1" />
 </p>



#### 5. Wait for Completion
- A progress bar will indicate the capture status.  
- Capture time depends on the system’s RAM size.  
- Once finished, the memory dump file will be available in the destination folder.
---


### Acquiring Non-Volatile Memory (Disk Image) Using FTK Imager


#### 1. Start the Process
- In FTK Imager, go to the top menu bar: **File → Create Disk Image...**.


 <p align="center">
 <img width="400"  alt="image" src="https://github.com/user-attachments/assets/479850a5-c2fb-4695-b830-2ab9dc3cc63d" />
 </p>



#### 2. Select Source Evidence Type
A window will appear asking you to choose the source type:

- **Physical Drive:** Images the entire disk, including all partitions, unallocated space, and the Master Boot Record (MBR).  
- **Logical Drive:** Images a specific partition (e.g., C: drive).  
- **Image File:** Converts or copies an existing image file.  
- **Contents of a Folder:** Creates an image of a specific folder only.  

> **Tip:** For full forensic imaging, select **Physical Drive**.
<p align="center">
<img width="400"  alt="image" src="https://github.com/user-attachments/assets/057d577e-5327-44e8-93b5-da3b5fca1fed" /> 
</p>


#### 3. Select the Source Drive
- From the dropdown, choose the physical drive to image (connected via **write-blocker**).  
- Click **Finish**.
 
<p align="center">
<img width="400"  alt="image" src="https://github.com/user-attachments/assets/7174ba85-f638-4ca5-b299-65dc9841d3ea" />
</p>

#### 4. Configure the Image Destination
- Click **Add...** in the "Create Image" window to define the image **format** and **destination**.
  
<p align="center">
<img width="400"  alt="image" src="https://github.com/user-attachments/assets/6b826126-f3d0-4964-8578-4022e3ab6a08" /></p>



#### Options:

- **Image Type:**  
  - **E01 (EnCase Format):** Recommended; includes compression, metadata, and error-checking.  
  - **Raw (DD):** Bit-for-bit copy with no extra features.
<p align="center">
<img width="400"  alt="image" src="https://github.com/user-attachments/assets/e5d806b5-edda-4f57-a60b-e4c58b8fd343" />
</p>



- **Fill in Evidence Item Information:**  
  - Enter case details, examiner name, and description.  
  - This information is stored in the image metadata (important for documentation).
 <p align="center">
<img width="400"  alt="image" src="https://github.com/user-attachments/assets/93d6b429-5dae-4973-82d2-024545b537d5" />
</p>



- **Choose Destination Folder:**  
  - Must be a different drive from the source.  
  - Name the image file (e.g., `Case001_SuspectHDD`).  

- **Image Fragment Size:**  
  - Set a value to split the image into multiple parts.  
  - Set to `0` for a single image file.
  
<p align="center">
<img width="400"  alt="image" src="https://github.com/user-attachments/assets/bba79e8f-512d-4097-b23c-e230cbe166a3" />
</p>




#### 5. Start the Imaging Process
- Click **Finish** to return to the "Create Image" screen.  
- **Check "Verify images after they are created"** to calculate hash values and ensure integrity.  
- Click **Start**.
  
  <p align="center">
  <img width="150"  alt="image" src="https://github.com/user-attachments/assets/739045f1-11bc-474a-9343-2e9aa19ec376" />
  <img width="150"alt="image" src="https://github.com/user-attachments/assets/7bef2114-0017-4a7b-9e19-0f356c3e3236" />
  </p>

  

#### 6. Completion and Hash Verification
- The imaging process may take time depending on the drive size.  
- After completion, FTK Imager verifies the hashes automatically.  
- A final window shows **MD5** and **SHA1** hashes for both the source drive and image.  
- Matching hashes confirm the forensic image’s integrity.

---
## Rubrics

| Criteria | Mark Allotted | Mark Awarded |
|---|---:|---:|
| 1. GitHub Activity & Submission Regularity | 3 | |
| 2. Application of Forensic Tools & Practical Execution | 3 | |
| 3. Documentation & Reporting | 2 | |
| 4. Engagement, Problem-Solving & Team Collaboration | 2 | |
| *Total* | *10* | |

## **Result:**
Successfully captured the **volatile memory (RAM)** and **non-volatile memory (disk image)** of the target system using **FTK Imager**.  
The generated image files were verified using **MD5** and **SHA1** hash values, confirming the **integrity and authenticity** of the acquired forensic data.    

</div>


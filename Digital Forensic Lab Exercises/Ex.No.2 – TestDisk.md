<div style="border: 3px solid #4CAF50; border-radius: 12px; padding: 20px; background-color: #f9fff9;">
  
##  Ex.No.2    TestDisk: Open-Source Data Recovery Tool

### Aim :
To use TestDisk step by step to recover a missing partition and repair a corrupted one.
### Procedure

#### 1. Create a Log File
- Launch TestDisk from your terminal or command prompt using sudo testdisk (or testdisk_win.exe on Windows).

- Select the [Create] option to generate a log file of the recovery session. This is helpful for future reference or troubleshooting.

<p align="center">
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/2364d9ca-bfde-4929-94d3-82dd2b0f35a7" />
</p>


#### 2. Select the Drive to Analyze
- TestDisk will display a list of all detected storage devices.

- Use the Up/Down arrow keys to highlight the drive that contains your lost data.


<p align="center">
<img width="500" alt="image" src="https://github.com/user-attachments/assets/4310ed86-2b64-43bc-a6ec-b0ff07eed18d" />
</p>



- Select [Proceed] to move to the next step.

#### 3. Choose the Partition Table Type
- TestDisk will automatically suggest the most likely partition table type (e.g., Intel/PC, EFI GPT).

- The default value is usually correct. Confirm the selection by pressing Enter.


<p align="center">
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/567649d7-7185-4d09-89bc-d93d249e0aa9" />
</p>



#### 4. Analyze Current Partition Structure
- From the main menu, choose [Analyse] and press Enter.


<p align="center">
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/d7a425c1-97b7-492d-9b1b-67cbe13ad331" />
</p>



- This will display the current partition table and check for errors or missing partitions.

#### 5. Perform a Quick Search
- After the analysis, you will be prompted to perform a [Quick Search].



<p align="center">
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/8abfafbf-5b7b-4ca7-9be4-0889acb81851" />
</p>



- Select it and press Enter to scan the drive for lost partitions.

- Once a partition is found, you can press p to list its files. Deleted files and folders often appear in red.

- Press q to return to the search results.

#### 6. Perform a Deeper Search
- If the Quick Search fails to find your lost partitions, select [Deeper Search].



<p align="center"> 
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/1ee7e8df-acbd-4ce6-8d7c-6b0c81ec809b" />
</p>



- This process can take a long time, as it scans the entire drive, block by block, to find remnants of partition structures.

- Again, use p to preview files and confirm if a found partition is the one you are looking for.

#### 7. Modify Partition Status
- After finding the correct partitions, use the Left/Right arrow keys to set their status.

- Use **Left/Right arrow keys** to change status:  
  - **P**: Primary  
  - ***:** Bootable  
  - **L**: Logical  
  - **D**: Deleted

 

<p align="center">
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/93dea845-3819-4665-ba68-c4830546ffe5" />
</p>



- Ensure that the partitions you want to recover are marked as Primary or Logical (and not deleted).

#### 8. Write the Partition Table
- Once you are confident the partition structure is correct, select [Write] from the menu.



<p align="center">
<img width="500" alt="image" src="https://github.com/user-attachments/assets/78263f06-1ad8-421c-b683-c7d67add03b4" />
</p>

- Confirm the operation by pressing y (for yes). This will write the new partition table to your disk.


<p align="center">
  <img width="500"  alt="image" src="https://github.com/user-attachments/assets/69095f90-5474-4bce-80e5-cc419d84f0ae" />
</p>




- WARNING: This is a permanent change. Double-check your selections before writing.

#### 9. Recover Files
- If you just need to recover a few files without fixing the partition table, you can do so from the file list (after pressing p).

- Navigate to the folder containing your desired files.

- Use the colon : key to select the files you want to recover.

- Press the uppercase C key to copy the selected file(s).

- Navigate to a safe destination on a different storage device and press uppercase C again to paste.

#### 10. Exit and Restart
- Once your task is complete, select [Quit] to exit the program.

- If you wrote a new partition table to the drive, it is recommended to restart your computer to allow the operating system to recognize the changes.

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
Successfully used **TestDisk** to analyze the storage drive, detect missing or corrupted partitions, and recover the desired data.  
The lost partitions were restored by rewriting the correct partition table, and important files were recovered safely to an external storage device, verifying that **TestDisk effectively performs open-source data recovery and partition repair.**

</div>

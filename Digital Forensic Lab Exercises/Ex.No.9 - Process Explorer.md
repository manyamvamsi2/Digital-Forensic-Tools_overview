## Ex.No.9 — Using Procmon to Identify Suspicious Processes

## Aim
To monitor and identify suspicious process activities in a Windows system using **Procmon (Process Monitor)**.


## Procedure
1. **Download and extract Procmon** from the Microsoft Sysinternals site.
2. **Run Procmon as Administrator** to allow system-level monitoring.
   <p align="center">
       <img width="600"  alt="image" src="https://github.com/user-attachments/assets/c3f5f5f2-cdfa-4bd5-9653-9d6d0632d95e" />
   </p>
4. **Start Capture** by clicking the **Capture Events (Ctrl + E)** icon.
  <p align="center">
    <img width="600"  alt="image" src="https://github.com/user-attachments/assets/1a8a45ea-ba33-4727-9071-545076b9a2b7" />
  </p>

5. Perform normal or suspicious operations (e.g., run unknown executables).
6. **Stop Capture** after sufficient data collection.
7. **Filter the events**:
   - Go to *Filter → Filter...*
   - Add filters such as:
     - `Process Name contains suspicious.exe`
     - `Operation contains WriteFile` or `CreateProcess`

 <p align="center">
      <img width="600"  alt="image" src="https://github.com/user-attachments/assets/357d7583-bcc5-4380-a340-3cfd831074bc" />
 </p>
 
8. Analyze the logs:
   - Check **Process Tree** to view parent-child relationships.
   - Identify unexpected registry changes or file access.
   - Export suspicious events to CSV for reporting.
   
<p align="center">
    <img width="600" alt="image" src="https://github.com/user-attachments/assets/cc4cf7ee-889a-4195-a373-b6bcdb3e26bb" />

</p>

9. **Close Procmon** and review captured data for persistence or injection signs.

--- 

## Rubrics

| Criteria | Mark Allotted | Mark Awarded |
|---|---:|---:|
| 1. GitHub Activity & Submission Regularity | 3 | |
| 2. Application of Forensic Tools & Practical Execution | 3 | |
| 3. Documentation & Reporting | 2 | |
| 4. Engagement, Problem-Solving & Team Collaboration | 2 | |
| *Total* | *10* | |
## Result
Successfully used **Procmon** to capture and analyze system process activities. Suspicious processes performing abnormal registry modifications, file writes, or network access were identified, providing insights into potential malicious behavior.


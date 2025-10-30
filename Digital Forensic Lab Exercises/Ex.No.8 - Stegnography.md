## Ex.No.8 — Detect Hidden Data in Images Using zsteg (Linux)

## Aim
To detect and extract hidden or steganographic data from image files using the **zsteg** tool in Linux.



## **Procedure**
1. Open the terminal on your Linux system.  
2. Place the suspect image file (e.g., `suspect.png`) in your working directory.  
3. Run zsteg to analyze the image for hidden data:  
   ```bash
   zsteg dog.png
   ```
   <p align="center">
       <img width="811"  alt="image" src="https://github.com/user-attachments/assets/7b2cf64d-d74e-499c-8908-906bbd9c6cae" />
   </p>

<p align="center">
   <img width="820"  alt="image" src="https://github.com/user-attachments/assets/6284c368-417c-4d8b-9e0f-84bb7b771dbe" />
</p>

4. To analyze all PNG files in a folder:  
   ```bash
   for f in *.png; do echo "=== $f ==="; zsteg "$f"; done
   ```
<p align="center">
  <img width="1694" alt="image" src="https://github.com/user-attachments/assets/8cc4d624-4e9c-4cb0-a527-7248fae190ce" />
</p>


5. When zsteg detects hidden data, extract it using the `-E` flag:  
   ```bash
   zsteg -E all suspect.png > extracted_data.bin
   ```
6. Check the extracted file type and content:  
   ```bash
   file extracted_data.bin
   strings extracted_data.bin | less
   hexdump -C extracted_data.bin | head
   ```
7. Record findings such as file name, detection method, and extracted data type.
   <br>

# Rubrics

| Criteria | Mark Allotted | Mark Awarded |
|---|---:|---:|
| 1. GitHub Activity & Submission Regularity | 3 | |
| 2. Application of Forensic Tools & Practical Execution | 3 | |
| 3. Documentation & Reporting | 2 | |
| 4. Engagement, Problem-Solving & Team Collaboration | 2 | |
| *Total* | *10* | |

## Result
Hidden information was successfully detected and extracted from the given image using **zsteg** on Linux.


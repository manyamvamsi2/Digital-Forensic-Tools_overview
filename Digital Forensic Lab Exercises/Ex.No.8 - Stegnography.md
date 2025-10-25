## 🕵️ Ex.No.8: Use Steg-Expose to Detect Hidden Data in Images

**Description**

**StegExpose** is a tool used to detect hidden data in images using steganography analysis. It works by evaluating the statistical properties of an image to estimate whether any hidden data is embedded. Below is a step-by-step guide on how to use StegExpose to detect hidden data in images:

---

### Prerequisites

* **Java Runtime Environment (JRE):** StegExpose is a Java-based tool, so ensure you have JRE installed.
* **StegExpose Tool:** Download StegExpose from the official GitHub repository.

---

### Step-by-Step Process

#### 1. Download and Set Up StegExpose
* **Download the tool:** Go to StegExpose GitHub and download the **StegExpose.jar** file..
* **Install Java:** Ensure that Java is installed on your machine.
* **Prepare environment:** Place the **.jar** file in a folder where you plan to work on the image files.

#### 2. Select Images for Analysis
* Collect the images you suspect might have hidden data. StegExpose supports formats such as **.png**, **.jpg**, **.bmp**, etc.

#### 3. Open Command Line or Terminal
* Navigate to the folder where you have saved the `StegExpose.jar` file.
* Open your Command Prompt (Windows) or Terminal (Linux/macOS).

#### 4. Run StegExpose on an Image
* Use the following command to check a single image for hidden data:

    ```bash
    java -jar StegExpose.jar <image_file_path>
    ```

    **Example:**
    ```bash
    java -jar StegExpose.jar test_image.png
    ```

#### 5. Analyze the Output
* The tool analyzes the image and provides a score.
* **StegExpose calculates a "suspect" score (between 0 and 1).** The higher the score, the more likely that hidden data is present.
* **Threshold values (suggested by the tool):**
    * Less than 0.2: Image is clean (no hidden data).
    * 0.2 - 0.3: Possibly some hidden data.
    * Above 0.3: Likely that steganography is present.

#### 6. Batch Analysis (Multiple Images)
* If you have multiple images to check, you can analyze them in bulk by specifying a folder:

    ```bash
    java -jar StegExpose.jar <folder_path>
    ```

#### 7. Advanced Options (Optional)
* Use `--help` to see the list of options:

    ```bash
    java -jar StegExpose.jar --help
    ```

#### 8. Review the Results
* Example Output:

    ```makefile
    Analyzing suspect_image.png...
    Result: 0.4
    Steganography likely present
    ```

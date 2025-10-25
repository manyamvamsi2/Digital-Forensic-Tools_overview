## 🕵️ Ex.No.9: Use Process Explorer to Identify Suspicious Processes

**Description**

**Process Explorer** is a powerful Windows tool that provides detailed information about running processes, allowing users to monitor, troubleshoot, and detect suspicious activities. It can be used to detect potential malware or harmful processes by analyzing various aspects of running applications.

---

### Step 1: Download and Set Up Process Explorer

* **Download Process Explorer:**
    Go to the official Microsoft Sysinternals website and download Process Explorer.
* **Extract the Program:**
    Extract the ZIP file to a folder.
* **Run Process Explorer:**
    Open the folder and run `procexp64.exe` or `procexp.exe` as **Administrator** (by right-clicking and selecting "Run as Administrator").

---

### Step 2: Familiarize Yourself with the Interface

The interface lists all running processes in a tree structure. Processes are **color-coded** for status:

| Color | Meaning |
| :--- | :--- |
| **Pink** | Suspended processes. |
| **Light Blue** | Processes running under the same user as you. |
| **Dark Blue** | Services or processes running under system accounts. |
| **Green** | New processes. |
| **Red** | Processes that have just exited. |

---

### Step 3: Identify Suspicious Processes

Follow these steps to investigate potentially suspicious processes:

1.  **Look for Unfamiliar Processes:**
    * Scan for names you don't recognize. **Legitimate processes** are usually from trusted sources (Microsoft, Intel, Adobe, etc.).
2.  **Verify Digital Signatures:**
    * Right-click the process $\rightarrow$ **Properties** $\rightarrow$ **Image** tab.
    * Check if the process has a valid **Digital Signature**. Processes without signatures are suspicious.
3.  **Check the Path of the Process:**
    * In **Properties** $\rightarrow$ **Image** tab, check the **Path**.
    * **Suspicious:** Running from temporary folders, user folders, or random directories (should typically be in `C:\Windows\System32` for system processes).
4.  **Monitor CPU, Memory, and Disk Usage:**
    * Look for a process using an **unusually high amount of resources** without explanation (e.g., high CPU usage on a background process).
5.  **Check Process Description and Company Name:**
    * **Suspicious:** Lack of information or unclear company names.
6.  **Check the Process Network Activity:**
    * Right-click $\rightarrow$ **Properties** $\rightarrow$ **TCP/IP** tab.
    * **Suspicious:** Unexpected or unexplained external connections.

---

### Step 4: Perform a Google Search on Suspicious Processes

* **Search online:** Use the process name (e.g., `processname.exe`) to check its reputation.
* **Check Malware Databases:** Verify the process against online databases like **VirusTotal** or **ProcessLibrary**.

---

### Step 5: Kill or Suspend Suspicious Processes

* **Kill the Process:**
    Right-click $\rightarrow$ **Kill Process** to terminate it immediately.
* **Suspend the Process:**
    Right-click $\rightarrow$ **Suspend** to stop execution temporarily for further investigation.
* **Remove the Source File:**
    Locate the executable using the Path and **delete the file** if confirmed to be malware.

---

### Step 6: Scan Your System

* Run a **full antivirus scan**.
* Use **Malware Removal Tools** (like Malwarebytes or Windows Defender) for an in-depth system scan.

***

Would you like the Markdown syntax for the **StegExpose** guide or the **AFLogical OSE** guide again?

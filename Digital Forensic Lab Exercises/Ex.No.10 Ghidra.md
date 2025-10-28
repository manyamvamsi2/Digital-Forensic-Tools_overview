# Ex.No.10 —  Use Ghidra to Disassemble and Analyze the Malware Code

## Aim
Perform a defensive static analysis of a suspicious Windows executable using Ghidra to identify likely functionality, extract Indicators of Compromise (IOCs), and document findings — without executing the sample.

## Procedure 
 
 ## 1. **Workspace setup**
   - Create/restore a clean snapshot of the isolated analysis VM.
   - Copy the sample into the VM (use a controlled channel). Work only on a copy.

## 2. **Triage & metadata**
   - Record file name and size.
   - Compute hashes for tracking:
     - `sha256sum payload.exe` → record SHA256.
     - `md5sum payload.exe` → record MD5.
   <img width="1062"  alt="image" src="https://github.com/user-attachments/assets/5b06a69a-bacd-4108-8bbe-9567ba22fee9" />

   - Note PE characteristics (32/64-bit) using PE viewers or Ghidra import info.


## 3. **Import into Ghidra**
   - Open Ghidra → New Project → Import `payload.exe`.
   - On import, accept recommended loader options; enable auto-analysis (function recovery, decompiler).
 <br>
 <img width="1882" alt="image" src="https://github.com/user-attachments/assets/31b44c71-a091-44f1-b690-53e93559457a" />
 <br>
 <img width="1888"  alt="image" src="https://github.com/user-attachments/assets/2648fc22-001c-400a-afdc-3f71e6c0026b" />
<br>

## 4. **Initial navigation**
   - Open **Listing** and **Symbol Tree**. Locate entry point and main-like functions.
   - Open **Decompiler** for the entry function to get C-like pseudocode.
 <br>
 <img width="1911"  alt="image" src="https://github.com/user-attachments/assets/089183b1-819b-4141-925c-0fa88513b02c" />
 <br>

## 5. Investigate imports & APIs (locate, bookmark, map to behavior)

- Open **Symbol Tree** and expand **Imports** → expand DLL names (e.g., `KERNEL32.DLL`, `ADVAPI32.DLL`, `WS2_32.DLL`).
- Scan for relevant API names. Right-click any import → **Add Bookmark** → choose a category (e.g., `Note` or `Security`) and add a short note like `networking: connect`.
- Useful imports to flag:
  - **Networking / C2:** `WSAStartup`, `socket`, `connect`, `send`, `recv`, `gethostbyname`, `InternetOpen`, `URLDownloadToFile`
  - **Persistence:** `RegSetValueEx`, `RegCreateKeyEx`, `CreateService`, `OpenSCManager`
  - **Process control / injection:** `CreateProcess`, `OpenProcess`, `CreateRemoteThread`, `WriteProcessMemory`
  - **Memory / loader:** `VirtualAlloc`, `VirtualProtect`, `VirtualFree`
- Make a short mapping in your notes, for example:
  - ``socket/connect → probable C2``
  - ``RegSetValueEx → probable persistence``

<img width="1898"  alt="image" src="https://github.com/user-attachments/assets/d2df11c0-02cd-4ebc-80ee-73e0d500d0c2" />
<br>
<img width="1630"  alt="image" src="https://github.com/user-attachments/assets/9e9dbd5f-63d6-46e1-9fb0-93a0499ef320" />

<br>

## 6. **Follow control flow**
   - Use Xrefs to trace which routines call network or persistence APIs.
   - Inspect loops/timers for beaconing logic or polling behavior.

## 7. **Detect unpacking/obfuscation**
   - Search for `VirtualAlloc` + `WriteProcessMemory`/`CreateThread` patterns (possible unpacker).
   - If strings look encoded, identify and statically trace the decoder routine in the decompiler to recover plaintext.

## 8. **Extract and document IOCs**
   - Collect hardcoded domains/IPs, file paths, mutex names, registry keys, and hashes.
   - Capture relevant code locations (function names/addresses) and representative pseudocode snippets.
## 9. **Summarize findings**
   - Write a short summary: likely capabilities, confidence level, and recommended defensive actions (isolate hosts, block domains, hunt for hashes/registry keys).


## Result
- Static analysis in Ghidra revealed network beaconing behavior and persistence routines in the executable.  
- The file shows unpacking characteristics, suggesting further dynamic analysis is needed under a controlled environment.




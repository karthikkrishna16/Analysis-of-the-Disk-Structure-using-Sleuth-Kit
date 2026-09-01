# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
## SAMPLE WORKFLOW (Windows)
```bash
# Step 1: View partitions
mmls.exe C:\forensics\disk.dd

# Step 2: View file system details
fsstat.exe -o 2048 C:\forensics\disk.dd

# Step 3: List files
fls.exe -r -o 2048 C:\forensics\disk.dd

# Step 4: Recover a file
icat.exe -o 2048 C:\forensics\disk.dd 6 > C:\forensics\image.jpg
```
## OUTPUT:
Disk Structure Analysis Results

<img width="625" height="410" alt="Screenshot 2026-08-21 223235" src="https://github.com/user-attachments/assets/813342ed-5bbf-4c48-809d-6f3ed37a370c" />
<img width="518" height="461" alt="Screenshot 2026-08-21 223306" src="https://github.com/user-attachments/assets/61381bc3-9e05-4126-ba7c-428d766352e5" />
<img width="637" height="462" alt="Screenshot 2026-08-21 223327" src="https://github.com/user-attachments/assets/5933bdf2-d0a4-4bc0-b0cc-a0680fd172f1" />
<img width="637" height="458" alt="Screenshot 2026-08-21 223346" src="https://github.com/user-attachments/assets/f65304bb-62b9-4d8d-bc8a-e05ed70916ec" />
<img width="629" height="456" alt="Screenshot 2026-08-21 223403" src="https://github.com/user-attachments/assets/190c2f0d-1944-4a75-8187-7dd4f9c98724" />
<img width="529" height="442" alt="Screenshot 2026-08-21 223421" src="https://github.com/user-attachments/assets/45c273b9-7295-4c88-bf0b-45b6910de729" />
<img width="487" height="451" alt="Screenshot 2026-08-21 223436" src="https://github.com/user-attachments/assets/613ec996-de82-4630-93c2-83a2a160dfe8" />
<img width="422" height="450" alt="Screenshot 2026-08-21 223451" src="https://github.com/user-attachments/assets/31637091-c05a-44a8-a752-600eab16a8dd" />
<img width="423" height="217" alt="Screenshot 2026-08-21 223508" src="https://github.com/user-attachments/assets/647350a4-9cb1-42c0-bc3e-a508e4dab322" />









## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.

# Digital Forensics Case Study: USB Drive Artifact Recovery

## 📌 Objective
Conduct a forensically sound acquisition of a target USB drive (NIST CFReDS dataset) and execute data carving to recover deleted artifacts while maintaining strict chain-of-custody protocols.

## 🛠️ Tools & Technologies
* **FTK Imager:** Physical drive imaging, Expert Witness format (.E01) creation, cryptographic hashing.
* **Autopsy:** File system analysis, hex/text data carving, `$OrphanFiles` recovery.
* **Concepts:** Write-blocking principles, Hash Verification (MD5/SHA-1), FAT32 File Systems.

## 🔎 Methodology & Execution

### 1. Evidence Acquisition & Integrity Verification
To ensure no data modification occurred during acquisition, the evidence was imaged using FTK Imager into a forensically sound `.E01` format. The tool automatically generated MD5 and SHA-1 hashes of the physical drive, which were verified against the final image to prove absolute data integrity.

> **Visual Evidence: Evidence Acquisition Setup**
> <img width="1600" height="900" alt="ftk" src="https://github.com/user-attachments/assets/ac151a6b-c419-44c9-a01d-a1008c73272c" />





### 2. Artifact Carving & Analysis
The verified `.E01` image was ingested into Autopsy. Using the Hash Lookup and PhotoRec Carver modules, the FAT32 file system was analyzed. By navigating into the unallocated space and the `$OrphanFiles` directory, several deleted artifacts (including database logs and configuration files) were successfully located and extracted using raw hex data analysis.

<img width="1600" height="900" alt="orphaned file" src="https://github.com/user-attachments/assets/d4083b00-9182-4c09-8b46-36cd6b66f10a" />

> **Visual Evidence: Recovered Deleted Files**
> <img width="1600" height="900" alt="autopsy ss 1" src="https://github.com/user-attachments/assets/6596a5b0-f8fa-43c8-9670-e2b8c19ac2d7" />
<img width="1600" height="900" alt="autopsy ss2 " src="https://github.com/user-attachments/assets/8c5608a5-ec07-463c-8ea7-36ee59adcf53" />
<img width="1600" height="900" alt="autopsy ss3" src="https://github.com/user-attachments/assets/b5dbbeaa-72ef-45cd-90c9-09ebdba154c7" />




## 💡 Conclusion
This project successfully demonstrated the ability to acquire compromised media, mathematically prove evidence integrity, and utilize standard forensic suites to extract hidden or deleted data from unallocated space.

# Data Management #
----
## **Storage Rule** ##
Every participant session must exist in four separate physical/logical locations before it is considered safely stored.

| **#** | **Location** |**Purpose** |
| ----------- |  ----------- | ------------ |
| 1 | Testing computer (KINARM / tablet) | Point-of-collection copy — the original session files as written by the software. |
| 2 | Encrypted backup drive (next to KINARM)| Offline copy, kept disconnected from the network. |
| 3 | CCM Dropbox| Shared copy that everyone else works from. |
| 4 | Personal computer working copy| Local copy used for active analysis. |

Transfer sequence for a new session:
1.	Collect the session on the testing computer (Location 1).
2.	At the end of each testing session, copy new session folders to the encrypted backup drive (Location 2).
3.	Transfer the data to your working computer with a USB, then upload the same session folders to the CCM Dropbox (Location 3), into the correct Project / Experiment / Subject path.
4.	Only after Locations 2 and 3 are confirmed should a personal working copy (Location 4) be used for analysis.


---
## **Dropbox Folder Structure** ##

Our CCM Lab Dropbox is organized into:

```language
Projects
├── _admin
│   ├── participant_key.xlsx     (links participant ID ↔ identity)
│   ├─ README_template.txt
├── <Project>                  e.g. Localization
│   ├── README.txt  
│   ├── <Experiment1>          e.g. Experiment 1
│   │   ├── protocol.txt
│   │   ├── data
│   │      │ 
│   │      ├── P01 	 e.g. 923483931_2026-11-01_24-52-16.kinarm
│   │      ├── P02
│   │      └── ...
│   └── <Experiment2>
└── <Project2>
```

***Every project folder must contain a README.txt describing:***
- What the project is
- Contact Person
- What each experiment subfolder contains

---
## **Naming Conventions** ##

**Participant IDs:**

- We will assign the participants sequentially per project through the participant_key.xlsx
- IDs are not to be derived from any identifying information (name, DOB, etc.), only through 2 digits (e.g. P01, P02, …)

**Dropbox Files**

Once copied into the correct Project/Experiment file, there is no need to rename it there.

**After processing .kinarm file**

Once you have processed the .kinarm file into a .csv file, rename it with the following conventions:

`
P<id>_<ConditionIfNeeded>
`

Example: P02_Baseline

---
## **Backup Schedule & Integrity Checks** ##
| **Task** | **Frequency** |**Responsible** |
| ----------- |  ----------- | ------------ |
| Copy new sessions to encrypted backup drive | Same day as collection | Data collector |
| Upload new sessions to CCM Dropbox | Same day as collection| Data collector |
| Verify session file counts match across Locations 1–3 | Weekly| Lab manager |
| Spot-check that a random file opens correctly in each location | Monthly | Lab manager |
| Confirm backup drive itself is not full / failing | Monthly| Lab manager |
| Backup KINARM Task Programs | Monthly | Lab manager |
| Move old/unused KINARM Task Programs into Documents/Dexterit Project Archives | Monthly | Lab manager |
---
## **New Data Collection Checklist** ##
**Use this checklist for every testing session:**
1.	Confirm participant ID has been assigned and matches the entry in Dropbox admin/participant_key.xlsx.
2.	Run the session; confirm raw files are written to the testing computer under the correct participant/session name.
3.	Same day: copy the session to the encrypted backup drive (this should be Elements D:/KINARM Backups/ or Elements D:/Tablet Backup/) under the correct participant file
4.	Same day: transfer session data to your working computer with a USB, then upload the session to the correct Dropbox path (do not rename raw files)
5.	Log the session as complete in the project tracking participant_key.xlsx (session date, participant ID, any notes on data quality).
6.	When ready to analyze, pull a personal working copy from Dropbox to run through our preprocessing script and rename based on naming conventions above

**Onboarding checklist for new lab members:**

- Read this document
- Check dropbox access (You can find log in details under Resource Access in our [Resources](/lab-wiki/resources))
- Shadow an experienced lab member for at least one full data-collection-to-backup cycle before collecting data independently

**Offboarding checklist when a lab member leaves:**
- Revoke Dropbox and any shared-drive access
- Confirm all locally stored participant data has been deleted from personal devices
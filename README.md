# Theme 4
## Mycobacterium tuberculosis


### November 2nd, 2026

I have finally received the overwhelming amount of data that I need to work with the TB project. I have it in the Secure Enclave under my credentials and other secure walls. The data I have goes from 2018 to 2025, all inclusive. Some key data I have are:

- 34,912 unique Genome Universal Identifiers (these are unique for all the data).
- 34,912 anonymized IDs, of which 23,233 are unique.
- There are 147 metadata fields in the metadata file.
- After making a subset of my data in the metadata file by removing the Genome Universal Identifiers, the aID, and the Sample Indicator, I can tell that all patients that have more than 1 genome sequenced show the exact same metadata throughout their linked info. For instance, there are no discrepancies in notification year and episode 1 and episode 2,3,4,5,6 in the same patient. This goes throughout the rest of the fields.

My next step is to create a table that summarizes some of this data by year, and show the missingness of it.

### November9th, 2026

After talking to Mailis and Sharon, I need to manually see the range of answers of almost all of the variables (columns) of the metadata file, as it is possible that some fields have a "" instead of an empty or a blank cell, which could bias my results. I did this in R, and I am reporting underneath anything that seems suspicious:

| Metadata field | No. of unique responses | Notes |
| ------------- | ------------- | ---------------|
| Episode no | 6 | A total of 33,624 are actual NA |
| Shared postcode count | 30 | No NAs on this one |
| Year | 8 | No NAs on this one |
| Ethnic group | 15 | All make sense, but there are 351 "unknown" and 0 NAs |
| Occupation | 3,907 | To look at the Excel file later |
| Country of birth (cob) | 180 | No repeated instances that I could find, 176 are unknowns and 0 are NAs |
| UK entry year | 84 | 9,558 are NA, which are not applicable if born in the UK? |
| Disease site list | 515 | Personalized answers? ask if these answers are standardized or if manually written. No NAs |
| Site pulmonary| 2 | Binary (0,1) answers, no NAs |
| Site bone spine | 2 | Binary (0,1) answers, no NAs |
| Site bone other | 2 | Binary (0,1) answers, no NAs |
| Site CNS Meningitis | 2 | Binary (0,1) answers, no NAs |
| Site CNS other | 2 | Binary (0,1) answers, no NAs |
| Site cryptic | 2 | Binary (0,1) answers, no NAs |
| Site gi | 2 | Binary (0,1) answers, no NAs |
| Site gu | 2 | Binary (0,1) answers, no NAs |
| Site it lymph nodes  | 2 | Binary (0,1) answers, no NAs |
| Site t lymph nodes | 2 | Binary (0,1) answers, no NAs |
| Site laryngeal | 2 | Binary (0,1) answers, no NAs |
| Site miliary | 2 | Binary (0,1) answers, no NAs |
| Site pleural | 2 | Binary (0,1) answers, no NAs |
| Site ep other | 2 | Binary (0,1) answers, no NAs |
| Other ep site | 455 | Similar to Disease site list, personalized answers. Two type of answers are unknown (unknown vs unknown, no site specified in legacy system), no NAs |
| Postmortem diagnosis | 2 | Binary (0,1) answers, 32,858 NAs (assuming those did not die?) |
| Started treatment | 2 | Binary (0,1) answers, 169 NAs |
| Treatment regimen | 4 | One answer is empty but not classified as NA, and has 6,235 |
| MDR expected duration | 23 | There is overlap in some answers' range, no NAs |
| Directly observed therapy (dot) offered | 3 | Answer (0,1,3), 10,302 NAs |
| DOT received | 3 | Answer (0,1,3) 27,630 are NAs |
| Chest Xray result | 5 | Answers (0,1,2,3,4) no NAs |
| Chest CT result | 5 | Answers (0,1,2,3,4), no NAs |






To address:
"Unknown" in ethnic group should be treated as NA?
"Occupation" has 3,907 answers, to look at this later in an excel file
"cob", 176 are labeled as "unknown", should be treated as NA?
"UK entry year", 9,558 are NA, which I am assuming those are UK born
"Siteitlyphnodes" vs "Sytetlymphnodes" ask for clarification
"Post-mortem" ask if NAs mean they did not die, and the 0,1 are for those who died
"Started treatment" ask if there was no follow up for those who had NA
"Treatment regimen", the sum of treatment regimen does not add up to started treatment, even after adding up the NAs and the 0s as not treated










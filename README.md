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

Sociodemographic 

| Metadata field | No. of unique responses | Notes |
| ------------- | ------------- | ---------------|
| Sex MF | 2 | Answers (0,1) binary, no NAs |
| Ethnic group | 15 | All make sense, but there are 351 "unknown" and 0 NAs |
| Ethgroup | 11 | Answers (1,2,3...11), no NAs |
| Occupation | 3,907 | To look at the Excel file later |
| Occupation category | 8 | Answers (1,2,...8) and no NAs |
| Country of birth (cob) | 180 | No repeated instances that I could find, 176 are unknowns and 0 are NAs |
| UK entry year | 84 | 9,558 are NA, which are not applicable if born in the UK? |
| Smoking YN | 2 | Answer is binary (0,1) and 3,424 are NAs |
| Smoking time frame | 4 | Answers (1,2,3,4) and 26,640 are NAs |
| Alcohol misuse | 2 | Answers are binary (0,1) and 2,396 are NAs |
| Drug misuse | 2 | Answers are binary (0,1) and 2,559 are NAs |
| Homeless YN | 2 | Answers are binary (0,1) and 2,484 are NAs |
| Homeless time frame | 4 | Answers (1,2,3,4) and 32,248 are NAs |
| Prison YN | 2 | Answers are binary (0,1) and 3,279 are NAs |
| Prison time frame | 4 | Answers (1,2,3,4) and 33,132 are NAs |
| Drug time | 0 | All 34,912 are NA |
| Asylum seeker | 2 | Answers are binary (0,1) and 11,114 are NAs |
| Immigration removal centre (IRC) Flag | 2 | Answers are binary (2,3) and 34,908 are NAs |

Comorbidities and other conditions

| Metadata field | No. of unique responses | Notes |
| ------------- | ------------- | ---------------|
| Mental health YN | 1 | Answers are 1 or NA, 33,587 are NA |
| Diabetes YN | 2 | Answers are binary (0,1) and 1,944 are NA |
| Hepatitis B YN | 2 | Answers are binary (0,1) and 3,684 are NA |
| Hepatitis C YN | 2 | Answers are binary (0,1) and 3,714 are NA |
| Chronic liver disease YN | 2 | Answers are binary (0,1) and 2,512 are NA |
| Chronic renal disease YN | 2 | Answers are binary (0,1) and 2,268 are NA |
| Immunosuppression YN | 2 | Answers are binary (0,1) and 2,380 are NA |
| Transplantation YN | 2 | Answers are binary (0,1) and 32,756 are NA |
| Other immunosuppression YN | Answers are binary (0,1) and 32,325 are NA |
| Other immunosuppression cat | 4 | Answers (1,2,3,4) and 32,870 are NA |

Contact tracing

| Metadata field | No. of unique responses | Notes |
| ------------- | ------------- | ---------------|
| Adult contacts identified | 83 | 7,605 NAs |
| Child contacts identified | 41 | 11,742 NAs |
| Total contacts identified | 86 | 7,498 NAs |
| Adult contacts assessed | 65 | 11,772 NAs |
| Child contacts assessed | 35 | 15,373 NAs |
| Total contacts assessed | 75 | 11,600 NAs |
| Adult contacts active TB | 8 | 14,696 NAs |
| Child contacts active TB | 8 | 17,477 NAs |
| Total contacts active TB | 10 | 14,457 NAs |
| Adult contacts LTBI | 22 | 14,255 NAs |
| Child contacts LTBI | 11 | 17,352 NAs |
| Total contacts LTBI | 24 | 13,925 NAs |
| Adult contacts LTBI treat | 19 | 16,359 NAs |
| Child contacts LTBI treat | 11 | 18,718 NAs |
| Total contacts LTBI treat | 21 | 15,942 NAs |
| Adult contacts LTBI treat complete | 14 | 17,313 NAs |
| Child contacts LTBI treat complete | 11 | 19,371 NAs |
| Total contacts LTBI treat complete | 17 | 16,857 NAs |
| Shared postcode count | 30 | No NAs on this one |
| To how many countries | 11 | 29,893 NAs |
| Travel country 1 | 115 | 29,940 are "" instead of NA, and no NA reporeted |
| Travel country 2 | 68 | 34,538 are "" instead of NA, and no NA reported |
| Travel country 3 | 35 | 34,820 are "", no NAs reported |
| Months travelled 1 | 24 | Answers (1,2,...24), 31,274 are NAs |
| Months travelled 2 | 34,682 NAs |
| Months travelled 3 | 8 | 34,856 are NA |
| No of visitor countries | 4 | Answers (1,2,3,5) and 34,057 are NAs |
| Visitor country 1 | 64 | 34,070 are "", no NAs reported, 1 is unknown, and 1 is other |
| Visitor country 2 | 10 | 34,891 are "", no NAs reported |
| Duration of visitors 1 | 5 | Answers (1,2,3,4,5) and 34,254 are NAs |
| Duration of visitors 2 | 4 | Answers (1,2,3,5) and 34,900 are NAs |
| Social context venue type list | 262 | 32,934 are "" , no NAs, and some are manually typed with some overlap with one another |
| MDR exposure to known case | 4 | 33,814 are "", 380 are unknown, 0 NAs |
| MDR relationship to case | 36 | 34,767 are "",  no NAs, and some are manually typed with some overlap with one another |

Diagnostics

| Metadata field | No. of unique responses | Notes |
| ------------- | ------------- | ---------------|
| Year | 8 | No NAs on this one |
| Prev diag | 2 | Answers are binary (0,1), 4,406 are NAs |
| Diagnosis date | 2,787 | To look at Excel file in more detail |
| Notification date | 2,437 | To look at Excel file in more detail |
| Culture YN | 2 | Answers are binary (0,1), no NAs |
| Resp microscopy | 4 | Answers (1,2,3,4) and 14,917 are NA |
| Resp microscopy date | 2,770 | To look at Excel file in more detail |
| Nonresp microscopy | 2 | Answers (0,1), and 26,992 are NA |
| Non resp microscopy date | 2,201 | To look at Excel file in more detail |
| Resp PCR | 4 | Answers (1,2,3,4) and 26,819 are NA |
| Non resp PCR | 2 | Answers (0,1) and 30,501 are NA |
| Non resp PCR date | 1,503  | To look at Excel file in more detail |
| Resp culture | 2 | Answers (1,2) and 14,772 are NA |
| Resp culture date | 2,777  | To look at Excel file in more detail |
| Non resp culture | 1 | Answer is 1 or NA, 18,445 are NA |
| Resp PCR date | 1,924 | To look at Excel file in more detail |
| Non resp culture date | 2,557 | To look at Excel file in more detail |
| Histology date | 1,315 | To look at Excel file in more detail |
| Chest Xray YN | 2 | Answers are binary (0,1), 20,822 are NAs |
| Chest Xray result | 5 | Answers (0,1,2,3,4) no NAs |
| Chest CT YN | 2 | Answers are binary (0,1) and 27,874 are NAs |
| Chest CT result | 5 | Answers (0,1,2,3,4), no NAs |
| PCR Test YN | 2 | Answers are binary (0,1), and 22,955 are NAs |
| Micro YN | 2 | Answers are binary (0,1) and 9,409 are NAs |
| Rec ID | 609 | To look at Excel file in more detail |
| Sample indicator | 18 | Answers (A,B,C...R) no NAs |


Disease

| Metadata field | No. of unique responses | Notes |
| ------------- | ------------- | ---------------|
| Episode no | 6 | A total of 33,624 are actual NA |
| Repeated episode YN | 2 | Answers are binary (0,1) and no NAs |
| Pulm YN | 2 | Answers are binary (0,1), no NAs |
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
| Final outcome 12 | 6 | Answers (1,2...6) and none are NAs |
| Final outcome 24 | 6 | Answers (1,2,...6) and 30,825 are NAs |
| Final outcome 48 | 1 | Answer is 1 or NA, 34,895 NAs in total |
| Overall outcome | 6 | Answers (1,2,...6) and no NAs |
| Date of death | 1,074 | To look at Excel file in more detail |
| Postmortem diagnosis | 2 | Binary (0,1) answers, 32,858 NAs (assuming those did not die?) |

Treatment, therapy & AMR

| Metadata field | No. of unique responses | Notes |
| ------------- | ------------- | ---------------|
| Started treatment | 2 | Binary (0,1) answers, 169 NAs |
| Treatment regimen | 4 | One answer is empty but not classified as NA, and has 6,235 |
| Start of treatment date | 2,841 | To look at Excel file in more detail |
| Treatment end date | 2,869 | To look at Excel file in more detail |
| Enhanced case management (ECM) YN | 2 | Answer is binary (0,1), no NAs |
| ECM level | 5 | Answers (0,1...5) no NAs |
| DR MDR cohort | 2 | Answers are binary (0,1) and none are NAs |
| MDR treatment date | 401 | To look at Excel file in more detail |
| MDR expected duration | 23 | There is overlap in some answers' range, no NAs |
| Directly observed therapy (dot) offered | 3 | Answer (0,1,3), 10,302 NAs |
| DOT received | 3 | Answer (0,1,3) 27,630 are NAs |
| Rif diag | 3 | Answers (0,1,3) 15 are NAs |
| PZA diag | 3 | Answers (0,1,3) and 15 are NAs |
| INH diag | 3 | Answers (0,1,3) and 15 are NAs |
| Emb diag | 3 | Answers (0,1,3) and 15 are NAs |
| RR MDR Diag | 2 | Answers are binary (0,1) and 15 are NAs |
| preXDR | 2 | Answers are binary (0,1) and 15 are NAs |
| INH no MDR total | 2 | Answers are binary (0,1) and 15 are NAs |
| INH total | 3 | Answers (0,1,3) and 15 are NAs |
| RIF total | 3 | Answers (0,1,3) and 15 are NAs |
| EMB total | 3 | Answers (0,1,3) and 15 are NAs |
| PZA total | 3 | Answers (0,1,3) and 15 are NAs |
| RR MDR total| 2 | Answers are binary (0,1) and 15 are NAs |
| Pre XDR total | 2 | Answers are binary (0,1) and 15 are NAs |
| Prev treat | 2 | Answers are binary (0,1), 33,816 are NAs |

To address:
"Unknown" in ethnic group should be treated as NA?
"Occupation" has 3,907 answers, to look at this later in an excel file
"cob", 176 are labeled as "unknown", should be treated as NA?
"UK entry year", 9,558 are NA, which I am assuming those are UK born
"Siteitlyphnodes" vs "Sytetlymphnodes" ask for clarification
"Post-mortem" ask if NAs mean they did not die, and the 0,1 are for those who died
"Started treatment" ask if there was no follow up for those who had NA
"Treatment regimen", the sum of treatment regimen does not add up to started treatment, even after adding up the NAs and the 0s as not treated
To look at "travel country n " deeply later on
"Notification date" to look at Excel file in more detail
"Diagnosis date" to look  at Excel file in more detail
"Start of treatment date", "MDR treatment date", and all that have a date involved
"Final outcome 12" has no NAs, but Final outcome 24 and 48 do. I could assume that the NAs mean that they fell in the 12 month outcome and thus it is not applicable










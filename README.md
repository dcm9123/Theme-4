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
| ------------- | ------------- |
| Episode no| 6 | A total of 33,624 are actual NA |
| Shared postcode count| 30 | No NAs on this one |
| Year | 8 | No NAs on this one |
| Ethnic group | 15 | All make sense, but there are 351 "unknown" and 0 NAs |
| Occupation | 3,907 | To look at the Excel file later |




To address:
"Unknown" in ethnic group should be treated as NA?
"Occupation" has 3,907 answers, to look at this later in an excel file






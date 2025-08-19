### India Electoral Rolls (2024–25)

------------------------------------------------------------------------

This repository contains the documentation for the parsed and analyzable voter records available via [Harvard Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/YNEY6G). It looks less like a repository at the moment. In the future, I will update this repository with the scripts used for downloading the rolls and subsequent text extraction using Surya-OCR. You can request access to this dataset using the following [Google Form](https://forms.gle/26spnRXCsYEoP1uQ7). Before using the dataset, I strongly recommend carefully reading the documentation (including the codebook) available [here](https://github.com/sharik19/India-Voter-Rolls-2024-25/blob/main/Documentation_India_Voter_Rolls_SL_v1.pdf). It will make your job easier and save me from answering issues already covered in the documentation.

While I have only released one state's parsed, analyzable files at the moment, I plan on regularly updating the dataset with voter records from more states, depending on resource availability.

If you use this dataset, please cite it appropriately. A suggested format is:\
**Sharik Laliwala. 2025. "India's Electoral Rolls (2024–25)." Harvard Dataverse.** **DOI: <https://doi.org/10.7910/DVN/YNEY6G>.**

Although it is already stated in the Google Form, I am reiterating two critical points here:

1\. This dataset is not meant for commercial usage that may lead to potential monetary benefits (telemarketing, political consultancy, etc.).

2\. If you are approved to access this dataset, you should not share it with anyone else (unless their details have been specified in the Google Form). You can direct them to the form to request access if they wish to use the dataset. This is absolutely necessary for the ethical use of this dataset.

------------------------------------------------------------------------

Here's more on what is available on the Dataverse and how it is organized:

| State   | Year | No. of Polling Stations (PS) / Parts | Mean Voters in a PS |
|:--------|:-----|:-------------------------------------|:--------------------|
| Haryana | 2024 | 20,626                               | \~987               |

#### Folderisation

1.  StateName_Year_CSVFiles.tar.lz4
    -   State_Code
        -   AC_NO
            -   Part_NO.CSV
2.  StateName_Year_JSONFiles.tar.lz4
    -   State_Code
        -   AC_NO
            -   Part_NO.JSONL
            -   Part_NO_Pages_Meta.JSON
3.  StateName_Year_Metadata.tar.lz4
    -   Meta_Checked_STATE_CODE.CSV
4.  StateName_Year_Metadata.tar.lz4
    -   State_Code
        -   AC_NO
            -   Out_PART_NO.JSON
            -   Out_Meta_PART_NO.JSON

------------------------------------------------------------------------

#### Potential validation checks

You can validate data fields by applying some basic checks. I have not implemented these because they might exclude voter records that are problematic within the roll itself, rather than errors from my OCR pipeline (for example, missing names or house numbers, duplicate EPICs, or ages greater than 125). Here is a suggestive list for such checks:

1.  Voter/Parent/Spouse Names: Are there names with just one character? Or voter names that do not make sense (such as "." or "\_")? Are there missing entries?
2.  Roll No & Voter ID: Are there roll numbers that exceed the typical maximum length of a roll (1500 voters + 20% margin of safety)? Any missing roll numbers or EPIC ID? Any EPIC ID that do not make sense (under 5 characters or over 30 characters)?
3.  Part Number: Any characters in this field instead of numeric values?
4.  Age: Unusual age numbers such as under 18 or over 110 years?
5.  Totals in Metadata file: Any extremely skewed gender ratio (5:1 : M:F) or over 200 voters in "Other" gender column? Additions or deletions exceeding 15-20 of the original totals?

------------------------------------------------------------------------

#### Acknowledgements

This work has been challenging but also rewarding in exploring the frontier of machine learning and high-performance computing. It would not have been possible without the high-performance computing resources made available via:

1.  University of California, Merced’s Pinnacles cluster

2.  NSF ACCESS-CI Allocations (Grant No. SOC250025), which provided access to:

    -   San Diego Supercomputer Center’s Expanse cluster

    -   Texas A&M University’s ACES and FASTER clusters

    -   Purdue University’s Anvil cluster

    -   Pittsburgh Supercomputing Center’s Bridges-2 cluster

The Haryana data was primarily processed on UC Merced’s Pinnacles and Purdue’s Anvil clusters. My text extraction script uses the Surya-OCR engine developed by Datalab.

Existing work on India’s then-machine-readable electoral rolls by Raphael Susewind as well as Gaurav Sood and colleagues' work served as an inspiration and a prototype to follow.

While I wrote the core scripts, I received troubleshooting support from a vendor. I also used generative AI tools, especially OpenAI’s o4-mini-high model, for coding assistance. All errors are mine, of course.

------------------------------------------------------------------------

#### Additional Resources

1.  Raphael Susewind’s [work](https://github.com/raphael-susewind/india-religion-politics) parsing India’s voter rolls over years

2.  Gaurav Sood and colleagues’ [work](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/MUEGDT) to parse India's voter rolls (2015-17, I think?)

3.  Datalab's fantastic [Surya-OCR](https://github.com/datalab-to/surya) engine

4.  Some music that I recommend :)

    -   Naveen Bharathi's lovely YouTube [channel](https://www.youtube.com/@naveenbharathi)

    -   The Inimitiable Begum Akhtar singing my favourite [ghazal](https://youtu.be/eEPcbMvKA0w?si=recg2p9p1JmknmB0)

    -   Ustad Nusrat's music on [OSA](https://www.youtube.com/@OrientalStarAgencies)

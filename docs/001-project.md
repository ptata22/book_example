# **Study CDISC Pilot01 Guide** {#intro}

**Note on Input Data Sources**

The analysis files for this study were derived from the submitted SDTM files. SDTM files were prepared from CRF data according to version 3.1.2 of the SDTM IG (with amendment 1).

No non-CRF or non-SDTM data were used to create the ADaM data.

The datasets include only subjects who were enrolled in the study. Subjects who failed screening criteria were not included in analysis datasets.

**Where to Find Key Data**

**Demographics and Populations**

The ADSL (Subject Level Analysis Data) dataset contains all subject-level variables for demographics, subject characteristics, and population flags.

[**Safety**]{.ul}

Key safety data are found in the datasets

-   ADAE (Adverse Events Analysis Data),

-   ADLBC (Laboratory Results Chemistry Analysis Data),

-   ADLBH (Laboratory Results Hematology Analysis Data),

-   ADLBHY (Laboratory Results Hy's Rule Analysis Data),

-   ADVS (Vital Signs Analysis Dataset).

-   ADTTE is specifically for safety analyses of the time to the first dermatologic AE. Dermatologic AEs are considered an adverse event of special interest.

    [**Efficacy**]{.ul}

    Study CDISCPilot01 has two primary endpoints,

    the Alzheimer's Disease Assessment Scale - Cognitive Subscale, total of 11 items [ADAS-Cog (11)] at Week 24 and the Video-referenced Clinician's Interview-based Impression of Change (CIBIC+) at Week 24.

    > **`All ADAS-Cog data, including the first primary endpoint, can be found in the dataset ADQSADAS.`**
    >
    > **`All CIBIC+ data, including the second primary endpoint, can be found in the dataset ADQSCIBC.`**
    >
    > **`Mean Revised Neuropsychiatric Inventory (NPI-X) data are considered secondary. These data can be found in the dataset ADQSNPIX.`**

    **Protocol Deviations**

    Protocol deviations were not reported in the source database and have not been incorporated into the SDTM data. As a result, such data do not exist among the analysis data.

    **Core Variables**

    The following core variables were merged from ADSL into all analysis datasets: [STUDYID, SITEID, USUBJID, TRTSDT, TRTEDT, AGE, AGEGR1, AGEGR1N, SEX, RACE, and RACEN.]{.ul}

    The table below summarizes the treatment variables and population flags that exist among different groups of analysis requirements:

    +------------------------------+---------------------------------+--------------------------------------+
    | Dataset(s)                   | Treatment Variables             | **Population Flags**                 |
    +==============================+=================================+======================================+
    | ADSL                         | TRT01P, TRT01PN, TRT01A,TRT01AN | SAFFL, DSRAEFL,ITTFL, EFFFL,COMP24FL |
    +------------------------------+---------------------------------+--------------------------------------+
    | ADAE                         | TRTA, TRTAN                     | SAFFL                                |
    +------------------------------+---------------------------------+--------------------------------------+
    | ADLBH,ADLBC, ADLBHY          | TRTP, TRTPN, TRTA,TRTAN         | SAFFL,COMP24FL,DSRAEFL               |
    +------------------------------+---------------------------------+--------------------------------------+
    | ADVS                         | TRTP, TRTPN, TRTA,TRTAN         | SAFFL                                |
    +------------------------------+---------------------------------+--------------------------------------+
    | ADTTE                        | TRTP, TRTA, TRTAN               | SAFFL                                |
    +------------------------------+---------------------------------+--------------------------------------+
    | ADQSADAS, ADQSNPIX, ADQSCIBC | TRTP, TRTPN                     | ITTFL, EFFFL,COMP24FL                |
    +------------------------------+---------------------------------+--------------------------------------+

    Treatment variable values are based on the numeric dose level (i.e., 0, 54, 81) to avoid the need for a separate variable that contains the treatment dose.

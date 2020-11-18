# **Overview of Analysis Datasets**

**Overview of Analysis Datasets**

Important information regarding specific analysis data sets can be found below. For full details of all analysis data sets, including key analysis results

## ADAE -- Adverse Events Analysis Data

-   ADAE contains one record per reported event per subject.

-   Subjects who did not report any Adverse Events are not represented in this dataset.

-   The data reference for ADAE is the SDTM AE (Adverse Events) domain and there is a 1-1 correspondence between records in the source and this analysis dataset.

-   These records can be linked uniquely by STUDYID, USUBJID, and AESEQ.

-   As with the SDTM AE data set, all MedDRA code variables (i.e. those variables that end in CD) have missing values and dummy terms have been applied to the MedDRA High Level Term (HLT) and High Level Group Term (HLGT). This is due to the proprietary nature of the MedDRA dictionary and the fact that the data with this project will be made available to the public. In a standard submission, these codes and terms should be non-missing and properly populated.

-   Events of particular interest (dermatologic) are captured in the customized query variable (CQ01NAM) in this dataset.Since ADAE is a source for ADTTE, the first chronological occurrence based on the start dates (and sequence numbers) of the treatment emergent dermatological events are flagged (AOCC01FL) to facilitate traceability between these two analysis datasets.

-   ADAE also contains additional Occurrence Flags to facilitate traceability, reviewability, and easy of reporting between the analysis dataset and the unique counts in the summary tables.

-   For treatment emergent adverse events refer to define.xml documentation for the following variables: AOCCFL, AOCCSFL, and AOCCPFL for summarization at the subject,System Organ Class, and Preferred Term levels, respectively.

-   Similarly, refer to the define.xml documentation for AOCC02FL, AOCC03FL, and AOCC04FL for summarization of serious adverse events at the subject, System Organ Class, and Preferred Term levels.

-   The three deaths reported during the conduct of this study are captured in the Results in Death Flag (AESDTH='Y') and Outcome of Adverse Event (AEOUT='FATAL').

-   The Start Date of the Adverse Event in ADAE is imputed to the first of the month if the day is missing.

-   The Study Day of Event Start (ASTDY) and the Treatment Emergent Analysis Flag (TRTEMFL) are derived based on this imputation and may differ from their corresponding SDTM AE/SUPPAE variables Study Day of Start of Adverse Event (AESTDY) and Treatment Emergent Flag (AETRTEM).

-   ADLBC&BH -- Laboratory Results Chemistry/Hematology Analysis Data\*\* ADLBC and ADLBH contain one record per lab analysis parameter, per time point, per subject.\*\*

-   ADLBC contains lab chemistry parameters and ADLBH contains hematology parameters and these data are derived from the SDTM LB (Laboratory Tests) domain.

-   Two sets of lab parameters exist in ADLBC/ADLBH. One set contains the standardized lab value from the LB domain and the second set contains change from previous visit relative to normal range values.

-   In some of the summaries the derived end-of-treatment visit (AVISITN=99) is also presented.

## ADLBHY -- Laboratory Results Hy's Rule Analysis Data

-   ADLBHY contains one record per lab test code per sample, per subject for the Hy's Law based analysis parameters. ADLBHY is derived from the ADLBC (Laboratory Results Chemistry Analysis Data) analysis dataset. It contains derived parameters based on Hy's law.

## ADQSADAS -- ADAS-COG Data

-   ADQSADAS contains analysis data from the ADAS-Cog questionnaire, one of the primary efficacy endpoints.

-   It contains one record per subject per parameter (ADAS-Cog questionnaire item) per VISIT.

-   Visits are placed into analysis visits (represented by AVISIT and AVISITN) based on the date of the visit and the visit windows.

-   If multiple visits fall into the same visit window, then the one closest to the target date is chosen for analysis.

-   Records where ANL01FL='Y' are the ones that were used for analysis. The last observation carried forward (LOCF) algorithm only considered records used for analysis as candidates to carry forward.

-   Records where DTYPE='LOCF' signify those where AVAL was imputed using the LOCF algorithm.

-   Source data can be traced back to the SDTM.QS domain using USUBJID and QSSEQ.Details on how to derive the primary efficacy result based on ADAS-Cog data can be found in the analysis results metadata in the define.xml.

## ADQSCIBC -- CIBC Data

-   ADQSCIBC contains analysis data from the from CIBIC+ questionnaire, one of the primary efficacy endpoints.

-   It contains one record per subject per VISIT. Note that for all records, PARAM='CIBIC Score'. Visits are placed into analysis visits (represented by AVISIT and AVISITN) based on the date of the visit and the visit windows.

-   If multiple visits fall into the same visit window, then the one closest to the target date is chosen for analysis.

-   Records where ANL01FL='Y' are the ones that were used for analysis. The last observation carried forward (LOCF) algorithm only considered records used for analysis as candidates to carry forward.

-   Records where DTYPE='LOCF' signify those where AVAL was imputed using the LOCF algorithm. Source data can be traced back to the SDTM.QS domain using USUBJID and QSSEQ.

-   Details on how to derive the primary efficacy result based on CIBIC+ data can be found in the analysis results metadata in the define.xml.

## ADQSNPIX -- NPI-X Item Analysis Data

-   ADQSNPIX contains one record per subject per parameter (NPI-X questionnaire item, total score, and mean total score from Week 4 through Week 24) per analysis visit (AVISIT).

-   The analysis visits (represented by AVISIT and AVISITN) are derived from days between assessment date and randomization date and based on the visit windows that were specified in the statistical analysis plan (SAP).

-   If multiple assessments fall into the same visit window, then the one closest to the target day is chosen for analysis. Records where analysis flag (ANL01FL) = 'Y' are the ones that were used for analysis.

-   The last observation carried forward (LOCF) algorithm was not used for these data.

-   Source data can be traced back to the SDTM.QS domain using USUBJID and QSSEQ. All the NPI-X parameters, except for the mean total score from Week 4 through Week 24 (NPTOTMN), are from SDTM.QS domain.

-   The value of parameter, NPTOTMN, contains the mean total score for each patient who had any assessments from Week 4 through Week 24.

-   The baseline value of the parameter, NPTOTMN, is the same as the baseline value of total score.

-   The baseline value is a covariate in the analysis of covariance (ANCOVA) model.

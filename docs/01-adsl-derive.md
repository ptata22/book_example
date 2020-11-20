# Adsl derivations Derived = 1 level {#Variable}

List of Variables Derived = 1

+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Variable**     | **Label**                          | **Source/Derivation/Comments**                                                            | R Dplyr Snippet                                                                                                                                                                                                    |
+==================+====================================+===========================================================================================+====================================================================================================================================================================================================================+
| STUDYID          | Study Identifier                   | DM.STUDYID                                                                                | `select ( dm , studyid)`                                                                                                                                                                                           |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| USUBJID          | Unique Subject Identifier          | DM.USUBJID                                                                                | `select ( dm , usubjid)`                                                                                                                                                                                           |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| SUBJID           | Subject Identifier for the Study   | DM.SUBJID                                                                                 | `select ( dm , subjid)`                                                                                                                                                                                            |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| SITEID           | Study Site Identifier              | DM.SITEID                                                                                 | `select ( dm , siteid)`                                                                                                                                                                                            |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ARM              | Description of Planned Arm         | DM.ARM                                                                                    | `select ( dm , arm)`                                                                                                                                                                                               |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| TRT01P           | Planned Treatment for Period 01    | DM.ARM                                                                                    | `select ( dm , arm)`                                                                                                                                                                                               |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| TRT01A           | Actual Treatment for Period 01     | TRT01A=TRT01P, i.e., no difference between actual and randomized treatment in this study. | `mutate ( dm , TRT01A= ARM)`                                                                                                                                                                                       |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| TRT01AN          | Actual Treatment for Period 01 (N) | Numeric code for TRT01A which corresponds to the randomized dose                          | `mutate( trt01pn  =ifelse( (arm %in% "Placebo" ) , 0 , ifelse( (arm %in% Xanomeline Low Dose" ) , 54, ifelse( (arm %in% "Xanomeline High Dose" ) , 81 , NA)))`                                                     |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| AGE              | Age                                | DM.AGE                                                                                    | `select ( dm , age)`                                                                                                                                                                                               |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RACE             | Race                               | DM.RACE                                                                                   | `select ( dm , race)`                                                                                                                                                                                              |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RACEN            | Race (N)                           | Numeric code for RACE                                                                     | `case_when( race %in% "WHITE" ~ 1 , race %in% "BLACK OR AFRICAN AMERICAN" ~ 2 ,                           race %in% "AMERICAN INDIAN OR ALASKA NATIVE" ~ 6 ,                              race %in% "ASIAN" ~ 7 )` |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| SEX              | Sex                                | DM.SEX                                                                                    | `select(dm,sex)`                                                                                                                                                                                                   |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ETHNIC           | Ethnicity                          | DM.ETHNIC                                                                                 | `select(dm,ethnic)`                                                                                                                                                                                                |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| DTHFL            | Subject Died?                      | DM.DTHFL                                                                                  | `select(dm,dthfl)`                                                                                                                                                                                                 |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RFSTDTC          | Subject Reference Start Date/Time  | DM.RFSTDTC                                                                                | `select(dm,rfstdtc)`                                                                                                                                                                                               |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RFENDTC          | Subject Reference End Date/Time    | DM.RFENDTC                                                                                | `select(dm,rfendtc)`                                                                                                                                                                                               |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                  |                                    |                                                                                           |                                                                                                                                                                                                                    |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                  |                                    |                                                                                           |                                                                                                                                                                                                                    |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                  |                                    |                                                                                           |                                                                                                                                                                                                                    |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                  |                                    |                                                                                           |                                                                                                                                                                                                                    |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                  |                                    |                                                                                           |                                                                                                                                                                                                                    |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                  |                                    |                                                                                           |                                                                                                                                                                                                                    |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                  |                                    |                                                                                           |                                                                                                                                                                                                                    |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                  |                                    |                                                                                           |                                                                                                                                                                                                                    |
+------------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

## Overview 

#### Important Functions {.history}

dplyr is a grammar of data manipulation, providing a consistent set of verbs that help you solve the most common data manipulation challenges:

-   [`mutate()`](https://dplyr.tidyverse.org/reference/mutate.html) adds new variables that are functions of existing variables

-   [`select()`](https://dplyr.tidyverse.org/reference/select.html) picks variables based on their names.

-   [`filter()`](https://dplyr.tidyverse.org/reference/filter.html) picks cases based on their values.

-   [`summarise()`](https://dplyr.tidyverse.org/reference/summarise.html) reduces multiple values down to a single summary.

-   [`arrange()`](https://dplyr.tidyverse.org/reference/arrange.html) changes the ordering of the rows.

## Your Turn {.exercise}

1.  \*\*List out various Character and Numeric Dplyr functions\*\*

    [[Learn to use R Dplyr Package]](https://dplyr.tidyverse.org/)

    List out all the functions for your Data manipulation

    ## Let's start programming 

    1.  Initialize all the Library's needed for the project


```r
#intilizing the Dplyr library
library(tidyverse)
```

```
## -- Attaching packages --------- tidyverse 1.3.0 --
```

```
## v ggplot2 3.3.2     v purrr   0.3.4
## v tibble  3.0.3     v dplyr   1.0.2
## v tidyr   1.1.2     v stringr 1.4.0
## v readr   1.3.1     v forcats 0.5.0
```

```
## -- Conflicts ------------ tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```


```r
# dm <- clinicalfd::dm 
 names(clinicalfd::dm )
```

```
##  [1] "studyid"  "domain"   "usubjid"  "subjid"   "rfstdtc"  "rfendtc" 
##  [7] "rfxstdtc" "rfxendtc" "rficdtc"  "rfpendtc" "dthdtc"   "dthfl"   
## [13] "siteid"   "age"      "ageu"     "sex"      "race"     "ethnic"  
## [19] "armcd"    "arm"      "actarmcd" "actarm"   "country"  "dmdtc"   
## [25] "dmdy"
```

```r
dm <- clinicalfd::dm
dm  <- dplyr :: filter(dm ,arm !="Screen Failure" )
adsl_deri01 <- dplyr::select ( dm , usubjid , siteid,arm) # Select 

#dm_01 <- mutate (dm_01 , usubjid = as.character(usubjid) )


adsl_deri01 <- dplyr::mutate( adsl_deri01 , TRT01P = arm) 
#Use of Mutate function to create new variable#
```

## Adsl Derivation Code part-1


```r
adsl_deri01 <- dm  %>% 
  filter (actarmcd !="Scrnfail")  %>% 
  mutate(sitegr1 = siteid , trt01p = arm , trt01a = arm , 
  trt01pn  = ifelse( (arm %in% "Placebo" ) , 0 ,
           ifelse( (arm %in% "Xanomeline Low Dose" ) , 54,
           ifelse( (arm %in% "Xanomeline High Dose" ) , 81 , NA))) ,
           trt01an = trt01pn ,
           ittfl   = ifelse (trt01pn %in% c(0,54,81) , "Y" , "N" ),
           agegr1  = case_when( age < 65  ~ "<65" , 
                              (65 <= age & age <= 80 ) ~ "65-80"  , 
                               (age > 80 ) ~ ">80"  ),

           
            agegr1n  = case_when( age < 65  ~ 1  , 
                                (65 <= age & age <= 80 ) ~ 2  , 
                                (age > 80 ) ~ 3  ),

           race  = case_when( race %in% "WHITE" ~ "WHITE" , 
                              race %in% "BLACK OR AFRICAN AMERICAN" ~                                "BLACK OR AFRICAN AMERICAN" ,
                              
            race %in% "AMERICAN INDIAN OR ALASKA NATIVE" ~ "AMERICAN INDIAN OR ALASKA NATIVE" ,
            race %in% "ASIAN" ~ "ASIAN" ) , 
            racen  = case_when( race %in% "WHITE" ~ 1 , 
            race %in% "BLACK OR AFRICAN AMERICAN" ~ 2 ,
            race %in% "AMERICAN INDIAN OR ALASKA NATIVE" ~ 6 ,
            race %in% "ASIAN" ~ 7 ),
            sex  =  case_when(sex %in% "F" ~ "Female"  , 
                             sex %in% "M" ~ "Male"    , 
                             sex %in% "U" ~  "Unknown" ) , 
           ethnic  =  case_when(ethnic %in% "NOT HISPANIC OR LATINO" ~ "NOT HISPANIC OR LATINO"  , 
           ethnic %in% "HISPANIC OR LATINO" ~ "HISPANIC OR LATINO"  , 
           ethnic %in% "U" ~  "Unknown" )
)


adsl_deri02 <- adsl_deri01 %>%  
               select (actarmcd , sitegr1, siteid , trt01p , arm , trt01a , trt01pn               ,trt01pn,ittfl,agegr1,age,agegr1n,race,racen,sex,ethnic )
adsl_deri02
```

```
##     actarmcd sitegr1 siteid               trt01p                  arm
## 1        Pbo     701    701              Placebo              Placebo
## 2        Pbo     701    701              Placebo              Placebo
## 3     Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 4     Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 5     Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 6        Pbo     701    701              Placebo              Placebo
## 7     Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 8     Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 9     Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 10       Pbo     701    701              Placebo              Placebo
## 11       Pbo     701    701              Placebo              Placebo
## 12    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 13    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 14    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 15       Pbo     701    701              Placebo              Placebo
## 16    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 17    Xan_Lo     701    701 Xanomeline High Dose Xanomeline High Dose
## 18    Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 19    Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 20       Pbo     701    701              Placebo              Placebo
## 21    Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 22       Pbo     701    701              Placebo              Placebo
## 23    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 24    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 25    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 26    Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 27    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 28    Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 29    Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 30    Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 31       Pbo     701    701              Placebo              Placebo
## 32    Xan_Lo     701    701 Xanomeline High Dose Xanomeline High Dose
## 33       Pbo     701    701              Placebo              Placebo
## 34    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 35       Pbo     701    701              Placebo              Placebo
## 36       Pbo     701    701              Placebo              Placebo
## 37       Pbo     701    701              Placebo              Placebo
## 38    Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 39       Pbo     701    701              Placebo              Placebo
## 40    Xan_Lo     701    701  Xanomeline Low Dose  Xanomeline Low Dose
## 41    Xan_Hi     701    701 Xanomeline High Dose Xanomeline High Dose
## 42    Xan_Lo     702    702  Xanomeline Low Dose  Xanomeline Low Dose
## 43       Pbo     703    703              Placebo              Placebo
## 44    Xan_Hi     703    703 Xanomeline High Dose Xanomeline High Dose
## 45    Xan_Lo     703    703  Xanomeline Low Dose  Xanomeline Low Dose
## 46       Pbo     703    703              Placebo              Placebo
## 47       Pbo     703    703              Placebo              Placebo
## 48    Xan_Lo     703    703  Xanomeline Low Dose  Xanomeline Low Dose
## 49       Pbo     703    703              Placebo              Placebo
## 50    Xan_Lo     703    703  Xanomeline Low Dose  Xanomeline Low Dose
## 51    Xan_Lo     703    703  Xanomeline Low Dose  Xanomeline Low Dose
## 52       Pbo     703    703              Placebo              Placebo
## 53    Xan_Hi     703    703 Xanomeline High Dose Xanomeline High Dose
## 54    Xan_Lo     703    703  Xanomeline Low Dose  Xanomeline Low Dose
## 55    Xan_Hi     703    703 Xanomeline High Dose Xanomeline High Dose
## 56       Pbo     703    703              Placebo              Placebo
## 57    Xan_Hi     703    703 Xanomeline High Dose Xanomeline High Dose
## 58    Xan_Lo     703    703  Xanomeline Low Dose  Xanomeline Low Dose
## 59    Xan_Lo     703    703 Xanomeline High Dose Xanomeline High Dose
## 60    Xan_Hi     703    703 Xanomeline High Dose Xanomeline High Dose
## 61    Xan_Hi     704    704 Xanomeline High Dose Xanomeline High Dose
## 62    Xan_Lo     704    704  Xanomeline Low Dose  Xanomeline Low Dose
## 63       Pbo     704    704              Placebo              Placebo
## 64    Xan_Hi     704    704 Xanomeline High Dose Xanomeline High Dose
## 65    Xan_Lo     704    704  Xanomeline Low Dose  Xanomeline Low Dose
## 66    Xan_Hi     704    704 Xanomeline High Dose Xanomeline High Dose
## 67    Xan_Hi     704    704 Xanomeline High Dose Xanomeline High Dose
## 68    Xan_Hi     704    704 Xanomeline High Dose Xanomeline High Dose
## 69    Xan_Lo     704    704  Xanomeline Low Dose  Xanomeline Low Dose
## 70    Xan_Lo     704    704  Xanomeline Low Dose  Xanomeline Low Dose
## 71       Pbo     704    704              Placebo              Placebo
## 72    Xan_Lo     704    704  Xanomeline Low Dose  Xanomeline Low Dose
## 73       Pbo     704    704              Placebo              Placebo
## 74    Xan_Lo     704    704  Xanomeline Low Dose  Xanomeline Low Dose
## 75       Pbo     704    704              Placebo              Placebo
## 76    Xan_Hi     704    704 Xanomeline High Dose Xanomeline High Dose
## 77       Pbo     704    704              Placebo              Placebo
## 78    Xan_Hi     704    704 Xanomeline High Dose Xanomeline High Dose
## 79    Xan_Lo     704    704  Xanomeline Low Dose  Xanomeline Low Dose
## 80    Xan_Lo     704    704  Xanomeline Low Dose  Xanomeline Low Dose
## 81    Xan_Hi     704    704 Xanomeline High Dose Xanomeline High Dose
## 82       Pbo     704    704              Placebo              Placebo
## 83       Pbo     704    704              Placebo              Placebo
## 84       Pbo     704    704              Placebo              Placebo
## 85       Pbo     704    704              Placebo              Placebo
## 86       Pbo     705    705              Placebo              Placebo
## 87    Xan_Lo     705    705  Xanomeline Low Dose  Xanomeline Low Dose
## 88       Pbo     705    705              Placebo              Placebo
## 89       Pbo     705    705              Placebo              Placebo
## 90    Xan_Lo     705    705  Xanomeline Low Dose  Xanomeline Low Dose
## 91    Xan_Hi     705    705 Xanomeline High Dose Xanomeline High Dose
## 92    Xan_Hi     705    705 Xanomeline High Dose Xanomeline High Dose
## 93       Pbo     705    705              Placebo              Placebo
## 94    Xan_Lo     705    705  Xanomeline Low Dose  Xanomeline Low Dose
## 95    Xan_Hi     705    705 Xanomeline High Dose Xanomeline High Dose
## 96    Xan_Hi     705    705 Xanomeline High Dose Xanomeline High Dose
## 97       Pbo     705    705              Placebo              Placebo
## 98    Xan_Hi     705    705 Xanomeline High Dose Xanomeline High Dose
## 99    Xan_Lo     705    705 Xanomeline High Dose Xanomeline High Dose
## 100   Xan_Lo     705    705  Xanomeline Low Dose  Xanomeline Low Dose
## 101   Xan_Lo     705    705  Xanomeline Low Dose  Xanomeline Low Dose
## 102      Pbo     706    706              Placebo              Placebo
## 103   Xan_Hi     706    706 Xanomeline High Dose Xanomeline High Dose
## 104   Xan_Lo     706    706  Xanomeline Low Dose  Xanomeline Low Dose
## 105   Xan_Lo     707    707  Xanomeline Low Dose  Xanomeline Low Dose
## 106      Pbo     707    707              Placebo              Placebo
## 107   Xan_Lo     708    708  Xanomeline Low Dose  Xanomeline Low Dose
## 108   Xan_Lo     708    708  Xanomeline Low Dose  Xanomeline Low Dose
## 109   Xan_Lo     708    708  Xanomeline Low Dose  Xanomeline Low Dose
## 110      Pbo     708    708              Placebo              Placebo
## 111      Pbo     708    708              Placebo              Placebo
## 112      Pbo     708    708              Placebo              Placebo
## 113   Xan_Hi     708    708 Xanomeline High Dose Xanomeline High Dose
## 114   Xan_Lo     708    708 Xanomeline High Dose Xanomeline High Dose
## 115   Xan_Hi     708    708 Xanomeline High Dose Xanomeline High Dose
## 116   Xan_Lo     708    708 Xanomeline High Dose Xanomeline High Dose
## 117      Pbo     708    708              Placebo              Placebo
## 118   Xan_Lo     708    708  Xanomeline Low Dose  Xanomeline Low Dose
## 119      Pbo     708    708              Placebo              Placebo
## 120      Pbo     708    708              Placebo              Placebo
## 121   Xan_Lo     708    708  Xanomeline Low Dose  Xanomeline Low Dose
## 122      Pbo     708    708              Placebo              Placebo
## 123   Xan_Hi     708    708 Xanomeline High Dose Xanomeline High Dose
## 124      Pbo     708    708              Placebo              Placebo
## 125   Xan_Hi     708    708 Xanomeline High Dose Xanomeline High Dose
## 126   Xan_Lo     708    708  Xanomeline Low Dose  Xanomeline Low Dose
## 127   Xan_Lo     708    708  Xanomeline Low Dose  Xanomeline Low Dose
## 128   Xan_Lo     708    708 Xanomeline High Dose Xanomeline High Dose
## 129      Pbo     708    708              Placebo              Placebo
## 130   Xan_Hi     708    708 Xanomeline High Dose Xanomeline High Dose
## 131   Xan_Lo     708    708  Xanomeline Low Dose  Xanomeline Low Dose
## 132      Pbo     709    709              Placebo              Placebo
## 133   Xan_Lo     709    709  Xanomeline Low Dose  Xanomeline Low Dose
## 134   Xan_Lo     709    709  Xanomeline Low Dose  Xanomeline Low Dose
## 135   Xan_Hi     709    709 Xanomeline High Dose Xanomeline High Dose
## 136   Xan_Lo     709    709  Xanomeline Low Dose  Xanomeline Low Dose
## 137      Pbo     709    709              Placebo              Placebo
## 138   Xan_Hi     709    709 Xanomeline High Dose Xanomeline High Dose
## 139   Xan_Lo     709    709  Xanomeline Low Dose  Xanomeline Low Dose
## 140   Xan_Hi     709    709 Xanomeline High Dose Xanomeline High Dose
## 141   Xan_Lo     709    709  Xanomeline Low Dose  Xanomeline Low Dose
## 142   Xan_Hi     709    709 Xanomeline High Dose Xanomeline High Dose
## 143      Pbo     709    709              Placebo              Placebo
## 144   Xan_Lo     709    709  Xanomeline Low Dose  Xanomeline Low Dose
## 145      Pbo     709    709              Placebo              Placebo
## 146      Pbo     709    709              Placebo              Placebo
## 147   Xan_Hi     709    709 Xanomeline High Dose Xanomeline High Dose
## 148      Pbo     709    709              Placebo              Placebo
## 149   Xan_Lo     709    709  Xanomeline Low Dose  Xanomeline Low Dose
## 150   Xan_Lo     709    709 Xanomeline High Dose Xanomeline High Dose
## 151      Pbo     709    709              Placebo              Placebo
## 152   Xan_Lo     709    709 Xanomeline High Dose Xanomeline High Dose
## 153   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 154   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 155   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 156      Pbo     710    710              Placebo              Placebo
## 157   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 158   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 159      Pbo     710    710              Placebo              Placebo
## 160   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 161      Pbo     710    710              Placebo              Placebo
## 162      Pbo     710    710              Placebo              Placebo
## 163      Pbo     710    710              Placebo              Placebo
## 164   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 165   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 166   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 167   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 168      Pbo     710    710              Placebo              Placebo
## 169   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 170   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 171   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 172      Pbo     710    710              Placebo              Placebo
## 173   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 174      Pbo     710    710              Placebo              Placebo
## 175   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 176   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 177      Pbo     710    710              Placebo              Placebo
## 178      Pbo     710    710              Placebo              Placebo
## 179   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 180   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 181      Pbo     710    710              Placebo              Placebo
## 182   Xan_Lo     710    710  Xanomeline Low Dose  Xanomeline Low Dose
## 183   Xan_Hi     710    710 Xanomeline High Dose Xanomeline High Dose
## 184   Xan_Hi     711    711 Xanomeline High Dose Xanomeline High Dose
## 185      Pbo     711    711              Placebo              Placebo
## 186   Xan_Lo     711    711  Xanomeline Low Dose  Xanomeline Low Dose
## 187   Xan_Lo     711    711 Xanomeline High Dose Xanomeline High Dose
## 188   Xan_Lo     713    713  Xanomeline Low Dose  Xanomeline Low Dose
## 189   Xan_Lo     713    713  Xanomeline Low Dose  Xanomeline Low Dose
## 190   Xan_Hi     713    713 Xanomeline High Dose Xanomeline High Dose
## 191   Xan_Hi     713    713 Xanomeline High Dose Xanomeline High Dose
## 192      Pbo     713    713              Placebo              Placebo
## 193   Xan_Hi     713    713 Xanomeline High Dose Xanomeline High Dose
## 194      Pbo     713    713              Placebo              Placebo
## 195      Pbo     713    713              Placebo              Placebo
## 196   Xan_Lo     713    713  Xanomeline Low Dose  Xanomeline Low Dose
## 197      Pbo     714    714              Placebo              Placebo
## 198   Xan_Lo     714    714  Xanomeline Low Dose  Xanomeline Low Dose
## 199   Xan_Lo     714    714  Xanomeline Low Dose  Xanomeline Low Dose
## 200   Xan_Hi     714    714 Xanomeline High Dose Xanomeline High Dose
## 201      Pbo     714    714              Placebo              Placebo
## 202   Xan_Lo     714    714 Xanomeline High Dose Xanomeline High Dose
## 203   Xan_Lo     715    715  Xanomeline Low Dose  Xanomeline Low Dose
## 204   Xan_Lo     715    715  Xanomeline Low Dose  Xanomeline Low Dose
## 205      Pbo     715    715              Placebo              Placebo
## 206      Pbo     715    715              Placebo              Placebo
## 207   Xan_Hi     715    715 Xanomeline High Dose Xanomeline High Dose
## 208   Xan_Hi     715    715 Xanomeline High Dose Xanomeline High Dose
## 209      Pbo     715    715              Placebo              Placebo
## 210   Xan_Lo     715    715  Xanomeline Low Dose  Xanomeline Low Dose
## 211      Pbo     716    716              Placebo              Placebo
## 212      Pbo     716    716              Placebo              Placebo
## 213   Xan_Lo     716    716 Xanomeline High Dose Xanomeline High Dose
## 214      Pbo     716    716              Placebo              Placebo
## 215   Xan_Lo     716    716  Xanomeline Low Dose  Xanomeline Low Dose
## 216   Xan_Hi     716    716 Xanomeline High Dose Xanomeline High Dose
## 217   Xan_Lo     716    716  Xanomeline Low Dose  Xanomeline Low Dose
## 218   Xan_Lo     716    716  Xanomeline Low Dose  Xanomeline Low Dose
## 219      Pbo     716    716              Placebo              Placebo
## 220   Xan_Lo     716    716  Xanomeline Low Dose  Xanomeline Low Dose
## 221   Xan_Lo     716    716  Xanomeline Low Dose  Xanomeline Low Dose
## 222      Pbo     716    716              Placebo              Placebo
## 223   Xan_Lo     716    716  Xanomeline Low Dose  Xanomeline Low Dose
## 224      Pbo     716    716              Placebo              Placebo
## 225   Xan_Hi     716    716 Xanomeline High Dose Xanomeline High Dose
## 226   Xan_Hi     716    716 Xanomeline High Dose Xanomeline High Dose
## 227   Xan_Lo     716    716  Xanomeline Low Dose  Xanomeline Low Dose
## 228      Pbo     716    716              Placebo              Placebo
## 229   Xan_Lo     716    716  Xanomeline Low Dose  Xanomeline Low Dose
## 230   Xan_Hi     716    716 Xanomeline High Dose Xanomeline High Dose
## 231   Xan_Hi     716    716 Xanomeline High Dose Xanomeline High Dose
## 232   Xan_Hi     716    716 Xanomeline High Dose Xanomeline High Dose
## 233      Pbo     716    716              Placebo              Placebo
## 234   Xan_Hi     716    716 Xanomeline High Dose Xanomeline High Dose
## 235   Xan_Lo     717    717  Xanomeline Low Dose  Xanomeline Low Dose
## 236   Xan_Hi     717    717 Xanomeline High Dose Xanomeline High Dose
## 237   Xan_Hi     717    717 Xanomeline High Dose Xanomeline High Dose
## 238      Pbo     717    717              Placebo              Placebo
## 239      Pbo     717    717              Placebo              Placebo
## 240   Xan_Hi     717    717 Xanomeline High Dose Xanomeline High Dose
## 241   Xan_Lo     717    717  Xanomeline Low Dose  Xanomeline Low Dose
## 242   Xan_Lo     718    718  Xanomeline Low Dose  Xanomeline Low Dose
## 243   Xan_Lo     718    718  Xanomeline Low Dose  Xanomeline Low Dose
## 244   Xan_Hi     718    718 Xanomeline High Dose Xanomeline High Dose
## 245      Pbo     718    718              Placebo              Placebo
## 246      Pbo     718    718              Placebo              Placebo
## 247   Xan_Lo     718    718  Xanomeline Low Dose  Xanomeline Low Dose
## 248      Pbo     718    718              Placebo              Placebo
## 249   Xan_Lo     718    718  Xanomeline Low Dose  Xanomeline Low Dose
## 250   Xan_Lo     718    718  Xanomeline Low Dose  Xanomeline Low Dose
## 251   Xan_Hi     718    718 Xanomeline High Dose Xanomeline High Dose
## 252      Pbo     718    718              Placebo              Placebo
## 253   Xan_Hi     718    718 Xanomeline High Dose Xanomeline High Dose
## 254   Xan_Hi     718    718 Xanomeline High Dose Xanomeline High Dose
##                   trt01a trt01pn ittfl agegr1 age agegr1n
## 1                Placebo       0     Y    <65  63       1
## 2                Placebo       0     Y    <65  64       1
## 3   Xanomeline High Dose      81     Y  65-80  71       2
## 4    Xanomeline Low Dose      54     Y  65-80  74       2
## 5   Xanomeline High Dose      81     Y  65-80  77       2
## 6                Placebo       0     Y    >80  85       3
## 7    Xanomeline Low Dose      54     Y  65-80  68       2
## 8    Xanomeline Low Dose      54     Y    >80  81       3
## 9    Xanomeline Low Dose      54     Y    >80  84       3
## 10               Placebo       0     Y    <65  52       1
## 11               Placebo       0     Y    >80  84       3
## 12  Xanomeline High Dose      81     Y    >80  81       3
## 13  Xanomeline High Dose      81     Y  65-80  75       2
## 14  Xanomeline High Dose      81     Y    <65  57       1
## 15               Placebo       0     Y  65-80  79       2
## 16  Xanomeline High Dose      81     Y    <65  56       1
## 17  Xanomeline High Dose      81     Y  65-80  79       2
## 18   Xanomeline Low Dose      54     Y  65-80  71       2
## 19   Xanomeline Low Dose      54     Y  65-80  80       2
## 20               Placebo       0     Y    >80  81       3
## 21   Xanomeline Low Dose      54     Y  65-80  76       2
## 22               Placebo       0     Y  65-80  69       2
## 23  Xanomeline High Dose      81     Y    <65  56       1
## 24  Xanomeline High Dose      81     Y    <65  61       1
## 25  Xanomeline High Dose      81     Y    <65  56       1
## 26   Xanomeline Low Dose      54     Y  65-80  67       2
## 27  Xanomeline High Dose      81     Y    <65  61       1
## 28   Xanomeline Low Dose      54     Y  65-80  68       2
## 29   Xanomeline Low Dose      54     Y  65-80  79       2
## 30   Xanomeline Low Dose      54     Y    <65  51       1
## 31               Placebo       0     Y    <65  63       1
## 32  Xanomeline High Dose      81     Y  65-80  67       2
## 33               Placebo       0     Y    >80  81       3
## 34  Xanomeline High Dose      81     Y  65-80  72       2
## 35               Placebo       0     Y    >80  87       3
## 36               Placebo       0     Y  65-80  78       2
## 37               Placebo       0     Y    >80  85       3
## 38   Xanomeline Low Dose      54     Y    >80  84       3
## 39               Placebo       0     Y  65-80  70       2
## 40   Xanomeline Low Dose      54     Y    <65  57       1
## 41  Xanomeline High Dose      81     Y    <65  63       1
## 42   Xanomeline Low Dose      54     Y    >80  84       3
## 43               Placebo       0     Y    <65  64       1
## 44  Xanomeline High Dose      81     Y  65-80  69       2
## 45   Xanomeline Low Dose      54     Y  65-80  71       2
## 46               Placebo       0     Y    >80  81       3
## 47               Placebo       0     Y    >80  84       3
## 48   Xanomeline Low Dose      54     Y    >80  81       3
## 49               Placebo       0     Y  65-80  75       2
## 50   Xanomeline Low Dose      54     Y    >80  84       3
## 51   Xanomeline Low Dose      54     Y  65-80  76       2
## 52               Placebo       0     Y  65-80  72       2
## 53  Xanomeline High Dose      81     Y  65-80  78       2
## 54   Xanomeline Low Dose      54     Y  65-80  72       2
## 55  Xanomeline High Dose      81     Y    >80  88       3
## 56               Placebo       0     Y    >80  81       3
## 57  Xanomeline High Dose      81     Y  65-80  67       2
## 58   Xanomeline Low Dose      54     Y    >80  81       3
## 59  Xanomeline High Dose      81     Y  65-80  67       2
## 60  Xanomeline High Dose      81     Y  65-80  76       2
## 61  Xanomeline High Dose      81     Y  65-80  76       2
## 62   Xanomeline Low Dose      54     Y    >80  83       3
## 63               Placebo       0     Y  65-80  80       2
## 64  Xanomeline High Dose      81     Y  65-80  77       2
## 65   Xanomeline Low Dose      54     Y    >80  81       3
## 66  Xanomeline High Dose      81     Y  65-80  75       2
## 67  Xanomeline High Dose      81     Y  65-80  80       2
## 68  Xanomeline High Dose      81     Y  65-80  79       2
## 69   Xanomeline Low Dose      54     Y  65-80  77       2
## 70   Xanomeline Low Dose      54     Y  65-80  71       2
## 71               Placebo       0     Y    >80  84       3
## 72   Xanomeline Low Dose      54     Y  65-80  74       2
## 73               Placebo       0     Y  65-80  67       2
## 74   Xanomeline Low Dose      54     Y    >80  81       3
## 75               Placebo       0     Y    >80  87       3
## 76  Xanomeline High Dose      81     Y    >80  86       3
## 77               Placebo       0     Y  65-80  71       2
## 78  Xanomeline High Dose      81     Y    >80  82       3
## 79   Xanomeline Low Dose      54     Y  65-80  68       2
## 80   Xanomeline Low Dose      54     Y    >80  81       3
## 81  Xanomeline High Dose      81     Y  65-80  80       2
## 82               Placebo       0     Y  65-80  70       2
## 83               Placebo       0     Y    >80  81       3
## 84               Placebo       0     Y  65-80  74       2
## 85               Placebo       0     Y  65-80  75       2
## 86               Placebo       0     Y  65-80  69       2
## 87   Xanomeline Low Dose      54     Y    <65  56       1
## 88               Placebo       0     Y  65-80  66       2
## 89               Placebo       0     Y    >80  84       3
## 90   Xanomeline Low Dose      54     Y    >80  87       3
## 91  Xanomeline High Dose      81     Y    <65  56       1
## 92  Xanomeline High Dose      81     Y  65-80  73       2
## 93               Placebo       0     Y  65-80  70       2
## 94   Xanomeline Low Dose      54     Y    <65  60       1
## 95  Xanomeline High Dose      81     Y  65-80  72       2
## 96  Xanomeline High Dose      81     Y  65-80  74       2
## 97               Placebo       0     Y    >80  86       3
## 98  Xanomeline High Dose      81     Y    <65  63       1
## 99  Xanomeline High Dose      81     Y    >80  82       3
## 100  Xanomeline Low Dose      54     Y    >80  84       3
## 101  Xanomeline Low Dose      54     Y  65-80  68       2
## 102              Placebo       0     Y    <65  64       1
## 103 Xanomeline High Dose      81     Y    <65  60       1
## 104  Xanomeline Low Dose      54     Y  65-80  74       2
## 105  Xanomeline Low Dose      54     Y  65-80  72       2
## 106              Placebo       0     Y  65-80  65       2
## 107  Xanomeline Low Dose      54     Y  65-80  68       2
## 108  Xanomeline Low Dose      54     Y    <65  62       1
## 109  Xanomeline Low Dose      54     Y  65-80  73       2
## 110              Placebo       0     Y  65-80  74       2
## 111              Placebo       0     Y    >80  81       3
## 112              Placebo       0     Y  65-80  77       2
## 113 Xanomeline High Dose      81     Y  65-80  77       2
## 114 Xanomeline High Dose      81     Y  65-80  76       2
## 115 Xanomeline High Dose      81     Y  65-80  78       2
## 116 Xanomeline High Dose      81     Y    >80  86       3
## 117              Placebo       0     Y    <65  61       1
## 118  Xanomeline Low Dose      54     Y    >80  82       3
## 119              Placebo       0     Y  65-80  80       2
## 120              Placebo       0     Y    <65  57       1
## 121  Xanomeline Low Dose      54     Y    <65  61       1
## 122              Placebo       0     Y  65-80  74       2
## 123 Xanomeline High Dose      81     Y  65-80  73       2
## 124              Placebo       0     Y    <65  59       1
## 125 Xanomeline High Dose      81     Y    <65  61       1
## 126  Xanomeline Low Dose      54     Y  65-80  79       2
## 127  Xanomeline Low Dose      54     Y    >80  87       3
## 128 Xanomeline High Dose      81     Y    >80  84       3
## 129              Placebo       0     Y  65-80  67       2
## 130 Xanomeline High Dose      81     Y  65-80  71       2
## 131  Xanomeline Low Dose      54     Y    >80  84       3
## 132              Placebo       0     Y  65-80  76       2
## 133  Xanomeline Low Dose      54     Y    <65  54       1
## 134  Xanomeline Low Dose      54     Y  65-80  72       2
## 135 Xanomeline High Dose      81     Y    >80  82       3
## 136  Xanomeline Low Dose      54     Y    >80  86       3
## 137              Placebo       0     Y  65-80  69       2
## 138 Xanomeline High Dose      81     Y  65-80  79       2
## 139  Xanomeline Low Dose      54     Y  65-80  71       2
## 140 Xanomeline High Dose      81     Y  65-80  72       2
## 141  Xanomeline Low Dose      54     Y  65-80  77       2
## 142 Xanomeline High Dose      81     Y  65-80  69       2
## 143              Placebo       0     Y    >80  82       3
## 144  Xanomeline Low Dose      54     Y    >80  87       3
## 145              Placebo       0     Y    <65  62       1
## 146              Placebo       0     Y    <65  60       1
## 147 Xanomeline High Dose      81     Y  65-80  65       2
## 148              Placebo       0     Y  65-80  68       2
## 149  Xanomeline Low Dose      54     Y  65-80  75       2
## 150 Xanomeline High Dose      81     Y  65-80  70       2
## 151              Placebo       0     Y    >80  81       3
## 152 Xanomeline High Dose      81     Y  65-80  77       2
## 153  Xanomeline Low Dose      54     Y    >80  88       3
## 154 Xanomeline High Dose      81     Y  65-80  77       2
## 155 Xanomeline High Dose      81     Y  65-80  79       2
## 156              Placebo       0     Y    >80  83       3
## 157  Xanomeline Low Dose      54     Y    >80  83       3
## 158  Xanomeline Low Dose      54     Y    >80  84       3
## 159              Placebo       0     Y    >80  82       3
## 160 Xanomeline High Dose      81     Y    >80  85       3
## 161              Placebo       0     Y  65-80  76       2
## 162              Placebo       0     Y    >80  81       3
## 163              Placebo       0     Y    >80  89       3
## 164 Xanomeline High Dose      81     Y  65-80  79       2
## 165 Xanomeline High Dose      81     Y  65-80  76       2
## 166  Xanomeline Low Dose      54     Y    >80  84       3
## 167  Xanomeline Low Dose      54     Y    >80  81       3
## 168              Placebo       0     Y  65-80  80       2
## 169 Xanomeline High Dose      81     Y  65-80  78       2
## 170  Xanomeline Low Dose      54     Y    <65  56       1
## 171 Xanomeline High Dose      81     Y  65-80  79       2
## 172              Placebo       0     Y  65-80  78       2
## 173  Xanomeline Low Dose      54     Y    >80  83       3
## 174              Placebo       0     Y    >80  86       3
## 175 Xanomeline High Dose      81     Y    >80  81       3
## 176  Xanomeline Low Dose      54     Y  65-80  78       2
## 177              Placebo       0     Y  65-80  78       2
## 178              Placebo       0     Y    >80  83       3
## 179 Xanomeline High Dose      81     Y  65-80  73       2
## 180  Xanomeline Low Dose      54     Y    >80  82       3
## 181              Placebo       0     Y    >80  88       3
## 182  Xanomeline Low Dose      54     Y  65-80  77       2
## 183 Xanomeline High Dose      81     Y  65-80  80       2
## 184 Xanomeline High Dose      81     Y  65-80  67       2
## 185              Placebo       0     Y  65-80  70       2
## 186  Xanomeline Low Dose      54     Y  65-80  76       2
## 187 Xanomeline High Dose      81     Y    >80  84       3
## 188  Xanomeline Low Dose      54     Y  65-80  78       2
## 189  Xanomeline Low Dose      54     Y  65-80  74       2
## 190 Xanomeline High Dose      81     Y  65-80  74       2
## 191 Xanomeline High Dose      81     Y  65-80  79       2
## 192              Placebo       0     Y    <65  64       1
## 193 Xanomeline High Dose      81     Y  65-80  77       2
## 194              Placebo       0     Y  65-80  71       2
## 195              Placebo       0     Y  65-80  73       2
## 196  Xanomeline Low Dose      54     Y  65-80  71       2
## 197              Placebo       0     Y    >80  88       3
## 198  Xanomeline Low Dose      54     Y  65-80  79       2
## 199  Xanomeline Low Dose      54     Y  65-80  75       2
## 200 Xanomeline High Dose      81     Y  65-80  77       2
## 201              Placebo       0     Y  65-80  78       2
## 202 Xanomeline High Dose      81     Y    >80  81       3
## 203  Xanomeline Low Dose      54     Y  65-80  77       2
## 204  Xanomeline Low Dose      54     Y  65-80  65       2
## 205              Placebo       0     Y    <65  59       1
## 206              Placebo       0     Y  65-80  78       2
## 207 Xanomeline High Dose      81     Y  65-80  65       2
## 208 Xanomeline High Dose      81     Y  65-80  75       2
## 209              Placebo       0     Y  65-80  76       2
## 210  Xanomeline Low Dose      54     Y  65-80  69       2
## 211              Placebo       0     Y    >80  87       3
## 212              Placebo       0     Y  65-80  73       2
## 213 Xanomeline High Dose      81     Y    >80  83       3
## 214              Placebo       0     Y  65-80  74       2
## 215  Xanomeline Low Dose      54     Y  65-80  80       2
## 216 Xanomeline High Dose      81     Y  65-80  78       2
## 217  Xanomeline Low Dose      54     Y    >80  82       3
## 218  Xanomeline Low Dose      54     Y  65-80  79       2
## 219              Placebo       0     Y    >80  86       3
## 220  Xanomeline Low Dose      54     Y    >80  83       3
## 221  Xanomeline Low Dose      54     Y    >80  85       3
## 222              Placebo       0     Y    >80  83       3
## 223  Xanomeline Low Dose      54     Y  65-80  68       2
## 224              Placebo       0     Y  65-80  72       2
## 225 Xanomeline High Dose      81     Y    >80  81       3
## 226 Xanomeline High Dose      81     Y  65-80  73       2
## 227  Xanomeline Low Dose      54     Y  65-80  76       2
## 228              Placebo       0     Y  65-80  76       2
## 229  Xanomeline Low Dose      54     Y  65-80  78       2
## 230 Xanomeline High Dose      81     Y    >80  84       3
## 231 Xanomeline High Dose      81     Y  65-80  74       2
## 232 Xanomeline High Dose      81     Y  65-80  80       2
## 233              Placebo       0     Y    >80  85       3
## 234 Xanomeline High Dose      81     Y  65-80  72       2
## 235  Xanomeline Low Dose      54     Y  65-80  80       2
## 236 Xanomeline High Dose      81     Y    >80  84       3
## 237 Xanomeline High Dose      81     Y  65-80  73       2
## 238              Placebo       0     Y    >80  85       3
## 239              Placebo       0     Y    <65  64       1
## 240 Xanomeline High Dose      81     Y  65-80  77       2
## 241  Xanomeline Low Dose      54     Y  65-80  75       2
## 242  Xanomeline Low Dose      54     Y  65-80  79       2
## 243  Xanomeline Low Dose      54     Y  65-80  67       2
## 244 Xanomeline High Dose      81     Y    >80  82       3
## 245              Placebo       0     Y  65-80  77       2
## 246              Placebo       0     Y  65-80  73       2
## 247  Xanomeline Low Dose      54     Y  65-80  80       2
## 248              Placebo       0     Y  65-80  74       2
## 249  Xanomeline Low Dose      54     Y    >80  82       3
## 250  Xanomeline Low Dose      54     Y  65-80  78       2
## 251 Xanomeline High Dose      81     Y    >80  86       3
## 252              Placebo       0     Y  65-80  79       2
## 253 Xanomeline High Dose      81     Y  65-80  69       2
## 254 Xanomeline High Dose      81     Y  65-80  74       2
##                                 race racen    sex                 ethnic
## 1                              WHITE     1 Female     HISPANIC OR LATINO
## 2                              WHITE     1   Male     HISPANIC OR LATINO
## 3                              WHITE     1   Male NOT HISPANIC OR LATINO
## 4                              WHITE     1   Male NOT HISPANIC OR LATINO
## 5                              WHITE     1 Female NOT HISPANIC OR LATINO
## 6                              WHITE     1 Female NOT HISPANIC OR LATINO
## 7                              WHITE     1   Male NOT HISPANIC OR LATINO
## 8                              WHITE     1 Female NOT HISPANIC OR LATINO
## 9                              WHITE     1   Male NOT HISPANIC OR LATINO
## 10                             WHITE     1   Male NOT HISPANIC OR LATINO
## 11                             WHITE     1   Male NOT HISPANIC OR LATINO
## 12                             WHITE     1 Female NOT HISPANIC OR LATINO
## 13                             WHITE     1 Female NOT HISPANIC OR LATINO
## 14                             WHITE     1   Male NOT HISPANIC OR LATINO
## 15                             WHITE     1 Female NOT HISPANIC OR LATINO
## 16                             WHITE     1   Male NOT HISPANIC OR LATINO
## 17                             WHITE     1 Female NOT HISPANIC OR LATINO
## 18                             WHITE     1   Male NOT HISPANIC OR LATINO
## 19                             WHITE     1 Female NOT HISPANIC OR LATINO
## 20         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 21                             WHITE     1 Female NOT HISPANIC OR LATINO
## 22                             WHITE     1   Male NOT HISPANIC OR LATINO
## 23                             WHITE     1   Male     HISPANIC OR LATINO
## 24  AMERICAN INDIAN OR ALASKA NATIVE     6   Male NOT HISPANIC OR LATINO
## 25                             WHITE     1 Female     HISPANIC OR LATINO
## 26                             WHITE     1   Male NOT HISPANIC OR LATINO
## 27                             WHITE     1   Male NOT HISPANIC OR LATINO
## 28                             WHITE     1   Male NOT HISPANIC OR LATINO
## 29                             WHITE     1   Male NOT HISPANIC OR LATINO
## 30                             WHITE     1   Male NOT HISPANIC OR LATINO
## 31                             WHITE     1 Female NOT HISPANIC OR LATINO
## 32                             WHITE     1   Male NOT HISPANIC OR LATINO
## 33         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 34                             WHITE     1 Female NOT HISPANIC OR LATINO
## 35                             WHITE     1 Female NOT HISPANIC OR LATINO
## 36                             WHITE     1   Male NOT HISPANIC OR LATINO
## 37                             WHITE     1   Male NOT HISPANIC OR LATINO
## 38                             WHITE     1 Female NOT HISPANIC OR LATINO
## 39                             WHITE     1   Male NOT HISPANIC OR LATINO
## 40         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 41                             WHITE     1   Male     HISPANIC OR LATINO
## 42                             WHITE     1 Female NOT HISPANIC OR LATINO
## 43                             WHITE     1   Male NOT HISPANIC OR LATINO
## 44                             WHITE     1   Male NOT HISPANIC OR LATINO
## 45                             WHITE     1   Male NOT HISPANIC OR LATINO
## 46                             WHITE     1 Female NOT HISPANIC OR LATINO
## 47                             WHITE     1 Female NOT HISPANIC OR LATINO
## 48                             WHITE     1 Female NOT HISPANIC OR LATINO
## 49                             WHITE     1   Male NOT HISPANIC OR LATINO
## 50                             WHITE     1   Male NOT HISPANIC OR LATINO
## 51         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 52                             WHITE     1 Female NOT HISPANIC OR LATINO
## 53                             WHITE     1 Female NOT HISPANIC OR LATINO
## 54                             WHITE     1 Female NOT HISPANIC OR LATINO
## 55                             WHITE     1 Female NOT HISPANIC OR LATINO
## 56                             WHITE     1 Female NOT HISPANIC OR LATINO
## 57         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 58         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 59                             WHITE     1   Male NOT HISPANIC OR LATINO
## 60                             WHITE     1 Female NOT HISPANIC OR LATINO
## 61                             WHITE     1 Female NOT HISPANIC OR LATINO
## 62                             WHITE     1   Male NOT HISPANIC OR LATINO
## 63                             WHITE     1   Male NOT HISPANIC OR LATINO
## 64                             WHITE     1   Male NOT HISPANIC OR LATINO
## 65                             WHITE     1 Female NOT HISPANIC OR LATINO
## 66                             WHITE     1   Male NOT HISPANIC OR LATINO
## 67                             WHITE     1 Female NOT HISPANIC OR LATINO
## 68                             WHITE     1   Male NOT HISPANIC OR LATINO
## 69                             WHITE     1   Male NOT HISPANIC OR LATINO
## 70                             WHITE     1 Female NOT HISPANIC OR LATINO
## 71                             WHITE     1 Female NOT HISPANIC OR LATINO
## 72                             WHITE     1 Female NOT HISPANIC OR LATINO
## 73                             WHITE     1 Female NOT HISPANIC OR LATINO
## 74                             WHITE     1 Female NOT HISPANIC OR LATINO
## 75                             WHITE     1 Female NOT HISPANIC OR LATINO
## 76                             WHITE     1   Male NOT HISPANIC OR LATINO
## 77                             WHITE     1 Female NOT HISPANIC OR LATINO
## 78                             WHITE     1   Male NOT HISPANIC OR LATINO
## 79                             WHITE     1 Female NOT HISPANIC OR LATINO
## 80                             WHITE     1   Male NOT HISPANIC OR LATINO
## 81                             WHITE     1   Male NOT HISPANIC OR LATINO
## 82                             WHITE     1   Male NOT HISPANIC OR LATINO
## 83                             WHITE     1   Male NOT HISPANIC OR LATINO
## 84                             WHITE     1   Male NOT HISPANIC OR LATINO
## 85                             WHITE     1   Male NOT HISPANIC OR LATINO
## 86                             WHITE     1 Female NOT HISPANIC OR LATINO
## 87                             WHITE     1 Female     HISPANIC OR LATINO
## 88                             WHITE     1 Female NOT HISPANIC OR LATINO
## 89                             WHITE     1 Female NOT HISPANIC OR LATINO
## 90                             WHITE     1   Male NOT HISPANIC OR LATINO
## 91                             WHITE     1 Female NOT HISPANIC OR LATINO
## 92         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 93         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 94         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 95                             WHITE     1   Male NOT HISPANIC OR LATINO
## 96                             WHITE     1 Female NOT HISPANIC OR LATINO
## 97                             WHITE     1 Female     HISPANIC OR LATINO
## 98         BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 99                             WHITE     1   Male NOT HISPANIC OR LATINO
## 100                            WHITE     1 Female NOT HISPANIC OR LATINO
## 101                            WHITE     1 Female     HISPANIC OR LATINO
## 102        BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 103                            WHITE     1 Female NOT HISPANIC OR LATINO
## 104                            WHITE     1 Female NOT HISPANIC OR LATINO
## 105                            WHITE     1 Female NOT HISPANIC OR LATINO
## 106                            WHITE     1   Male NOT HISPANIC OR LATINO
## 107                            WHITE     1   Male NOT HISPANIC OR LATINO
## 108                            WHITE     1   Male NOT HISPANIC OR LATINO
## 109                            WHITE     1 Female NOT HISPANIC OR LATINO
## 110                            WHITE     1 Female NOT HISPANIC OR LATINO
## 111                            WHITE     1 Female NOT HISPANIC OR LATINO
## 112                            WHITE     1 Female NOT HISPANIC OR LATINO
## 113        BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 114                            WHITE     1 Female NOT HISPANIC OR LATINO
## 115                            WHITE     1   Male NOT HISPANIC OR LATINO
## 116                            WHITE     1 Female NOT HISPANIC OR LATINO
## 117                            WHITE     1   Male NOT HISPANIC OR LATINO
## 118                            WHITE     1   Male NOT HISPANIC OR LATINO
## 119        BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 120        BLACK OR AFRICAN AMERICAN     2   Male NOT HISPANIC OR LATINO
## 121                            WHITE     1   Male NOT HISPANIC OR LATINO
## 122                            WHITE     1 Female NOT HISPANIC OR LATINO
## 123                            WHITE     1   Male NOT HISPANIC OR LATINO
## 124                            WHITE     1 Female NOT HISPANIC OR LATINO
## 125                            WHITE     1 Female NOT HISPANIC OR LATINO
## 126                            WHITE     1 Female NOT HISPANIC OR LATINO
## 127        BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 128                            WHITE     1   Male NOT HISPANIC OR LATINO
## 129        BLACK OR AFRICAN AMERICAN     2   Male NOT HISPANIC OR LATINO
## 130                            WHITE     1 Female NOT HISPANIC OR LATINO
## 131                            WHITE     1 Female NOT HISPANIC OR LATINO
## 132                            WHITE     1 Female NOT HISPANIC OR LATINO
## 133                            WHITE     1 Female NOT HISPANIC OR LATINO
## 134                            WHITE     1 Female NOT HISPANIC OR LATINO
## 135                            WHITE     1   Male NOT HISPANIC OR LATINO
## 136                            WHITE     1 Female NOT HISPANIC OR LATINO
## 137                            WHITE     1   Male NOT HISPANIC OR LATINO
## 138                            WHITE     1 Female NOT HISPANIC OR LATINO
## 139                            WHITE     1 Female NOT HISPANIC OR LATINO
## 140                            WHITE     1 Female NOT HISPANIC OR LATINO
## 141                            WHITE     1   Male NOT HISPANIC OR LATINO
## 142                            WHITE     1   Male NOT HISPANIC OR LATINO
## 143                            WHITE     1   Male NOT HISPANIC OR LATINO
## 144                            WHITE     1   Male NOT HISPANIC OR LATINO
## 145                            WHITE     1 Female NOT HISPANIC OR LATINO
## 146                            WHITE     1 Female NOT HISPANIC OR LATINO
## 147                            WHITE     1   Male NOT HISPANIC OR LATINO
## 148                            WHITE     1 Female NOT HISPANIC OR LATINO
## 149                            WHITE     1 Female NOT HISPANIC OR LATINO
## 150                            WHITE     1   Male NOT HISPANIC OR LATINO
## 151                            WHITE     1   Male NOT HISPANIC OR LATINO
## 152                            WHITE     1   Male NOT HISPANIC OR LATINO
## 153                            WHITE     1   Male NOT HISPANIC OR LATINO
## 154                            WHITE     1   Male NOT HISPANIC OR LATINO
## 155        BLACK OR AFRICAN AMERICAN     2   Male NOT HISPANIC OR LATINO
## 156                            WHITE     1   Male NOT HISPANIC OR LATINO
## 157                            WHITE     1 Female NOT HISPANIC OR LATINO
## 158                            WHITE     1 Female NOT HISPANIC OR LATINO
## 159                            WHITE     1   Male NOT HISPANIC OR LATINO
## 160                            WHITE     1 Female NOT HISPANIC OR LATINO
## 161                            WHITE     1 Female NOT HISPANIC OR LATINO
## 162                            WHITE     1 Female NOT HISPANIC OR LATINO
## 163                            WHITE     1 Female NOT HISPANIC OR LATINO
## 164        BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 165                            WHITE     1 Female NOT HISPANIC OR LATINO
## 166                            WHITE     1   Male     HISPANIC OR LATINO
## 167                            WHITE     1 Female NOT HISPANIC OR LATINO
## 168                            WHITE     1 Female NOT HISPANIC OR LATINO
## 169                            WHITE     1 Female NOT HISPANIC OR LATINO
## 170                            WHITE     1 Female     HISPANIC OR LATINO
## 171                            WHITE     1   Male NOT HISPANIC OR LATINO
## 172                            WHITE     1   Male NOT HISPANIC OR LATINO
## 173                            WHITE     1 Female NOT HISPANIC OR LATINO
## 174                            WHITE     1 Female NOT HISPANIC OR LATINO
## 175                            WHITE     1   Male NOT HISPANIC OR LATINO
## 176                            WHITE     1 Female NOT HISPANIC OR LATINO
## 177                            WHITE     1 Female NOT HISPANIC OR LATINO
## 178                            WHITE     1 Female NOT HISPANIC OR LATINO
## 179                            WHITE     1   Male NOT HISPANIC OR LATINO
## 180                            WHITE     1   Male NOT HISPANIC OR LATINO
## 181                            WHITE     1 Female NOT HISPANIC OR LATINO
## 182                            WHITE     1   Male NOT HISPANIC OR LATINO
## 183                            WHITE     1   Male NOT HISPANIC OR LATINO
## 184                            WHITE     1 Female NOT HISPANIC OR LATINO
## 185        BLACK OR AFRICAN AMERICAN     2   Male NOT HISPANIC OR LATINO
## 186                            WHITE     1 Female NOT HISPANIC OR LATINO
## 187                            WHITE     1 Female NOT HISPANIC OR LATINO
## 188                            WHITE     1 Female NOT HISPANIC OR LATINO
## 189        BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
## 190                            WHITE     1   Male NOT HISPANIC OR LATINO
## 191                            WHITE     1   Male NOT HISPANIC OR LATINO
## 192                            WHITE     1 Female NOT HISPANIC OR LATINO
## 193                            WHITE     1 Female NOT HISPANIC OR LATINO
## 194                            WHITE     1   Male NOT HISPANIC OR LATINO
## 195                            WHITE     1   Male NOT HISPANIC OR LATINO
## 196                            WHITE     1 Female NOT HISPANIC OR LATINO
## 197                            WHITE     1 Female NOT HISPANIC OR LATINO
## 198                            WHITE     1 Female NOT HISPANIC OR LATINO
## 199                            WHITE     1   Male NOT HISPANIC OR LATINO
## 200        BLACK OR AFRICAN AMERICAN     2   Male NOT HISPANIC OR LATINO
## 201                            WHITE     1 Female NOT HISPANIC OR LATINO
## 202                            WHITE     1   Male NOT HISPANIC OR LATINO
## 203                            WHITE     1 Female NOT HISPANIC OR LATINO
## 204                            WHITE     1   Male NOT HISPANIC OR LATINO
## 205                            WHITE     1 Female NOT HISPANIC OR LATINO
## 206                            WHITE     1 Female NOT HISPANIC OR LATINO
## 207                            WHITE     1   Male NOT HISPANIC OR LATINO
## 208                            WHITE     1 Female NOT HISPANIC OR LATINO
## 209                            WHITE     1 Female NOT HISPANIC OR LATINO
## 210                            WHITE     1   Male NOT HISPANIC OR LATINO
## 211                            WHITE     1 Female NOT HISPANIC OR LATINO
## 212                            WHITE     1 Female NOT HISPANIC OR LATINO
## 213                            WHITE     1 Female NOT HISPANIC OR LATINO
## 214                            WHITE     1   Male NOT HISPANIC OR LATINO
## 215                            WHITE     1   Male NOT HISPANIC OR LATINO
## 216                            WHITE     1 Female NOT HISPANIC OR LATINO
## 217                            WHITE     1   Male NOT HISPANIC OR LATINO
## 218                            WHITE     1   Male NOT HISPANIC OR LATINO
## 219                            WHITE     1 Female NOT HISPANIC OR LATINO
## 220                            WHITE     1 Female NOT HISPANIC OR LATINO
## 221                            WHITE     1   Male NOT HISPANIC OR LATINO
## 222                            WHITE     1 Female NOT HISPANIC OR LATINO
## 223                            WHITE     1   Male NOT HISPANIC OR LATINO
## 224                            WHITE     1   Male NOT HISPANIC OR LATINO
## 225                            WHITE     1   Male NOT HISPANIC OR LATINO
## 226                            WHITE     1 Female NOT HISPANIC OR LATINO
## 227                            WHITE     1 Female NOT HISPANIC OR LATINO
## 228                            WHITE     1 Female NOT HISPANIC OR LATINO
## 229                            WHITE     1   Male NOT HISPANIC OR LATINO
## 230                            WHITE     1 Female NOT HISPANIC OR LATINO
## 231                            WHITE     1   Male NOT HISPANIC OR LATINO
## 232                            WHITE     1 Female NOT HISPANIC OR LATINO
## 233                            WHITE     1   Male NOT HISPANIC OR LATINO
## 234                            WHITE     1 Female NOT HISPANIC OR LATINO
## 235                            WHITE     1 Female NOT HISPANIC OR LATINO
## 236                            WHITE     1   Male NOT HISPANIC OR LATINO
## 237                            WHITE     1   Male NOT HISPANIC OR LATINO
## 238                            WHITE     1 Female NOT HISPANIC OR LATINO
## 239                            WHITE     1 Female NOT HISPANIC OR LATINO
## 240                            WHITE     1   Male NOT HISPANIC OR LATINO
## 241                            WHITE     1 Female NOT HISPANIC OR LATINO
## 242                            WHITE     1 Female NOT HISPANIC OR LATINO
## 243                            WHITE     1 Female NOT HISPANIC OR LATINO
## 244        BLACK OR AFRICAN AMERICAN     2   Male NOT HISPANIC OR LATINO
## 245                            WHITE     1   Male NOT HISPANIC OR LATINO
## 246                            WHITE     1 Female NOT HISPANIC OR LATINO
## 247                            WHITE     1 Female NOT HISPANIC OR LATINO
## 248                            WHITE     1   Male NOT HISPANIC OR LATINO
## 249                            WHITE     1 Female     HISPANIC OR LATINO
## 250                            WHITE     1   Male     HISPANIC OR LATINO
## 251                            WHITE     1   Male NOT HISPANIC OR LATINO
## 252                            WHITE     1   Male NOT HISPANIC OR LATINO
## 253                            WHITE     1 Female NOT HISPANIC OR LATINO
## 254        BLACK OR AFRICAN AMERICAN     2 Female NOT HISPANIC OR LATINO
```

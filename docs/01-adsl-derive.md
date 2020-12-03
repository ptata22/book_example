# Adsl derivations Derived = 1 level {#Variable}

List of Variables Derived = 1

+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Variable** | **Label**                          | **Source/Derivation/Comments**                                                            | R Dplyr Snippet                                                                                                                                                                                                    |
+==============+====================================+===========================================================================================+====================================================================================================================================================================================================================+
| STUDYID      | Study Identifier                   | DM.STUDYID                                                                                | `select ( dm , studyid)`                                                                                                                                                                                           |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| USUBJID      | Unique Subject Identifier          | DM.USUBJID                                                                                | `select ( dm , usubjid)`                                                                                                                                                                                           |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| SUBJID       | Subject Identifier for the Study   | DM.SUBJID                                                                                 | `select ( dm , subjid)`                                                                                                                                                                                            |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| SITEID       | Study Site Identifier              | DM.SITEID                                                                                 | `select ( dm , siteid)`                                                                                                                                                                                            |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ARM          | Description of Planned Arm         | DM.ARM                                                                                    | `select ( dm , arm)`                                                                                                                                                                                               |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| TRT01P       | Planned Treatment for Period 01    | DM.ARM                                                                                    | `select ( dm , arm)`                                                                                                                                                                                               |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| TRT01A       | Actual Treatment for Period 01     | TRT01A=TRT01P, i.e., no difference between actual and randomized treatment in this study. | `mutate ( dm , TRT01A= ARM)`                                                                                                                                                                                       |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| TRT01AN      | Actual Treatment for Period 01 (N) | Numeric code for TRT01A which corresponds to the randomized dose                          | `mutate( trt01pn  =ifelse( (arm %in% "Placebo" ) , 0 , ifelse( (arm %in% Xanomeline Low Dose" ) , 54, ifelse( (arm %in% "Xanomeline High Dose" ) , 81 , NA)))`                                                     |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| AGE          | Age                                | DM.AGE                                                                                    | `select ( dm , age)`                                                                                                                                                                                               |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RACE         | Race                               | DM.RACE                                                                                   | `select ( dm , race)`                                                                                                                                                                                              |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RACEN        | Race (N)                           | Numeric code for RACE                                                                     | `case_when( race %in% "WHITE" ~ 1 , race %in% "BLACK OR AFRICAN AMERICAN" ~ 2 ,                           race %in% "AMERICAN INDIAN OR ALASKA NATIVE" ~ 6 ,                              race %in% "ASIAN" ~ 7 )` |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| SEX          | Sex                                | DM.SEX                                                                                    | `select(dm,sex)`                                                                                                                                                                                                   |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ETHNIC       | Ethnicity                          | DM.ETHNIC                                                                                 | `select(dm,ethnic)`                                                                                                                                                                                                |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| DTHFL        | Subject Died?                      | DM.DTHFL                                                                                  | `select(dm,dthfl)`                                                                                                                                                                                                 |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RFSTDTC      | Subject Reference Start Date/Time  | DM.RFSTDTC                                                                                | `select(dm,rfstdtc)`                                                                                                                                                                                               |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RFENDTC      | Subject Reference End Date/Time    | DM.RFENDTC                                                                                | `select(dm,rfendtc)`                                                                                                                                                                                               |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
+--------------+------------------------------------+-------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

## Overview

#### Important Functions {.history}

dplyr is a grammar of data manipulation, providing a consistent set of verbs that help you solve the most common data manipulation challenges:

-   [`mutate()`](https://dplyr.tidyverse.org/reference/mutate.html) adds new variables that are functions of existing variables

-   [`select()`](https://dplyr.tidyverse.org/reference/select.html) picks variables based on their names.

-   [`filter()`](https://dplyr.tidyverse.org/reference/filter.html) picks cases based on their values.

-   [`summarise()`](https://dplyr.tidyverse.org/reference/summarise.html) reduces multiple values down to a single summary.

-   [`arrange()`](https://dplyr.tidyverse.org/reference/arrange.html) changes the ordering of the rows.

## Your Turn {.exercise}

\*\*List out various Character and Numeric Dplyr functions\*\*

[[Learn to use R Dplyr Package]](https://dplyr.tidyverse.org/)

1.  List out all the functions used

    [Filter](https://dplyr.tidyverse.org/reference/filter_all.html?q=filter "Filter within a selection of variables")

    [Select](https://dplyr.tidyverse.org/reference/select.html "Used to select the variables needed")

    [case_when](https://dplyr.tidyverse.org/reference/case_when.html?q=case%20_%20when "R equivalent of the SQL CASE WHEN statement. If no cases match, NA is returned")

    [if_else()](https://dplyr.tidyverse.org/reference/if_else.html?q=if%20_%20else "Compared to the base ifelse(), this function is more strict. It checks that true and false are the same type")

    as.character

    mutate

    inner_join

    as.Date(as.character(svstdtc) )

    as.Date

    [as.Date.numeric](https://www.rdocumentation.org/packages/zoo/versions/1.5-7/topics/as.Date.numeric "Date Conversion Functions From Numeric, Integer And Ts Objects Functions to convert numeric and related classes to objects of class "Date" representing calendar dates.")

    ## Let's start programming

    1.  Initialize all the Library's needed for the project


```r
#intilizing the Dplyr library
library(tidyverse)
```

```
## -- Attaching packages --------------- tidyverse 1.3.0 --
```

```
## v ggplot2 3.3.2     v purrr   0.3.4
## v tibble  3.0.3     v dplyr   1.0.2
## v tidyr   1.1.2     v stringr 1.4.0
## v readr   1.3.1     v forcats 0.5.0
```

```
## -- Conflicts ------------------ tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
library(lubridate)
```

```
## 
## Attaching package: 'lubridate'
```

```
## The following objects are masked from 'package:base':
## 
##     date, intersect, setdiff, union
```

```r
library(clinicalfd)  # To read in fake clinical data
library(arsenal)     # for comparing datasets
```

```
## 
## Attaching package: 'arsenal'
```

```
## The following object is masked from 'package:lubridate':
## 
##     is.Date
```

[*Remove all the objects in the Global Environment ( Kind of clearing SAS work directory ) , This is kind of needed as you might get an Error saying the variable not found .*]{.ul}


```r
remove ( list = ls())
```

2.  Bring in the datasets needed


```r
# dm <- clinicalfd::dm 
# names(clinicalfd::dm )
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
         usubjid = as.character(usubjid),
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
ethnic=case_when(ethnic %in% "NOT HISPANIC OR LATINO" ~ "NOT HISPANIC OR LATINO", 
                ethnic %in% "HISPANIC OR LATINO" ~ "HISPANIC OR LATINO"    , 
                ethnic %in% "U" ~  "Unknown" )  
)
```

<div>

## **Date of First Exposure to Treatment**

</div>

**Date of First Exposure to Treatment (TRTSDT) derivation**

**SV.SVSTDTC when SV.VISITNUM=3, converted to SAS date**


```r
sv_visit <- clinicalfd::sv   

sv_visit3 <- sv_visit %>% 
             filter(visitnum == 3) %>% 
             mutate(usubjid = as.character(usubjid) , 
                    trtsdt = as.Date(as.character(svstdtc))  
                   ) %>% 
             select (usubjid , svstdtc , trtsdt )

# For derive DURDIS (duration of Disease (months))

sv_visit1 <- sv_visit %>% 
             filter(visitnum == 1 ) %>% 
             mutate(usubjid = as.character(usubjid) , 
                    visit1dt = as.Date(as.character(svstdtc))  
                   ) %>% 
             select (usubjid ,  visit1dt )


# nature of usubjid is character and svstdtc is <s3.labelled> 

adsl_deri01 <- inner_join(adsl_deri01, sv_visit3 , by = "usubjid")

adsl_deri01 <- inner_join(adsl_deri01, sv_visit1 , by = "usubjid")
```

## Date of Last Exposure to Treatment (TRTEDT)

The date of final dose (from the CRF) is EX.EXENDTC on the subject's last EX record. If the date of final dose is missing for the subject and the subject discontinued after visit 3, use the date of discontinuation as the date of last dose.

Steps to arrive at logic

1.  Check for the subjects whose final dose date is missing
2.  **`Check if these subjects discontinued after visit 3 (Check  if they have any records after the Visit 3 , this needs checked )`**
3.  If they have not discontinued then use the SV date as date of last dose
4.  To find last.date use **slice_tail , slice_max within by group** or use **Dplyr::first or last functions** , compare it original dataset


```r
#Final dates check 

exendtc <- ex %>% 
            mutate(usubjid = as.character(usubjid) ,  
                   exendtc_orig = exendtc, 
                   exendtc = as.Date(as.character(exendtc)) ) %>% 
           select( usubjid ,visit , visitnum,  exendtc , exendtc_orig )

ds_disp <- ds %>% 
             filter (   dscat == "DISPOSITION EVENT" ) %>%
             mutate (usubjid = as.character(usubjid))   %>% 
           select ( usubjid , dsstdtc)

exendtc <- inner_join(exendtc , ds_disp  , by = "usubjid")
```

NOTE : Handling the Missing is different from SAS approach "disconfl_com =="NA" won't work and = would give an error too "


```r
ds_orig  <- ds %>% 
            mutate (usubjid = as.character(usubjid )) %>% 
            select (  usubjid , dsdecod )

ds_con01 <- ds %>% 
filter (dsdecod == "COMPLETED" & dsdecod != "SCREEN FAILURE" ) %>%
             mutate (usubjid = as.character(usubjid) , 
                     disconfl_com = "Y")   %>% 
             distinct (usubjid, disconfl_com  ) 

ds_con02 <- ds %>% 
filter (dsdecod != "COMPLETED" & dsdecod != "SCREEN FAILURE") %>%
             mutate (usubjid = as.character(usubjid) , 
                     disconfl_not_com = "Y" , 
                     dsdecod_02 = dsdecod )   %>% 
        distinct (usubjid , .keep_all  = TRUE  ) %>%
        select (usubjid, disconfl_not_com , dsdecod_02 )


ds_con03   <- right_join ( ds_con01 , ds_con02  , "usubjid") %>% 
              arrange(usubjid)


ds_con04   <- ds_con03 %>%  
mutate(
disconfl = case_when( (disconfl_com =="Y" & disconfl_not_com == "Y") ~ " " ,
                      
                      (disconfl_com %in% NA & disconfl_not_com == "Y") ~ "Y") , 

dcreascd = ifelse( disconfl == " " ,  "Completed" , 
           ifelse     ( disconfl == "Y" , as.character(dsdecod_02) , NA) 
                 ) , 

dsraefl = ifelse (disconfl == "Y" & dsdecod_02 =="ADVERSE EVENT" , "Y" , " " ) 

) %>% 
       distinct(usubjid , .keep_all =  TRUE  ) %>% 
        select (usubjid , disconfl , dcreascd , dsraefl )


#merge back 
adsl_deri01 <- inner_join(adsl_deri01, ds_con04 , by = "usubjid") 


adsl_chk <- select (adsl , usubjid, disconfl , dcreascd , dsraefl )
```

**`NOTE: Using the as.Date(as.Character ()) is creating numerical dates and date formats are not being , need to learn more about the as.Date .using the`**

**`as.Date( as.character () ) is creating numerical dates and date formats are not Below Logic is how you conditionally create a new column trtedt based DSSTDTC and exendtc_orig`**


```r
# Subjects whose does dates are missing 
exendtc_1 <- exendtc %>% 
           mutate ( flag = ifelse (exendtc   %in% NA  ,  "N" ,"Y"   ) ,
           trtedt =   ifelse(flag == "N", as.character(dsstdtc), 
                        ifelse (flag =="Y" ,as.character(exendtc_orig)  , NA  ))  ) %>% 
           filter (visitnum >= 3 )
```

## **Getting the First and Last observations**


```r
# One of the ways to get the First and Last group by values 
# Make sure you use the right variables used group_by 

exendtc_2  <- exendtc_1 %>% 
         group_by (usubjid) %>% 
         dplyr:: mutate(
           first = dplyr::first(trtedt) , 
           last  = dplyr::last (trtedt)
         ) %>% 
          summarise(trtedt = last(trtedt) )
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```r
#exendtc <- select(exendtc,usubjid ,visitnum , trtedt, trtedt_c  )
```

Merging back with ADSL data set


```r
#Final dates check 

adsl_deri01 <- inner_join(adsl_deri01, exendtc_2 , by = "usubjid") 
```

::: {#note .notechk style="red"}
NOTE : Variables that are not calculated

1.  AVGDD (Avg Daily Dose (as planned )) and\

2.  CUMDOSE (Cumulative Dose (as planned) )\

3.  COMP8FL , COMP16FL , COMP24FL ,

4.  VISNUMEN ( End of Trt Visit (Vis 12 or Early )
:::

Population Flag

**`1. SAFFL(Safety Population Flag ) 2. EFFFL (Efficacy Population Flag ) 3. DSRAEFL (Discontinued due to AE ? )`**

Y if SAFFL='Y AND subject has at least one record in QS for ADAS-Cog with VISITNUM\>3 AND at least one record in QS for CIBIC+ with VISITNUM\>3, N otherwise

::: {.notechk style="red"}
**NOTE: try using ['and']{.ul} ( gives an error ) , while ['&' Not]{.ul}\
For example when (25\<= bmibl \< 30 ) or (25\<= bmibl and bmibl \<30 ) we get an error use (25\<= bmibl & bmibl \<30 )**
:::


```r
#Saffl (safety flag)
 


adsl_deri01 <- adsl_deri01 %>% 
        mutate( rfendt = as.Date(as.character(rfendtc)) ,
                saffl =   case_when ((ittfl %in% "Y" & !is.na(trtsdt))~ "Y" ) , 
                trtdur = as.numeric ( as.Date(trtedt)  - as.Date (trtsdt) ) + 1 ) 

effi_01 <-qs %>% 
          filter( qstestcd =="ACTOT" & visitnum > 3  ) %>% 
          mutate( usubjid = as.character(usubjid)) %>% 
          distinct(usubjid , .keep_all =  TRUE )  %>% 
          select ( usubjid , qstestcd )


adsl_deri01 <- left_join(adsl_deri01, effi_01 , by = "usubjid")

#Efficacy flag (safety flag)
 
adsl_deri02 <- adsl_deri01 %>%  
  mutate( efffl =   case_when ((saffl %in% "Y" & !is.na(qstestcd) )~ "Y" ) )  
```

## Baseline Variables

**DISONSDT Date of Onset of disease**


```r
disonsdt <- mh %>% 
            filter(mhcat =="PRIMARY DIAGNOSIS") %>% 
            mutate (disonsdt =  as.Date(as.character(mhstdtc) )  , 
                    usubjid = as.character(usubjid) ) %>% 
            select (usubjid , disonsdt)
```

**Baseline Height**


```r
heightbl  <- vs %>%  
             filter ( vstestcd == "HEIGHT" & visitnum == 1 ) %>% 
             mutate (heightbl = round(vsstresn, 1)  , 
                     usubjid = as.character(usubjid) ) %>% 
             select ( usubjid , heightbl)
```

**Baseline Weight**


```r
weightbl  <- vs %>%  
             filter ( vstestcd == "WEIGHT" & visitnum == 3 ) %>% 
             mutate (weightbl = round(vsstresn, 1)  , 
                     usubjid = as.character(usubjid) ) %>% 
             select ( usubjid , weightbl)
```

**Years of Education**


```r
educlvl <-  sc %>%
             mutate (educlvl = scstresn   ,
                     usubjid = as.character(usubjid) ) %>%
             select ( usubjid , educlvl )
```

**Getting derived variables into main dataset**


```r
adsl_deri02 <- left_join(adsl_deri02 , disonsdt , by = "usubjid") 

adsl_deri02 <- left_join(adsl_deri02 , heightbl , by = "usubjid")            

adsl_deri02 <- left_join(adsl_deri02 , weightbl , by = "usubjid")        

adsl_deri02 <- left_join(adsl_deri02 , educlvl , by = "usubjid") 


adsl_deri02 <-  adsl_deri02 %>% 
mutate (bmibl = round((weightbl/((heightbl*heightbl ))*100*100  ) , 1 ) , 
         
        bmiblgr1  = case_when(  (bmibl<25) ~ "Normal" , 
                            
                                (25<= bmibl & bmibl <30 ) ~ "Overweight" , 
                                ( bmibl >= 30 ) ~ "Obese"
                              ) 
                         
        )
```

Number of months difference between the two dates, in SAS

when the difference is 43 months and 26 days INTCK function calculates 26 days is what fraction is 26 days in a month while R gives just 43 months


```r
adsl_durdis <- adsl_deri02  %>% 
             mutate (visit1dt2 =   as.Date(visit1dt)  ,
                     disonsdt2 =   as.Date(disonsdt)  , 
    durdis    = interval( disonsdt2  ,  visit1dt2) %/% months(1) , 
    durdsgr1 = case_when ( durdis < 12 ~ "<12" , 
                           durdis >= 12 ~ ">=12"  )
                     ) %>%
select (  usubjid , visit1dt  , disonsdt  , durdis , durdsgr1 )


adsl_deri02 <- left_join(adsl_deri02 , adsl_durdis , by = "usubjid")
```

## Comparing the values generated against the production data set


```r
#install.packages("arsenal")

# 
# adsl_deri02 <- adsl_deri02 %>% 
#                 mutate( usubjid = as.character(usubjid) , 
#                         trtedt = as.character(trtedt) , 
#                         trtdur = as.numeric( trtdur) , 
#                         saffl  = as.character(saffl ) , 
#                         efffl  = as.character(efffl ) , 
#                         disonsdt = as.character(disonsdt)
#                   )%>% 
#   
# select (usubjid , saffl , efffl , trtdur, disconfl ,dcreascd , dsraefl , heightbl , weightbl , bmibl , bmiblgr1 , educlvl , disonsdt 
#         ) %>% 
# arrange( usubjid)

#   
# 
# 
# 
# 
# 
# adsl_prog  <-   clinicalfd::adsl %>%
#                 mutate( usubjid = as.character(usubjid) , 
#                         trtedt = as.character(trtedt) , 
#                         trtdur = as.numeric( trtdur) , 
#                         saffl  = as.character(saffl ) , 
#                         efffl  = as.character(efffl ) , 
#                         disonsdt = as.character(disonsdt)
#                         
#                   )%>%
# select (usubjid , saffl , efffl  , trtdur , disconfl ,                             dcreascd , dsraefl , heightbl ,weightbl , bmibl , bmiblgr1 , educlvl ,disonsdt  )%>% 
# arrange( usubjid)
# 
# 
# adsl_orig <- clinicalfd::adsl
# 
#  arsenal::comparedf ( adsl_prog , adsl_deri02 )
# 
#  summary(comparedf ( adsl_prog , adsl_deri02 ))
```


```r
adsl_orig <- clinicalfd::adsl
adsl_durdis <- dplyr::select (adsl_orig , usubjid , visit1dt, disonsdt , durdis )


#adsl_durdis <- select ( adsl_deri02 , usubjid , disonsdt , durdis )
#names(adsl_orig)
```


```r
ds_orig <- ds 
```

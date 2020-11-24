# Adsl derivations Derived = 1 level {#Variable}

List of Variables Derived = 1

| **Variable** | **Label**                          | **Source/Derivation/Comments**                                                            | R Dplyr Snippet                                                                                                                                                                                                    |
|--------------|------------------------------------|-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| STUDYID      | Study Identifier                   | DM.STUDYID                                                                                | `select ( dm , studyid)`                                                                                                                                                                                           |
| USUBJID      | Unique Subject Identifier          | DM.USUBJID                                                                                | `select ( dm , usubjid)`                                                                                                                                                                                           |
| SUBJID       | Subject Identifier for the Study   | DM.SUBJID                                                                                 | `select ( dm , subjid)`                                                                                                                                                                                            |
| SITEID       | Study Site Identifier              | DM.SITEID                                                                                 | `select ( dm , siteid)`                                                                                                                                                                                            |
| ARM          | Description of Planned Arm         | DM.ARM                                                                                    | `select ( dm , arm)`                                                                                                                                                                                               |
| TRT01P       | Planned Treatment for Period 01    | DM.ARM                                                                                    | `select ( dm , arm)`                                                                                                                                                                                               |
| TRT01A       | Actual Treatment for Period 01     | TRT01A=TRT01P, i.e., no difference between actual and randomized treatment in this study. | `mutate ( dm , TRT01A= ARM)`                                                                                                                                                                                       |
| TRT01AN      | Actual Treatment for Period 01 (N) | Numeric code for TRT01A which corresponds to the randomized dose                          | `mutate( trt01pn  =ifelse( (arm %in% "Placebo" ) , 0 , ifelse( (arm %in% Xanomeline Low Dose" ) , 54, ifelse( (arm %in% "Xanomeline High Dose" ) , 81 , NA)))`                                                     |
| AGE          | Age                                | DM.AGE                                                                                    | `select ( dm , age)`                                                                                                                                                                                               |
| RACE         | Race                               | DM.RACE                                                                                   | `select ( dm , race)`                                                                                                                                                                                              |
| RACEN        | Race (N)                           | Numeric code for RACE                                                                     | `case_when( race %in% "WHITE" ~ 1 , race %in% "BLACK OR AFRICAN AMERICAN" ~ 2 ,                           race %in% "AMERICAN INDIAN OR ALASKA NATIVE" ~ 6 ,                              race %in% "ASIAN" ~ 7 )` |
| SEX          | Sex                                | DM.SEX                                                                                    | `select(dm,sex)`                                                                                                                                                                                                   |
| ETHNIC       | Ethnicity                          | DM.ETHNIC                                                                                 | `select(dm,ethnic)`                                                                                                                                                                                                |
| DTHFL        | Subject Died?                      | DM.DTHFL                                                                                  | `select(dm,dthfl)`                                                                                                                                                                                                 |
| RFSTDTC      | Subject Reference Start Date/Time  | DM.RFSTDTC                                                                                | `select(dm,rfstdtc)`                                                                                                                                                                                               |
| RFENDTC      | Subject Reference End Date/Time    | DM.RFENDTC                                                                                | `select(dm,rfendtc)`                                                                                                                                                                                               |
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |
|              |                                    |                                                                                           |                                                                                                                                                                                                                    |

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
## -- Attaching packages ------------- tidyverse 1.3.0 --
```

```
## v ggplot2 3.3.2     v purrr   0.3.4
## v tibble  3.0.3     v dplyr   1.0.2
## v tidyr   1.1.2     v stringr 1.4.0
## v readr   1.3.1     v forcats 0.5.0
```

```
## -- Conflicts ---------------- tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
library(clinicalfd)
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
           ethnic  =  case_when(ethnic %in% "NOT HISPANIC OR LATINO" ~ "NOT HISPANIC OR LATINO"  , 
           ethnic %in% "HISPANIC OR LATINO" ~ "HISPANIC OR LATINO"  , 
           ethnic %in% "U" ~  "Unknown" )
)
```

<div>

**Date of First Exposure to Treatment** `SV.SVSTDTC when SV.VISITNUM=3, converted to SAS date`

</div>

### **Date of First Exposure to Treatment (TRTSDT)**


```r
sv_visit3 <- clinicalfd::sv   
sv_visit3 <- sv_visit3 %>% 
             filter(visitnum == 3) %>% 
             mutate(usubjid = as.character(usubjid) , 
                    trtsdt = as.Date(as.character(svstdtc))  
                   ) %>% 
             select (usubjid , svstdtc , trtsdt )

sv_visit3
```

```
##         usubjid    svstdtc     trtsdt
## 1   01-701-1015 2014-01-02 2014-01-02
## 2   01-701-1023 2012-08-05 2012-08-05
## 3   01-701-1028 2013-07-19 2013-07-19
## 4   01-701-1033 2014-03-18 2014-03-18
## 5   01-701-1034 2014-07-01 2014-07-01
## 6   01-701-1047 2013-02-12 2013-02-12
## 7   01-701-1097 2014-01-01 2014-01-01
## 8   01-701-1111 2012-09-07 2012-09-07
## 9   01-701-1115 2012-11-30 2012-11-30
## 10  01-701-1118 2014-03-12 2014-03-12
## 11  01-701-1130 2014-02-15 2014-02-15
## 12  01-701-1133 2012-10-28 2012-10-28
## 13  01-701-1146 2013-05-20 2013-05-20
## 14  01-701-1148 2013-08-23 2013-08-23
## 15  01-701-1153 2013-09-23 2013-09-23
## 16  01-701-1180 2013-02-12 2013-02-12
## 17  01-701-1181 2013-12-05 2013-12-05
## 18  01-701-1188 2013-02-15 2013-02-15
## 19  01-701-1192 2012-07-22 2012-07-22
## 20  01-701-1203 2013-02-02 2013-02-02
## 21  01-701-1211 2012-11-15 2012-11-15
## 22  01-701-1234 2013-03-30 2013-03-30
## 23  01-701-1239 2014-01-11 2014-01-11
## 24  01-701-1275 2014-02-07 2014-02-07
## 25  01-701-1287 2014-01-25 2014-01-25
## 26  01-701-1294 2013-03-24 2013-03-24
## 27  01-701-1302 2013-08-29 2013-08-29
## 28  01-701-1317 2014-05-22 2014-05-22
## 29  01-701-1324 2012-10-02 2012-10-02
## 30  01-701-1341 2013-01-05 2013-01-05
## 31  01-701-1345 2013-10-08 2013-10-08
## 32  01-701-1360 2013-07-31 2013-07-31
## 33  01-701-1363 2013-05-30 2013-05-30
## 34  01-701-1383 2013-02-04 2013-02-04
## 35  01-701-1387 2014-03-12 2014-03-12
## 36  01-701-1392 2012-10-28 2012-10-28
## 37  01-701-1415 2013-09-23 2013-09-23
## 38  01-701-1429 2013-03-19 2013-03-19
## 39  01-701-1440 2013-08-08 2013-08-08
## 40  01-701-1442 2013-10-26 2013-10-26
## 41  01-701-1444 2013-01-05 2013-01-05
## 42  01-702-1082 2013-07-26 2013-07-26
## 43  01-703-1042 2013-03-02 2013-03-02
## 44  01-703-1076 2013-10-25 2013-10-25
## 45  01-703-1086 2012-09-02 2012-09-02
## 46  01-703-1096 2013-01-25 2013-01-25
## 47  01-703-1100 2013-03-13 2013-03-13
## 48  01-703-1119 2013-02-20 2013-02-20
## 49  01-703-1175 2013-12-20 2013-12-20
## 50  01-703-1182 2013-10-17 2013-10-17
## 51  01-703-1197 2013-06-16 2013-06-16
## 52  01-703-1210 2013-03-16 2013-03-16
## 53  01-703-1258 2012-07-20 2012-07-20
## 54  01-703-1279 2013-05-13 2013-05-13
## 55  01-703-1295 2013-11-21 2013-11-21
## 56  01-703-1299 2012-09-12 2012-09-12
## 57  01-703-1335 2014-03-17 2014-03-17
## 58  01-703-1379 2013-09-22 2013-09-22
## 59  01-703-1403 2012-12-12 2012-12-12
## 60  01-703-1439 2014-03-12 2014-03-12
## 61  01-704-1008 2013-01-13 2013-01-13
## 62  01-704-1009 2013-08-27 2013-08-27
## 63  01-704-1010 2014-02-21 2014-02-21
## 64  01-704-1017 2013-10-06 2013-10-06
## 65  01-704-1025 2013-09-27 2013-09-27
## 66  01-704-1065 2013-10-24 2013-10-24
## 67  01-704-1074 2014-01-22 2014-01-22
## 68  01-704-1093 2013-03-15 2013-03-15
## 69  01-704-1114 2013-01-23 2013-01-23
## 70  01-704-1120 2013-12-02 2013-12-02
## 71  01-704-1127 2013-10-02 2013-10-02
## 72  01-704-1135 2013-10-31 2013-10-31
## 73  01-704-1164 2012-09-19 2012-09-19
## 74  01-704-1218 2012-11-19 2012-11-19
## 75  01-704-1233 2013-03-21 2013-03-21
## 76  01-704-1241 2013-08-25 2013-08-25
## 77  01-704-1260 2012-08-30 2012-08-30
## 78  01-704-1266 2013-10-13 2013-10-13
## 79  01-704-1323 2013-07-08 2013-07-08
## 80  01-704-1325 2014-04-23 2014-04-23
## 81  01-704-1332 2013-12-09 2013-12-09
## 82  01-704-1351 2013-10-12 2013-10-12
## 83  01-704-1388 2012-12-07 2012-12-07
## 84  01-704-1435 2012-11-17 2012-11-17
## 85  01-704-1445 2014-05-11 2014-05-11
## 86  01-705-1018 2013-07-05 2013-07-05
## 87  01-705-1031 2013-11-27 2013-11-27
## 88  01-705-1059 2013-08-05 2013-08-05
## 89  01-705-1186 2014-01-08 2014-01-08
## 90  01-705-1199 2013-09-16 2013-09-16
## 91  01-705-1280 2014-01-17 2014-01-17
## 92  01-705-1281 2013-11-28 2013-11-28
## 93  01-705-1282 2012-12-26 2012-12-26
## 94  01-705-1292 2013-10-14 2013-10-14
## 95  01-705-1303 2013-12-16 2013-12-16
## 96  01-705-1310 2013-11-02 2013-11-02
## 97  01-705-1349 2013-03-10 2013-03-10
## 98  01-705-1377 2014-01-04 2014-01-04
## 99  01-705-1382 2013-05-13 2013-05-13
## 100 01-705-1393 2012-09-07 2012-09-07
## 101 01-705-1431 2013-06-23 2013-06-23
## 102 01-706-1041 2013-12-31 2013-12-31
## 103 01-706-1049 2013-05-14 2013-05-14
## 104 01-706-1384 2012-09-15 2012-09-15
## 105 01-707-1037 2013-12-20 2013-12-20
## 106 01-707-1206 2013-10-28 2013-10-28
## 107 01-708-1019 2013-12-20 2013-12-20
## 108 01-708-1032 2013-02-09 2013-02-09
## 109 01-708-1084 2013-05-09 2013-05-09
## 110 01-708-1087 2012-10-22 2012-10-22
## 111 01-708-1158 2014-02-08 2014-02-08
## 112 01-708-1171 2012-12-06 2012-12-06
## 113 01-708-1178 2013-12-29 2013-12-29
## 114 01-708-1213 2013-02-09 2013-02-09
## 115 01-708-1216 2012-10-24 2012-10-24
## 116 01-708-1236 2013-09-21 2013-09-21
## 117 01-708-1253 2013-05-07 2013-05-07
## 118 01-708-1272 2013-02-06 2013-02-06
## 119 01-708-1286 2013-09-10 2013-09-10
## 120 01-708-1296 2013-06-14 2013-06-14
## 121 01-708-1297 2013-01-25 2013-01-25
## 122 01-708-1316 2013-08-23 2013-08-23
## 123 01-708-1336 2012-12-07 2012-12-07
## 124 01-708-1342 2012-12-29 2012-12-29
## 125 01-708-1347 2013-04-20 2013-04-20
## 126 01-708-1348 2013-08-05 2013-08-05
## 127 01-708-1353 2013-07-04 2013-07-04
## 128 01-708-1372 2013-04-12 2013-04-12
## 129 01-708-1378 2013-09-03 2013-09-03
## 130 01-708-1406 2013-12-26 2013-12-26
## 131 01-708-1428 2013-11-09 2013-11-09
## 132 01-709-1001 2013-10-08 2013-10-08
## 133 01-709-1007 2012-07-31 2012-07-31
## 134 01-709-1020 2012-12-01 2012-12-01
## 135 01-709-1029 2012-12-25 2012-12-25
## 136 01-709-1081 2014-01-18 2014-01-18
## 137 01-709-1088 2014-04-12 2014-04-12
## 138 01-709-1099 2013-10-25 2013-10-25
## 139 01-709-1102 2013-01-15 2013-01-15
## 140 01-709-1168 2013-08-02 2013-08-02
## 141 01-709-1217 2013-03-04 2013-03-04
## 142 01-709-1238 2013-05-15 2013-05-15
## 143 01-709-1259 2013-01-26 2013-01-26
## 144 01-709-1285 2013-03-24 2013-03-24
## 145 01-709-1301 2013-07-19 2013-07-19
## 146 01-709-1306 2014-02-03 2014-02-03
## 147 01-709-1309 2013-06-19 2013-06-19
## 148 01-709-1312 2014-04-20 2014-04-20
## 149 01-709-1326 2013-04-05 2013-04-05
## 150 01-709-1329 2013-08-15 2013-08-15
## 151 01-709-1339 2012-12-23 2012-12-23
## 152 01-709-1424 2013-03-03 2013-03-03
## 153 01-710-1002 2014-01-14 2014-01-14
## 154 01-710-1006 2013-02-10 2013-02-10
## 155 01-710-1021 2013-09-27 2013-09-27
## 156 01-710-1027 2014-02-28 2014-02-28
## 157 01-710-1045 2013-06-03 2013-06-03
## 158 01-710-1053 2012-12-26 2012-12-26
## 159 01-710-1060 2013-01-01 2013-01-01
## 160 01-710-1070 2012-09-08 2012-09-08
## 161 01-710-1077 2013-11-17 2013-11-17
## 162 01-710-1078 2013-09-17 2013-09-17
## 163 01-710-1083 2013-07-22 2013-07-22
## 164 01-710-1137 2013-10-11 2013-10-11
## 165 01-710-1142 2012-10-02 2012-10-02
## 166 01-710-1154 2014-03-29 2014-03-29
## 167 01-710-1166 2012-11-30 2012-11-30
## 168 01-710-1183 2013-11-16 2013-11-16
## 169 01-710-1187 2012-11-10 2012-11-10
## 170 01-710-1235 2012-09-26 2012-09-26
## 171 01-710-1249 2013-12-28 2013-12-28
## 172 01-710-1264 2013-06-13 2013-06-13
## 173 01-710-1270 2014-02-12 2014-02-12
## 174 01-710-1271 2012-09-27 2012-09-27
## 175 01-710-1278 2012-12-24 2012-12-24
## 176 01-710-1300 2012-12-15 2012-12-15
## 177 01-710-1314 2013-04-24 2013-04-24
## 178 01-710-1315 2013-02-27 2013-02-27
## 179 01-710-1354 2012-11-11 2012-11-11
## 180 01-710-1358 2012-09-17 2012-09-17
## 181 01-710-1368 2013-10-23 2013-10-23
## 182 01-710-1385 2012-10-29 2012-10-29
## 183 01-710-1408 2013-01-05 2013-01-05
## 184 01-711-1012 2013-04-03 2013-04-03
## 185 01-711-1036 2012-07-29 2012-07-29
## 186 01-711-1143 2013-04-03 2013-04-03
## 187 01-711-1433 2013-01-27 2013-01-27
## 188 01-713-1043 2013-09-15 2013-09-15
## 189 01-713-1073 2014-03-30 2014-03-30
## 190 01-713-1106 2012-10-31 2012-10-31
## 191 01-713-1141 2013-05-31 2013-05-31
## 192 01-713-1179 2013-08-09 2013-08-09
## 193 01-713-1209 2013-05-27 2013-05-27
## 194 01-713-1256 2012-09-19 2012-09-19
## 195 01-713-1269 2014-01-27 2014-01-27
## 196 01-713-1448 2014-01-19 2014-01-19
## 197 01-714-1035 2014-04-17 2014-04-17
## 198 01-714-1068 2013-08-08 2013-08-08
## 199 01-714-1195 2013-04-26 2013-04-26
## 200 01-714-1288 2013-12-04 2013-12-04
## 201 01-714-1375 2013-02-26 2013-02-26
## 202 01-714-1425 2013-08-15 2013-08-15
## 203 01-715-1085 2013-02-16 2013-02-16
## 204 01-715-1107 2013-02-26 2013-02-26
## 205 01-715-1155 2013-12-13 2013-12-13
## 206 01-715-1207 2012-11-18 2012-11-18
## 207 01-715-1319 2013-02-17 2013-02-17
## 208 01-715-1321 2014-02-11 2014-02-11
## 209 01-715-1397 2013-04-03 2013-04-03
## 210 01-715-1405 2013-07-06 2013-07-06
## 211 01-716-1024 2012-07-09 2012-07-09
## 212 01-716-1026 2014-04-02 2014-04-02
## 213 01-716-1030 2013-12-28 2013-12-28
## 214 01-716-1044 2013-04-27 2013-04-27
## 215 01-716-1063 2013-05-09 2013-05-09
## 216 01-716-1071 2013-06-08 2013-06-08
## 217 01-716-1094 2012-12-19 2012-12-19
## 218 01-716-1103 2014-03-20 2014-03-20
## 219 01-716-1108 2013-02-12 2013-02-12
## 220 01-716-1151 2013-02-01 2013-02-01
## 221 01-716-1157 2013-10-02 2013-10-02
## 222 01-716-1160 2013-04-05 2013-04-05
## 223 01-716-1167 2012-10-08 2012-10-08
## 224 01-716-1177 2014-09-02 2014-09-02
## 225 01-716-1189 2012-10-09 2012-10-09
## 226 01-716-1229 2013-02-20 2013-02-20
## 227 01-716-1298 2013-04-08 2013-04-08
## 228 01-716-1308 2013-08-28 2013-08-28
## 229 01-716-1311 2014-05-14 2014-05-14
## 230 01-716-1364 2013-07-04 2013-07-04
## 231 01-716-1373 2012-12-14 2012-12-14
## 232 01-716-1418 2013-05-05 2013-05-05
## 233 01-716-1441 2014-01-22 2014-01-22
## 234 01-716-1447 2013-12-16 2013-12-16
## 235 01-717-1004 2014-01-14 2014-01-14
## 236 01-717-1109 2014-01-27 2014-01-27
## 237 01-717-1174 2013-01-22 2013-01-22
## 238 01-717-1201 2013-12-19 2013-12-19
## 239 01-717-1344 2014-01-11 2014-01-11
## 240 01-717-1357 2013-05-01 2013-05-01
## 241 01-717-1446 2013-09-01 2013-09-01
## 242 01-718-1066 2013-07-07 2013-07-07
## 243 01-718-1079 2012-09-19 2012-09-19
## 244 01-718-1101 2013-02-17 2013-02-17
## 245 01-718-1139 2013-05-19 2013-05-19
## 246 01-718-1150 2013-01-19 2013-01-19
## 247 01-718-1170 2013-09-16 2013-09-16
## 248 01-718-1172 2013-09-21 2013-09-21
## 249 01-718-1250 2013-09-21 2013-09-21
## 250 01-718-1254 2013-07-10 2013-07-10
## 251 01-718-1328 2013-02-01 2013-02-01
## 252 01-718-1355 2013-02-28 2013-02-28
## 253 01-718-1371 2013-04-26 2013-04-26
## 254 01-718-1427 2012-12-17 2012-12-17
```

```r
# nature of usubjid is character and svstdtc is <s3.labelled> 

adsl_deri01 <- inner_join(adsl_deri01, sv_visit3 , by = "usubjid")


adsl_deri02 <- adsl_deri01 %>%  
               
               select (usubjid , trtsdt, svstdtc , actarmcd , sitegr1, siteid , trt01p, arm , trt01a , trt01pn ,trt01pn,ittfl,agegr1,age,agegr1n,race               ,racen,sex,ethnic , rfstdtc ,
               rfendtc , sex , ethnic , dthfl )
#adsl_deri02
```

### Date of Last Exposure to Treatment (TRTEDT)

The date of final dose (from the CRF) is EX.EXENDTC on the subject's last EX record. If the date of final dose is missing for the subject and the subject discontinued after visit 3, use the date of discontinuation as the date of last dose.

Steps to arrive at logic

1.  Check for the subjects whose final dose date is missing
2.  `Check if these subjects discontinued after visit 3 (Check  if they have any records after the Visit 3 , this needs checked )`
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



 
adsl_chk <- select (adsl , usubjid , trtedt )
```

`Using the as.Date(as.Character ()) is creating numerical dates and date formats are not being , need to learn more about the as.Date .`{=beamer}

using the as.Date( as.character () ) is creating numerical dates and date formats are not

Below Logic is how you conditionally create a new column trtedt based DSSTDTC and exendtc_orig


```r
# Subjects whose does dates are missing 
exendtc_1 <- exendtc %>% 
           mutate ( flag = ifelse (exendtc   %in% NA  ,  "N" ,"Y"   ) ,
           trtedt =   ifelse(flag == "N", as.character(dsstdtc), 
                        ifelse (flag =="Y" ,as.character(exendtc_orig)  , NA  ))  ) %>% 
           filter (visitnum >= 3 )
```


```r
#Final dates check 

exendtc <- ex %>% 
            mutate(usubjid = as.character(usubjid) ,  
                   exendtc_orig = exendtc, 
                   exendtc = as.Date(as.character(exendtc)) ) %>% 
           select( usubjid ,visit , visitnum,  exendtc , exendtc_orig )


exendtc <- inner_join(exendtc , sv_visit3 , by = "usubjid")

# Subjects whose does dates are missing 
exendtc <- exendtc %>% 
  
           mutate ( flag = ifelse (exendtc   %in% NA  ,  "N" ,"Y"   ), 
                    
           trtedt_c  = ifelse(exendtc   %in%  NA  , svstdtc , exendtc_orig ) , 
           trtedt   =  as.Date(as.character(trtedt_c))   ,
           
trtedt_n     = as.numeric(ifelse(exendtc   %in%  NA  ,trtsdt , exendtc ) ) 
#, trtedt_ndt   =  as.Date.numeric (trtedt_n)   
           
           )   %>% 
           filter (visitnum >= 3 )
 
# One of the ways to get the First and Last group by values 
# Make sure you use the right variables used group_by 

exend <- exendtc %>% 
         group_by (usubjid) %>% 
         dplyr:: mutate(
           first = dplyr::first(exendtc) , 
           last  = dplyr::last (exendtc)
         ) %>% 
          summarise(trtedt = last(exendtc))
```

```
## `summarise()` ungrouping output (override with `.groups` argument)
```

```r
#exendtc <- select(exendtc,usubjid ,visitnum , trtedt, trtedt_c  )
```

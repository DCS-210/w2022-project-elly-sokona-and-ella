Project proposal
================
Elly, Sokona and Ella

``` r
library(tidyverse)
library(broom)
```

## 1. Introduction

General research question:

Is there a correlation between the racial majority of the neighborhood
and the number of allegations against police officers? Is there a
correlation between the racial majority of the neighborhood and how
likely the allegation is to be disciplined?

Sub questions: Which neighborhoods are complaints most likely to be
disciplined? Sustained? Exonerated? (which means that the incident was
deemed lawful and proper) Are repeat complaints against an officer more
likely to be sustained? Overruled? Does the race of the
officer/complainant impact how likely a complaint is to be disciplined?
Does the rank/time as an officer impact how likely the officer is
disciplined? Does the rank/time as an officer impact how likely the
officer has more complaints against them?

Introducing our data:

We are using data collected from the Invisible Institute, an
investigative journalism production company on the South Side of
Chicago. In 2007, the invisible institute sued the city to demand the
release of complaint records against the Chicago Police Department. The
files were finally released in 2016, revealing over 100,000 complaint
records to the public. This data is publicly available at
<https://github.com/invinst/chicago-police-data>. This dataset is
massive, as such, we will only be using a small subset of the data. Here
are links to the raw data:

Community demographics:
<https://github.com/invinst/chicago-police-data/blob/master/data/context_data/district_demographics/Districts.csv>

Accused officer:
<https://github.com/invinst/chicago-police-data/blob/master/data/older_data/cleaned_data/complaints-accused_2000-2016_2016-11.csv.gz>

Complainants:
<https://github.com/invinst/chicago-police-data/blob/master/data/older_data/cleaned_data/complaints-complainants_2000-2016_2016-11.csv.gz>

Content of complaints:
<https://github.com/invinst/chicago-police-data/blob/master/data/older_data/cleaned_data/complaints-complaints_2000-2016_2016-11.csv.gz>

Active duty officer:
<https://github.com/invinst/chicago-police-data/blob/master/data/context_data/CPD%20Employees%20active-duty-only.csv>

## 2. Data

## 3. Data analysis plan

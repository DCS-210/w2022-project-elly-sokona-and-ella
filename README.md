Elly, Sokona and Ella
================
by Team name

## Summary

Write-up of your project and findings go here. Think of this as the text
of your presentation. The length should be roughly 5 minutes when read
out loud. Although pacing varies, a 5-minute speech is roughly 750
words. To use the word count addin, select the text you want to count
the words of (probably this is the Summary section of this document, go
to Addins, and select the `Word count` addin). This addin counts words
using two different algorithms, but the results should be similar and as
long as you’re in the ballpark of 750 words, you’re good! The addin will
ignore code chunks and only count the words in prose.

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
Chicago. In 2007, the Invisible Institute sued the city of Chicago,
demanding the release of complaint records against the Chicago Police
Department. The files were finally released in 2016, revealing over
100,000 complaint records to the public. This data is publicly available
at <https://github.com/invinst/chicago-police-data>. This dataset is
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

You can also load your data here and present any analysis results /
plots, but I strongly urge you to keep that to a minimum (maybe only the
most important graphic, if you have one you can choose). And make sure
to hide your code with `echo = FALSE` unless the point you are trying to
make is about the code itself. Your results with proper output and
graphics go in your presentation, this space is for a brief summary of
your project.

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✓ ggplot2 3.3.5     ✓ dplyr   1.0.7
    ## ✓ tibble  3.1.4     ✓ stringr 1.4.0
    ## ✓ tidyr   1.1.3     ✓ forcats 0.5.1
    ## ✓ purrr   0.3.4

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

    ## Rows: 22 Columns: 16

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (8): District_Name, Latino%, White%, Black%, Native_American%, Asian%, O...
    ## dbl (2): District_No, Native_American

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

    ## Rows: 13530 Columns: 11

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (9): LAST_NME, FIRST_NME, EMPLOYEE_POSITION, CPD_UNIT_ASSIGNED_NO, UNITA...
    ## dbl (2): AGE, STAR_NO

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

    ## Warning: One or more parsing issues, see `problems()` for details

    ## Rows: 125581 Columns: 22

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (12): gender, race, current_rank, complaint_category, recommended_findi...
    ## dbl   (7): row_id, cr_id, birth_year, current_unit, current_star, recommende...
    ## lgl   (2): middle_initial, middle_initial2
    ## date  (1): appointed_date

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

    ## Rows: 48214 Columns: 4

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): gender, race
    ## dbl (2): cr_id, age

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

    ## Rows: 131142 Columns: 12

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (6): beat, location_code, address_number, street, apartment_number, cit...
    ## dbl  (2): row_id, cr_id
    ## date (3): incident_date, complaint_date, closed_date
    ## time (1): incident_time

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

    ## Rows: 22
    ## Columns: 16
    ## $ District_No        <dbl> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 14, 15, 16, …
    ## $ District_Name      <chr> "Central", "Wentworth", "Grand Crossing", "South Ch…
    ## $ Population         <dbl> 62781, 95439, 75235, 123575, 74396, 90841, 71071, 2…
    ## $ Latino             <dbl> 3766, 3242, 1123, 35381, 2524, 914, 1167, 139854, 9…
    ## $ White              <dbl> 32952, 17747, 1472, 9925, 843, 312, 262, 51491, 243…
    ## $ Black              <dbl> 13452, 65993, 71010, 76399, 70064, 88525, 68787, 52…
    ## $ Native_American    <dbl> 95, 138, 169, 223, 118, 164, 136, 247, 173, 144, 73…
    ## $ Asian              <dbl> 10790, 5837, 312, 258, 38, 61, 56, 2001, 25894, 239…
    ## $ Other              <dbl> 1726, 2482, 1149, 1389, 809, 865, 663, 1561, 1173, …
    ## $ `Latino%`          <chr> "6%", "3%", "1%", "29%", "3%", "1%", "2%", "57%", "…
    ## $ `White%`           <chr> "52%", "19%", "2%", "8%", "1%", "0%", "0%", "21%", …
    ## $ `Black%`           <chr> "21%", "69%", "94%", "62%", "94%", "97%", "97%", "2…
    ## $ `Native_American%` <chr> "0%", "0%", "0%", "0%", "0%", "0%", "0%", "0%", "0%…
    ## $ `Asian%`           <chr> "17%", "6%", "0%", "0%", "0%", "0%", "0%", "1%", "1…
    ## $ `Other%`           <chr> "3%", "3%", "2%", "1%", "1%", "1%", "1%", "1%", "1%…
    ## $ Majority           <chr> "White", "Black", "Black", "Black", "Black", "Black…

    ## Rows: 13,530
    ## Columns: 11
    ## $ LAST_NME             <chr> "ABDELMAJEID", "ABRON", "ALVAREZ", "ANDERSON", "A…
    ## $ FIRST_NME            <chr> "AZIZ", "FLOYD", "ARMANDO", "COREY", "ARTURO", "J…
    ## $ EMPLOYEE_POSITION    <chr> "POLICE OFFICER", "POLICE OFFICER", "POLICE OFFIC…
    ## $ CPD_UNIT_ASSIGNED_NO <chr> "001", "001", "001", "001", "001", "001", "001", …
    ## $ UNITASGDESC          <chr> "DISTRICT 001", "DISTRICT 001", "DISTRICT 001", "…
    ## $ AGE                  <dbl> 31, 42, 39, 47, 48, 51, 49, 32, 29, 53, 59, 47, 5…
    ## $ APPOINTED_DATE       <chr> "28-Apr-08", "29-Jun-98", "30-Apr-07", "26-Mar-01…
    ## $ SEX_CODE_CD          <chr> "M", "M", "M", "M", "M", "M", "F", "M", "F", "M",…
    ## $ RACE                 <chr> "ASIAN/PACIFIC ISLANDER", "BLACK", "HISPANIC", "B…
    ## $ STAR_NO              <dbl> 14008, 12861, 7861, 6023, 13718, 244, 4673, 8533,…
    ## $ SWORN_OFFICER_I      <chr> "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y",…

    ## Rows: 131,142
    ## Columns: 12
    ## $ row_id           <dbl> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16…
    ## $ cr_id            <dbl> 258996, 258997, 258998, 258999, 259000, 259001, 25900…
    ## $ beat             <chr> "1524", "1115", "1834", "0", "1524", "0423", "2221", …
    ## $ location_code    <chr> "04", "17", "17", "17", "04", "17", "17", "04", "14",…
    ## $ address_number   <chr> "5327", "4316", "500", NA, "5327", "2940", "8726", NA…
    ## $ street           <chr> "W CHICAGO", "W JACKSON", "W ILLINOIS", NA, "W CHICAG…
    ## $ apartment_number <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, "-----", NA, …
    ## $ city_state       <chr> "CHICAGO IL", "CHICAGO IL", "CHICAGO IL", "CHICAGO IL…
    ## $ incident_date    <date> 2000-01-01, 2000-01-01, 2000-01-01, 2000-01-01, 2000…
    ## $ incident_time    <time> 01:20:00, 01:30:00, 00:28:00, 03:30:00, 05:00:00, 04…
    ## $ complaint_date   <date> 2000-01-01, 2000-01-01, 2000-01-01, 2000-01-01, 2000…
    ## $ closed_date      <date> 2001-01-26, 2000-10-14, 2001-01-18, 2000-03-23, 2001…

Below is the Codebook for our datasets

Codebook:

District_demographics: `District_No`: District number `District_Name`:
The name of the district `Population`: The number of people in each
district `Latino`: The Latino population in the district `White`: The
white population in the district `Black`: The Black population in the
district `Native_American`: The Native American population in the
district `Asian`: The Asian population in the district `Other`: The
number of people in a district where race is not recorded or does not
fall into the above categories `Latino%`: The percent of Latino people
in a district `White%`: The percent of White people in a district
`Black%`: The percent of Black people in a district `Native_American%`:
The percent of Native American people in a district `Asian%`: The
percent of Asian people in a district `Other%`: The percent of people in
a district where race is not recorded or does not fall into the above
categories `Majority`: What the racial majority in a district is

Complaints-accused `Row_id`: The row number `Cr_id`: Individual
identification number for each complaint `Birth_year`: Birth year of
officer `Gender`: Gender of officer `Race`: Race of officer
`Appointed_date`: Date the officer was appointed `Curent_unit`: Current
unit of officer `Current_rank`: Current rank of officer `Current_star`:
The star number of the officer accused `Complaint_category`: The
category of the complaint against the officer `Recommend_finding`: The
recommended findings following an investigation of the complaint.
Possible outcomes are unfounded (UN), exonerated (EX), not sustained
(NS) and Sustained (SU). `Recommended_discipline`: The recommended
disciplinary action taken against the officer `Final_finding`: The final
findings following an investigation of the complaint. Possible outcomes
are unfounded (UN), exonerated (EX), not sustained (NS) and Sustained
(SU). `Final_discipline`: The actual disciplinary action taken against
the officer `First_name`: First name of officer `first _name_NS`: First
name of officer `Full_name`: Full name of officer `Last_name`: Last name
of officer `last_name_NS`: Last name of officer `Middle_initial`: Middle
initial of officer `Middle_initial2`: Second middle initial of officer
`Suffix_name`: Suffix of officer

Complaints-complainants `Gender`: Gender of complainant `Age`: Age of
complainant `Race`: Race of complainant

Complaints-complaints_2000-2016_2016-11 `Row_id`: The row number
`Cr_id`: Individual identification number for each complaint `Beat`:
Which beat the the complaint issue occurred `Location_code`: The
location code of where the complaint issue occurred `Address_number`:
The address number where the complaint issue occurred `Street`: The
street where the complaint issue occurred `Apartment_number`: The
apartment number where the complaint issue occurred `City_state`: The
city where the complaint issue occurred `Incident_date`: The date when
the complaint issue occurred `Incident_time`: The time that the
complaint issue occurred `Complaint_date`: The date the complaint was
made `Closed_date`: The date the complaint was closed

active-duty-only `Last_nme`: Last name of officer `First_nme`: First
name of officer `Employee_position`: Position of officer
`Cpd_unit_assigned_no`: CPD unit number of officer `Unit_assigned_no`:
Number of the unit the officer was assigned to `Units_Desc`: District of
officer `Age`: Age of officer `Appointed_date`: Date officer was
appointed `Sex_code_cd`: Sex of officer `Race`: Race of officer
`Star_no`: The star number of the police officer `sworn_officer_I`:
Whether officer is a sworn officer or not

## Presentation

Hypothesis: We will see more complaints from Black residents, regardless
of the racial makeup of the neighborhood. We expect to see more
allegations per capita in neighborhoods with higher proportions of Black
residents.

Is there a correlation between the racial majority of the neighborhood
and the number of allegations against police officers? Outcome – number
of allegations against officers Predictor – neighborhood’s racial
demographics (likely percentage of one racial group) Statistical methods
– calculating correlation coefficient Ways to display this data –
geom(point)

Is there a correlation between the racial majority of the neighborhood
and how likely the allegation is to be disciplined? Outcome – Proportion
of allegations disciplined Predictor – neighborhood’s racial
demographics (likely percentage of one racial group) Statistical methods
– determine proportion of each complaints resulting in discipline or
finding of fault in each neighborhood

I calculated the average age and the number of proportions of
complainants by race and gender. Even without the proportion calculated
and looking at the frequency for each group, we can see that there’s a
large amount of complainants coming from Black male and female
residents.

According to the US Census Bureau QuickFacts, found here:
\[<https://www.census.gov/quickfacts/chicagocityillinois>\] Chicago is
33.3% white, 29.6% Black, 28.8% Hispanic or Latino, 0.3% American Indian
and Alaskan Native, 6.6% Asian, and 2.8% multiracial. The above summary
statistics show a disproportionately high number of complaints from
Black Chicagoans.

``` r
#calculating total for the proportions 
total <- complainants %>%
  nrow()

complainants %>%
  group_by(race, gender) %>%
  summarise(mean = mean(age, na.rm = TRUE), n_1 = n(), prop = n_1/total)
```

    ## `summarise()` has grouped output by 'race'. You can override using the `.groups` argument.

    ## # A tibble: 15 × 5
    ## # Groups:   race [6]
    ##    race                           gender  mean   n_1      prop
    ##    <chr>                          <chr>  <dbl> <int>     <dbl>
    ##  1 ASIAN/PACIFIC ISLANDER         FEMALE  43.4   134 0.00278  
    ##  2 ASIAN/PACIFIC ISLANDER         MALE    43.8   293 0.00608  
    ##  3 BLACK                          FEMALE  44.7 14543 0.302    
    ##  4 BLACK                          MALE    42.5 14589 0.303    
    ##  5 BLACK                          <NA>    39.2     4 0.0000830
    ##  6 HISPANIC                       FEMALE  42.3  2261 0.0469   
    ##  7 HISPANIC                       MALE    41.7  3149 0.0653   
    ##  8 NATIVE AMERICAN/ALASKAN NATIVE FEMALE  41.9    17 0.000353 
    ##  9 NATIVE AMERICAN/ALASKAN NATIVE MALE    46.9    21 0.000436 
    ## 10 WHITE                          FEMALE  47.9  3590 0.0745   
    ## 11 WHITE                          MALE    49.6  6732 0.140    
    ## 12 WHITE                          <NA>   NaN       1 0.0000207
    ## 13 <NA>                           FEMALE  45.9   769 0.0159   
    ## 14 <NA>                           MALE    44.0  1840 0.0382   
    ## 15 <NA>                           <NA>    43.8   271 0.00562

Our presentation can be found [here](presentation/presentation.html).

## Data

Include a citation for your data here. See
<http://libraryguides.vu.edu.au/c.php?g=386501&p=4347840> for guidance
on proper citation for datasets. If you got your data off the web, make
sure to note the retrieval date.

## References

List any references here. You should, at a minimum, list your data
source.

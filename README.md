Understanding the Relationship Between Neighborhood Demographics and
Allegations of Police Misconduct in Chicago
================
Sokona, Ella, and Elly

## Introduction:

This project was concerned with examining a social justice issue using
data. The data we used was collected by the Invisible Institute about
police complaints in Chicago from 1988-2018. Through FOI requests, in
2016 more than 100,000 complaint records were released to the public.

Using this data, we examined patterns in that data around racial
composition of neighborhoods, the number of complaints, and complaint
outcomes. We ask three main questions of this data: What are the racial
makeups of different neighborhoods in Chicago? In which neighborhoods
are there the most police complaints per capita? What are the outcomes
of police complaints? The methodology on how we examined these questions
is detailed further below. These sorts of questions have been
increasingly asked of data concerning police behavior as awareness of
police brutality across America has grown. While issues of over policing
and police brutality have long been things that many Americans,
particularly Black Americans have long said are major community issues,
data empirically backs up findings that Black people and other people of
color are more likely to be targets of police abuse. The questions we
asked of this data are aligned with these issues. Hopefully, these sorts
of inquiries inspire policy changes that make communities safer from the
police.

## Methodology:

We created a number of leaflet maps to give our viewers a better sense
of the demographic distribution of Chicago and help contextualize later
visualizations. These showed the percentage of Black, white, and Latino
residents in each neighborhood.

To understand the relationship between racial makeup of a neighborhood
and complaints per capita, we filtered the data set of those accused in
complaints to only include entries where the complaint could be matched
to an officer from a unit matching the neighborhoods in the district
demographics dataset. Then we joined this with the demographic data from
the districts and mutated to create a new variable showing the
complaints per capita, then created a lollipop plot. We also made a
leaflet map to show this data spatially.

We next aimed to visualize the final result of the complaints by
district. To do this, we cleaned up the data, sorting it into usable
categories of sustained, unsustained, no affidavit/cooperation, and
missing. When the complaint is missing an affidavit it means that the
person who made the complaint did not provide a written statement of
their complaint. We then created a filled bar plot that showed the
proportion of complaints that were sustained, not sustained, missing an
affidavit or had missing data.

We also took the data used to create the findings visualization and,
filtering for just missing, sustained, and no affidavit complaints
respectively, created visualizations of each of these complaint types
per capita. In these three visualizations, we choose not to include
disciplined or no cooperation as this represented a negligible number of
complaints (only 6 and 29 complaints out of around 70,000).

## Findings/Discussion:

We hypothesized that most complaints would happen in Black
neighborhoods, given the nature of police brutality and the interactions
that police have with Black people in the United States. Our lollipop
plot illustrated that besides two districts (Central and Near North, the
10 districts with the most complaints per capita were majority Black. In
considering the outcomes of police complaints, about 87% of the
investigations ended with no finding of fault. When we look at these
results more closely across district, through our bar plot, Wentworth, a
majority Black district which didn’t have the most complains per capita,
had the most sustained complaints out of all of the districts; despite
this, most districts align with the distribution of findings among the
whole data, with no one district being disproportionate. It is worth
noting that Central (majority white) had the second most sustained
complaints per capita. It also had the most missing complaints per
capita, followed by a number of Black majority districts. It is also
worth noting that the top 6 no affidavit complaints per capita were in
Black majority districts. All of our findings confirmed our initial
expectations about what the data would reveal. Chicago’s long history of
housing segregation and current continued housing segregation allowed us
to see a stark contrast between the way neighborhoods with majority
Black residents are policed and how majority white neighborhoods are.

Because of the limited district data available, we only looked at 25
districts; this dataset still left us with 70,000 complaints.
Regardless, unless the allegation involved criminal conduct or a
residency violation, anonymous complaints can’t be investigated. Thus,
even with the ability to file a complaint, 27.8% of the data includes
complaints from those who didn’t provide an affidavit, mostly from
majority Black districts, and therefore don’t get investigated. While it
may be harder to check the validity of anonymous complaints, we wonder
if this requirement is preventing complaints from filing as a result of
safety or other personal reasons. When complaints are investigated, out
of 47,000 complaints, 6% justified disciplinary action and .008% (6) led
to Officers being reprimanded, suspended for a set number of days, or
separated. Therefore, while Black complaints are more likely to complain
against police officers in this dataset, it is unlikely that the
complaint would even justify disciplinary action and even lead to any
action regardless of race.

Further research should look at what type of allegations were more
likely to be sustained and if there’s a correlation between the type of
allegations and the person who made it. Research should also be done on
the effectiveness of filing complaints against police officers and about
the power they have, which prevents any change happening. If given more
time, we would want to further explore how complaints have changed over
the years, and more about the correlation between the race of the
officer versus the race of the accuser in these complaints.

Our presentation can be found [here](presentation/presentation.html).

## Data

This data is publicly available at
<https://github.com/invinst/chicago-police-data>. This dataset is
massive and broken into many different dataframes so much of our time at
first was spent choosing and merging the best data frames together.

## References

Links to the raw data:

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

Unit codes:
<https://github.com/invinst/chicago-police-data/blob/master/data/context_data/current_and_past_units/Current_and_Past_CPD_Units_2016-05-06.csv>

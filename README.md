# NICAR 2026: Using immigration data to tell stories in your community
Friday, March 6, 9-10 a.m. CT

Julia Ingram and Joe Yerardi

## Overview

As record numbers of immigrants are being arrested and detained under the second Trump administration, those with active immigration cases are also seeing dramatically shifting outcomes. But data on immigration cases, released monthly by the [Executive Office for Immigration Review (EOIR)](https://www.justice.gov/eoir/foia-library-0) as a massive relational database, can be hard to parse. The Transactional Records Access Clearinghouse (TRAC) has a few [useful tools](https://tracreports.org/immigration/tools) based on this data that make tracking immigration cases easier. 

Case data is broken down by the city of the immigration court, which means you can zoom in to see what's happening in your city or state, and then compare it to what's happening across the country.

TRAC displays its data in tools that are easy to use for extracting quick statistics. But it lacks an easy download button for more in-depth analysis on the underlying data. We'll show you how to take advantage of an undocumented API on TRAC's website to extract the data. Then, we'll walk you through a few different analysis questions.

This session will be modeled after Joe's Philadelphia Inquirer story ["Philadelphia’s immigration court now rejects three in four asylum cases under Trump"](https://archive.is/62i4T) from October 2025. 

## TRAC Tools

TRAC has several tools for tracking immigration court outcomes. Here's an overview for the ones that will likely be the most useful to reporting on local immigration in 2026:

- Proceeding Outcomes: Each time an immigration judge issues a significant ruling on a case, it is logged in the EOIR data as a proceeding. An individual's case can, and often does, have multiple proceedings. TRAC here allows you to toggle between deprotation cases, also known as removal cases, and all. Removal cases constitute the vast majority of immigration court cases. Immigrants who are in removal proceedings can request asylum, so most asylum cases are included here as well. The available outcomes include:
    - Removals: deportations
    - Vol departure: voluntary departures, in which an immigrant can request that a judge allow them to return home on their own rather than receieve a deportation order. These individuals still may end up on a deportation flight operated by ICE if they are returning to a country the U.S. frequently deports people to. This allows immigrants to avoid having a deportation on their record, allowing for a lower bar to re-entry. Voluntary departures are far more common among detained immigrants, and are reaching new heights under the current administration. 
    - Terminations: This is when an immigration judge dismisses a case. Once a case is terminated, it cannot be reopened by DHS unless a new charging document is filed against the immigrant. This is different from administrative closure, which temporarily takes the case off the docket. 
    - Relief granted: The individual was granted asylum or some other form of relief that allows them to stay in the U.S.
    - Other: All other outcomes, including administrative closure or transfers to the Board of Immigration Appeals
- Court backlog: This tool shows cases before immigration courts that have not yet been adjudicated. These can be split by charge type - the portion of the Immigration and Nationality Act the individual is accused of violating - but note that immigrants with prior criminal records are not necesarily charged with criminal violations of immigration law. In other words, those with prior charges or convictions can still a appear in the "immigration" charge type category.
- Mapping representation: This 50-state map shows the number of pending cases in each state and how many of the individuals those cases represent have lawyers. Many immigrants represent themselves (pro se), though those individuals historically see less favorable outcomes.
- Asylum decisions:
- Asylum decisions by judge: TRAC periodically releases an analysis of how asylum grant rates differ by judge. Historically, there is a huge range of outcomes, and you can zoom in to your city or state to see how it compares with those in other places. In the past, California judges have had higher grant rates than judges in the southern U.S., for example. 
- Bond decisions: Since the second Trump administration has widely expanded its use of mandatory detention, a record number of people are being detained -- and staying in detention. Bond rates are hitting new lows. 


Across all of these tools, TRAC lets you select a geographic area and drill down on up to two variables, such as custody, legal representation or nationality, which you can select by clicking the down arrow on each column header to expand the dropdown menu.


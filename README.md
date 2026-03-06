# NICAR 2026: Using immigration data to tell stories in your community
Friday, March 6, 9-10 a.m.

Julia Ingram and Joe Yerardi

## Session Overview

As a record number of immigrants are being arrested and detained under the second Trump administration, those with active immigration cases are also seeing dramatically shifting outcomes. But data on immigration cases, released monthly by the [Executive Office for Immigration Review (EOIR)](https://www.justice.gov/eoir/foia-library-0) as a massive relational database, can be hard to parse. The Transactional Records Access Clearinghouse (TRAC) has a few [useful tools](https://tracreports.org/immigration/tools) based on this data that make tracking immigration cases easier. 

Case data is broken down by immigration court, which means you can zoom in to see what's happening in your city or state, and then compare it to what's happening across the country.

TRAC displays its data in tools that are easy to use for extracting quick statistics. But it lacks an easy download button for more in-depth analysis on the underlying data. We'll show you how to take advantage of an undocumented API on TRAC's website to extract the data. Then, we'll walk you through a few different analysis questions so you can report a story on asylum denial or grant rates in your city. The analysis will be modeled after Joe's Oct. 2025 piece in the Philadelphia Inquirer finding that Philly's immigration court rejects [three in four asylum cases under Trump](https://archive.is/62i4T). 

## This Repo

The code for pulling data from the TRAC tools using the undocumented API can be found in the **`trac_asylum_scraper`** notebooks. This code focuses on the API endpoints for the asylum tool, but similar endpoints exist for other TRAC tools. 

The code for the analysis of this data can be found in the **`asylum_analysis`** notebooks.

TRAC identifies each immigration court by a different numeric code. We've pulled these codes out, along with data on the locations of each court, into the [`court_metadata.csv`](data/court_metadata.csv) file.

The rest of this README contains rundown of other TRAC tools and data sources for reporting local immigration stories.

[**Click here to access the TRAC asylum tool to get started.**](https://tracreports.org/phptools/immigration/asylum/)

## Immigration Data Sources 

### Immigration Court Data: TRAC Tools

TRAC has several tools for tracking immigration court proceedings. Here's an overview for the ones that will likely be the most useful in 2026:

- [**Proceeding Outcomes**](https://tracreports.org/phptools/immigration/closure/): Each time an immigration judge issues a ruling on a case, it is logged in the EOIR data as a proceeding. An individual's case can have multiple proceedings, such as when it is transferred between courts, but this TRAC tool highlights proceeding decisions that typically end a case. Here, you can filter to just deportation cases, also known as removal cases, or view all cases. Removal cases constitute the vast majority of cases. Immigrants who are in removal proceedings can request asylum, so most asylum cases are included here as well. The available outcomes include:
    - **Removals**: Deportations
    - **Vol departure**: Voluntary departures, in which an immigrant can request that a judge allow them to return to their citizenship country on their own rather than receive a deportation order. This allows them to avoid having a deportation on their record, allowing for a lower bar to re-entry. Voluntary departures are far more common among detained immigrants, and are reaching new heights under the current administration. 
    - **Terminations**: Dismissals or case closures by a judge, which can be issued for a [variety of reasons](https://www.ecfr.gov/current/title-8/part-1003/section-1003.18#p-1003.18(d)). Once a case is terminated, it cannot be reopened by DHS unless a new charging document is filed against the immigrant. This is different from administrative closure, which temporarily takes the case off the docket. 
    - **Relief granted**: The individual was granted asylum or some other form of relief that allows them to stay in the U.S.
- [**Court backlog**](https://tracreports.org/phptools/immigration/backlog/): This tool shows pending cases. These can be split by charge type, or the portion of the Immigration and Nationality Act the individual is accused of violating and that would constitute the legal basis for removal. Note that immigrants with prior criminal records are not necessarily charged with criminal violations of immigration law. In other words, those with prior charges or convictions can still appear in the "immigration" charge type category.
- [**Mapping representation**](https://tracreports.org/phptools/immigration/addressrep/): This 50-state map shows the number of pending cases in each state and the share of cases whose respondents have lawyers. Many immigrants represent themselves (pro se), and tend to see less favorable outcomes when they do.
- [**Asylum decisions**](https://tracreports.org/phptools/immigration/asylum/): This tool provides data on completed asylum cases over time by immigration court. "Other relief granted" means an immigration judge allowed the individual to stay in the U.S. using a mechanism other than asylum. Asylum grant rates have declined under the second Trump administration.
- [**Asylum decisions by judge**](https://tracreports.org/immigration/reports/judgereports/): TRAC periodically releases an analysis of how asylum grant rates differ by judge. There can be a range of grant rates, and you can zoom in to your city or state to see how it compares with those in other places. For example, California judges have historically had higher grant rates than judges in the southern U.S.
- [**Bond decisions**](https://tracreports.org/phptools/immigration/bond/): Because the second Trump administration has widely expanded its use of mandatory detention, a record number of people are being detained — and staying in detention. Bond rates are hitting new lows, as mandatory detention takes the discretionary power away from the judge to release someone. This tool allows you to see how often bond requests are granted and view outcomes by whether or not bond was granted. 

Across all of these tools, TRAC lets you select a geographic area and drill down on up to two variables, such as custody, legal representation or nationality, which you can select by clicking the down arrow on each column header to expand the dropdown menu.

### Immigration Enforcement Data

While EOIR and TRAC are the main sources for data on immigration cases, data on immigration enforcement actions mostly comes from ICE and from a few secondary sources that analyze or publish ICE data.

- [**The Deportation Data Project**](https://deportationdata.org/data/ice.html) periodically obtains data from ICE via an ongoing Freedom of Information Act lawsuit. This data contains anonymized, individual-level data on encounters, arrests, detentions, detainers and removals. The Deportation Data Project also provides several [tools](https://deportationdata.org/tools.html) for exploring their data, which also allows you to download a pre-filtered slice of it. We recomend reviewing their [documentation and FAQ](https://deportationdata.org/docs/ice.html) before using the data. They also publish a useful [codebook](https://deportationdata.org/docs/ice/codebook.html), with the caveat that it does not come from ICE and the definitions for some fields are still uncertain. 

    Localizing enforcement data from the Deportation Data Project depends on which data set you use. It is difficult to determine where arrests took place at a level any more granular than the state level, although some information can be gleaned from the "apprehension site landmark" field. Use caution with this field, as it can sometimes simply refer to the field office or area that has jurisdiction over the ICE agent that made the arrest, rather than denote where an arrest actually took place. The Area of Responsibility (AOR) field can also serve as a proxy for estimating arrests by region, but should also be interpreted with caution. AORs are administrative jurisdictions that often span multiple states. [See this map.](https://deportationdata.org/data/processed/ice-offices.html) 

    Data on detentions, on the other hand, can be directly geolocated to the facility. The Vera Institute of Justice publishes [metadata](https://github.com/vera-institute/ice-detention-trends/blob/main/metadata/facilities.csv) on detention facilities that you can link to this data using the detention_facility_code. You can use the location of an individual's first detention book-in to get a sense of where they were arrested. (See [this story](https://www.cbsnews.com/news/immigration-crackdowns-mostly-non-criminals-chicago-dc-los-angeles-data/) as an example)

- [**ICE Detention Management Data**](https://www.ice.gov/detain/detention-management) Approximately every two weeks, ICE publishes data on the detention population. The Deportation Data Project stores the [previous releases](https://deportationdata.org/data/reports.html) on their site. Some of this data is nationwide, but one of the spreadsheet tabs contains facility-level data, excluding temporary hold facilities and a few other facility types. It's important to note that much of this data, including the average daily detention population, is averaged from the start of the government fiscal year, which begins on Oct. 1. This means that the population figures do not always represent current or recent trends. For more accurate facility-level detention populations, we recommend using [Detention Reports by Relevant Research](https://detentionreports.com/), which uses a different method for estimating average daily population that reflects more recent changes. [Here's an example](https://share.inquirer.com/0z9kQh) of a story that adapted Relevant Research's method to calculate up-to-date facility-level detention counts in one region.

- [**287g data**](https://www.ice.gov/identify-and-arrest/287g) This data from ICE shows which local agencies have active partnerships with ICE. There are a few different types of agreements agencies can have with varying levels of involvement. Some simply allow the partnering agency to execute an ICE warrant when they encounter someone in jail, others (the task force model) grants them some of the authority ICE agents have to make immigration-related arrests. There is no comprehensive dataset available on the number of arrests conducted via 287(g) programs. Although some of the arrests or detentions in the ICE data from the Deportation Data Project will point to 287(g), experts believe this to be an undercount. 

- [**Austin Kocher's substack**](https://austinkocher.substack.com/): Not a direct source of data, but [Austin Kocher](https://austinkocher.com/), a professor at Syracuse University who used to work at TRAC, publishes an excellent newsletter on immigration data and immigration news. 

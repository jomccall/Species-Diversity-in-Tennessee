# Species Diversity in Tennessee

This project was my Capstone project for the Nashville Software School Data Analytics Bootcamp. I explored biodiversity in the State of Tennessee by analyzing natural heritage species data.


## Table of Contents
* The Motivation
* The Question
* The Data
* The Analysis Process
* The Findings

## The Motivation:
As a Tennessee native, I've always heard that our state boasts a high level of biodiversity. I wanted to find data to analyze that could give me an idea of the scope of this, how it can be defined and discussed, and would give me an understanding of how the scientific community collects and presents this information.

## The Question:
How do watersheds in Tennessee compare in terms of species diversity? What is the scope of biodiversity in the State of Tennessee?

## The Data:
In my quest, I stumbled on Natural Heritage data; information about what species are found in different parts of the world. Nonprofit organization NatureServe hosts the bulk of this data, and has multiple member organizations and individuals who contribute to the larger dataset. This ensures that the methodology is consistent and scientists and other audiences can be assured of a certain quality standard. The gathering methodology has evolved with time but has basic continuity over the last 40 years. This particular state dataset is a compilation of observations from the past 40 years.

The Tennessee Department of Environment and Conservation is one of the organizations that participates. I used data directly from their Rare Species Data Viewer, found here: https://www.tn.gov/environment/program-areas/na-natural-areas/na-natural-heritage-inventory-program.html

This is part of the Natural Heritage Inventory program which maintains a GIS database containing information on the distribution and ecology of rare plants, animals, and ecological communities across Tennessee. This data is managed by TDEC but any citizen can contribute species sightings to this dataset. I used full lists of species at both county and watershed levels.

## The Analysis Process
Using Python and Jupyter Notebooks, I began the data exploration. What kind of spread are we talking about when we look at biodiversity in this data? What categories does the data give us that we’re going to explore?

Species have a type and category. This data also has three classification systems: global rank – which is the global or world-wide rank of a species (this is a non-legal rank indicating the rarity and vulnerability of a species)., next is the state rank – which is much like the global rank but indicates the rarity and vulnerability of a species at the state level, and finally the federal status – which is the federal listing under the US Endangered Species Act. Some species' categories indicate need for further determination, and I did not use these in my analysis.

This information all came in string datatype format in a column for each: Type, Category, Global Rank, State Rank, and Federal Rank. At this point I decided to branch my analysis off in a couple ways so that I could clean the data efficiently.

First, I left the data as it was regarding the category columns, and used the Matplotlib package to create simple bar graphs illustrating the breakout of the different data categories. I did this by creating a list with counts (using the collections package) of string occurrences in each column in question. From there I converted each of these into their own respective dataframes in order to generate charts.

Second, I tested each row in each respective column to see if it did or did not contain each string option (for example, G1 - G5 for the global ranks). This generated a new column, a Boolean datatype, which I then converted back into an integer (1 or 0). This format allowed me to generate multiple choropleth maps where I summed occurrences of each former string in each column and grouped them by watersheds or counties. This allows the viewer to see where concentrations of different types, categories, and ranks of species are located in the state.

Additionally, I used the Boolean formatted data to create interactive maps with Folium, so that the viewer can zoom in and out, see relative geographical features such as cities (watersheds can be hard to relatively comprehend boundaries of since most of us are not used to thinking of the state this way), and to appreciate a tooltip displaying other information that may not be available via polygon boundaries or a choropleth layer.

## The Findings

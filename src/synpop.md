# Project 2: Generating Synthetic Populations

## Part 1
- Visit the [DHS data](https://dhsprogram.com/data/available-datasets.cfm) site, and select a standard DHS survey dataset to obtain.
- Register with DHS and login.  Review the [DHS video](https://dhsprogram.com/data/Access-Instructions.cfm) on how to create a new project, request access to DHS data for your selected study area, and to provide a description of your research (study) area.
- Post your study description, including your research question, research design and data analysis plan to your GitHub page and link it to you index.  The study description should be more than 300 but not less than 2500 characters in length.
- Select a recent standard DHS survey and download the household and individual datasets.  Using the stata format (.dta) for import to RStudio typically works fine.
- Review:
  - DHS report
  - questionnaire
  - survey design
  - .DO file
- Import households survey from DHS dataset
- Identify:
  - Survey weights
  - Number of household members
  - Location of your selected research area
  - Gender of household members  
  - Age of household members
- Post results to your GitHub pages site and link in your index

## Part 2
- Import your DHS data
- Identify predictor variables within your dataset
- Stretch goal: import DHS cluster GPS coordinates and randomly distribute
- Clean DHS survey data for use
- Randomly locate each survey observation using a spatial distribution
- Convert and join predicted household locations with DHS household data	
- Review stretch goal progress

## Part 3
- Review methods for cleaning DHS data based on each select household survey
- Review survey design
- Transform survey weights
- Distribute households at adm0 & adm1
- Join spatial and survey data
- Join spatial and survey data
- estimate error
- analyze adm1 data
- disaggregate from households to persons
- Train, test & predict

## Project 2 deliverables : 
- Please upload and provide a link from your GitHub index to a 3 to 4 page project report that analyzes the synthetic household and person population you generated. Include arguments that address the following aspects from your work.
    - Provide a written description of your selected household survey including the number of household and person observations as well as the variables in your source data.
    - Provide a written description of your spatially located households at the adm0 level of your selected location, including how you located each household, generated the household structure including demographic attributes of persons, and the percent error calculated.  If you faced computational issues at the adm0 level when attempting to pivot from households to persons, describe those limitations.
    - Provide a written description of your spatially located households at the adm1 or adm2 level of your selected location, again including how you located each household, generated the household structure including demographic attributes of persons, and the percent error calculated.  Further analyze your synthetically generated households and persons with regard to percent error.  Do you think this population is more or less accurate than the one generated at the adm0 level? What could you have done to improve your measures of accuracy?
    - When compared to a randomly generated synthetic population that describes the demographic attributes of households and persons, does yours more closely approximate reality? How is yours an improvement over a synthetic population that was generated in accordance with complete spatial randomness?  Generate plots and incorporate results from your work as evidence in support of an argument that the synthetic population you generated is a good approximation of the reality that existed in your selected location at that given time.


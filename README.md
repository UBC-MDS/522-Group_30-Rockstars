# Prediction Modelling for Property Assessments
* authors: Cal Schafer, Daniel Ortiz, Jordan Lau, William Xu

A data science project for Predicting the property assessments of Single-Family Dwellings in Strathcona County for DSCI 522 (Data Science Workflows); a course in the Master of Data Science program at the University of British Columbia.

## About

Canadian municipalities rely on property taxes to fund their operations. It is common practice for municipal governments to assess the taxable value of properties through linear regression. Our research interest is to build a prediction model for property assessment values, specifically for single-family-dwellings, using the property-attributes of these properties as model inputs. As well, we are interested in going beyond the traditional linear regression model and instead predict using more complex models more commonly used in machine-learning applications. 

The data set used in our project is [2018 property assessments](https://data.strathcona.ca/Housing-Buildings/2018-Property-Tax-Assessment/6wvk-j7e9), restricted to single-family dwellings in Strathcona County, Alberta (“2018 Property Tax Assessment”). Each row in the data set represents a distinct property within the border of Strathcona County, and each column represents a potential modelling input, along with our dependent variable (the property assessment value). Our set of explanatory variables is composed of continuous, categorical, and binary data types, these being: Building Size, Building Description, Age of Property, Year Built, Presence of Basement, Presence of Furnished Basement, Presence of Garage, Presence of Fireplace, and Longitude and Latitude. Altogether our dataset is composed of 28,450 observations.

To get an accurate assessment of the R-square performance of our predictive models, we build our models using 90% of our observations and conduct cross-validation splitting when comparing our R-square scores across different models. We find that R-square performance does range considerably from model to model: Ridge Regression had an R-square of 76.7%, 80.2% using Random Forest Regression, and 89.6% using XGBoost Regression. Finally, after deciding to use Ridge Regression as a final candidate model, we find its R-square score to be robust when we applied it to our 10% remaining out-of-sample data, as the R-square improved from 76.7% with cross-validation testing, to 78.8% with this out-of-sample data. 

## Report
The final report can be found [here](http://htmlpreview.github.io/?https://raw.githubusercontent.com/UBC-MDS/522-Group_30-Rockstars/main/doc/strathcona_housing_price_predict_report.html).

## Usage

There are two suggested ways to run this analysis:

#### 1. Using Docker
*note - the instructions in this section also depends on running this in a unix shell (e.g., terminal or Git Bash)*

To replicate the analysis, install [Docker](https://www.docker.com/get-started). Then clone this GitHub repository and run the following command at the command line/terminal from the root directory of this project:

```
docker run --rm -v /$(pwd):/home/data_analysis_eg williamxu7/dockerfile-practice:v0.8.0 make -C /home/data_analysis_eg all
```

To reset the repo to a clean state, with no intermediate or results files, run the following command at the command line/terminal from the root directory of this project:

```
docker run --rm -v /$(pwd):/home/data_analysis_eg williamxu7/dockerfile-practice:v0.8.0 make -C /home/data_analysis_eg clean
```

#### 2. Without using Docker

To replicate the analysis, clone this GitHub repository, install the [dependencies](#dependencies) listed below, and run the following command at the command line/terminal from the root directory of this project:

```
make all
```

To reset the repo to a clean state, with no intermediate or results files, run the following command at the command line/terminal from the root directory of this project:

```
make clean
```
## Makefile Dependency Graph
The image below shows the Makefile dependency, click it to see the original image:
![Image of Makefile](https://github.com/UBC-MDS/522-Group_30-Rockstars/blob/main/Makefile.png)

## Dependencies
- Python 3.8.6 and Python packages:
   - altair==4.1.0
   - altair_data_server==0.4.1
   - altair_saver==0.5.0
   - docopt==0.6.2
   - matplotlib==3.3.3
   - numpy==1.19.4
   - pandas==0.24.2
   - scikit-learn==0.23.2
   - seaborn==0.11.0
   - selenium==3.141.0
   - XGBoost==1.2.0
- R version 4.0.2 and R packages:
  - knitr==1.30
  - rmarkdown==2.5
  - reticulate==1.18
  - tidyverse==1.3.0

## License
The Strathcona County Housing Price Predictor materials here are licensed under the Creative Commons Attribution 2.5 Canada License (CC BY 2.5 CA). If re-using/re-mixing please provide attribution and link to this webpage.

## References
“2018 Property Tax Assessment”. Strathcona County’s Open Data Portal. https://data.strathcona.ca/Housing-Buildings/2018-Property-Tax-Assessment/6wvk-j7e9

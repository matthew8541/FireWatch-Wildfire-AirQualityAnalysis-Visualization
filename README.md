#Fire and Air Pollution Visualization
##CSE 6242 Final Project

### DESCRIPTION
The package contains two folders DOC/ and CODE/. The DOC/ directory contains our final report and team poster in PDF format.
The CODE/ directory contains all the necessary files to load our data visualizer. In this project, we attempted several things:
to visualize over 1.88 million wilfires from 1992 to 2015 and corresponding national AQI data for those years on a choropleth map,
to analyze any correlations between fires and their air quality levels, and lastly to abstract findings from acreage burned and
unsupervised learning classifications. All of this data visualization and analysis is presented in the webpage.

Upon loading, the webpage first displays the AQI choropleth map. The range values are color coded based on values observed here:

https://www.airnow.gov/aqi/aqi-basics/

The map has a dropdown selector for Year, month, and day. User may select day they are interested in and the data will load in a matter
of seconds. Tooltip for the fires data will show on county mouseover, displaying data such as State and County Names, Defining AQI Parameter, overall AQI level
assessment, and the air quality score itself.

User may click the Fires toggle button to view fires data, heatmapped according to annual scaling of fire size. Mouseover for county
will show relevant and informative data (i.e. state and county name, max fire size by day, most common cause for that county on that date, average fire size by year).

User can click on "Analysis Dropdowns" and select any item from the dropdown menu to read detailed descriptions of our analysis for this project.
The Discussion and Conclusions tab contains a summation of our findings.

All of our analysis notebooks have been provided as (*.ipynb) files for the benefit of the end user who can observe our analysis.

### INSTALLATION
1. Unzip the team017final.zip file that this README.txt file is located in.

2. cd team017final/

3. Ensure the following python 3 packages are installed:

	pip3
	numpy
	pandas
	sqlite3
	csv

	If not, please run pip3 install <pkg_name> as needed.

4. Create a symbolic link
    
    MacOS/Linux:
        cd /CODE/; ln -sf Webpage/datasets .
    Windows/PC:
        cd CODE/; mklink /D .\datasets .\Webpage\datasets

    This is required to link the datasets to our analysis notebooks.

Steps 5 and 7 are recommended but optional. They are needed if the user wants to run the analysis notebooks and view the complete dataset from years 1992-2015.
The dataset included in this package only contains the fire and aqi data for the year 1992.

5. Download datasets:

	Fires:
		https://www.kaggle.com/rtatman/188-million-us-wildfires
		Download 168MB data zip and extract the SQLite file from the zip.
		NOTE: Will have to sign into Kaggle account to download data.

	AQI:
		https://aqs.epa.gov/aqsweb/airdata/download_files.html#AQI
		Download the daily_aqi_by_county_<year>.zip and extract the csv files for years 1992-2015 (inclusive).
	and place them in the datasets/ directory.


6. cd installer/Webpage/datasets/. Run the dataset pre-processing scripts:

	To process fires data, run the following commands (in exactly this order):
		1. python3 ../../scripts/convert_fires_sqlite_to_csv.py
		2. python3 ../../scripts/clean_fire_data.py
		3. python3 ../../scripts/group_fires_by_year.py

	This will generate all the necessary yearly and aggregate fires related csv files.

	To process AQI data, run the following commands (in exactly this order):
		1. python3 ../../scripts/aqi_col_rename.py
		2. python3 ../../scripts/combine_aqi.py

	This will reformat the AQI annual data to that which is required by our choropleth map and analysis notebooks.

NOTE: Any csv required by our analysis not generated by the above process will be created within the analysis notebooks themselves.

### Launching the interactive Choropleth map

1. cd Code/Webpage/
2. In a command prompt (e.g iTerm2 on MacOS) type: python3 -m http.server 8888 to launch the http server
3. Go to http://localhost:8888 in your browser.
4. Observe the Map. Notice the "Analysis Dropdown" and "Discussion and Conclusions" tabs.
   Note that selecting the years from 1993-2015 from the Year drop down is not possible unless the installation steps 4 and 5 have been run.
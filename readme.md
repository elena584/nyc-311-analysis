Data Analysis Exercise on the NYC 311 Complaints Dataset
Executive Summary
Project objective:
clean and analyze a data collection in json format related to the 311 reports of the city of new york,
turning it into a format suitable for analysis and exploring its main features
dataset used:
NYC 311 Complaints,a collection of citizen reports regarding traffic violations, disturbances, and
urban issues.
main results:
•Transforming a JSON file into CSV to proceed with analysis
•identifying the main structure of the dataset:
•most important columns, data types, missing data, treatment of columns reporting dates
The analysis shows that the dataset is a collection of major traffic violation complaints originating
from major neighborhoods in New York City.
The analyzed collection includes only data relating to the month of March and only for the days
from March 20th to 25th. So the analysis of events by month and day of the week is not enough
significant to be able to draw definitive conclusions or trace trends and habits.
The hourly analysis is more significant because the data here is more complete and it is possible to
verify the habits of the population reporting that remain concentrated mainly in the 9am-5pm time
slot and then decrease but not completely exhaust themselves in the 2am-4am time slot.
Introduction
The dataset is a partial collection of reports of traffic violations by the population on a few days in
March.
Analyzing the data, the main questions to ask are:
• what are the most frequent complaints,
• in what time slots do they occur,
• from what areas of the city do they come
Dataset Description
the dataset has 50000 rows and 50 columns
the most significant columns are:
• created_date,
• closed_date,
• complaint_type,
• descriptor,
• incident_address,
• city,borough,•
•
latitude,
longitude
The data format is mainly string,created_date and closed_date include date and
time,latitude,longitude,latitude_from_location,latitude_from_location are float data.
The period to which the dataset refers is the month of March limited to the days 20 to 25.
Data Cleaning
A preliminary analysis shows that there are some columns that have approximately 47,000 to more
than 49,000 null rows. In this case, since they don't provide significant information, and even if you
wanted to fill in the missing data with machine learning techniques, the information entered in this
way wouldn't be reliable and wouldn't correspond to reality, I decided to eliminate them.
These are the columns:
• vehicle_type ,
• bridge_highway_name,
• bridge_highway_segment,
• bridge_highway_direction,
• road_ramp,
• taxi_pick_up_location,
• two_dates,
• taxi_company_borough.
I also noticed that the incident_address and street_name columns collect the same information, but
incident_address contains more, more specific information so I decided to delete street_name.
The created_date column was transformed into a format suitable for manipulation in pandas, after
which this data was transformed so that the month, day, time and name of the day were immediately
read.
Subsequently,we moved on to cleaning the format of the string columns. We proceeded to remove
the leading and trailing spaces, convert everything to lowercase and standardize the duplicate
categories. Empty strings were filled with NaN,but in the most important columns,complaint_type',
'descriptor', 'borough', 'city', the NaN was replaced with ‘Unknow’ to allow more effective data
manipulation also through predictive models and to create graphs.
String columns aren't all the same: some are categories, others are text-only or identifier-only. This
distinction requires a different degree of cleanliness to avoid losing information and introducing
errors.
For the columns representing categories,complaint_type, descriptor, borough, agency,
agency_name, city, location_type, and status, we proceeded to remove spaces, standardize hyphens,
reduce the text to all lowercase, and manage NaNs.
For columns with descriptive text, resolution_description, incident_address, spaces have been
removed, the text has been left as is without lowercase.
Same process for columns with textual geographic fields, such as the landmark column.
Exploratory Data Analysis (EDA)I created a graph to display the 10 most frequent complaints. Among these, the top 3 positions are
occupied by illegal parking, noise residential and street conditions, while complaints about
abandoned vehicles and street cleaning conditions are reduced.
Graphical analysis of the temporal columns reveals a dataset with incomplete data. Data collection
in this case focuses only on the month of March, from March 20 to 25, with little data for the 25th,
indicating a likely incomplete collection of reports. There is a spike in complaints in the early days
of the week, then it drops sharply on Wednesdays and drops to zero on Thursdays. From this it can
be deduced that the data collection is probably incomplete or completely missing for these two
days.
More significant is the hourly analysis which reveals constant reports throughout the day including
the night, but with peaks during the day in the 9-17 range, and a significant decrease between 2 and
5 in the morning.
Geospatial analysis reveals that the neighborhoods where complaints occur are Brooklyn and
Queens, stable Manhattan and the Bronx, less frequent in Staten Island. By creating maps, it is
possible to visualize the locations where the reports are concentrated, thus revealing the
demographic distribution of the various neighborhoods.
Conclusions
The dataset is incomplete, representing only one month of the year and only one week of that
month, so it is not possible to plot a trend regarding traffic violations. However, the hourly analysis
reveals a city active all day including night and densely populated and very active neighborhoods
with regard to reports and complaints

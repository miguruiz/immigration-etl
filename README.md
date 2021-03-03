# immigration-etl

The following project is part of UDACITY - Data Engineer Nanodegree. It consist in creating an ETL in a jupyter notebook from data sources stored in multiple formats.


### Project Description

For the project we are going to assume we are an Intelligence Company inside the airline industry, and we are creating a new product called 'Travel Intelligence' that sells data to Airports & Airlines.

We will be cleaning the provided datasets and creating a star-scheme table where clients can purchase the fact table, and separately the dimension tables.


### Datasources

##### Immigration Dataset
International visitor arrival statistics by world regions and select countries (including top 20), type of visa, mode of transportation, age groups, states visited (first intended address only), and the top ports of entry (for select countries).

source: https://travel.trade.gov/research/reports/i94/historical/2016.html

##### Airports Dataset
Contains the list of all airport codes. Some of the columns contain attributes identifying airport locations, other codes (IATA, local if exist) that are relevant to identification of an airport.

Source: https://datahub.io/core/airport-codes#data

##### Temperatures Dataset

Temperature data for cities around the globe. 

Soruce: https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data

##### Cities demographics Dataset

This dataset contains information about the demographics of all US cities and census-designated places with a population greater or equal to 65,000. 

This data comes from the US Census Bureau's 2015 American Community Survey.

Source: https://public.opendatasoft.com/explore/dataset/us-cities-demographics/table/

### Execution Instructions

1. Paste in  **raw** folder the datasets (available in the udacity environment)

2. Execute the **Capstone Project.ipynb** - ensure access to Spark.


### Output tables
##### IMMIGRATION FACT
```
cicid                   -> Identifier of the traveller
visa_id                 -> Identifier of the visa, creted with the cicid and the arrival visa admission date
arrival_date            -> Arrival date of the traveller in US
origin_dep_date         -> Date of departure before arriving to US
arrival_airline         -> Iata code of the airline
arriving_from_city_dec  -> City where the traveller started the trip to US
arrival_city            -> US city where traveller landed
arrival_state           -> US state where traveller landed
arrival_port            -> Code of arrival city
flight_number           -> Flight number of the arriving flight
us_departure_date       -> Expected departure date from the US
```
##### TRAVELLER DIM
```
cicid                 -> Identifier of the traveller
traveller_residency   -> Traveller residency outside US
traveller_age         -> Age at the time of travelling
gender                -> Gender
traveller_birth_date  -> Date of birth
us_address            -> US state where the traveller intends to stay
```

#### VISA DIM
```
visa_id                -> Identifier of the visa, creted with the cicid and the arrival visa admission date.
visa_admission_number  -> Visa admission number 
visa_type              -> Class of admission legally admitting the non-immigrant to temporarily stay in U.S
admission_date         -> Date of admission
dep_visa_issued        -> Departament that issued the visa
i94_record_date        -> Dare of i94 record
visa_code              -> Intention of travel: Business / Pleasure / Student
records_match          -> Match of arrival and departure records
arrival_flag           -> Admitted or paroled into the U.S.
departure_flag         -> Departed, lost I-94 or is deceased
```
##### AIRPORT DIM
```
ident                   -> Airport identifier
local_code              -> Airport local code
gps_code                -> Airport gsp code
iata_code               -> Airport iata code
name as airport_name    -> Name of the airport
type                    -> Type of airport (large, small, heliport,etc)
elevation_ft            -> Elivation in feet
country                 -> Country where airport is located
city                    -> City where airport is located
state_code              -> State where airport is located
```

#### CITIES DIM
```
city                    -> City name
state                   -> State name
state_code              -> State code
median_age              -> Median age in city
male_population         -> Male population of males in city
female_population       -> Female population
number_of_veterans      -> Number of veterans in the city
foreign_born            -> Number of foreign born population
average_household_size  -> Average household size in city
```

##### RACES DIM

```
city                               -> City name
state_code                         -> State code of city
asian                              -> asian population
white                              -> white population
american_indian_and_alska_native   -> american indian and alska native population
hispanic_or_latino                 -> hispanic or latino population
black_or_african_american          -> black or african american population
```

##### TEMPERATURES DIM
```
date                     -> date 
city                     -> city name
state_code               -> state_code
avg_temp                 -> average temperature
```
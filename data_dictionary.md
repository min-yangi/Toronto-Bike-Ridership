Data Dictionary and Data Flow
Ridership Dataset
Each row in the ridership dataset represents a single bike trip recorded by the Bike Share Toronto system. The dataset captures key behavioral and contextual information about user trips, which can be analyzed to understand ridership patterns and influences. The main data entities include:
Timestamp-Related Entities
Start Time: The specific date and time a bike trip begins, crucial for aligning with hourly weather records and identifying peak periods.
End Time: The specific date and time a bike trip ends, allowing for the calculation of trip duration and analysis of time-based usage.
Trip Characteristics
Trip Id: A unique identifier for each bike trip, essential for distinguishing and tracking individual journeys.
Trip Duration: The total time of the trip in seconds, reflecting user travel habits and potentially indicating trip purposes, such as short commutes or leisure rides.
Geographic Entities
Start Station Id: A numeric identifier for the station where a trip originates, facilitating linkage to station location and capacity data.
Start Station Name: The name of the starting station, providing geographic context for trip origins.
End Station Id: A numeric identifier for the station where a trip ends, enabling the analysis of travel routes and station-to-station flow.
End Station Name: The name of the ending station, supporting spatial analysis of trip destinations.
Bike & User Attributes
Bike Id: A unique identifier for the bicycle used, allowing for tracking of bike utilization and maintenance needs.
User Type: Categorizes users as either Casual or Annual members, aiding in the differentiation between short-term and regular riders’ behavioral patterns.
Data Flow
Each bike trip is recorded through the Bike Share Toronto system, capturing key details like trip time, duration, start/end stations, and user type.
The trip data is transmitted to Bike Share Toronto’s central database, where it is logged and structured.
The validated data is then published on the Toronto Open Data Portal, enabling access for public use and analytical insights.
Table 1
Data Dictionary for the Ridership Dataset
| Field Name | Unit | Data Type | Description | Example Value |
| :--- | :---: | :---: | :--- | :--- |
| **Trip Id** |  | String | A unique identifier assigned to each individual bike trip. | 26682749 |
| **Trip Duration** | sec | Integer | Total time of the trip, measured in seconds. | 2464 |
| **Start Station Id** |  | String | Numeric ID of the station where the trip began. | 7391 |
| **Start Time** |  | date/time | Start date and time of the trip. | 01-01-2024 00:05 |
| **Start Station Name** |  | String | Name of the station where the trip originated. | Yonge St / Dundas Sq |
| **End Station Id** |  | String | Numeric ID of the station where the trip ended. | 7163 |
| **End Time** |  | date/time | End date and time of the trip. | 01-01-2024 00:46 |
| **End Station Name** |  | String | Name of the station where the trip terminated. | Yonge St / Wood St |
| **Bike Id** |  | String | Unique identifier for the bicycle used. | 6974 |
| **User Type** |  | String | The type of user that took the trip (Casual/Annual). | Casual Member |






Weather Dataset
Each row in the weather dataset represents a single hourly weather observation recorded by Environment Canada at a designated weather station (Environment and Climate Change Canada, n.d.). The dataset captures key environmental conditions that could influence bike ridership behavior. The main data entities include:
Timestamp-Related Entities
Timestamp: Represents the specific hour of observation on a given date. Critical for aligning weather data with hourly ridership records.
Temperature & Dew Point
Temperature: Measures the ambient air temperature in degrees Celsius, crucial for assessing thermal comfort.
Dew Point: Measures the temperature at which air becomes saturated and condensation forms, in degrees Celsius. Important for understanding potential for condensation.
Humidity & Precipitation
Relative Humidity: Indicates the moisture percentage in the air, influencing perception of conditions (e.g., muggy or dry).
Precipitation: Records the amount of rainfall in millimeters during the observation, significantly affecting bike usage.
Wind Conditions
Wind Direction: The direction from which the wind blows, in tens of degrees.
Wind Speed: Speed of the wind in kilometers per hour, impacting cycling comfort and safety.
Visibility & Pressure
Visibility: Measures how far one can see, in kilometers. Poor visibility may deter cycling, especially under adverse conditions.
Station Pressure: Atmospheric pressure in kilopascals at station elevation, supporting complex weather pattern analysis.
Indices & Description
Humidex and Wind Chill: Calculated indices reflecting how the weather feels, accounting for humidity or wind, providing a realistic sense of rider comfort.
Weather Description: A qualitative summary of observed atmospheric conditions (e.g., snow, fog, clear), useful for categorizing rider-friendly vs. unfriendly weather.
These entities collectively define the environmental context in which bike trips occur. They enable the study of how different weather factors affect ridership patterns across hours, days, or seasons.
Data Flow
The weather station across Ontario records hourly observations (temperature, wind, precipitation, etc.).
This information is transmitted to Environment and Climate Change Canada’s central database, where it’s stored and validated.
The data is made available to the public via the climate data portal and used in weather forecasts and climate monitoring reports.
Table 2
Data Dictionary for the Weather Dataset
| Field Name | Unit | Data Type | Description | Example Value |
| :--- | :---: | :---: | :--- | :--- |
| **Month** |  | date/time | Month of the measurement | 1 |
| **Year** |  | date/time | Year of the measurement | 2024 |
| **Temp** | °C | Float | Temperature in degrees Celsius | 2.5 |
| **Dew Point** | °C | Float | Dew point temperature in degrees Celsius | -3.6 |
| **Rel Hum** | % | Float | Relative humidity as a percentage | 64 |
| **Wind Direction** | 10's deg | Float | Direction from which the wind blows | 25 |
| **Wind Speed** | Km/h | Float | Speed of air in kilometres per hour | 28 |
| **Visibility** | Km | Float | Distance objects can be identified | 16.1 |
| **Stn Press** | KPa | Float | Atmospheric pressure at station elevation | 100.08 |
| **Wind Chill** |  | Float | Index of how cold the weather feels | -6 |
| **Hmdx** |  | Float | Index of how hot/humid the weather feels | 27 |
| **Weather** |  | String | Observations (e.g., snow, rain, fog) | snow, rain, fog |

Station Dataset
Each row in the station dataset represents a physical bike share station in Toronto. The dataset captures static and dynamic attributes that define station characteristics and usage, enabling analysis of infrastructure efficiency and demand. The main data entities include:
Identification & Location
Station Id: A unique numeric identifier for each station, serving as a key to link with ridership data.
Station Name: The textual address or landmark associated with the station, facilitating geographic referencing and user navigation.
Latitude: The north-south geographic coordinate (in decimal degrees) for precise mapping of the station location.
Longitude: The east-west geographic coordinate (in decimal degrees) for precise mapping of the station location.
Operational Attributes
Capacity: The maximum number of bikes or docks available at the station, critical for evaluating demand-to-capacity ratios.
Is Charging Station: A boolean indicator of whether the station includes charging facilities for e-bikes, reflecting infrastructure modernization.
Installation Date: The timestamp when the station became operational, useful for analyzing historical usage trends and infrastructure expansion.
Categorical & Relational Entities
Area Category: A classification of the station’s land use (e.g., Downtown, Residential, Recreational), aiding in analysis of usage patterns by geographic context.
Groups: A textual label indicating the station’s belonging to a specific group (e.g., Downtown), supporting comparative analysis across zones.
Data Flow
Static metadata (ID, name, coordinates, capacity) sourced from Toronto Open Data Portal or official API.
Dynamic usage data (e.g., hourly trip counts) derived from ridership dataset via Station ID linkage.
Merge static and dynamic data into a unified dataset.
Validate coordinates against geographic information systems (GIS) for accuracy.
Stored in a relational database (e.g., PostgreSQL) with foreign key links to ridership (Start Station Id, End Station Id).





Table 3
Data Dictionary for the Station Dataset
| Field Name | Unit | Data Type | Description | Example Value |
| :--- | :---: | :---: | :--- | :--- |
| **Station ID** |  | Integer | Unique station identifier | 7000 |
| **Station Name** |  | String | Full station address or landmark | Fort York Blvd / Capreol Ct |
| **Latitude** | °C | Float | North-south coordinate | 43.639832 |
| **Longitude** | °C | Float | East-west coordinate | -79.395954 |
| **Capacity** | Bikes | Integer | Maximum bikes/docks available | 135 |
| **Is Charging Station**|  | Boolean | TRUE if station has e-bike charging | TRUE |
| **Installation Date** |  | Date | Date station was installed | 2017-01-01 |
| **Groups** |  | String | Group where the station belongs | Downtown |


 # TASK 1: The Five V’s

### 1. Variety
   
Variety refers to the diversity of data types. JONSON data is semi- structured because this data supports nesting and irregular formats between entries, dataset contain different types of data

Example:
* Different sensor type E.g (“sensor_type”: “temperature” and “sensor_type”: “traffic”.)

* Mixed value format : some readings are numeric(“value”:22.5)  while others might be          categorical(“status”: “active”)
This demonstrates the variety because the data include multiple formats

### 2. Velocity
   
Velocity refers to how quickly data is generated and how quickly that data moves. if we were receiving real-time data from thousands of sensors, managing the speed at which it arrives is critical. Without proper handling (e.g., stream processing), we risk delays, overload, or even system crashes—especially during emergencies where real-time decisions are needed.

### 3. Veracity
   
 It refers to the quality and accuracy of data.The data_source_veracity field likely represents how       trustworthy or accurate the data source is (e.g., "high", "low", or null). A null value means we can’t   verify the data’s reliability.
 Example:
 
{
  "sensor_id": "T101",
  "data_source_veracity": null
}

This record may be unreliable and poses a veracity issue.

### 4. Volume
   
Refers to the amount of data that exists. If we collect data from 10,000 sensors every 5 seconds for a year, we would end up with about billions records in a year. This huge amount of data can cause problems. First, we would need a lot of storage space to keep all the data. Second, it might become slow or difficult to find and use the data quickly when we need it. Third, we would need strong processing power (like fast computers or servers) to analyze the data. Without solving these problems, the Smart Germiston system might become slow, unreliable, or too expensive to run.

### 5. Value
   
This refers to the value that big data can provide, and it relates directly to what organizations can do with that collected data.This data can offer actionable insight to improve city operation.

  # Task 2: Data Quality Assessment

### 1. Data Quality
   
Means how good and reliable data is.which based on accurate, up-to-date, Complete with data in every field unless explicitly deemed optional, Unique so that there is only one record for a given entity and context, formatted the same across all data sources and trusted by those that rely on the data  

### 2. Identify Issues
   
* Missing values: Some records have null in critical fields like value or timestamp.
      Problem: Missing data reduces accuracy and breaks calculations.

* Inconsistent formats: Timestamps not using ISO 8601 (2023-04-25 13:00 instead of 2023-04-25T13:00:00Z).
      Problem: Causes parsing errors and affects time-based analytics.

* Invalid data types: Some value fields contain strings like "twenty" instead of numbers.
      Problem: Prevents numeric calculations and visualizations.
   
### 3. Practical Step
   
* PYTHON

mport re

record = {

    "sensor_id": "T101",
    
    "value": "twenty",
    
    "timestamp": "2025-07-30 08:30"
}

//Check if value is a number

try:
    float(record["value"])
    
except ValueError:

    print(f"Invalid value: {record['value']} for sensor {record['sensor_id']}")
   
//Check if timestamp matches ISO 8601

iso_pattern = r"\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}Z"

if not re.match(iso_pattern, record["timestamp"]):

    print(f"Invalid timestamp: {record['timestamp']} for sensor {record['sensor_id']}")

# Task 3: Data Governance & Security

### 1. Access Control
   
* Modified Record Example:

{
    "sensor_id": "TC-05-GER",

    "timestamp": "2025-07-29T08:46:15Z",

    "location": { "latitude": -26.2260, "longitude": 28.1620 },

    "data": { "type": "traffic_count", "value": 152, "unit": "vehicles_per_minute" },

    "data_source_veracity": null 

    "access_level": "Internal"
  },
  

This "access_level" field could help control who can view or process the record.

### 2. Breach Implications 

* For business organizations: A data breach can have a devastating effect on an organization's reputation and financial bottom line.

 * For government organizations: compromised data can mean exposing highly confidential information to foreign parties. Military operations, political dealings, and details on essential national infrastructure can pose a major threat to a government and its citizens.
   
  
### 3. Authority and Control
Data protection officer are the ones who should have the authority to define the access levels. They understand compliance laws(e.g POPIA, GDPR), Manage enterprise-wide data strategy, and balance security, privacy, and utility.
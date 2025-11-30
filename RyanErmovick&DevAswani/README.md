# Team Metro

## Team members
Ryan Ermovick & Dev Aswani

## Data Source

What data source did you work with?

The data source we worked with was multiple API's from the Washington Metropolitan Area Transit Authority (WMATA). The first API we pulled information from was the Bus update API, which gave information on delays, status, etc.. The second API that we pulled information from was the Bus position API, which gave position information (latitude and longitude), speed, and more. To access this data source an account is needed (free). 


## Challenges / Obstacles

What challenges did this data choice present in data gathering, processing and analysis, and how did you work through them? What methods and tools did you use to work with this data?

A challenge that we encountered in processing this data was the format. Since the APIs were giving information about vehicles, the data was presented in General Transit Feed Specification (GTFS). This required an additional parsing step to make it easily accessible. Another challenge/consideration was time of collecting and processing data into Kafka. Both APIs dump out records for every bus in use at the time of the API call. If the API was called continously, then not much new information would be gathered about each bus (it is very unlikely that the information about a bus will change in less than 1 second). To address, we made a loop that would wait 45 seconds before collecting data again. Additionally, the amount of time for data collection can be varied. PLEASE PUT A CHALLENGE WITH DATA ANALYSIS

To worth with this data, we used kafka to collect streams of data from both API endpoints. Then we used specific packages to parse the GTFS format of the data. After producing and consuming the streaming data, we placed inside of a duckdb database. We also used Prefect to create flows for our processes and to ensure retries in case an error occurred. 

## Analysis

Our analysis revealed several meaningful dynamics in WMATA’s bus operations. By aggregating tens of thousands of position records, we observed that only a small subset of routes such as A58, C63, and F60 dominated the live feed, suggesting that specific corridors generate disproportionately higher operational activity. A spatial density heatmap showed that WMATA bus traffic concentrates heavily along a few high-volume urban corridors, forming distinct geographic hot zones of movement rather than evenly distributed coverage. Using the delay feeds, we also compared average delays across routes and found clear differences: some routes consistently experienced higher delays than others, which indicates that certain lines may be more sensitive to congestion, scheduling pressure, or operational bottlenecks. Combining streaming positions with delay updates shows that real-time bus data is far from uniform, and meaningful patterns only emerge after processing large volumes of streaming records. These patterns reveal where the WMATA network experiences the greatest stress and variability.


## Plot / Visualization

Include at least one compelling plot or visualization of your work. Add images in your subdirectory and then display them using markdown in your README.md file.

## GitHub Repository

https://github.com/


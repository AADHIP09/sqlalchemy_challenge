# sqlalchemy_challenge

The purpose of this exercise is to do a climate analysis of a particular area. 

## Part 1: Analyze and Explore the Climate Data

The first task is to use Python and SQLAlchemy to do a basic climate analysis and data exploration of the climate database. This will include the use of SQLAlchemy ORM queries, Pandas, and Matplotlib.

### Precipitation Analysis
The following tasks were completed: 
> 1. Find the most recent date in the dataset.
>2. Using that date, get the previous 12 months of precipitation data by querying the previous 12 months of data.
>3. Select only the "date" and "prcp" values
>4. Load the query results into a Pandas DataFrame. Explicitly set the column names
>5. Sort the DataFrame values by "date".
>6. Plot the results by using the DataFrame plot method.
>7. Use Pandas to print the summary statistics for the precipitation data.

### Station Analysis
The following tasks were completed: 
> 1. Design a query to calculate the total number of stations in the dataset
> 2. Design a query to find the most-active stations. To do this, the following tasks were completed:
> 3. Design a query that calculates the lowest, highest, and average temperatures that filters on the most-active station id found in the previous query
> 4. Design a query to get the previous 12 months of temperature observation (TOBS) data:
> Plot the results as a histogram with bins=12


## Part 2: Designing A Climate App

> Start at the Homepage and list all available routes
 ```
@app.route("/")
def welcome():
    """List all available api routes."""
    return (
        f"Available Routes:<br/>"
        f"Precipitation: /api/v1.0/precipitation<br/>"
        f"List of Stations: /api/v1.0/stations<br/>"
        f"Temperature for one year: /api/v1.0/tobs<br/>"
        f"Temperature stat from the start date(yyyy-mm-dd): /api/v1.0/yyyy-mm-dd<br/>"
        f"Temperature stat from start to end dates(yyyy-mm-dd): /api/v1.0/yyyy-mm-dd/yyyy-mm-dd"
    )

```

> Coding to return the respective values for each of the above routes:

1. Precipitation Data: Convert the query results from the precipitation analysis (i.e. retrieve only the last 12 months of data) to a dictionary using 'date' as the key and 'prcp' as the value, and return as JSON. 
```
@app.route('/api/v1.0/precipitation')
def precipitation():
```

2. Stations Data: Return a JSON list of stations from the dataset.
```
@app.route('/api/v1.0/stations')
def stations():
```

3. TOBS: Return a JSON list of temperature observations for the previous year
```
@app.route('/api/v1.0/tobs')
def tobs():
```

4. Start and Stop: Return a JSON list of the minimum temperature, the average temperature, and the maximum temperature for a specified start or start-stop range.


```
@app.route('/api/v1.0/<start>')
def get_t_start(start):
```

```
@app.route('/api/v1.0/<start>/<stop>')
def get_t_start_stop(start,stop):
```

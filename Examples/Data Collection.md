#Data Collection
The collection of data is where data science starts. To be able to ask any questions about data, it needs 
to be present. The collection of data can be done numerous ways. It can already be existent and be retrieved from an 
external source. In some cases the data has to be manually retrieved for example interviews or manual measurements. 
In some cases it can be a derived data such as meta-data. 

Not all examples mentioned below originated from the project. The ones that are have this clarified in the description. 
## Examples

### Retrieving from an API
Retrieving the data from an api every day. 

#### Process
```python
#Data retrieval 

```

#### Result
table of data

### Retrieving sentences from dataset 
The project data set was a big collection of emails. We needed sentences to be able to classify if something is a 
question or not. This 'collecting' of sentences can be classified as processing and collection as well, because it is 
retrieving something. Therefore this task is mentioned in this document. 

#### Example email
```text

```

#### Process
```python

```

#### Example sentences from email
List of sentences from above email: 
* A
* B 
* C
* D

### Collecting meta-data
For example collecting all the data types from all the files on a hard drive. 


### Manual observations
Checking the weather everyday on your weather station and writing it down, is a way of collecting data. 
This process would take a lot of time and since this data is publicly available, would be redundant but for 
the explanation:

#### Process
* Waking up
* Checking the thermometer
* Checking the wind speed
* Checking the wind direction
* Checking the humidity
* Write these statistics down

#### Result
Doing this process daily for x amount of time could result in a dataset as such: 

Date | Temperature | Wind Speed | Wind Direction | Humidity |
-----| ------------| -----------| ---------------| ---------|
01-12-2018 | 28 | 15 | NW | 5 |
02-12-2018 | 26 | 13 | NW | 12 |
03-12-2018 | 25 | 18 | SW | 8 |
04-12-2018 | 24 | 19 | SW | 4 |
05-12-2018 | 23 | 3 | NW | 7 |
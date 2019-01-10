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
For example retrieving the recent public event on GitHub. This way of getting data is very common and could 
be used in a variety of ways. We did not use any such way of retrieving data in our project, but it is 
important to know the possibility.

```python
import requests
import json

#Easy API call to the github api using the Requests package. 
r = requests.get('https://api.github.com/events').json()
```

#### Result
```json
{
    "actor": {
        "avatar_url": "https://avatars.githubusercontent.com/u/178444?",
        "display_login": "tomberek",
        "gravatar_id": "",
        "id": 178444,
        "login": "tomberek",
        "url": "https://api.github.com/users/tomberek"
    },
    "created_at": "2019-01-10T13:05:36Z",
    "id": "8864608996",
    "payload": {
        "before": "ea27e1987d0c3ce9f05e7002436c8c4f2663cda5",
        "commits": [
            {
                "author": {
                    "email": "tom@dds.mil",
                    "name": "Tom Bereknyei"
                },
                "distinct": true,
                "message": "More usage printing for make-client-ovpn",
                "sha": "1e4d7eaeaa4a3bf26d7188e967390715b96de096",
                "url": "https://api.github.com/repos/tomberek/easy-ca/commits/1e4d7eaeaa4a3bf26d7188e967390715b96de096"
            }
        ],
        "distinct_size": 1,
        "head": "1e4d7eaeaa4a3bf26d7188e967390715b96de096",
        "push_id": 3197464862,
        "ref": "refs/heads/master",
        "size": 1
    },
    "public": true,
    "repo": {
        "id": 126281158,
        "name": "tomberek/easy-ca",
        "url": "https://api.github.com/repos/tomberek/easy-ca"
    },
    "type": "PushEvent"
}
```

The result in API calls is in JSON with most API calls. The code above is an example of a JSON response.

### Retrieving sentences from dataset 
The project data set was a big collection of emails. We needed sentences to be able to classify if something is a 
question or not. This 'collecting' of sentences can be classified as processing and collection as well, because it is 
retrieving something. Therefore this task is mentioned in this document. 

#### Example email
```text
Als ik inkomensdata over buurten wil opvragen via Statline, krijg ik constant een 404 foutmelding. Dit gaat via deze 
URL:
http://statline.cbs.nl/Statweb/selection/?VW=T&DM=SLNL&PA=81903NED&D1=0-10%2c26-32%2c88&D2=2018-2023&D3=1&HDR=T&STB=G1%2cG2
Aangezien jullie gepubliceerde wijken-en-buurten Excel files geen inkomensdata bevatten, zou ik deze graag via Statline 
willen opvragen. Vanaf welke computer ik het ook probeer, deze dataset blijft een 404 foutmelding geven. 
Wat kan ik het beste doen?
```

#### Process
To actually get the sentences from an email body, we apply a nltk function, sent_tokenize to the email body. 
This is relatively easy. Just import and install the package then run the function with the email body and it 
returns a list of sentences.

```python
import nltk

nltk.sent_tokenize(email, 'dutch')
```
#### Result
```python
[
'Als ik inkomensdata over buurten wil opvragen via Statline, krijg ik constant een 404 foutmelding.', 
'Dit gaat via deze URL:  http://statline.cbs.nl/Statweb/selection/?VW=T&DM=SLNL&PA=81903NED&D1=0-10%2c26-32%2c88&D2=2018-2023&D3=1&HDR=T&STB=G1%2cG2', 
'Aangezien jullie gepubliceerde wijken-en-buurten Excel files geen inkomensdata bevatten, zou ik deze graag via Statline willen opvragen.',
'Vanaf welke computer ik het ook probeer, deze dataset blijft een 404 foutmelding geven.', 
'Wat kan ik het beste doen?'
]
```

These sentences are easily splitted with the nltk package, specifically the sen_tokenize function. Our jow however 
was to split the most unuseful text before this tokenization by nltk. Usually it included extra information, 
emptied tags for the anonymization, formIds, whitespaces among other data.

### Collecting meta-data
For example collecting all the data sizes from all the files in a folder. For this example, I used a package glob, 
to get all the files in a folder. And os.stat to collect metadata from a file. 

```python
import os
import glob

csv_files_list = glob.glob('/home/jan-laptop/Encfs/encryptedCBS/Emails_2/*.csv')

file_sizes = list()

for file in csv_files_list:
    file_sizes.append(os.stat(file).st_size)

print(file_sizes)
```

#### Result
The result in this case is a list of appended file sizes only. To make any useful conclusions, 
more information could be necessary. 

```python
[996844, 441042, 1774124, 482039, 2313891, 779334, 93313, 244707, 902, 1518910, 306037, 638204, 14348, 180045, 370400,
 167437, 151258, 26001, 5708492, 251742, 5922, 259823, 840430, 792685, 750991, 623709, 490938, 587255, 1188337, 228382, 
 333982, 88232, 1465931, 617849, 125772, 141245, 274742, 156698, 291811, 2762716, 1474973, 86153, 374348, 1548650, 
 1340277, 351880, 2303203, 167325, 3414839, 954847, 115226, 1321579, 50231, 1439777, 922, 2875144, 406573, 86501, 
 576244, 1216955, 573381, 133331, 181652, 158567, 75471, 137501, 304317, 433053, 274204, 3764516, 8397, 190193, 
 397197, 81363, 414402, 1283599, 1575950, 358952, 559547, 912438, 4471333, 1042222, 1068397, 178085, 1477548, 504882, 
 699892, 118355, 524013, 309084, 19096, 827927, 280116, 225003, 4899970, 476795, 1790263, 841950, 16908289, 25681, 
 890, 26671, 7543061, 175029, 173998, 244422, 155047, 287333, 720014, 888654, 52759, 154771, 347828, 1133198, 9720769, 
 466198, 2121776, 470148, 854836, 188721, 4935856, 1717242, 566924, 1289253, 4071, 126339, 8519, 5593717, 503752, 
 2041506, 274046, 472139, 134458, 37261, 666361, 169796, 264141, 1054811, 39823, 504782, 237663, 139183]
```

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
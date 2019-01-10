# SCRUM 
During the starting week of our project, we were advised to use SCRUM as a way to track our progress. 
This document contains a few examples of tasks I have participated in or have completed myself. 
These tasks will be explained by how they have been useful for the project.

## Cleaning data
### Description:
This ticket was made to clean the data we received from our project owner. We had received the data as a text 
file that included loads of not useful data. After the analysis of data, we were able to clean the data partially. 
### Process: 
We started from the analysis, which showed us that the emails included an empty from tag, an empty to tag, 
a formId and some other attributes and texts that weren’t part of the email. In the process we removed this data by splitting on them and joining the rest of the mails.

### Result
This task resulted in a function that was able 


## Formulating the research question
### Description:
For this task we had a meeting with our product owner. We discussed the general goal of the project and tried to phrase a research question that corresponded to their wishes.

### Process: 
To the best of our abilities at the time, we set up a few options to discuss during the meeting with our product owner. During the conversation however, we found out the assignment was different than what we were told. The options we had set up, did contribute to the conversation.  

### Result: 
The result of this task was the research question we came up with during this week. It has been revised in the meantime. The research question was: “Which data mining and Natural Language Processing methods can be used to filter the most frequently asked questions from unstructured e-mails sent to the Central Bureau of Statistics between 2017 and 2018?”


## Analyzing Received Data:
### Description: 
This ticket was made to analyze the data we received from our project owner. 
The data was given in a  txt file with no explanation of the structure. So we had to do our analyses the file by ourself and figure out the way the file was dumped from their database. 



### Process:
We started by opening the file in a text editor to get an idea of the structure. 
After some time we noticed it was a dump of emails containing the original questions asked to our project owner and replies from the people who answer their questions. For us the goal of this task was to find a specific separator to filter out the questions asked. 

### Result:
In the file we found that the word: Vraag:  (question in dutch) was a separator that we could use to filter out the asked question. After this separator the questions was noted and it would end with the word: Category. This could be used as a second separator to filter out the original question. With this result we could start our next task to build a data cleaner to filter out all the asked questions from the datafile. 

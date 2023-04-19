# Starbucks Project

The purpose of this project is a machine learning classifier that reads customer behavior data when starbucks application sends to them different types of offers and classifies which type of customer respond to offer and complete it based on his age, income, and gender.


### Data File Descriptions

#### Data Dictionary:

The data is contained in three files:

- portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)\
- profile.json - demographic data for each customer\
- transcript.json - records for transactions, offers received, offers viewed, and offers completed\

Here is the schema and explanation of each variable in the files:

#### portfolio.json

id (string) - offer id\
offer_type (string) - type of offer ie BOGO, discount, informational\
difficulty (int) - minimum required spend to complete an offer\
reward (int) - reward given for completing an offer\
duration (int) - time for offer to be open, in days\
channels (list of strings)


#### profile.json

age (int) - age of the customer\
became_member_on (int) - date when customer created an app account\
gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)\
id (str) - customer id\
income (float) - customer's income


#### transcript.json

event (str) - record description (ie transaction, offer received, offer viewed, etc.)\
person (str) - customer id\
time (int) - time in hours since start of test. The data begins at time t=0\
value - (dict of strings) - either an offer id or transaction amount depending on the record


## 📁 Directory structure
```
+
|   Project Proposal.pdf
|   Project Report.pdf
|   README.md
|   report.pdf
|   Starbucks_Capstone_notebook.ipynb
|   
\---data
|      portfolio.json
       profile.json
       transcript.json
       

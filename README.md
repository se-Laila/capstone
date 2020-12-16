# Starbucks Capstone Project

### Table of Contents
1.	[Project Motivation](#project-motivation)
2.	[File Descriptions](#file-descriptions)
3.	[Results](#results)
4. [Conclusion](#conclusion)
5. [Reflection](#reflection)
6. [Improvement](#improvement)
7.	[Installation](#installation)
8.	[Licensing, Authors, and Acknowledgements](#licensing-authors-and-acknowledgements)

### Project Motivation

The motivation behind this project is to apply data science to analyze data proivded by Starbucks and combine transaction, demographic and offer data 
to determine which demographic groups respond best to which offer type. This data set is a simplified version of the real Starbucks app because the 
underlying simulator only has one product whereas Starbucks actually sells dozens of products. 

### File Descriptions
There are 1 folder here and 3 files:
1. data folder:
 - portfolio.json
 
 It contains information about each offer. There is a total of 10 different offers. The schema and explanation of each variable in the files:
    - id (string) - offer id
    - offer_type (string) - type of offer ie BOGO, discount, informational
    - difficulty (int) - minimum required spend to complete an offer
    - reward (int) - reward given for completing an offer
    - duration (int) - time for offer to be open, in days
    - channels (list of strings) - four possible channels are used: email, mobile, social and/or web
 
 ![result](https://miro.medium.com/max/1400/1*I_2_mKXftRMXk6WBMaMHSA.png)
 
 - profile.json
 
 It has the demographic data of 17,000 unique customers:
    - age (int) - age of the customer
    - became_member_on (int) - date when customer created an app account
    - gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
    - id (str) - customer id
    - income (float) - customer's income
 
 ![result](https://miro.medium.com/max/1400/1*R1AIpVQdgFsYXgkegpTQXg.png)
 
 - transcript.json
 
 It has 306,534 records for transactions, offers received, offers viewed, and offers completed:
    - event (str) - record description (ie transaction, offer received, offer viewed, etc.)
    - person (str) - customer id
    - time (int) - time in hours since start of test. The data begins at time t=0
    - value - (dict of strings) - either an offer id or transaction amount depending on the record

![result](https://miro.medium.com/max/1400/1*Q78Fa5t2f54epwbDYlkwIw.png)

2. Starbucks_Capstone-Data_Exploration.ipynb
A jupyter notebook that has the code necessery to explore, visualize and understand the data.

3. Starbucks_Capstone_Preprocessing&Analysis.ipynb
A jupyter notebook that has the preprocessing and analysis of the data.

4. transcript_transaction_data.csv: a file used to hold the results of the following:
read transcript_offer_completed_data & transcript_transaction_data row by row. If the 2 records have the same person_id and the were completed at the same time, I'm assuming that the transaction belongs to that particular offer. Then, fill in the new offer_id_1 column with the offer_id from the offer_completed record
This took 6 hours to run, so I decided to hold the results in a CSV then read it to complete the analysis.


### Results
The results of the analysis can be found in this medium article: https://laila-mamh.medium.com/which-customers-should-starbucks-attract-and-how-402aa6694435


Here are some information on demographics of the customers:
![results](https://miro.medium.com/max/1000/1*-5fAkk-ecAdrnDLyKTIgCg.png)

![results](https://miro.medium.com/max/1400/1*L26drRQ4hrMb54ZQrTdUfw.png)

![results](https://miro.medium.com/max/1000/1*TmTR1uZglh4ZLBxjqbakOQ.png)

![results](https://miro.medium.com/max/1400/1*3_EjwtTdrY92fmqGd1BZcA.png)

![results](https://miro.medium.com/max/1400/1*AgG0K8KEjcwgokeo4vgOYA.png)

The below categories were used to group customers based on their income: 

![results](https://miro.medium.com/max/1264/1*wAUoG6qF8BI6eEwMTy2juA.png)

And here is the status of all events:

![results](https://miro.medium.com/max/1000/1*VGw5KZs-C2-J8IGJbheu_w.png)

and types of all offers:

![results](https://miro.medium.com/max/1000/1*oJYQBvbud7IQVD-a9IQynQ.png)

![results](https://miro.medium.com/max/1400/1*RhF339eCdkWM29NJ3w6-DA.png)

The most completed offers are:

![results](https://miro.medium.com/max/1400/1*xzy1JIU0exB1U5deGQyUTQ.png)

These are their info:

![results](https://miro.medium.com/max/1400/1*DA7p4cN7wVeT-2tPGjJlQg.png)

They also caused the most amount spent by customers:

![results](https://miro.medium.com/max/1400/1*E5SIvtnJz8NmzEtrEiKS2g.png)

and the ratio of the rewarded amount to the full amount spent is the lowest:
![results](https://miro.medium.com/max/1400/1*L1FtNicw4tDThlLeFbkdLQ.png)

I also tried to use another way to determine the effectiveness:
- 1 means offer is effective: if offer_viewed == offer_completed. This means the customer saw the offer and felt motivated to use it.
- 0 means offer is ineffective: if offer_viewed > offer_completed. This means that the customer saw it but didn’t care for using it.
- -1 offer is unnecessary: if offer_viewed < offer_completed. This means that the customer didn’t know about it, and was willing to pay full price.

The offers can be grouped in the 3 categories, and the accumulated information is shown in the table below:

![results](https://miro.medium.com/max/1400/1*n29O6uocQlFrK2KuDzrXDw.png)

Customers Interaction and Response:

The most number of offer_received per customer is 6. The following grouped charts show the characteristics of the customers who viewed and completed all 6 offers:
Gender wise, there is no big difference. However, the majority of those customers are Adults from the Lower Middle Class who became members in 2016.

![results](https://miro.medium.com/max/1400/1*jtDlZRIEIwAO81r1vi23WA.png)

Customers with the Most Spent Amount:

![results](https://miro.medium.com/max/1400/1*Ai0xfUVLMHFIhy7TAfxR5g.png)

Most Rewarded Customers:

![results](https://miro.medium.com/max/1400/1*awkD29rqXXkKiEVPEhvTgg.png)

More details:

![results](https://miro.medium.com/max/768/1*wvMUWauXn6c-cuSu4Mtxgw.png)

![results](https://miro.medium.com/max/692/1*qPcoS7u81gxJz2QtbTUoXQ.png)

![results](https://miro.medium.com/max/988/1*X-tpNOf4I5UJ135a4WCVHg.png)

### Conclusion 
The data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. It has 10 offers, 14825 complete records of customers, and 306534 records in the event log. 

As a result of the analysis, we found out that both offers: fafdcd668e3743c1bb461111dcafc2a4 and 2298d6c36e964ae4a3e7e9706d1fb8c2 were utilized more than the other offers and more money was made out of them. In addition, they both were communicated to customers via all 4 channels. We also realized that there is a correlation between offer_viewed and offer_completed: the more the offers are viewed by customers, the more likely they will be used.

On the customer side, the majority of the customers who viewed and completed all offers received were adults (both genders) from the lower middle class who became members in 2016.

The Loyal Customers who will buy their favorite drink no matter what are mostly males than females, adults, lower middle class and those who became members in 2017.

We also saw that a senior male spent 1608 on coffee that month!

### Reflection
- Understanding the data took so much time. I kept learning and I still think there is so much to learn.
- There is no end for the possibilities for the analysis. Having a clear idea at the beginning is important to avoid being stuck in analysis paralysis.
- Having a plan on how the data will be used is critical when collecting the data. Some records are outliers where for example there are some records of completed offers but no transactions related to that record. This and others harm the analysis and decrease its accuracy.

### Improvement

Collecting Data: When running the experiment, add a primary key to connect between the offer different events, especially transaction and completed. Offer_expired value can be calculated on the spot and added to the data instead of reverse engineer it.

Analysis: At the end of the analysis I realized that changing some column names or even values would have helped me throughout the analysis. For example: Person_id was a weird name for customer id. I could have changed it. Also the offers names: I could have used the first letter of the offer type. For example: ae264e3637204a6fb9bb56bc8210ddfd is of type BOGO. I could have changed it to BOGO1 or even B1. This would have enhanced readability.

Performance: I have re-written some of the logic to enhance the performance. However, I haven't measured the time to run the entire workspace. More enhancements could be done.


### Installation Instructions
1. Download project files:

Download the project files to your local machine, and make sure you keep the same folder structure.

2. Run the jupyter notebook and then view Starbucks_Capstone-Data_Exploration.ipynb. Run the cells to understand the data.
3. view Starbucks_Capstone_Preprocessing&Analysis.ipynb. Run the cells to analyze the data.



### Licensing, Authors, Acknowledgements
Credit goes to Starbucks and Udacity for the data.

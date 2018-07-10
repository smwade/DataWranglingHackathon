# Data Wrangling Hackathon

## Objective

You just arrived at SuperBank, please read carefully the following letter you just received from your new CEO.


```
Hi Data Scientist!

Welcome to SuperBank! We aim to become a data-driven institution so we decided that having someone like you exploring the type and quality of data we have in-house would be a great idea. If we could extract some value out of it, great!

But what is “value” here? Our objective is that you help us decide which are the best people to whom we should provide loans. In essence:

Can you predict how capable each applicant is of repaying a loan?

I think they call this “binary classification”.

We are all in a big of a hurry, as always, so I give you a full working day to have a sense on what we have. Since I’m the CEO, I managed to get the information from all departments. Believe me… If it were you, I think you wouldn’t have been able to do that. Well, in the end you would manage to do it since it is part of your job to be transversal to all company.

Regarding the data I managed to get… We are a big organization and we actually don’t have a clue that one should ever have an organized database. Which would be the reason to do that? Life already has too many problems. You might find that the data comes in different formats. I feel that the departments should have worked a bit harder to help you out, but I think they still don’t believe you will be able to get something out of it.

Best of luck,
Your CEO
```


## Tasks

In the data directory you’ll find many files with precious data for this hackathon. Read them and clean them.

Call the API to get more data.

Explore the SQL database to get even more data.

Merge all the data you can. 

Each portion of data you find contains a number of columns (features) that you can use in your modelling stage.
The target is in the SQL database (column `target`, table `credit_risk_target`). You will find the values:

```
0, 1: Training set (0 = non-default; 1 = default)
NaN (missing value): Test set. You will be evaluated by predicting on these observations.
```

## Submission

You have to submit a csv file with two columns:
`SK_ID_CURR`: simply the Test dataset (the ones that you found as NaN in SQL table `credit_risk_target`).
`TARGET` is the probability that a person will default (e.g., output of predict_proba). Sometimes it is not exactly “probability”, but it is ok if the ranking order is correct among all observations.


## Querying the API
You can get even more data from our API.
Here you can find a small documentation, that shows you the available endpoints.

The steps for you to get your data using the API are the following:
The root URL is https://api.hackathon-03.batch2.lisbondatascience.org, this means that when you do a GET request to the API, the URL will always look like: https://api.hackathon-03.batch2.lisbondatascience.org/blabla (where blabla should obviously be replaced with something else)
Call the token endpoint to get an authentication token. Here you should replace blabla with api/token-auth and send the query parameter username with value ixperience_student. This will give you a token for you to authenticate in the next request.
Call the data endpoint to get your data.
This endpoint requires you to provide an authentication header. Check the docs of the Python requests library. The header name is Authorization and the value is token {here goes your token}. Example:
{‘Authorization’: ‘token 235n7bf387n2f78h2f74ghr28f48’}

Your data is not going to be given to you all at once. Because this would make the requests take a long time. So you’ll have to use the page and page_size query parameters. The maximum allowed page_size is 2000. Do some test requests to see the response and understand how to get all the data.

## Evaluation

The accuracy is validated with the AUC metric.


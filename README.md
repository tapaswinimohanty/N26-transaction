# N26 Hacker Rank Coding Challange

The project demonstrates below aspects:
1. Building REST end points using spring MVC
2. REST conventions.
3. Global Error Handling.
6. Spring AOP.
7. Unit testing
8. Integration testing.


The project consists of :
-entities
-repositories
-services
-controllers
-test
Running project:
just run ./mvn clean install to build the project

once ready go to target folder and run the command java -jar transationApp-0.0.1-SNAPSHOT.jar

Please find my understanding below.


For /statistics GET api, as per my understanding we are fetching all transaction ,whose timestamp value and current timestamp diffrence
is less or equal than  60 seconds  transcation and performing sum,avg,min,max and count operation on that list of transction.


We would like to have a RESTful API for our statistics. The main use case for the API is to calculate realtime statistics for the last 60 seconds of transactions.

The API needs the following endpoints:

POST /transactions – called every time a transaction is made. It is also the sole input of this rest API.

GET /statistics – returns the statistic based of the transactions of the last 60 seconds.

DELETE /transactions – deletes all transactions.

You can complete the challenge offline using an IDE of your choice. To download the application skeleton, please enable Use Git in the editor and follow the instructions on screen. Please make sure you push your changes to the master branch and test your solution on HackerRank before submitting.

Specs
POST /transactions
This endpoint is called to create a new transaction. Body:
Where:
 amount – transaction amount; a string of arbitrary length that is parsable as aBigDecimal
 timestamp – transaction time in the ISO 8601 format YYYY-MM-DDThh:mm:ss.sssZ in the UTC timezone (this is not the current timestamp)
 
Returns: Empty body with one of the following: 201 – in case of success

204 – if the transaction is older than 60 seconds
400 – if the JSON is invalid
422 – if any of the fields are not parsable or the transaction date is in the future

GET /statistics 
{
  "amount": "12.3343",
  "timestamp": "2018-07-17T09:59:51.312Z"
}
  
This endpoint returns the statistics computed on the transactions within the last 60 seconds.
Returns:
{
  "sum": "1000.00",
  "avg": "100.53",
  "max": "200000.49",
  "min": "50.23",
  "count": 10
}
Where: 
 sum – a BigDecimal specifying the total sum of transaction value in the last60 seconds
 avg – a BigDecimal specifying the average amount of transaction value in the last 60 seconds
  – a specifying single highest transaction value in the last 60 seconds – a   specifying single lowest transaction value in the last 60 seconds
  – a     specifying the total number of transactions that happened in the last 60 seconds
  All BigDecimal values always contain exactly two decimal places and use `HALF_ROUND_UP` rounding. eg: 10.345 is returned as 10.35 10.8 is returned as 10.80
  
DELETE /transactions

This endpoint causes all existing transactions to be deleted
The endpoint should accept an empty request body and return a 204 status code.

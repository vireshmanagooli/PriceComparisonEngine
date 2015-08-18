# PriceComparisonEngine
Price Comparison Engine is to compare the prices of an items across e-commerce sites.

Following are the modules involved.
## 1. Scraper
In this module, scraping is done from various e-commerece site and gets the latest data in the form of JSON.

Following is the <b>Scraper Object</b> structure.
{
  "id": "1234",
  "name": "Website Products",
  "targeturl": "http://www.mywebsite.com/products/3334432",
  "frequency": "manually",
  "instructions": {
    "urls": [
      "http://www.mywebsite.com/products/2342356",
      "http://www.mywebsite.com/products/3467721",
      "http://www.mywebsite.com/products/4030011",
      "http://www.mywebsite.com/products/3111124",
      "http://www.mywebsite.com/products/0039811",
      "http://www.mywebsite.com/products/3392017"
    ]
  },
  "lastrun": "2014-04-27T00:12:52.097Z",
  "lastsuccess": "2014-04-26T19:00:33.687Z",
  "lastrunstatus": "success",
  "lastversion": 7,
  "newdata": false,
  "meta": false,
  "online": true,
  "webhookuris": [],
  "alertemails": [],
  "collectionNames": [
    "collection1"
  ]
}

The API object

1. <b>id <string> : </b> unique 8 character identifier for the API
2. <b>name <string> : </b> user defined name for the API
3. <b>targeturl <string> : </b> target url from which the API extracts data
4. <b>frequency <string> : </b> frequency with which kimono fetches new data from the target url [fifteenminutely, halfhourly, hourly, daily, weekly, monthly]
instructions.
5. <b>urls <array[string]> : </b> list of urls to visit during a targeted crawl
note that the instructions property is only included when you retrieve one API, not when you list all APIs
instructions.
6. <b>limit <number> : </b> maximum number of pages to visit during a pagination crawl
note that the instructions property is only included when you retrieve one API, not when you list all APIs
7. <b>lastrun <date> : </b> An ISO date string for the last time kimono attempted to fetch data from the target url
8. <b>lastrunstatus <string> : </b> result status for the last attempted run
9. <b>lastsuccess <date> : </b> An ISO date string for the last time kimono successfully fetched data from the target url
10. <b>lastversion <number> : </b> version number of this particular result set. Find out more in by reading about Historical data
11. <b>newdata <boolean> : </b> whether or not the most recent fetch of this data returned results different from the last time you called this API
12. <b>nextrun <string> : </b> An ISO date string for the next time kimono will attempt to fetch data from the target url
13. <b>online <boolean> : </b> whether or not the API is set to run on automatically on a schedule
14. <b>webhookuris <array[string]> : </b> list of urls to which the API posts successfully fetched of new data
15. <b>alertemails <array[string]> : </b> list of email address to which the API posts successfully fetched of new data
16. <b>collectionNames <array[string]> : </b> list of names of the collections contained in the results object when calling the API endpoint.

## 2. Data Normalizer
Once data is recieved from the <b>Scraper,</b> data has to be normalised. Only the normalised data will be shown to the users.

## 3. Schedular
Scrapers and Notications will be triggered based on Schedular.

## 4. Assets Manager
Images will be staored and managed by <b>Asset Manager.</b>

## 5. Product Manager
Products will be managed by <b>Product Manager.</b>

## 6. Store Manager
Addition of new Store and Deletion of new store is done by <b>Store Manager.</b>

## 7. Search
Searching of the items based on category, Brand and name is seached by this module.

## 8. Logger
All the requests are Logged along with logged in user details.

## 9. oAuth
Tokanization based oAuth is done for all the APIs. oAuth will have the roles defined and based on the role appropriate access will be given to the user.

## 10. Price Manager
Latest and History prices will be managed. 

## 11. Notification Manager
Keep a track of the prices and if price goes down then users will get notified by email.

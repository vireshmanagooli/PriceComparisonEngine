# PriceComparisonEngine
Price Comparison Engine is to compare the prices of an items across e-commerce sites.

Following are the modules involved.
## 1. Scraper
In this module, scraping is done from various e-commerece site and gets the latest data in the form of JSON.

Following is the <b>Scraper Object</b> structure.

<pre>
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
</pre>
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

## 12. Database structure

### 1. Reviews : 
Following is the data structure for the Reviews data.
<pre>
{
     id:        'Id of the Review',
     prodId:    'Product Id',
     source:    'Source store of the review, Ex- Flipkart, Amazon etc',
     sourceURL: 'Source URL from flipkart and Amazon etc',
     header:    'Header of the review',
     author:    'Review Author',
     text:      'Review text',
     date:      'Review date',
     rating:    'Rating in the scale of 1 to 5', 
     like:      'Like count to the Review'    
}
</pre>

### 2. Price History
Following is the data structure for the Price History
<pre>
{
     id:      'id of the price history',
     prodId:  'Product Id',
     ticker:  [{date: price}]                 
}
</pre>

### 3. Specification
Following is the data structure for the product specification.
<pre>
{
      id:           'specification Id',
      productId:    'Product Id',
      general:      'JSON type - Brand, sim type etc.',
      display:      'JSON type - Resolution, size etc',
      camera:       'JSON type  - rare camera etc',
      warranty:     'JSON type - Has the Warranty Summary',
      battery:      'JSON type - Has the camera Camera type',
      connectivity: 'JSON type - Bluetooth etc',
      memory:       'JSON type - Memory etc',
      dimension:    'JSON type -  Weight etc',
      multimedia:   'JSON type - Music Player etc',
      platform:     'JSON type - OS, Processor etc',
      otherFeature: 'JSON type - Sensors etc',
}
</pre>

### 4. Store
Following has the online store prices
<pre>
{
       id:           'store product id',
       name:         'Store name. Ex- Amazon, Flipkart',
       scrape:       'Scrape Object to scrape the product from the store.',
       img:          'location of the image',
       price:        'Price of the product',
       avgRate:      'Average rating',
       offer:        'Offer text',
       cod:          'Boolean type to indicate COD',
       emi:          'Boolean type to indicate EMI is available or not',
       returnPolicy: 'Number of days within which product is accepted',
       color:        'Available colors',
       link:         'Link to the product in the store',
       delivery:     'delivery of the product in days' ,
       alert:        'Alert of price drop for particular product for a give store.'
}
</pre>

### 5. Product
Following is the Product details
<pre>
{
        id:         'Product Id',
        title:      'Title of the product',
        category:   'Category of the item. Ex- Mobile, Tv etc',
        price:      'Least price from the store',
        img:        'Image link to the product',
        colors:     [Array of available colors],
        sizes:      [Array of available sizes],
        brief:      [Array of details],
        stores:     [Array of Stores],
        specs:      'Specs',
        review:     'Review',
        history:    'History'
}
</pre>

### 6. Scrape
Following is the Store details
<pre>
{
      id:        'Scrape Id',
      url:       'URL of the product',
      structure: 'Structure of the scraping iteems.'      
}
</pre>

# PriceComparisonEngine
Price Comparison Engine is to compare the prices of an items across e-commerce sites.

Following are the modules involved.
## 1. Scraper
In this module, scraping is done from various e-commerece site and gets the latest data in the form of JSON.

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

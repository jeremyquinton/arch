# Architecture stuff

AWS account has three lambda functions in the cape town region. All done with the serverless stuff. 
- One for converting html to pdfs.
- One which does the takealot journey to get the stock level.
- One for fetching the product detail page with the buybox expanded. Use by swing time to check competitor price.

# Buybox Alerts Server 
- running on an linode - 178.79.166.193

## Buybox Alerts 
- is working well. It currently scans all buyable offers and checks if we have squatters. 
- 23/03/2022 - using more data from offers API and added flag
- Has Buybox Alerts, Swing time share a database.  
   checks for squatters   
   ```/usr/bin/php /var/www/html/application.php buybox:check```    
   notfies us of squatters    
   ```/usr/bin/php /var/www/html/application.php buybox:notify```    
   notfies us of squatters once a week even if offer not buyable  
   ```/usr/bin/php /var/www/html/application.php buybox:notify  --checkAllOffers```    

## Swing Time. Runs on the buybox server.
 ```/usr/bin/php /var/www/html/application.php priceswing:swingtime```
- use to adjust prices for competitors once we detect them with buybox alerts.  
- TODO : would be nice to have a UI on top of it.   
- TODO : supplier specific logic.    

## Takealot Sales. Runs on the buybox server. Seperate php app. 
```/root/a.sh && /usr/bin/php /var/www/takealot-sales/application.php takealotsales:fetch --period today```
- Has Takealot sales running which is pulled in from the takealot api.
- TODO whatever metrics we want to add.

## Takealot Stock Metrics. Runs on the buybox server. Part of the sales app.
- Has Stock metrics store in the stockLevelMetrics table

## Takealot Keyword Metrics. Runs on the buybox server. Part of the sales app.




# Product data tracking


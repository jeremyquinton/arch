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
- use to adjust prices for competitors. 
- TODO : would be nice to have a UI on top of it. 
- TODO : supplier specific logic.  

## Takealot Sales
```/root/a.sh && /usr/bin/php /var/www/takealot-sales/application.php takealotsales:fetch --period today```
- Has Takealot sales running which is pulled in from the takealot api.

- Has Stock metrics store in the stockLevelMetrics table





 
  Below notifies us of products which aren't buyable in the seller portal but another seller is winning the buybox
  Previously we did not get this information
  

- swing time then needs a manual config and can win buybox back - happy to have manual for now. Relies on the one service endpoint for getting product competitor page



# Product data tracking


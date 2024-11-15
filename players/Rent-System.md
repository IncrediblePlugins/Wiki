Areas can be setup for rental or to be purchased via the GUI menu or by using a sign. The setup via the GUI menu is recommended, but both ways result in either a sign or a hologram, which players can use to rent or purchase.

# Menu
1. Place a sign in the sub area that you want to setup to be rented or sold.
2. Execute `/lands menu here` while standing in the area.
3. Click on the setup rental item.
4. Set all values and confirm.

# When the Setup is Done
The rent or sell sign or hologram is setup and players can now access it.

## Reant & Extend Time
To rent a area, just click on the sign or hologram. To add more time to your rental, just click again on the sign or hologram.

## Purchase a Area
Just click on the sell sign or hologram.

## Brose Listings
Use `/lands rent list` to view all areas and lands that can be rented or bought. There you can also filter and sort these offers.

## Cancel Rental
Tenants can use `/lands rent cancel` to cancel their rental while standing inside the area.
 
## Remove the Rental
As the area owner you can either remove the sign or execute `/lands rent remove` while standing inside the area.

## Remove Tenant
Depending on your servers config, you can remove tenants by executing `/lands rent remove tenant`. This may require you to pay a compensation fee to the tenant.

# Signs
An alternative way to setup areas for rental, is by using signs. However, the menu alternative is recommended, since it's just easier.

## Rent Sign Setup
Rental signs can only be created in subareas. Whole lands can only be sold.\
![Rent sign setup](https://imgur.com/am5U7Sp.jpg) 

### Explanation
Parameters surrounded by `[]` are optional. Parameters surrounded by `<>` are required.

* `[area]`: This parameter is only needed if the sign is placed outside the area.
* `<interval>`: The tenant can extend their rental by `<interval>`. Time units: d (days), h (hours) and m (minutes). Default is `d`. Example: `15d` = 15 days
* `<max>`: Is the max. duration of the rental. After that the tenant can't extend their rental.
* `<cost>`: Defines the cost per `<interval>`.

You can only set up sub areas for rental. The default area can only be set up for sale (= selling the whole land; more information below)

#### Example
The following example lets players rent the area for a maximum of 30 days. They can expand their rental for $1000 for every 7 days until they have accumulated a maximum time of 30 days.\
![Rent sign input example](https://imgur.com/IX3XwlJ.jpg)

## Sell Sign Setup
Sell signs can be placed in sub areas and in the default area (= selling the whole land).\
![Sell sign setup](https://imgur.com/Qy68zNh.jpg)

### Explanation
Parameters surrounded by `[]` are optional. Parameters surrounded by `<>` are required.

* `[area]`: This parameter is only needed if the sign is placed outside the area.
* `<cost>`: Defines the total cost.

#### Example
The following example lets players buy the area or land (if placed in the default area) for $5000.\
![Sell sign input example](https://imgur.com/9uRyayN.jpg)

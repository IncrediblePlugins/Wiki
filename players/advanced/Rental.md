Lands can let players rent or buy areas. Servers can offer rentals through a sign or hologram, and some servers also let land owners create offers themselves.

# Browse Offers

Use `/lands rent list` to see areas and lands that can be rented or bought.

The menu can filter and sort offers. Depending on your server settings, you may also be able to teleport to an offer from the list.

# Rent an Area

Click the rent sign or hologram.

Click it again to extend the rental time. You can only extend up to the maximum time set by the owner.

While renting, you are treated as the tenant of that area. The area owner cannot edit the rented area normally until the rental ends or the tenant is removed.

# Buy an Area or Land

Click the sell sign or hologram.

Subareas can be sold. Whole lands can also be sold if the offer is set on the default area.

# Cancel Your Rental

Stand inside the rented area and use:

`/lands rent cancel`

# Remove an Offer

If you manage the area, stand inside it and use:

`/lands rent remove offer`

This removes the rent or sell offer.

# Remove a Tenant

If you manage the area, stand inside it and use:

`/lands rent remove tenant`

Depending on the server, you may need to pay compensation to the tenant.

# Check Rental Info

Stand inside the area and use:

`/lands rent info`

This shows the current rent or sell information for that area.

# Create Offers with the Menu

The menu setup is the easiest way.

1. Place a sign where the offer should appear.
2. Stand in the area.
3. Use `/lands menu here`.
4. Choose the rental setup option.
5. Set the price, time, and other values.
6. Confirm the offer.

Depending on the server, Lands will use the sign or create a hologram.

# Create Offers with Signs

Signs are another way to create offers.

The first line must be `[lands]`, `[land]`, or `[l]`.

## Rent Sign

Rent signs can only be used for subareas.

```text
[lands]
rent [area]
<time> [max-time]
<cost>
```

`[area]` is only needed if the sign is not inside the area.

`<time>` is how much time each payment adds. You can use `m`, `h`, or `d`, such as `30m`, `12h`, or `7d`. If no unit is used, days are used.

`[max-time]` is the most time a tenant can have at once. If you leave it out, the server uses a very high limit.

`<cost>` is the price for each time period.

## Sell Sign

Sell signs can be used for subareas or for the whole land.

```text
[lands]
sell [area]
<cost>
```

`[area]` is only needed if the sign is not inside the area.

`<cost>` is the total price.

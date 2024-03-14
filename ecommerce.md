# eCommerce

## journal articles

Edify enables users to purchase access to articles through the site. This works as follows.

### prices and purchase buttons
Users without access to a content item are shown pricing options and purchase buttons on content item homepages as well as on issue table of contents pages and search result pages. (Pricing and a purchase button can be shown directly on the page or in a popup).

### shopping cart
Users can add multiple items to their shopping cart and buy them through a single transaction. When users add an item to their cart, the top navigation of the site will show an indicator of the number of cart items on the shopping cart icon. Logged in users as well as guest users can add items to their cart. When guest users click on the shopping cart icon to go ahead with the purchase, they are prompted to sign in with existing credentials or register themselves for a new account on the site.

On the shopping cart page, users can view the items in their cart. If any discounts are applicable to users after they have logged in, these discounts are also applied and visible on the shopping cart page. Users can remove items if they wish or increase the quantity of a print item. They can also redeem offer codes for additional discounts.

### VAT
The price displayed to users at this point is exclusive of VAT. If any discounts are applicable at this point, users are shown the discounted price along with the struck-through original price.

In sites where VAT is enabled, after a logged in user clicks on the shopping cart icon, Edify compares the country in the user's profile with the country determined from their current IP address. If these two countries do not match, users will see a form with a drop-down showing both countries and the user is asked to verify their country. After they choose their country and submit the form, they are taken to the shopping cart.

If the two countries already match or if VAT is not enabled in the site, users are directly taken to the shopping cart page.

### payment
If a site has multiple payment methods, users can click on the radio button corresponding to their chosen payment method and then click on the Submit button to move ahead in the purchase. If there is a singe payment method, users will see information about the payment method and can simply click Submit to move ahead with the purchase.

On clicking Submit, users are taken to the Billing Details page. The billing details form is pre-populated with information from the user's profile. If the cart includes print items, users will be shown a Shipping Details section. Users can either fill in the shipping details section or opt to re-use the billing details information.

The bottom of the billing details page shows the final cart contents.

After completing billing details, users will click the “purchase” button. At this point, they will be taken to the payment provider’s website, where they will enter their payment information.

Upon successful payment, they will be directed back to the Edify site, where they will get immediate access to the electronic content they have purchased. For print items, they will see a message that the order is waiting to be sent to the fulfilment party.

Users will also receive an email from Edify confirming their purchase. Typically the payment provider also sends an email to the user.

### order history
Users can view their order history and download receipts for their orders through a centralized interface. They can click on the "My Profile" icon in the top navigation to access their profile dashboard. This dashboard contains a link to view their orders. Clicking on the link takes them to a list of their recent orders as per the screenshot below. They can select "all" in the dropdown to view all their orders or "completed" to only view completed orders.

Clicking on an order shows the user a detailed view of the order. They can click on "View receipt" to view the receipt for that order.

### see also 
For a complete overview, see the [Ecommerce Purchase Documentation](https://confluence.ingenta.com/confluence/display/AUP/Ecommerce+Purchase+Documentation) page on Ingenta's Confluence.

## book, volume, and issue purchases
Edify can also offer options for book, volume, and issue purchases. We can also integrate with print and print on demand fulfilment providers for print purchases and provide Patron Driven Acquisition access to institutions.

## Publisher Administration Tools

### set prices
The site admin can set prices, discounts and offer codes for content items through Edify's price management tools.

Percentage discount offer codes for books can be created through automated feeds _if this functionality has been configured in the site_. Similarly, setting or updating _all_ prices for a content type _needs the help of Ingenta_. There is a [page](https://confluence.ingenta.com/confluence/display/AUP/Discount+and+Offer+Codes+Documentation) in Ingenta's Confluence devoted to discounts.

For a complete overview, see the [Price Management Tool](https://confluence.ingenta.com/confluence/display/AUP/Price+Management+Tool) page on Ingenta's Confluence.

### reports
eCommerce reports give a real-time view of ecommerce orders within the site. 

For a complete overview, see the [Ecommerce Reports Documentation](https://confluence.ingenta.com/confluence/display/AUP/Ecommerce+Reports+Documentation) page on Ingenta's Confluence.

## institution subscriptions
Edify offers options for institution subscriptions.

### automated feeds
Publishers can supply subscription information in automated feeds in CSV format which are processed on a schedule to automatically create subscription access for those institutions in the site.

### offline purchasing capabilities
Publishers can enable offline purchasing capabilities within the site. Institutional administrators can add items to their cart and submit the cart for offline payment instead of purchasing it online through e-commerce. An email with the contents of the cart as an invoice will be sent to the institutional administrator as well as AUP sales staff. In the background, Edify creates a pending license against the selected content for the institution’s account. The institution won’t have access at this point because the payment hasn’t yet been made and the license is in pending state. After the payment has been made offline, AUP staff can activate the license through a single click in the user management tool.

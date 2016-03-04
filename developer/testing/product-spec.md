# Product test plan

## Products grid

### Non-admin user
#### Product Card display
* Card should display `Sold Out!` label when inventory qty < min.inventory qty, but only if "Inventory Tracking" option is enabled. 
* if any product's variant.inventoryQuantity <= variant.lowInventoryWarningThreshold the card should display `Limited Supply`
* if any product's !variant.inventoryManagement || variant.inventoryQuantity > 0 display `Backorder`
* a product card should display a range of pricing from the lowest variant price to the highest variant price.
* if the product has images, the first image in the array should display
* if the product has no images, but a variant of the product has images, the image should be the first image of the first variant
#### Product Card Layouts
* product should use the product layout selected by admin (small, medium, large)
* "small" is the normal, single image view
* "medium" should display three "mini" product variants using primary variant image in a sidebar
* "large" should display a full page width version with the primary product image

#### Interaction with product cards
* When you click on product **image** you should be redirected to PDP (Product Details Page).
* When you click on product **price** you should be redirected to PDP.

#### Autoscroll
* grid should limit to an initial set of 10 products
* should automatically load the next 10 products when scrolling to bottom
* footer should display when the there are no additional products

### Admin user
#### Interaction with product cards

##### Basic Operations:

* When you click on product **image** you should be redirected to PDP.
* When you click on product **price** you should be redirected to PDP.
* When you click on “More Options” button (gear icon), the right sidebar should appear. _on mobile/narrow viewports the sidebar will replace the product grid_
* When “Publish” button has strikethrough eye and you click on it, you should see an alert with text “_ Product name _ is now visible”
* When “Publish” button has just an eye and you click on it, you should see an alert with text “_ Product name _ is now hidden”



##### Selecting Multiple Products:

* By pressing “shift” or “ctrl” + left mouse button (LMB) click on a card you should see appearing `ActionBar`. Also, you should see a border around card. Within `ActionBar` “Product” section you should see Product image and title with price.
* By pressing “shift” or “ctrl” + left mouse button  click on several cards you should see how additional products you selected are added to “Product” section of `ActionBar`.
* By clicking LMB + “ctrl” on selected Product card you should see how this card become unselected. `ActionBar` will not close automatically. You should see a message within it “No selected products....”

##### Reordering Products

* When you have several products on a grid, you could drag a product card by holding left-mouse-button (LMB) and move it relative to another product card. When you drop it in new location, product card should be in it. Try to reload the page by pressing “F5”. Product should be in a new position.
* when product is positioned it should be related to the `tag` currently in use, and should maintain its original position when viewed using other tags of the product

#### Interaction with right side action bar

* When selecting one or several products after click on `ActionBar` “Publish” button you should see an alert about each of the selected products with “is now visible/hidden” notification, also product card “Publish” buttons should change their icons (eye/strikethrough eye).

* When you click on “Duplicate Product” button you should see a new product appear on the grid. It should have the same images, price as original and it should have the title “original product title + -copy” or “original product title + -copy-N” if original was a copy of some other product, where N is the number of copies.
* Duplicated Products should retain images/variants of original
* New `_id` should be assigned to duplicated products and variants.(true in new structure?)

* When several products are selected clicking on “Duplicate Product” button should create a copy of each of those products.
* When you click on “Delete Product” button, you should see a dialog with confirmation “Delete this product?”. By choosing “OK” you should see how product card will disappear and alert will pop-up with message: “Deleted _ Product_name _ ”.
* The same is true when several products selected.
* When you click on product title inside “Product” section, you should be redirected to product page.
* If you browser opened wide enough and you click to one of three elements in “Size” section, you should see how product card change it's sizes. Left element – default size; middle – two size from default; right element – product card will fill all grid width. In a third case product title and price should be moved into blue block in a left bottom corner of a card.

## Product Details Page (PDP)
### Non-admin user

#### Images
* If you see several images on the page – one big and one small below. When you hover over the small image, it should replace the big one.
* If variants/options don't have images, a user should not see empty images. The nearest image should be used.
* If there are no images at all, the default reaction placeholder should display
* 

#### Tags
* If product has tags you should see them under the **Tags** header. If you click on one of these tags you should be redirected to this tag's page. There you could see all products with the same tag.
* if the product has no tags you should not see `Tags` label (or any tag artifacts)

#### Details
* if product has details you should see a detail header and a list of Details. 
* if product has no details you should not see a detail header or any detail artifacts

#### Options
* Product could have variants. Variants could have options. You could see variant as a long (maybe colored) block under the **Options** header. If product has several variants you could switch between them by clicking on colored blocks. If variants have different images, you should see how images change.
* If variant has options you should see it as small blocks with title under phrase “There are more options available for this selection.”. When you click on option you should see how images change (if option has individual images) and how price changes under the product title. Option block should become pressed.
* if a option is selected you should pricing of the specific option
* if a variant is selected, and the variant has a range of options you should see a pricing range display

#### Add to cart
* If you visit a product page and the product has variants and options, you'll need to select an option (if the variant has it) or select a variant (if it has no options) before clicking on “Add to cart” button, otherwise you should see an alert message warning. Selected variant should have a border around it.

* You can change the number of items that want to add to cart by clicking on the selector element inside “Add to cart” button. The maximum number of items that you can add should be limited by the system. When you type a value that exceeds the quantity, it should be changed to the quantity. e.g. If the quantity is 15 and you enter 100 it should change the add to cart quantity to 15.

* You should not be allowed to enter a number with a minus sign in this field.

* When you click to “Add to cart” button with selected variant or option, you should see how this variant or options were added to you cart. You should see a green notification block in a top left corner of a page with the number you choose and the title of selected variant/option.

* When you order all items from variants/options in this product, you should see a notification that item is “Sold out!”

* When you add to cart all product's variants and options and switching to product grid page, you should see a label within product image “Sold out!”

### Admin user
#### Product management
* If you see a link that reads “Make invisible” near “Product management:” on top of the page and you click on it, you should see an alert with text “This product is not visible to customers....”.

* If you see a colored alert on top of a page with link “You can make it visible” and you click on it, the alert should go away and you should see “Product management Make invisible”.

* Near the “Product management” you could see a “Delete” link. If you click on it, you should see a confirmation request window. If you press “OK”, you should be redirected to the products grid page and this product should be removed. You should see an alert with text “Deleted _ Product name _”
* Tab order should start with product title, then tags, details, description, variants (left col, right col)

#### Title
* When you click inside top product title you could change it. After you finished your changes click somewhere out of this field and you should see how URL change against you changes.

* When you click on a page title (second big title) it should become editable. After you finished and click outside it you should see a green blink inside this field. Your changes should be saved.

* If a Tag has been selected as a `hashtag` (the bookmark next to the tag), this should be the url/handle.
* TODO: If a tag has been selected as a `hashtag` changing the title should not change the url. There should be an bookmark icon available to use the title as a bookmark (thus releasing the hashtag url)

#### Images
* You could add images to each of product variants or options. To do that you need to select variant/option and then click on a image or on a “Drop file to upload” block. Also you could drop files from outside of browser. All images you have uploaded should be displayed in this section.

* (Note: is this true?) You can't add images to product itself, only to variants. Try to remove all variants by click on variant “Edit” button, and then on “Remove” button. When you'll remove all variants you should see “+ Create Variant” phrase. Try to add an image. You should see an alert “Please, create new Variant first.”

* You could change images order by dragging and dropping them. Every change should be saved automatically.
* If variants/options don't have images, an admin should see empty images
* You should not be able to upload invalid image types (like .svg) (broken?)

#### Tags
* You could add tags to product by putting cursor in an empty field on **Tags** section and typing tag name. If tag exist, you should see it. You could select an existing tag or add new by clicking outside of this field.
* You could change tags order by dragging them to another position.
* When you click on remove icon on tag, it should be removed.
* When you click on bookmark icon on tag, it's URL should change to the tag name.
* When you click on active bookmark icon on tag, product URL should change to product title.
* Tab/enter/blur should save tag

#### Details
* When you add text to both empty fields inside **Details** section and click outside of this fields, you should see how new details will appears within this section table.
* When you click on remove icon near one of a detail row, it should be removed.
* You should be able to tab and enter details as a key/value (tab/tab submit)

#### Description
* When you click on “Product Vendor” field, you can edit it. Changes should be saved after you click outside of this field.
* When you click on a product description field you can edit it. Changes should be saved after you click outside of this field.

#### Options
* You can see an edit menu of each variant by clicking on “Edit” button, which is from the right side of variant block (pencil icon). By clicking on this “Edit” button you should see a block with two sections: variant settings and options list with their settings.
* By editing variant Label field you should change variant label. You should see changes immediately within variant block.
* Variant block has a badge with number, which represents the quantity for this variant (if it has no options) or sum of all options quantities for this variant.
* TAXABLE – NOT READY

* If "Inventory Tracking" is disabled the "Deny When our of stock" and "Warn @" fields should be hidden.

* By enabling “Inventory Tracking” you allow system to notify when variant will be sold out, or when it's options' quantity will be lower than threshold, which you set in “Warn @” field.

* By enabling “Deny when out of stock” you prevent variant from being ordered if it or it variants is out of stock.

* If variant has options you can edit only “Weight”, “MSRP” and “Warn @” fields.
* If variant has no options you can edit all it's fields.
* When you click on “Add Option” button, you should see an appearance of a new option.
* When you click on “Duplicate” button, you should see an appearance of a clone of this variant. It should be with the same images, but without titles.
* When you click on “Remove” button, first you should see confirmation request and then, when you press “OK” you should see how this variant will be removed.
* If option is newly created and when you edit option field “Option”, you should see how option block appears with this text. (This is old logic)
* When you edit “Label” field you should see how this text appears within option block (new logic).
* **Old logic to review on changes:**
	* Label was the label used to uniquely identify product in cart drawer
	* Option was the label to be used on the product detail page
	* Cart drawer and checkout should be displaying a unique name for the selected option
* When you add numbers to the “Quantity” field you should see how variant block changes it's badge quantity number on a left side of variant block. This number is a sum of all options' quantities. (if options exist for this variant)
* When you fill price field, you should see how product price field reflects to you changes reactively.
* When you click on remove icon from the right side of an option row, you should see confirmation request and after you press “OK”, you should see how option will be removed without any alerts.
* You could change variants order by dragging them.

## Cart
* Cart Icon should display qty as a sum of the qty of all products in cart
* product added to cart should carry through orders unchanged

## Checkout Drawer
* Products in cart should display in checkout drawer
* Image displayed in checkout drawer should be the primary image of the option/variant selected
* Checkout drawer products are in mobile swipable drawer that collapse to display only cart summary card
* Click a product in the drawer should redirect to the PDP page with the selected option displayed (same product configuration, pricing, images as the selected option.)

## Cart Summary
* should display "Items in cart" as a sum of the qty of all products in cart
* should display shipping if previously selected in the cart session
* taxes - to be implemented, will use a flat rate by geo
* should use cart transforms to display Total - sum of these transforms.

## Inventory
* inventory hooks should trigger inventory updates on use/edit of any variant

## Order	
* product in it's original format when it was added to cart should carry through unchanged
* products should display in order details on the cart/completed page
* products should display in order details on the account/profile page
* products should display in order details on the dashboard/orders page
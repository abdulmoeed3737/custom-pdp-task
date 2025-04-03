# Shopify Custom PDP

## Overview

This is a test task. The provided liquid files adds a custom PDP section to any shopify theme for creating custom cusrtains product, the setup details for this has been described below. The product page design is fully responsive.

## Setup Instructions

### Add Product Variants

Add the following variants to the product

Fabric Panel: 1, 2, 3, 4, 5, 6

Drop: 300 cm, 400 cm


### Add Metafields

Ensure the following metafields are added to the products

#### Price Mappings
type: JSON

name: price_mappings

Defines the price based on the combination of fabric panel count and drop length. See example below


#### Fabric Panel Count 
type: JSON

name: fabric_panel_count

Specifies how many panels are needed per width. See example below


### Width 
type: Single line text (list of values)

name: width

Lists available width options.


### Example metafield values:

  price_mappings: 
  
  {
    "1/300": 1000,
    "1/400": 2000,
    "2/300": 2000,
    "2/400": 3000,
    "3/300": 4000,
    "3/400": 6000,
    "4/300": 6000,
    "4/400": 9000,
    "5/300": 8000,
    "5/400": 12000,
    "6/300": 10000,
    "6/400": 15000
  }  
  
  fabric_panel_count:
  
  {
    "50": 1,
    "100": 2,
    "150": 3,
    "200": 4,
    "250": 5,
    "300": 6
  },
  
  width: "50 cm, 100 cm, 150 cm, 200 cm, 250 cm, 300 cm"
  


### Install & Apply the Custom Code

Upload the provided custom-pdp.liquid file to your Shopify theme in the sections folder.

Now open the product page in customizer and add custom pdp section on your product page and click on Save.

Verify that the metafields and variants are correctly set up for the product.

## Pricing Logic 💰

The price calculation is based on the metafields price_mappings and fabric_panel_count. The logic follows these steps:

When a user selects a particular width it retrieve the corresponding fabric panel count from metafield and check drop length.

Check the price_mappings metafield for a key matching {fabric_panel}/{drop}.

Retrieve the price value from the metafield and update the product price dynamically.

## Example Calculation:

If a customer selects Width: 150 cm and Drop: 400 cm, first it gets the corresponding fabric panel count from the metfield which is 3 and then calculates the corresponding metafield key as 3/400, which maps to 4000 in price mapping metafield.

The product price is then updated in add to cart button with necessary currency.

It then also updates the variant id so that the selected variant is added to cart.


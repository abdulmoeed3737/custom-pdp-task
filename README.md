# Shopify Custom PDP

## Overview

This Shopify customization modifies the product detail page (PDP) to allow customers to select fabric panel count and drop length dynamically. The pricing logic is controlled via metafields.

## Features

✅ Dynamic pricing based on metafields.

✅ Custom options for fabric panel count and drop length.

✅ Seamless integration with Shopify's native product options.

## Setup Instructions

1️⃣ ### Add Metafields

Ensure the following metafields are added to the products:

Price Mappings (price_mappings): Defines the price based on the combination of fabric panel count and drop length.

Fabric Panel Count (fabric_panel_count): Specifies how many panels are needed per width.

Width (width): Lists available width options.

Example metafield values:

{
  "price_mappings": {
    "1/300": 1000,
    "1/400": 2000,
    "2/300": 2000,
    "2/400": 3000,
    "3/300": 3000,
    "3/400": 4000
  },
  "fabric_panel_count": {
    "50": 1,
    "100": 2,
    "150": 3,
    "200": 4,
    "250": 5,
    "300": 6
  },
  "width": "50 cm, 100 cm, 150 cm, 200 cm, 250 cm, 300 cm"
}

2️⃣ ### Add Product Variants

Add the following variants to the product:

Fabric Panel options: 2, 3, 4, 5, 6

Drop options: 300 cm, 400 cm

3️⃣ ### Install & Apply the Custom Code

Upload the provided custom-pdp.liquid file to your Shopify theme.

Ensure your theme settings allow custom product pages.

Verify that the metafields and variants are correctly set up for the product.

## Pricing Logic 💰

The price calculation is based on the metafields price_mappings and fabric_panel_count. The logic follows these steps:

Retrieve the selected fabric panel count and drop length.

Check the price_mappings metafield for a key matching {fabric_panel}/{drop}.

Retrieve the price value from the metafield and update the product price dynamically.

## Example Calculation:

If a customer selects Fabric Panel: 3 and Drop: 400 cm, the corresponding metafield key is 3/400, which maps to 4000.

The product price is then updated to $4000.

🛠 ## Testing & Verification

Ensure all metafield values are correctly set in the Shopify admin.

Check that selecting different variants updates the price correctly.

Test on multiple browsers and devices to confirm responsive behavior.


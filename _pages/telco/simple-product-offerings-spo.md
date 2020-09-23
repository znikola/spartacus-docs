---
title: Simple Product Offering (SPO)
---

{% capture version_note %}
{{ site.version_note_part1 }} 1.4 {{ site.version_note_part2 }}
{% endcapture %}

{% include docs/feature_version.html content=version_note %}

## Overview

A Product Offering includes the specification of a product and also the market details of the product offering for a particular period of time. When customers select a particular product from the `ProductCatalog`, either from an online portal or from a brochure, the details of the selected product offering is displayed for the customers, which allows them to check and confirm before purchasing.

In Product Details, the minimum price algorithm is used to determine the minimum price for the product offering (the algorithm is the same as in the backend). The product summary component is updated to include not only the sum of the pay now prices, but the recurring charges as well.

**Note:** These are displayed only if such prices are configured for the Product Offering in the Backoffice.

## Minimum Price Algorithm

If the product offerings have multiple eligible prices, minimum price algorithm is used to determine the minimum price: 

- Only recurring charges and one-time charges are taken into consideration when determining minimum price.
- The first defined recurring charges are compared. Price that has the smaller recurring charge will be the minimum price.
- If the recurring charges are equal, the first price will be the minimum price.
- If neither price has recurring charges, one-time charges are compared. 
- The first defined one-time charges are compared. Price that has the smaller one-time charge will be the minimum price. 
- If one of the prices does not have recurring charges or one-time charges, the value for the recurring charge or one-time charge is interpreted as 0 by the algorithm.

## Further Reading

For more information, see [Product Offerings](https://help.sap.com/viewer/32f0086927f44c9ab1199f1dab8833cd/2007/en-US/315410098c024e50adf4c43373761936.html) in the TUA Help portal.
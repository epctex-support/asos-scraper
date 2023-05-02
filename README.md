# Actor - Asos Scraper

## Asos scraper

Since Asos doesn't provide an API, this actor should help you to retrieve data from it.

The Asos data scraper supports the following features:

- Scrape product details - You can scrape attributes like images, pricing, variants, colors and all kinds of metadata.

- Scrape any categories - Pick your category, select any filters as you like and scrape all the products that is showing up.

- Scrape and search by keyword - Actor supports built-in keyword search in Asos. You can search any keyword and retrieve all the results.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/asos-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Asos that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on Asos.

- `startUrls`: (Optional) (Array) List of Asos URLs. You should only provide product detail, search or listing URLs.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific item URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape many as items as possible. Therefore, it forefronts all item detail requests. If actor doesn't block very often it'll scrape 100 items in 1 minute with ~0.04-0.08 compute units.

### Asos Scraper Input example

```json
{
  "startUrls":[
    "https://www.asos.com/search/?q=women%27s+dress",
    "https://www.asos.com/asos-design/asos-design-barbie-necklace-in-gold-tone/prd/202940265?clr=gold&colourWayId=202940268&cid=27869",
    "https://www.asos.com/women/a-to-z-of-brands/aldo/cat/?cid=11476&refine=attribute_10992:61388&nlid=ww|shoes|shop+by+brand|aldo"
  ],
  "search": "women dress",
  "proxy":{
    "useApifyProxy": true
  },
  "maxItems": 50,
  "endPage": 2
}


```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of
what is wrong.

## Asos Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Asos actor.

## Scraped Asos Products
The structure of each item in Asos products looks like this:

```json
{
  "productCode": "114609010",
  "name": "Topshop shirring seersucker check puff sleeve mini dress in blue",
  "gender": "Women",
  "id": 201693957,
  "isNoSize": false,
  "isOneSize": false,
  "isInStock": true,
  "isDeadProduct": false,
  "pdpLayout": "Core",
  "hasVariantsWithProp65Risk": false,
  "productType": {
    "id": 8416,
    "name": "Dresses"
  },
  "brandName": "Topshop",
  "brandId": 16305,
  "variants": [
    {
      "variantId": 201693961,
      "size": "UK 4",
      "isInStock": true,
      "sizeId": 387375,
      "colour": "BLUE",
      "colourWayId": 201693958,
      "isPrimary": true,
      "sizeOrder": 10,
      "seller": null,
      "sku": "114609054",
      "hasIngredients": false,
      "pricing": {
        "id": 201693961,
        "variantId": 201693961,
        "sku": "114609054",
        "isInStock": true,
        "isLowInStock": false,
        "stockLastUpdatedDate": "2022-05-08T15:41:23.062Z",
        "warehouse": null,
        "source": null,
        "seller": null,
        "price": {
          "current": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "previous": {
            "value": 35,
            "text": "£35.00",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "rrp": {
            "value": null,
            "text": null,
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "xrp": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "currency": "GBP",
          "isMarkedDown": true,
          "isOutletPrice": false,
          "startDateTime": "2022-06-15T01:00:00Z",
          "wasPriceStartDate": "2022-03-15T12:18:37.025Z"
        },
        "discountPercentage": 61.43
      }
    },
    {
      "variantId": 201693964,
      "size": "UK 6",
      "isInStock": true,
      "sizeId": 387376,
      "colour": "BLUE",
      "colourWayId": 201693958,
      "isPrimary": true,
      "sizeOrder": 20,
      "seller": null,
      "sku": "114609052",
      "hasIngredients": false,
      "pricing": {
        "id": 201693964,
        "variantId": 201693964,
        "sku": "114609052",
        "isInStock": true,
        "isLowInStock": false,
        "stockLastUpdatedDate": "2022-03-15T12:18:33.416Z",
        "warehouse": null,
        "source": null,
        "seller": null,
        "price": {
          "current": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "previous": {
            "value": 35,
            "text": "£35.00",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "rrp": {
            "value": null,
            "text": null,
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "xrp": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "currency": "GBP",
          "isMarkedDown": true,
          "isOutletPrice": false,
          "startDateTime": "2022-06-15T01:00:00Z",
          "wasPriceStartDate": "2022-03-15T12:18:37.025Z"
        },
        "discountPercentage": 61.43
      }
    },
    {
      "variantId": 201693966,
      "size": "UK 8",
      "isInStock": true,
      "sizeId": 387377,
      "colour": "BLUE",
      "colourWayId": 201693958,
      "isPrimary": true,
      "sizeOrder": 30,
      "seller": null,
      "sku": "114609053",
      "hasIngredients": false,
      "pricing": {
        "id": 201693966,
        "variantId": 201693966,
        "sku": "114609053",
        "isInStock": true,
        "isLowInStock": false,
        "stockLastUpdatedDate": "2022-03-15T12:18:33.423Z",
        "warehouse": null,
        "source": null,
        "seller": null,
        "price": {
          "current": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "previous": {
            "value": 35,
            "text": "£35.00",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "rrp": {
            "value": null,
            "text": null,
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "xrp": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "currency": "GBP",
          "isMarkedDown": true,
          "isOutletPrice": false,
          "startDateTime": "2022-06-15T01:00:00Z",
          "wasPriceStartDate": "2022-03-15T12:18:37.025Z"
        },
        "discountPercentage": 61.43
      }
    },
    {
      "variantId": 201693960,
      "size": "UK 10",
      "isInStock": true,
      "sizeId": 387370,
      "colour": "BLUE",
      "colourWayId": 201693958,
      "isPrimary": true,
      "sizeOrder": 40,
      "seller": null,
      "sku": "114609047",
      "hasIngredients": false,
      "pricing": {
        "id": 201693960,
        "variantId": 201693960,
        "sku": "114609047",
        "isInStock": true,
        "isLowInStock": false,
        "stockLastUpdatedDate": "2022-03-15T12:18:33.418Z",
        "warehouse": null,
        "source": null,
        "seller": null,
        "price": {
          "current": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "previous": {
            "value": 35,
            "text": "£35.00",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "rrp": {
            "value": null,
            "text": null,
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "xrp": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "currency": "GBP",
          "isMarkedDown": true,
          "isOutletPrice": false,
          "startDateTime": "2022-06-15T01:00:00Z",
          "wasPriceStartDate": "2022-03-15T12:18:37.025Z"
        },
        "discountPercentage": 61.43
      }
    },
    {
      "variantId": 201693962,
      "size": "UK 12",
      "isInStock": true,
      "sizeId": 387371,
      "colour": "BLUE",
      "colourWayId": 201693958,
      "isPrimary": true,
      "sizeOrder": 50,
      "seller": null,
      "sku": "114609048",
      "hasIngredients": false,
      "pricing": {
        "id": 201693962,
        "variantId": 201693962,
        "sku": "114609048",
        "isInStock": true,
        "isLowInStock": false,
        "stockLastUpdatedDate": "2022-03-15T12:18:33.422Z",
        "warehouse": null,
        "source": null,
        "seller": null,
        "price": {
          "current": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "previous": {
            "value": 35,
            "text": "£35.00",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "rrp": {
            "value": null,
            "text": null,
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "xrp": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "currency": "GBP",
          "isMarkedDown": true,
          "isOutletPrice": false,
          "startDateTime": "2022-06-15T01:00:00Z",
          "wasPriceStartDate": "2022-03-15T12:18:37.025Z"
        },
        "discountPercentage": 61.43
      }
    },
    {
      "variantId": 201693965,
      "size": "UK 14",
      "isInStock": true,
      "sizeId": 387372,
      "colour": "BLUE",
      "colourWayId": 201693958,
      "isPrimary": true,
      "sizeOrder": 60,
      "seller": null,
      "sku": "114609049",
      "hasIngredients": false,
      "pricing": {
        "id": 201693965,
        "variantId": 201693965,
        "sku": "114609049",
        "isInStock": true,
        "isLowInStock": false,
        "stockLastUpdatedDate": "2022-06-18T15:45:34.945Z",
        "warehouse": null,
        "source": null,
        "seller": null,
        "price": {
          "current": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "previous": {
            "value": 35,
            "text": "£35.00",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "rrp": {
            "value": null,
            "text": null,
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "xrp": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "currency": "GBP",
          "isMarkedDown": true,
          "isOutletPrice": false,
          "startDateTime": "2022-06-15T01:00:00Z",
          "wasPriceStartDate": "2022-03-15T12:18:37.025Z"
        },
        "discountPercentage": 61.43
      }
    },
    {
      "variantId": 201693959,
      "size": "UK 16",
      "isInStock": false,
      "sizeId": 387373,
      "colour": "BLUE",
      "colourWayId": 201693958,
      "isPrimary": true,
      "sizeOrder": 70,
      "seller": null,
      "sku": "114609050",
      "hasIngredients": false,
      "pricing": {
        "id": 201693959,
        "variantId": 201693959,
        "sku": "114609050",
        "isInStock": false,
        "isLowInStock": false,
        "stockLastUpdatedDate": "2022-06-20T16:20:43.705Z",
        "warehouse": "FC06",
        "source": {
          "id": "ASOSUK2",
          "description": "ASOS UK (Lichfield)"
        },
        "seller": null,
        "price": {
          "current": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "previous": {
            "value": 35,
            "text": "£35.00",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "rrp": {
            "value": null,
            "text": null,
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "xrp": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "currency": "GBP",
          "isMarkedDown": true,
          "isOutletPrice": false,
          "startDateTime": "2022-06-15T01:00:00Z",
          "wasPriceStartDate": "2022-03-15T12:18:37.025Z"
        },
        "discountPercentage": 61.43
      }
    },
    {
      "variantId": 201693963,
      "size": "UK 18",
      "isInStock": false,
      "sizeId": 387374,
      "colour": "BLUE",
      "colourWayId": 201693958,
      "isPrimary": true,
      "sizeOrder": 80,
      "seller": null,
      "sku": "114609051",
      "hasIngredients": false,
      "pricing": {
        "id": 201693963,
        "variantId": 201693963,
        "sku": "114609051",
        "isInStock": false,
        "isLowInStock": false,
        "stockLastUpdatedDate": "2022-06-21T13:33:23.784Z",
        "warehouse": null,
        "source": null,
        "seller": null,
        "price": {
          "current": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "previous": {
            "value": 35,
            "text": "£35.00",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "rrp": {
            "value": null,
            "text": null,
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "xrp": {
            "value": 13.5,
            "text": "£13.50",
            "versionId": "PRMP000002000200000005247768520220615020000",
            "conversionId": "0"
          },
          "currency": "GBP",
          "isMarkedDown": true,
          "isOutletPrice": false,
          "startDateTime": "2022-06-15T01:00:00Z",
          "wasPriceStartDate": "2022-03-15T12:18:37.025Z"
        },
        "discountPercentage": 61.43
      }
    }
  ],
  "images": [
    {
      "isPrimary": true,
      "colour": "BLUE",
      "colourWayId": 201693958,
      "imageType": "Standard1",
      "url": "https://images.asos-media.com/products/topshop-shirring-seersucker-check-puff-sleeve-mini-dress-in-blue/201693957-1-blue",
      "productId": 201693957,
      "alternateText": "Thumbnail 1 of 4",
      "isVisible": true
    },
    {
      "isPrimary": false,
      "colour": "",
      "colourWayId": null,
      "imageType": "Standard2",
      "url": "https://images.asos-media.com/products/topshop-shirring-seersucker-check-puff-sleeve-mini-dress-in-blue/201693957-2",
      "productId": 201693957,
      "alternateText": "Thumbnail 2 of 4",
      "isVisible": true
    },
    {
      "isPrimary": false,
      "colour": "",
      "colourWayId": null,
      "imageType": "Standard3",
      "url": "https://images.asos-media.com/products/topshop-shirring-seersucker-check-puff-sleeve-mini-dress-in-blue/201693957-3",
      "productId": 201693957,
      "alternateText": "Thumbnail 3 of 4",
      "isVisible": true
    },
    {
      "isPrimary": false,
      "colour": "",
      "colourWayId": null,
      "imageType": "Standard4",
      "url": "https://images.asos-media.com/products/topshop-shirring-seersucker-check-puff-sleeve-mini-dress-in-blue/201693957-4",
      "productId": 201693957,
      "alternateText": "Thumbnail 4 of 4",
      "isVisible": true
    }
  ],
  "totalNumberOfColours": 1,
  "media": {
    "catwalkUrl": "",
    "threeSixtyUrl": ""
  },
  "buyTheLookId": null,
  "sizeGuideVisible": true,
  "sizeGuide": "https://www.asos.com/web/pages/size-guides/index.html?sizeSchema=UK&data=https://www.asos.com/api/sizing/sizeapi/v1/SizeGuide/394%3flanguage%3den-GB",
  "shippingRestrictions": {
    "shippingRestrictionsForSellers": false,
    "shippingRestrictionsLabel": "This product has shipping restrictions.",
    "shippingRestrictionsVisible": true,
    "shippingRestrictionsIncludedCountries": [
      "AD",
      "AE",
      "AI",
      "AL",
      "AM",
      "AO",
      "AR",
      "AT",
      "AU",
      "AX",
      "AZ",
      "BA",
      "BB",
      "BD",
      "BE",
      "BF",
      "BG",
      "BH",
      "BJ",
      "BL",
      "BM",
      "BN",
      "BO",
      "BQ",
      "BR",
      "BT",
      "BW",
      "CA",
      "CC",
      "CD",
      "CF",
      "CG",
      "CH",
      "CI",
      "CK",
      "CL",
      "CM",
      "CN",
      "CO",
      "CR",
      "CW",
      "CX",
      "CY",
      "CZ",
      "DE",
      "DK",
      "DM",
      "DO",
      "DZ",
      "EE",
      "EG",
      "EH",
      "ER",
      "ES",
      "ET",
      "FI",
      "FK",
      "FM",
      "FO",
      "FR",
      "GB",
      "GE",
      "GH",
      "GI",
      "GL",
      "GM",
      "GN",
      "GQ",
      "GR",
      "GU",
      "GW",
      "GY",
      "HK",
      "HR",
      "HU",
      "ID",
      "IE",
      "IN",
      "IQ",
      "IS",
      "IT",
      "JO",
      "JP",
      "KE",
      "KG",
      "KH",
      "KR",
      "KW",
      "KZ",
      "LA",
      "LB",
      "LI",
      "LK",
      "LS",
      "LT",
      "LU",
      "LV",
      "MA",
      "MC",
      "MD",
      "ME",
      "MF",
      "MG",
      "MH",
      "MK",
      "MN",
      "MO",
      "MP",
      "MR",
      "MS",
      "MT",
      "MV",
      "MW",
      "MX",
      "MY",
      "MZ",
      "NA",
      "NE",
      "NF",
      "NG",
      "NL",
      "NO",
      "NP",
      "NR",
      "NU",
      "NZ",
      "OM",
      "PE",
      "PH",
      "PK",
      "PL",
      "PM",
      "PN",
      "PR",
      "PS",
      "PT",
      "PW",
      "PY",
      "QA",
      "RO",
      "RS",
      "RU",
      "RW",
      "SA",
      "SB",
      "SE",
      "SG",
      "SH",
      "SI",
      "SJ",
      "SK",
      "SL",
      "SM",
      "SN",
      "SS",
      "ST",
      "SV",
      "SX",
      "SZ",
      "TF",
      "TG",
      "TH",
      "TJ",
      "TK",
      "TL",
      "TN",
      "TR",
      "TT",
      "TV",
      "TW",
      "TZ",
      "UG",
      "US",
      "UY",
      "UZ",
      "VA",
      "VC",
      "VG",
      "VI",
      "VN",
      "YT",
      "ZA",
      "ZM",
      "ZW"
    ]
  },
  "plpIds": [
    {
      "id": 5235,
      "type": "Standard"
    },
    {
      "id": 7046,
      "type": "Standard"
    },
    {
      "id": 8799,
      "type": "SEO"
    },
    {
      "id": 8834,
      "type": "Standard"
    },
    {
      "id": 13489,
      "type": "Standard"
    },
    {
      "id": 13597,
      "type": "Standard"
    },
    {
      "id": 13929,
      "type": "Standard"
    },
    {
      "id": 15346,
      "type": "Standard"
    },
    {
      "id": 15623,
      "type": "Standard"
    },
    {
      "id": 15627,
      "type": "Standard"
    },
    {
      "id": 15944,
      "type": "Standard"
    },
    {
      "id": 15945,
      "type": "Standard"
    },
    {
      "id": 16396,
      "type": "Standard"
    },
    {
      "id": 16646,
      "type": "Standard"
    },
    {
      "id": 16654,
      "type": "Standard"
    },
    {
      "id": 16824,
      "type": "Standard"
    },
    {
      "id": 19680,
      "type": "Standard"
    },
    {
      "id": 20246,
      "type": "Standard"
    },
    {
      "id": 28023,
      "type": "Standard"
    },
    {
      "id": 28041,
      "type": "Standard"
    },
    {
      "id": 28179,
      "type": "Standard"
    },
    {
      "id": 28249,
      "type": "Standard"
    },
    {
      "id": 28254,
      "type": "Standard"
    },
    {
      "id": 28605,
      "type": "Standard"
    },
    {
      "id": 28609,
      "type": "Standard"
    },
    {
      "id": 28611,
      "type": "Standard"
    },
    {
      "id": 29298,
      "type": "Brand"
    },
    {
      "id": 30227,
      "type": "Standard"
    },
    {
      "id": 50047,
      "type": "Standard"
    },
    {
      "id": 50050,
      "type": "Standard"
    },
    {
      "id": 50053,
      "type": "Standard"
    },
    {
      "id": 50054,
      "type": "Standard"
    }
  ],
  "sellingFast": true,
  "paymentPromotions": {
    "clearpay": {
      "gb": {
        "gbp": {
          "minimumTransactionAmount": 25,
          "maximumTransactionAmount": 800
        }
      }
    },
    "payPalPayIn3": {
      "gb": {
        "gbp": {
          "minimumTransactionAmount": 30,
          "maximumTransactionAmount": 2000
        }
      }
    },
    "klarnaPI3": {
      "gb": {
        "gbp": {
          "minimumTransactionAmount": 25,
          "maximumTransactionAmount": 800
        }
      }
    }
  },
  "hasPaymentPromotionAvailable": true,
  "hasVariantsWithIngredients": false,
  "url": "https://www.asos.com/topshop/topshop-shirring-seersucker-check-puff-sleeve-mini-dress-in-blue/prd/201693957?clr=blue&colourWayId=201693958&SearchQuery=women+dress",
  "pricing": {
    "current": {
      "value": 13.5,
      "text": "£13.50",
      "versionId": "PRMP000002000200000005247768520220615020000",
      "conversionId": "0"
    },
    "previous": {
      "value": 35,
      "text": "£35.00",
      "versionId": "PRMP000002000200000005247768520220615020000",
      "conversionId": "0"
    },
    "rrp": {
      "value": null,
      "text": null,
      "versionId": "PRMP000002000200000005247768520220615020000",
      "conversionId": "0"
    },
    "xrp": {
      "value": 13.5,
      "text": "£13.50",
      "versionId": "PRMP000002000200000005247768520220615020000",
      "conversionId": "0"
    },
    "currency": "GBP",
    "isMarkedDown": true,
    "isOutletPrice": false,
    "startDateTime": "2022-06-15T01:00:00Z",
    "wasPriceStartDate": "2022-03-15T12:18:37.025Z"
  }
}
```

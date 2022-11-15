---
title: Implement a data layer on a product page
description: Implement a data layer on a product page
exl-id: 0debf34a-48d4-4029-b790-7fd78865c334
---
# Implement a data layer on a product page

For this tutorial, you implement the Adobe Client Data Layer for a typical e-commerce website. If you have not already done so, please read [How to use the Adobe Client Data Layer](how-to-use-the-adobe-client-data-layer.md) first to understand the Adobe Client Data Layer.

Let's assume the user browses your products and clicks on a foam roller to learn more. The user lands on the foam roller product detail page.

## Create a simple product details page

1. Copy and paste the following code into a new HTML file and save it on your computer.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Product Page</title>
    <script>
      // Code will go here.
    </script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button">Add to cart</button>
    <a href="https://example.com/download">Download the app</a>
  </body>
</html>
```

Inside the `<head>` tag there is a `<script>` tag. This is where you place your JavaScript code. Although it's not required to place the `<script>` tag inside the `<head>` container, it is recommended. This ensures data is available to the data layer as soon as possible to support a variety of use cases.

## Add the Adobe Data Layer

1. Inside the `<script>` tag, add this code that creates the `adobeDataLayer` array and then pushes appropriate event and data information into the array. The data conforms to the XDM schema [you previously created](../configure-the-server/create-a-schema.md).

```js
window.adobeDataLayer = window.adobeDataLayer || [];
window.adobeDataLayer.push({
  "event": "pageViewed",
  "web": {
    "webPageDetails": {
      "name": "Foam Roller",
      "siteSection": "Equipment"
    },
  }
});
window.adobeDataLayer.push({
  "event": "productViewed",
  "productListItems": [
    {
      "SKU": "eqfr08",
      "currencyCode": "USD",
      "name": "Foam Roller",
      "priceTotal": 18.95
    }
  ]
});
```

In this example, you've made two pushes to the data layer, each containing an `event` key. Including an `event` key not only communicates what event has occurred on the page, but also makes it simpler for the marketer to create appropriate rules inside tags.

The first push to the data layer notifies listeners (tag rules) that the user has viewed the page. It also adds the page name and site section to the data layer.

The second push to the data layer notifies listeners (tags rules) that the user has viewed a product. It also adds product information to the data layer. 

## Add code for cart add tracking

For this tutorial, you track when the user clicks on the [!UICONTROL Add to cart] button.

1. Copy and paste this code after the data layer code. The function is called when the user clicks the [!UICONTROL Add to cart] button.

```js
window.onAddToCartClick = function() {
  // In a real implementation, you would change this condition to 
  // only pass if a cart doesn't already exist. You would typically 
  // do this by checking a cookie or variable value.
  if (true) {
    window.adobeDataLayer.push({
      "event": "cartOpened",
    });
  }
  window.adobeDataLayer.push({
    "event": "productAddedToCart"
  });
};
```

This function initially checks to see whether a cart already exists for a user.  If the cart does not exist, you push a `cartOpened` event to the data layer. Later, you push a `productAddedToCart` event into the data layer. The product information already exists in the data layer, so you don't need to add it again.

## Add attribute to add to cart button

1. Add an `onclick` attribute to the [!UICONTROL Add to cart] button that calls your new `onAddToCartClick` function.

The result of your HTML page should look as follows:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Product Page</title>
    <script>
      window.adobeDataLayer = window.adobeDataLayer || [];
      window.adobeDataLayer.push({
        "event": "pageViewed",
        "web": {
          "webPageDetails": {
            "name": "Foam Roller",
            "siteSection": "Equipment"
          },
        },
        "productListItems": [
          {
            "SKU": "eqfr08",
            "currencyCode": "USD",
            "name": "Foam Roller",
            "priceTotal": 18.95
          }
        ]
      });
      window.adobeDataLayer.push({
        "event": "productViewed"
      });
      window.onAddToCartClick = function() {
        // In a real implementation, you would change this condition to 
        // only pass if a cart doesn't already exist. You would typically 
        // do this by checking a cookie or variable value.
        if (true) {
          window.adobeDataLayer.push({
            "event": "cartOpened",
          });
        }
        window.adobeDataLayer.push({
          "event": "productAddedToCart"
        });
      };
    </script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button" onclick="onAddToCartClick()">Add to cart</button>
    <a href="https://example.com/download">Download the app</a>
  </body>
</html>
```

## Add code for app download tracking

One last thing to track is when the user clicks the _[!UICONTROL Download the app]_ link.

1. To do this, copy and paste this code below the cart add code. This function is called when the user clicks the _[!UICONTROL Download the app]_ link.

```js
window.onDownloadAppClick = function(event) {
  window.adobeDataLayer.push({
    "event": "downloadAppClicked",
    "eventInfo": {
      "web": {
        "webInteraction": {
          "URL": "https://example.com/download",
          "name": "App Download",
          "type": "download"
        }
      }
    }
  });
};
```

In this case, the information about the link is wrapped inside an `eventInfo` key. As discussed in [How to use the Adobe Client Data Layer](how-to-use-the-adobe-client-data-layer.md), this tells the data layer to communicate this data along with the event, but to _not_ retain the data within the data layer. For a link click, it's not useful to add information about the clicked link to the data layer because it doesn't pertain to the page as a whole and is not applicable to other events that may occur.

## Add attribute to download app link

1. Add an `onclick` attribute to the [!UICONTROL Download the app] link that calls your new `onDownloadAppClick` function.

The result of your HTML page should look as follows:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Product Page</title>
    <script>
      window.adobeDataLayer = window.adobeDataLayer || [];
      window.adobeDataLayer.push({
        "event": "pageViewed",
        "web": {
          "webPageDetails": {
            "name": "Foam Roller",
            "siteSection": "Equipment"
          },
        },
        "productListItems": [
          {
            "SKU": "eqfr08",
            "currencyCode": "USD",
            "name": "Foam Roller",
            "priceTotal": 18.95
          }
        ]
      });
      window.adobeDataLayer.push({
        "event": "productViewed"
      });
      window.onAddToCartClick = function() {
        // In a real implementation, you would change this condition to 
        // only pass if a cart doesn't already exist. You would typically 
        // do this by checking a cookie or variable value.
        if (true) {
          window.adobeDataLayer.push({
            "event": "cartOpened",
          });
        }
        window.adobeDataLayer.push({
          "event": "productAddedToCart"
        });
      };
      window.onDownloadAppClick = function() {
        window.adobeDataLayer.push({
          "event": "downloadAppClicked",
          "eventInfo": {
            "web": {
              "webInteraction": {
                "URL": "https://example.com/download",
                "name": "App Download",
                "type": "download"
              }
            }
          }
        });
      };
    </script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button" onclick="onAddToCartClick()">Add to cart</button>
    <a href="https://example.com/download" onclick="onDownloadAppClick()">Download the app</a>
  </body>
</html>
```

[Next: **Create a tag property and install extensions**](create-a-tags-property-and-install-extensions.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Data Collection. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)

---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more - Define an external data source
description: Adobe Journey Optimizer - External Weather API, SMS Action & more - Define an external data source
kt: 5342
doc-type: tutorial
exl-id: 0ad27ffb-51fe-4bd1-b0be-feeb232039fa
---
# 3.2.2 Define an external data source

In this exercise, you'll create a custom external data source by making use of Adobe Journey Optimizer.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

In the left menu, scroll down and click **Configurations**. Next, click the **Manage** button under **Data Sources**.

![Demo](./images/menudatasources.png)

You'll then see the **Data Sources** list.
Click **Create Data Source** to start adding your data source.

![Demo](./images/dshome.png)

You'll see an empty data source popup.

![Demo](./images/emptyds.png)

Before you can start configuring this, you'll need an account with the **Open Weather Map** service. Follow these steps to create your account and get your API key.

Go to [https://openweathermap.org/](https://openweathermap.org/). On the homepage, click **Sign In**.

![WeatherMap](./images/owm.png)

Click **Create an Account**.

![WeatherMap](./images/owm1.png)

Fill out the details. Click **Create Account**.

![WeatherMap](./images/owm2.png)

You'll then be redirected to your Account Page.

![WeatherMap](./images/owm4.png)

In the menu, click **API Keys** to retrieve your API Key, which you'll need to setup your custom external data source.

![WeatherMap](./images/owm5.png)

An **API Key** looks like this: `b2c4c36b6bb59c3458d6686b05311dc3`.

You can find the **API Documentation** for the **Current Weather** [here](https://openweathermap.org/current).

For this use-case, you'll implement the connection with Open Weather Map based on the city the customer is in, using the **Built-in API request by city name**.

![WeatherMap](./images/owm6.png)

Go back to **Adobe Journey Optimizer**, to your empty **External Data Source** popup.

![Demo](./images/emptyds.png)

As a Name for the data source, use `--aepUserLdap--WeatherApi`.

Set Description to: `Access to the Open Weather Map`.

The URL for the Open Weather Map API is: `http://api.openweathermap.org/data/2.5/weather?units=metric`.

![Demo](./images/dsname.png)

Next, you need to select the Authentication to use.

Use these variables:

| Field               | Value              |
|:-----------------------:| :-----------------------|
| Type            |**API key**            |
| Name           | **APPID**         |
| Value           | **your API Key**         |
| Location           | **Query Parameter**         |

![Demo](./images/dsauth.png)

Finally, you need to define a **FieldGroup**, which is basically the request you'll be sending to the Weather API. In our case, we want to use the name of the City to request the Current Weather for that City.

![Demo](./images/fg.png)

According to the Weather API Documentation, you need to send a parameter `q=City`.

![Demo](./images/owmapi.png)

In order to match the expected API Request, configure your FieldGroup as follows:

>[!IMPORTANT]
>
>The Field group name has to be unique, please use this naming convention: `--aepUserLdap--WeatherByCity`

![Demo](./images/fg1.png)

For the Response Payload, you need to paste an example of the Response that will be sent by the Weather API.

You can find the expected API JSON Response on the API Documentation page [here](https://openweathermap.org/current), under the **JSON** subject.

![Demo](./images/owmapi1.png)

Or you can copy the JSON Response from here:

```json
{
   "coord": {
      "lon": 7.367,
      "lat": 45.133
   },
   "weather": [
      {
         "id": 501,
         "main": "Rain",
         "description": "moderate rain",
         "icon": "10d"
      }
   ],
   "base": "stations",
   "main": {
      "temp": 284.2,
      "feels_like": 282.93,
      "temp_min": 283.06,
      "temp_max": 286.82,
      "pressure": 1021,
      "humidity": 60,
      "sea_level": 1021,
      "grnd_level": 910
   },
   "visibility": 10000,
   "wind": {
      "speed": 4.09,
      "deg": 121,
      "gust": 3.47
   },
   "rain": {
      "1h": 2.73
   },
   "clouds": {
      "all": 83
   },
   "dt": 1726660758,
   "sys": {
      "type": 1,
      "id": 6736,
      "country": "IT",
      "sunrise": 1726636384,
      "sunset": 1726680975
   },
   "timezone": 7200,
   "id": 3165523,
   "name": "Province of Turin",
   "cod": 200
}    
```

Copy the above JSON Response to your clipboard, then go to your custom data source configuration screen.

Click the **Edit Payload** icon.

![Demo](./images/owmapi2.png)

You'll see a popup where you now have to paste the above JSON Response.

![Demo](./images/owmapi3.png)

Paste your JSON Response, after which you'll see this. Click **Save**.

![Demo](./images/owmapi4.png)

Your custom data source configuration is now complete. Scroll up and click **Save**.

![Demo](./images/dssave.png)

Your data source has now been created successfully and is part of the **Data Sources** list.

![Demo](./images/dslist.png)

## Next Steps

Go to [3.2.3 Define a custom action](./ex3.md){target="_blank"}

Go back to [Adobe Journey Optimizer: External data sources and custom actions](journey-orchestration-external-weather-api-sms.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}

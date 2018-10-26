# homebridge-STIBMIVB

**Homebridge plugin for displaying STIB-MIVB next departure at Stop,  from opendata.stib-mivb.be**

[![GITHUB version](https://badge.fury.io/gh/swebdesign%2Fhomebridge-STIBMIVB.svg)](https://npmjs.org/package/homebridge-STIBMIVB)


# Installation

1. Install Homebridge using: `(sudo) npm install -g homebridge`
2. Install this plugin using: `(sudo) npm install -g homebridge-STIBMIVB`
3. Get an API-Key from <a href="http://opendata.stib-mivb.be">Opendata STIB-MIVB</a>
4. <a href="https://www.stib-mivb.be/irj/go/km/docs/resource/OpenData/be7b0f46-6608-44e6-9149-a40ab0cee0c7.pdf">Find</a> your point id  (make sure the query only returns a single result!). Alternatively you can use a different query parameter (see 'Fields')
5. Update your Homebridge `config.json` using the sample below (append in the block 'accessories' not 'platforms').

# Configuration

## STIBMIVB

Example for configuration by point id

```json
"accessories": [
    {
      "accessory": "STIBWaitingTime",
      "apikey": "YOUR_KEY_HERE",
      "stopid": "8161",
      "name": "Stokel"
    }
]
```

## Hint

**You can add multiple accessories if you want to display additional information like oder direction stop or different locations. Just make sure that the field `name` is unique**


## Polling

By default, no polling-interval is specified. That means, the next Departure at Stop is only updated when the Home-App is opened. 
There might be scenarios though, where you would want to periodically update the temperature e.g. as source for trigger-rules.

Opendata.STIB-MIVB has a generous amount of [free calls](https://opendata.stib-mivb.be/store/data) per API-key: you can poll the next departure up to 60 times a minute.
Beware that **just because you can doesn't mean you should**


## Config file


Take a look at the <a href="config.example.json">example config.json</a>


Fields:

* `accessory` must be "StibWaitingTimer" (required).
* `apikey` API-Key for accessing OpenData.STI-MIVB API (required).
* `pointid` pointid query string (resembles to <a href="https://www.stib-mivb.be/irj/go/km/docs/resource/OpenData/e5ccae47-7a5d-4768-9c97-5d7618a9ff8b.pdf">q-parameter</a>) (required).
* `name` is the name of the published accessory (required).
* `nameStop` nameStop is displayed  can have a different name (optional, only works if `showHumidity` is true, defaults to the same as `name`).
* `type` the type of the displayed value, either `min`, `max`, `current`, `clouds` or `sun` (optional, defaults to `current`)
* `pollingInterval` the time (in minutes) for periodically updating the temperature (optional, defaults to 0 which means polling only happens when opening the Home-App)

## Known Issues

* Default Home-App can't trigger scenes: try [Hesperus App](https://itunes.apple.com/de/app/hesperus/id969348892?mt=8) instead

## Advanced usage

comming soon

---
layout: page
title: "Deutsche Bahn"
description: "Instructions how to integrate timetable data for travelling in Germany within Home Assistant."
date: 2015-06-02 21:45
sidebar: true
comments: false
sharing: true
footer: true
ha_category: Transport
logo: db.png
ha_iot_class: "Cloud Polling"
ha_release: 0.14
---


The `deutsche_bahn` sensor will give you the departure time of the next train for the given connection. In case of a delay, the delay is also shown. Additional details are used to inform about eg. the type of the train, price, and if it is ontime.

To enable this sensor, add the following lines to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: deutsche_bahn
    from: NAME_OF_START_STATION
    to: NAME_OF_FINAL_STATION
```

Configuration variables:

- **from** (*Required*): The name of the start station.
- **to** (*Required*): The name of the end/destination station.

As already mentioned this sensor contains a lot of information to access those a [template senosr](/components/sensor.template/) can come handy.

```yaml
# Example configuration.yaml entry
sensor:
  platform: template
  sensors:
    next_departure:
      value_template: '{% raw %}{{ states.sensor.munich_to_ulm.attributes.next }}{% endraw %}'
      friendly_name: 'Next departure'
```

The data is coming from the [bahn.de](http://www.bahn.de/p/view/index.shtml) website.

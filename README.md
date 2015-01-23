running-for-nerds
=================

_contribute! if you have facts to share, please submit a pull request or leave an issue_

Types of running websites:

* "Fitness Portals" offered by hardware companies, like Garmin and Polar
* "Fitness Portals" offered by web companies, like Strava and RunKeeper
* Connectors, like [Tapiriik](https://tapiriik.com/) and [IFFT](https://ifttt.com/)

# Websites


## [endomoto](https://www.endomondo.com/)

* **tapiriik support**

## [RunKeeper](http://runkeeper.com/)

* [API](http://developer.runkeeper.com/healthgraph/overview)
* **tapiriik support**

## [Strava](http://www.strava.com/)

Actively developed.

* **tapiriik support**
* [API Reference](http://strava.github.io/api/)
* Custom JSON encoding for activities

## [Garmin Connect](http://connect.garmin.com/)

Sporadic developer activity.

* **tapiriik support**
* [API Reference](http://developer.garmin.com/)

## [Polar Flow](https://flow.polar.com/)

* _unsupported in tapiriik_
* [API Reference](http://www.polar.com/en/connect_with_polar/polar_accesslink)

## [Nike+](http://nikeplus.nike.com/)

* [API](https://developer.nike.com/)
* _unsupported in tapiriik_
* [IFTTT Support](https://ifttt.com/nikeplus)

## [Motivato](http://motivato.pl/#/): Polish Only

* **tapiriik support**

## [Movescount](http://movescount.com/)

Can be synced directly to Strava and other third party apps, but no public API available.

# Watches

* Polar: locked down to FlowSync
* TomTom: connects to many services, can save files locally
* Garmin: supports a browser plugin that works on many websites - RunKeeper, Strava, Garmin Connect, etc.
* Suunto: locked to Movescountvia Moveslink, but has exports to Strava and can also download as Garmin FIT files.

## GPS

The basics of GPS:

GPS is one system, but there are others, and some devices use more than one. For instance, a new iPhone
connects to GPS, GLONAS (Russia's system), as well as local wifi access points to derive an accurate location.

GPS's accuracy has two user-facing problems

* Time to first lock
* Jitter

The first problem is often ameliorated by 'quickfix' tables - these store recent estimates of satellite
positions so that your receiver can make better guesses initially for where exactly you are.

The second is based on a few different problems - in cities, [multipath propagation](http://en.wikipedia.org/wiki/Multipath_propagation) will distort a signal that bounces off of a big
building, making the track end up offset from its original location.

## Formats

Running data is fun because it's potentially 5-dimensional: within a single GPX or TCX file, you can have

* longitude & latitude & elevation `[x, y, z]`
* heart rate
* time

But traditional GIS formats like Shapefiles can't store all of this data in a non-hacky way,
since they only support attributes at the line level, not at the line-segment level.
[toGeoJSON](https://github.com/mapbox/togeojson) converts GPX to GeoJSON with these properties
put into arrays that work parallel to coordinates.

* [GPX](http://www.topografix.com/gpx.asp)
  * [GPSBabel](http://www.gpsbabel.org/) is an essential swiss-army knife
* [TCX](http://en.wikipedia.org/wiki/Training_Center_XML)

## Sensors

A few basic sensor types:

* Heart rate
* Cadence (for cycling)

Most heart rate sensors work via [EKG](http://en.wikipedia.org/wiki/Electrocardiography), which means
that a big part of their effectiveness comes from skin contact and they often work better with sweat moisture.

Not all do, however - for instance [Fitbit PurePulse](http://help.fitbit.com/articles/en_US/Help_article/Heart-rate-FAQs) uses an optical sensor to estimate blood flow and supposedly derives heart rate from this measurement.

### Protocols

* [Bluetooth Low Energy](http://en.wikipedia.org/wiki/Bluetooth_low_energy)
* [Polar Wearlink](https://groups.google.com/forum/#!topic/btstack-dev/TusCxtbq7ug) - proprietary
* [ANT+](http://en.wikipedia.org/wiki/ANT%2B)

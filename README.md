# py-watering
Home watering system written in python and targeted at a raspberry pi zero with Scroll phat HD display and ModMyPi PiOT Relay Board.

The aim of the system is for a simple home irrigation setup, with compensation based on daily weather. There are existing products out there like the b-hyve, but this is utilising hardware that I already had.

## Watering algorithm

The general idea is to water [1-3 times a week](https://www.yates.com.au/lawn/grow/lawn-watering-tips/), with water either coming from rain or by the sprinklers controlled by the pi, and also taking into account particularly hot weather that may dry out the lawn.
I am assuming that the rain reading at the weather station will be accurate to my property, that the lawn has sufficient drainage, and that if there is an occasional incorrect watering, the lawn won't die.

From this, the following conditions for watering have been crafted:

* Conditions where we should water:
  * If it's a monday, wednesday, or friday
  * If the forecast temperature is over 30
* Conditions that can cancel watering:
  * If there has been rainfall (>=2mm) in the previous day
  * If there is a chance of rain (>=70%, >=2mm) today

Calculations and watering will be done at 7am each day.

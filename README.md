## electioncymru2015
Working repository for information being compiled by Welsh Government for the 2015 UK General Election in Wales

## Introduction
This repo has been put together by the Geography and Technology Team at Welsh Government, as a sort of experiment in what a broader community of developers might be able to do with open data to do with the 2015 General Election in Wales. Although there are lots of potential ideas, one particular focus is to generate a 'find my polling station' application. 

## Data
On 18th February, a request was sent to the 22 Returning Officers (or equivalent) in the Welsh Local Authorities for:

> 2015 General Election polling stations, full address, together with any further attribution held;

> 2015 General Election polling districts as either GIS polygon datasets (e.g. shapefile), or alternatively as a list of addresses or postcodes;

> Any further information assets which might be of relevance to support the matching of individual addresses to their appropriate polling station.

The data is being added to the repository as it is being received in the [rawdata](../rawdata/) directories - one per local authority.

## Ideas and approaches to dealing with the data
### Find My Polling Station
A 'find my polling station' application is slightly more complicated than just directing a user to their nearest one. Every local authority segments parliamentary constituencies into electoral divisions and these divisions into polling districts. Each polling district has its own polling station, which is what is printed on the polling card sent out before the election. We cannot assume that postcode areas (which have a geography all of their own) will correspond neatly with the boundaries of the polling districts.

The ideal architecture therefore would be to firstly create a lookup between postcodes and polling districts. One approach to this would be to use the [Code Point with Polygons](http://www.ordnancesurvey.co.uk/business-and-government/products/code-point-with-polygons.html) dataset. Unfortunately, not available as an OpenData product. That is where Welsh Government might be able to provide some assistance as we have access to this data under the Public Sector Mapping Agreement. We will confirm with Ordnance Survey if we can create a look-up table that is then made available. What the lookup would provide is either a direct polling station result or flag if a postcode happens to fall into more than one polling district. In the latter case, a second service could then kick-in which would use individual house by house data to identify the right polling district and hence polling station. Again, WG input will be needed. Some investigations will be required as to how many postcodes straddle more than one polling district - hopefully none!

Having created a look-up in this way, it should then be possible to create a service which allows users to enter a postcode - or where needed a full address - and then return them their polling station. Lots of other features that could be wrapped around this.

### Other information
The [Ordnance Survey Election Maps](http://www.ordnancesurvey.co.uk/election-maps/) are a pretty good resource, but they don't necessarily integrate the social and demographic information very neatly. Combining these maps with ONS APIs on demographic data could be excellent. Resources include
* [Neighbourhood Statistics API](http://neighbourhood.statistics.gov.uk/dissemination/Info.do?page=nde.htm)
* [ONS Census API](https://www.ons.gov.uk/ons/apiservice/web/apiservice/home)


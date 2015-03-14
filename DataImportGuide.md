**Table of Content**


**Note**
  * You may refer to _gogogo-hk/gogogo/models/__init__.py_ for model detail
  * The design derived from [GTFS](http://code.google.com/transit/spec/transit_feed_specification.html) but not guarantee 100% compatibility

---

# Agency #

You may also refer [GTFS Agency model](http://code.google.com/transit/spec/transit_feed_specification.html#agency_txt___Field_Definitions).

| **Field** | **Detail** |
|:----------|:-----------|
| Agency ID |  |
| Agency Name | Name in multiple language. Each language name should be separated by "|". |
| URL |  |
| Timezone |  |
| Language |  |
| Phone |  |

**Example**
| Agency ID | Agency Name | URL | Timezone | Language | Phone |
|:----------|:------------|:----|:---------|:---------|:------|
| MTR | Mass Transit Railway (MTR)|港鐵公司|港铁公司 | http://www.mtr.com.hk/eng/homepage/cust_index.html | Asia/Hong\_Kong | zh | 852-28818888 |

---

# Stop #

You may also refer [GTFS Stop model](http://code.google.com/transit/spec/transit_feed_specification.html#stops_txt___Field_Definitions).

| **Field** | **Detail** |
|:----------|:-----------|
| Stop ID |  |
| Agency ID | The ID of the agency that manage the stop. |
| Stop Code | Optional. This field contains short text or a number that uniquely identifies the stop for passengers.<br /> For details, read GTFS definition. |

| Stop Name | Name in multiple language. Each language name should be separated by "|". |
| Description | Multiple language description. Each language name should be separated by "|". |
| Address | Multiple language address. Each language name should be separated by "|". |
| Lat |  |
| Lng |  |
| Zone ID | Leave blank for fare rules. |
| URL | Optional. |
| Location Type | 0 or blank - Stop. A location where passengers board or disembark from a transit vehicle.<br /> 1 - Station. A physical structure or area that contains one or more stop. |
| Parent station | The ID of parent station. |

**Example**
| Stop ID | Agency ID | Stop Code | Stop Name | Description | Address | Lat | Lng | Zone id | URL | Location Type | Parent Station |
|:--------|:----------|:----------|:----------|:------------|:--------|:----|:----|:--------|:----|:--------------|:---------------|
| MTR\_Admiralty | MTR	|  | MTR Admiralty Station|港鐵金鐘站|港铁金钟站 | MTR Admiralty Station|港鐵金鐘站|港铁金钟站 |  | 22.2791 | 114.1649 |  | http://www.mtr.com.hk | 1 |  |
| MTR\_AdmiraltyA | MTR |  | MTR Admiralty Station - A|港鐵金鐘站 - A|港铁金钟站 - A | MTR Admiralty Station - A|港鐵金鐘站 - A|港铁金钟站 - A |  | 23 | 123 |  |  | 0 | MTR\_Admiralty |
| MTR\_AdmiraltyB | MTR |  | MTR Admiralty Station - B|港鐵金鐘站 - B|港铁金钟站 - B |	MTR Admiralty Station - B|港鐵金鐘站 - B|港铁金钟站 - B |  | 23 | 16 |  |  | 0 | MTR\_Admiralty |

---

# Route #

You may also refer [GTFS Route model](http://code.google.com/transit/spec/transit_feed_specification.html#routes_txt___Field_Definitions).

| **Field** | **Detail** |
|:----------|:-----------|
| Route ID |  |
| Agency ID | The ID of the agency that manage the route. |
| Route Short Name |  |
| Route Long Name | Long name with multiple language. Each language name should be separated by "|". |
| Route Description | Description with multiple language. Each language name should be separated by "|". |
| Route Type | This field describes the type of transportation used on a route. For valid values, read GTFS definition. |
| Route Url | Optional. |
| Route Color | Optional. 32bit Hex. |
| Route Text Color | Optional. 32bit Hex. |

**Example**
| Route ID | Agency ID | Route Short Name |	Route Long Name | Route Description | Route Type | Route Url | Route Color | Route Text Color |
|:---------|:----------|:-----------------|:----------------|:------------------|:-----------|:----------|:------------|:-----------------|
| MTR\_East\_Rail\_Line | MTR | ERL | MTR East Rail Line|港鐵東鐵線|港铁东铁线 |  | 2 |  | FFFFFF | 0 |
| KMB\_49X | KMB | 49X | 49X|49X|49X |  | 3 |  |  |  |

---

# Trip #

You may also refer [GTFS Trip model](http://code.google.com/transit/spec/transit_feed_specification.html#trips_txt___Field_Definitions) but not 100% compatible.

| **Field** | **Detail** |
|:----------|:-----------|
| Route ID | Route of the Trip |
| Service ID |  |
| Trip ID |  |
| Trip Headsign | Multi language trip's headsign. Each language name should be separated by "|". |
| Trip Short Name |  |
| Direction ID | Optional. This field contains a binary value that indicates the direction of travel for a trip.<br />0 - travel in one direction (e.g. outbound travel)<br /> 1 - travel in the opposite direction (e.g. inbound travel) |
| Block ID |  |
| Shape ID |  |
| Stops | A list of Stops' ID that are forming the trip. |
| Arrival Time List | A list of arrival time for stops in the trip. |

**Example**
| Route ID | Service ID | Trip ID | Trip Headsign | Trip Short Name | Direction ID | Block ID | Shape ID | Stops | Arrival Time List |
|:---------|:-----------|:--------|:--------------|:----------------|:-------------|:---------|:---------|:------|:------------------|
| MTR\_East\_Rail\_Line |  | MTR\_East\_Rail\_Line\_To\_Lo\_Wu | Lo Wu|羅湖|罗湖 |  | 0 |  |  | MTR\_East\_Tsim\_Sha\_Tsui,MTR\_Sha\_Tin,MTR\_Lo\_Wu	|  |
| MTR\_East\_Rail\_Line |  | MTR\_East\_Rail\_Line\_To\_East\_Tsim\_Sha\_Tsui | East Tsim Sha Tsui|尖東|尖东 |  | 1 |  |  | MTR\_Lo\_Wu,MTR\_Sha\_Tin,MTR\_East\_Tsim\_Sha\_Tsui |  |

---

# Calendar #

You may also refer [GTFS Calendar model](http://code.google.com/transit/spec/transit_feed_specification.html#calendar_txt___Field_Definitions) but not 100% compatible.

| **Field** | **Detail** |
|:----------|:-----------|
| Service ID |  |
| Monday |  |
| Tuesday |  |
| Wednesday |  |
| Thursday |  |
| Friday |  |
| Saturday |  |
| Sunday |  |
| Holiday |  |
| Special | Only work in special day. |
| Special Remark | Remark of the special service in multiple language. Each language name should be separated by "|". |

**Example**
| Service ID | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday | Sunday | Holiday | Special | Special Remark |
|:-----------|:-------|:--------|:----------|:---------|:-------|:---------|:-------|:--------|:--------|:---------------|
| KMB\_49X | 05:30 - 24:20 | 05:30 - 24:20 | 05:30 - 24:20 | 05:30 - 24:20 | 05:30 - 24:20 | 05:30 - 24:20 | 05:30 - 24:20 | 05:30 - 24:20 |  |  |
| MTR\_East\_Rail\_Line\_To\_Lo\_Wu | 05:30 - 23:30 | 05:30 - 23:30 | 05:30 - 23:30 | 05:30 - 23:30 | 05:30 - 23:30 | 05:30 - 23:30 | 05:30 - 23:30 | 05:30 - 23:30 |  |  |
| MTR\_East\_Rail\_Line\_To\_Lo\_Wu\_W\_Racecourse |  |  |  |  |  |  |  |  | 08:00-08:30,18:00-18:30 | |賽馬日特別車| |

---

# Shape #

You may also refer [GTFS Shape model](http://code.google.com/transit/spec/transit_feed_specification.html#shapes_txt___Field_Definitions).

| **Field** | **Detail** |
|:----------|:-----------|
| Shape ID |  |
| Color |  |
| Type | 0 = polyline , 1 = polygon |
| Points | a list of lat,lng points |

**Example**
| Shape ID | Color | Type | Points |
|:---------|:------|:-----|:-------|
| mtr\_east\_rail\_line |  | 1 | 22.417462,114.213172,22.417001,114.212935,22.416242,114.212267,.... |
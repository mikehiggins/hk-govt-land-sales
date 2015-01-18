# Hong Kong Government Land Sales
This dataset contains information on Hong Kong Government land sales since 1985. The data is compiled from government sources
including the Lands Department at [http://www.landsd.gov.hk/en/landsale/index.htm](http://www.landsd.gov.hk/en/landsale/index.htm)

## Data format
The dataset is in JSON format and the file structure conforms to the Data Package format detailed at [http://dataprotocols.org/data-packages/](http://dataprotocols.org/data-packages/)

I am happy to accept pull requests for additional data or errors/typos. Particular interest on any information on identity of
purchaser for the `purchaser` field.

### Schema
Below represents a typical object in the dataset

```
{
    "date": "2006-11-28",
    "disposal_type": "AUC",
    "premium": "1940000000",
    "purchaser": null,
    "location": [
      {
        "lot_no": "NKIL 6374",
        "address": "1 BROADCAST DRIVE, KOWLOON TONG, KOWLOON",
        "user": "R2",
        "area_sqm": "6088.00"
      }
    ]
},
```

### Fields

The fields included in the dataset are explained below

**`date`** - _The date the auction or tender took place_

_string_ - formatted as a date in the form YYYY-MM-DD. In some cases, the auction or tender was withdrawn and so instead of
a valid date string, the field contains information on the withdrawal or tender cancellation.

**`disposal_type`** - _The method of disposal of the property_

_string_ - Letter A/B Tender is an interesting historical peculiarity - well worth reading
up on the history of these. See table below for meaning of abbrevations

| Abbreviation  | Meaning 			|
| ------------- | ----------------- |
| AUC 			| Auction 			|
| LAB 			| Letter A/B Tender |
| TEN 			| Tender 			|


**`premium`** - _Land premium paid or auction price for the land_

_string_ - Currency is Hong Kong Dollars (HKD)

**`purchaser`** - _Legal entity of purchaser or winning bidder/tenderer_

_string_ - This field is currently null as the identity of the purchaser is not revealed in the Lands Department records.
The information is available through the Government Gazette and I hope to add in the purchaser identity in due course.

**`location`**

An array of location objects as some land sales may include multiple lots or parcels of land. These multiple parcels are part of 
the same transaction and only the total premium value is provided.

**`location[lot_no]`**

_string_ - The lot number of the land.

**`location[address]`**

_string_ - The description of the location of the lot or land. In most cases this would be a street address.

**`location[user]`**

_string_ - The permitted use of the land. Please see below table for explanation of the abbreviations.

| Abbreviation  | Meaning 			|
| ------------- | ----------------- |
|	C			|	COMMERCIAL
|	C / MCP		|	COMMERCIAL / MULTI-STOREY CAR PARK
|	C / OU		|	COMMERCIAL / OTHER USES
|	C / R		|	COMMERCIAL / RESIDENTIAL
|	DGG			|	DANGEROUS GOODS GODOWN
|	G			|	GODOWN
|	HTL			|	HOTEL
|	I			|	INDUSTRIAL
|	I / G		|	INDUSTRIAL / GODOWN
|	IO			|	INDUSTRIAL OFFICE
|	MCP			|	MULTI-STOREY CAR PARK
|	NR			|	NON-RESIDENTIAL
|	OU			|	OTHER USES
|	PFS			|	PETROL FILLING STATION
|	PSPS		|	PRIVATE SECTOR PARTICIPATION SCHEME
|	R1			|	RESIDENTIAL R1
|	R2			|	RESIDENTIAL R2
|	R3			|	RESIDENTIAL R3
|	R4			|	RESIDENTIAL R4
|	V			|	VILLAGE TYPE DEVELOPMENT

**`location[area_sqm]`**

_string_ - The are of the parcel of land, in square metres and to two decimal places.

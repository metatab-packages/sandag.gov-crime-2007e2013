Processed crime incidents, based on data supplied by SANDAG.

Important:

  * See Caveats for limitations and warnings regarding this data. 
  * Use of this data is subject to multiple terms and conditions. See Terms for details. 

This dataset includes geocoded crime incidents from 1 Jan 2007 to 31 March 2013 that were returned by SANDAG for Public Records request 12-075. 


Asr\_zone Codes
===============

The integer values in the asr\_zone field are taken directly from the [SANGIS parcel data](http://rdw.sandag.org/file_store/Parcel/Parcels.pdf). These values are: 

	╔════╦═════════════════════════════════╗
	║ -1 ║ Unset                           ║
	║  0 ║ Unzoned                         ║
	║  1 ║ Single family residential (R-1) ║
	║  2 ║ Minor multiple (R-2)            ║
	║  3 ║ Restricted multiple (R-3)       ║
	║  4 ║ Multiple residential (R-4)      ║
	║  5 ║ Restricted commercial           ║
	║  6 ║ Commercial                      ║
	║  7 ║ Industrial (M zone)             ║
	║  8 ║ Agricultural                    ║
	║  9 ║ Special and/or misc.            ║
	╚════╩═════════════════════════════════╝				



Addresses and Geocoding
=======================
SANDAG returns the position of incidents as a block address, and occasionally as an intersection. Block addresses are the original address of the incident, with the last two digits set to '00'. 

Before geocoding, all of the original block addresses are normalized to be more consistent and to remove different versions of the same address. There are a few transformations performed on the address, including:

  * Converting street types synonyms like 'Avenue', 'Avenu' and 'ave.' to standard abbreviations like 'ave.'
  * Converting street directions ( 'West main Street' ) to abbreviations like 'W Main st'

Many geocoders are designed to work with mailable addresses, and block addresses are not real postal addresses. This data is geocoded with custom code that uses the SANGIS streets database, matching the block addresses to a street segment. This produces more sensible results, because the crime is attributed to an entire block, rather than to an arbitrary point on the block. However, with the crime is represented as a point, it will appear at the location of the center of the street segment, usually in the middle of the block. 

This means that all of the incidents on a block will appear at a single location. In most GIS programs, it is difficult to see that there are actually many points in one place. Be aware that each point you see may actually be dozens of incidents. 

The files that SANDAG returned included 1,008,524 incident records, and 953,824 records were geocoded (95%). The 'gctype' field has a value of NONE when the  record was not geocoded, and any field that depends on a locations, such as x, y, lon, lat, segment_id, community, and others, will have default values. 

Caveats
=======

As with most crime data, there are many issues, limitations and problems that users must be aware of to avoid making incorrect conclusions. 

*Crime incident data is inherently problematic.* Crime incident reports are collected by busy officers in stressful situations who are trying to describe complex situations with rigid categories. Virtually every point of the data collection process has multiple opportunities for errors and few opportunities for correction after the fact. Analysts must consider the difficulties of collecting crime data when assessing the validity of any conclusions. 

*Data is collected by 19 different agencies.* While the data is all sourced from SANDAG, it originates with 19 different police departments. These departments may have different policies that can result in different categorizations for the same crime, and they may have different emphases on  which crimes they pursue. 

*Many incidents at a single point.* Because all of the crimes on a block are geocoded to the middle of the block, many incidents will appear as a single point. 

*5% of crimes are not geocoded*. GIS users should consider that about 5% of the incidents were not properly geocoded, and are not included in the shapefiles. These crimes appear in the CSV files, and can be included in time series analysis, but they will not be available for spatial analysis. 

*Time and dates are often unreliable* Time and dates for many incidents are unreliable, with times being more unreliable than dates. 

  * Property crimes that occur while the owner is gone may be recorded as the time a responsible person left the property, arrived at the property to discover the crime, or the average between the two. There is no information available to select among these possibilities, so these incidents have very unreliable times. 

  * Because the time is unreliable, so is the date, for crimes that occurred at night. 

  * Times may have not been recorded in the original report. These times may be entered as midnight, or as another time. 


*Multiple crime incidents may not have all crimes recorded.* If a single person is charged with multiple violations for a single arrest, departments may enter only the most serious charge, the last charge, or all of the charges. There is no information to disambiguate these possibilities. 

*Locations may be unreliable*. Crimes that involve pursuits or violations committed and multiple locations may be recorded and any of many different locations.  When the location is ambiguous, tt is common for incidents to have the address recorded as the location where the arrested person was charged. Because of this, the highest crime block in San Diego is the downtown police station. Check high crime locations to ensure they are not police stations. 


Dataset Statistics
==================

Number of incidents by year:

	year        count     
	----------  ----------
	2007        186014    
	2008        178445    
	2009        163646    
	2010        160133    
	2011        147270    
	2012        141318    
	2013        31699

Crime types, from the "type" field, and the number of that type

	type                      count     
	------------------------  ----------
	DRUGS/ALCOHOL VIOLATIONS  230462    
	THEFT/LARCENY             138030    
	VEHICLE BREAK-IN/THEFT    123955    
	MOTOR VEHICLE THEFT       97498     
	BURGLARY                  91695     
	VANDALISM                 83912     
	ASSAULT                   70687     
	DUI                       58311     
	FRAUD                     55219     
	ROBBERY                   22685     
	SEX CRIMES                22281     
	WEAPONS                   11117     
	ARSON                     2145      
	HOMICIDE                  528

Incidents by city:

	name                       code        count     
	-------------------------  ----------  ----------
	San Diego                  SndSAN      401787    
	S.D. County                SndSDO      342282    
	Oceanside                  SndOCN      44022     
	Chula Vista                SndCHU      38387     
	Escondido                  SndESC      26079     
	Vista                      SndVIS      20044     
	Carlsbad                   SndCAR      18330     
	La Mesa                    SndLAM      17871     
	El Cajon                   SndELC      16548     
	National City              SndNAT      16509     
	San Marcos                 SndSNM      14230     
	Santee                     SndSNT      12328     
	Encinitas                  SndENC      12302     
	Poway                      SndPOW      8565      
	Imperial Beach             SndIMP      5442      
	Del Mar                    SndDEL      4876      
	Lemon Grove                SndLEM      4198      
	Coronado                   SndCOR      2466      
	Solana Beach               SndSOL      2259


Citation
=========

*Name of file*, extracted from clarinova.com-crime-incidents-casnd-7ba4. San Diego Regional Data Library. 2013-08-07 http://sandiegodata.org


Terms
=======================

This data is released under the following terms and conditions. 

Clarinova and the San Diego Regional Data Library disclaim any warranty for this data shall not be liable for loss or harm. [See the SDRDL Disclaimers and Limitations web page for complete details.](http://www.sandiegodata.org/get-data/data-disclaimers-and-limitations/)

This data is based on data from SANGIS, which is subject to its own terms and conditions. See the [SANGIS Legal Notice for details](http://www.sangis.org/Legal_Notice.htm). 

This data is based on data from SANDAG, which is subject to its own terms and conditions. See the [SANDAG Legal Notice for details](http://rdw.sandag.org/m). 





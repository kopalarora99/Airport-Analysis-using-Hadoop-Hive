# Airport-Analysis-using-Hadoop-Hive

Dataset Description

In this use case there are 3 data sets. Final_airlines, routes.dat, airports_mod.dat

AIRPORT TABLE

Airport ID	Unique OpenFlights identifier for this airport.

Name	Name of airport. May or may not contain the City name.

City	Main city served by airport. May be spelled differently from Name.

Country		Country or territory where airport is located.

IATA/FAA	3-letter FAA code, for airports located in Country "United States of America".

3-letter IATA code, for all other airports. Blank if not assigned.

ICAO	4-letter ICAO code. Blank if not assigned.

Latitude	Decimal degrees, usually to six significant digits. Negative is South, positive is North.

Longitude	Decimal degrees, usually to six significant digits. Negative is West, positive is East.

Altitude		In feet.

Timezone	Hours offset from UTC. Fractional hours are expressed as decimals, eg. India is 5.5.

DST	Daylight savings time. One of E (Europe), A (US/Canada), S (South America), O (Australia), Z (New Zealand), N (None) or U (Unknown). See also: Help: Time

Tz 	database time Timezone in "tz" (Olson) format, eg. "America/Los_Angeles". zone
 

Air Lines Data set:

It contains the following fields:

Airline Unique OpenFlights identifier for this airline. ID 

Name Name of the airline.

Alias	Alias of the airline. For example, All Nippon Airways is commonly known as "ANA". 

IATA	2-letter IATA code, if available.

ICAO	3-letter ICAO code, if available. 

Callsign Airline callsign.

Country Country or territory where airline is incorporated.




Routes Table

Airline	2-letter (IATA) or 3-letter (ICAO) code of the airline.

Airline ID	Unique OpenFlights identifier for airline (see Airline).

Source airport	3-letter (IATA) or 4-letter (ICAO) code of the source airport.

Source airport ID	Unique OpenFlights identifier for source airport (see Airport)

Destination airport	3-letter (IATA) or 4-letter (ICAO) code of the destination airport

Destination airport ID Unique OpenFlights identifier for destination airport (see Airport)

Codeshare	"Y" if this flight is a codeshare (that is, not operated by Airline, but another carrier),

empty otherwise.

Stops	Number of stops on this flight ("0" for direct)

Equipment	3-letter codes for plane type(s) generally used on this flight, separated by spaces

creating table airport for airports_mod.dat: 
create table airports (airport_id int,airport_name string,airport_city string,airport_country string,airport_faa string,airport_icao string,airport_lat double,airport_long double,airport_alt double,airport_timezone double,airport_dst string,airport_tz string) row format delimited fields terminated by ',';

creating table finalairlines for Final_airlines :
create table final_airlines (airlineID string,airline_name string, airline_alias string, airline_iata string, airline_icao string,callsign string,territory string, active string) row format delimited fields terminated by ',';

Creating table route for routes.dat: 
create table routes (route_iata string,route_airid int,route_source_iata string,route_source_airid int,route_des_iata string,route_des_airid int,route_codeshare string,route_stops int,route_equip string) row format delimited fields terminated by ',';

LOAD DATA LOCAL INPATH 'airports_mod.dat' OVERWRITE INTO TABLE airports;

LOAD DATA LOCAL INPATH 'Final_airlines' OVERWRITE INTO TABLE final_airlines;

LOAD DATA LOCAL INPATH 'routes.dat' INTO TABLE routes;

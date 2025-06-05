Introduction

This document contains a reference of the fields used by the KJAW API for searching and filtering API data sets. It is aimed at API consumers, and can be used as a supplement to the API User Guide.

Instructions on how to run API requests can be found in the Getting Started Guide. 


Result Set 1

These search fields are used with the function getOperation1.

	Name	Definition	Quick Search	Search Return	Search Filter	Format	Example
1	id	ID, search result ID	No	Yes	No	Numeric (16)	1111111111111111
2	type	type, data field type	No	Yes	Yes	Text, List Value	Data Type 1
3	name	name, data field name	Yes	Yes	Yes	Alphanumeric (250)	Data Type 1 name


 
Result Set 2

These search fields are used with the function getOperation2.

	Name	Definition	Quick Search	Search Return	Search Filter	Format	Example
1	id	ID, search result ID	No	Yes	Yes	Numeric (16)	1111111111111111
2	timestamp	timestamp	No	Yes	No	Date	YYYY-MM-ddTHH:mm:ss.ss±hh:mm





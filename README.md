![Mikes Data Work Git](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")

# Financial Data Filtering


## Contents

- [About Process](##About-Process)
- [Regular Expressions](#RegEx)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## About-Process

<p>Basic Regular Expression Script Logic to apply to modified .PDF exported text which is copied from edited .PDF to text editor.  In this example the text editor of choice is [Sublime Text 3]

Remember to always set your text editor to use Regular Expressions before proceeding.
Regular Expressions listed in order of execution.



---
## RegEx
```Python
### 1.
# REMOVE EXTRA 15-CHARACTER ID LINE (#)###############
#[0-9]{15}
# REPLACE WITH: 
<blank>'

### 2.
# REMOVE ALL EMPTY\BLANK LINES
^(?:[\t ]*(?:\r?\n|\r))+
# REPLACE WITH:
<blank>

### 3.
# ADD YEAR TO THE DATE: MM/DD(/YYYY)
([0-9]{2}/[0-9]{2}).*?
# REPLACE WITH:
$0/####

### 4.
# CONVERT DATE MM/DD/YYYY TO YYYY/MM/DD
([0-9]{2})/([0-9]{2})/([0-9]{4})
# REPLACE WITH:
$3/$1/$2,

### 5. 
# COMBINE 4 LINES
(?-s)^(.+)\R(.+)\R(.+)\R(.+)\R*
# REPLACE WITH:
\1, \2, \3, \4 \n

### 6.
# FIND [US] AND DELETE
 (US,\s{1})
# REPLACE WITH:
<blank>

### 7.
# REMOVE LINES WITH THE WORDS "ATM", "DEPOSIT" etc...
((^.*Deposit.*$)|(^.*ATM.*$)|(^.*Payroll.*$)|(^.*Transfer.*$)|(^.*Interest.*$)|(^.*Beginning.*$))
# REPLACE WITH:
<blank>

### 8.
# REMOVE ALL EMPTY\BLANK LINES
^(?:[\t ]*(?:\r?\n|\r))+
# REPLACE WITH:
<blank>


```

## Exported Sample Results 

| Date | Currency | Merchant | State | Cost | Balance |
|----------|--------------------------------------------|----------------------------------------|----|----------|----------| 
2012/09/29	|Visa Purchase	|Macy's 023 8000 McLean	|Va	|$20.71	|$398.77|
2012/09/29	|Visa Purchase	|Target T1416 Springfield |Va	|$94.30	|$304.47|
2012/09/30	|Visa Purchase	|JCPenny Store 1462 Springfield	|Va	|$63.00	|$241.47|
2012/09/30	|Visa Purchase	|Target T1416 Target T14 Springfield	|Va	|$9.23	|$232.24|
2012/10/01	|Visa Purchase	|Panera Bread#0118Alexandria	|Va	|$4.50	|$227.74|
2012/10/01	|Visa Purchase	|The Vitamin Shoppe 137 Springfield	|Va	|$40.92	|$186.82|
2012/10/02	|Visa Purchase	|Outback 4713 Springfield	|Va	|$52.20	|$134.62|
2012/10/03	|Visa Purchase	|Subway 0331Falls Church	|Va	|$9.29	|$125.33|
2012/10/03	|Visa Purchase	|Panera Bread#0118Alexandria	|Va	|$3.40	|$121.93|
2012/10/04	|Visa Purchase	|Subway 0331Falls Church	|Va	|$9.29	|$112.64|
2012/10/06	|Visa Purchase	|Shell Service Station S Alexandria	|Va	|$49.56	|$63.08|
2012/10/07	|Visa Purchase	|Subway 0001Arlington|Va	|$9.37	|$53.71|
2012/10/08	|Visa Purchase	|Wegmans 14801 Dining WA Woodbridge	|Va	|$8.87	|$44.84|
2012/10/11	|Visa Purchase	|Subway 0331Falls Church	|Va	|$9.56	|$35.28|
2012/10/11	|Visa Purchase	|Moe's SW Grill 244Falls Church|Va	|$9.74	|$25.54|
2012/10/11	|Visa Purchase	|Moe's SW Grill 244Falls Church|Va	|$1.88	|$23.66|
2012/10/11	|Visa Purchase	|Panera Bread#0118Alexandria	|Va	|$3.45	|$20.21|
2012/10/12	|Visa Purchase	|Harris Teeter #027Falls Church	|Va	|$7.56	|$12.65|
2012/10/13	|Visa Purchase	|Subway 0001Arlington|Va	|$9.37	|$3.28|
2012/10/20	|Visa Purchase	|The Home Depot 4640 Alexandria	|Va	|$12.54	|$164.93|
2012/10/21	|Visa Purchase	|Best Buy #283 Falls Church	|Va	|$31.49	|$133.44|
2012/10/21	|Visa Purchase	|Best Buy #283 Falls Church	|Va	|$15.74	|$117.70|
2012/10/21	|Visa Purchase	|Moe's SW Grill 244Falls Church|Va	|$10.46	|$107.24|
2012/10/21	|Visa Purchase	|Panera Bread#0118Alexandria	|Va	|$3.45	|$103.79|
2012/10/21	|Visa Purchase	|Best Buy #283 Falls Church	|Va	|$28.34	|$75.45|
2012/10/22	|Visa Purchase	|Moe's SW Grill 244Falls Church|Va	|$10.47	|$64.98|
2012/10/22	|Visa Purchase	|Panera Bread#0118Alexandria	|Va	|$4.45	|$60.53|
2012/10/23	|Visa Purchase	|Harris Teeter 6351 Colu Falls Church	|Va	|$13.17	|$47.36|
2012/10/24	|Visa Purchase	|Subway 0331Falls Church	|Va	|$4.46	|$42.90|
2012/10/24	|Visa Purchase	|Panera Bread#0118Alexandria	|Va	|$2.21	|$40.69|
2012/10/25	|Visa Purchase	|Subway 0001Arlington|Va	|$9.37	|$31.32|
2012/10/25	|Visa Purchase	|Moe's SW Grill 244Falls Church|Va	|$9.01	|$22.31|
2012/10/25	|Visa Purchase	|Panera Bread#0118Alexandria	|Va	|$4.45	|$17.86|
2012/10/26	|Visa Purchase	|Moe's SW Grill 244Falls Church|Va	|$9.01	|$8.85|
2012/10/26	|Visa Purchase	|Panera Bread#989 Arlington|Va	|$5.74	|$3.11|

[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)


## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")


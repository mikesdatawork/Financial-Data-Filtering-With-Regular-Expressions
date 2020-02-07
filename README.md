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
#REMOVE EXTRA 15-CHARACTER ID LINE (#)###############
#[0-9]{15}
#REPLACE WITH: 
<blank>'

### 2.
#REMOVE ALL EMPTY\BLANK LINES
^(?:[\t ]*(?:\r?\n|\r))+
#REPLACE WITH:
<blank>

### 3.
#ADD YEAR TO THE DATE: MM/DD(/YYYY)
([0-9]{2}/[0-9]{2}).*?
#REPLACE WITH:
$0/####

### 4.
#CONVERT DATE MM/DD/YYYY TO YYYY/MM/DD
([0-9]{2})/([0-9]{2})/([0-9]{4})
#REPLACE WITH:
$3/$1/$2,

### 5. 
#COMBINE 4 LINES
(?-s)^(.+)\R(.+)\R(.+)\R(.+)\R*
#REPLACE WITH:
\1, \2, \3, \4 \n

### 6.
#FIND [US] AND DELETE
 (US,\s{1})
REPLACE WITH:
<blank>

### 7.
#REMOVE LINES WITH THE WORDS "ATM", "DEPOSIT" etc...
((^.*Deposit.*$)|(^.*ATM.*$)|(^.*Payroll.*$)|(^.*Transfer.*$)|(^.*Interest.*$)|(^.*Beginning.*$))
#REPLACE WITH:
<blank>

### 8.
#REMOVE ALL EMPTY\BLANK LINES
^(?:[\t ]*(?:\r?\n|\r))+
#REPLACE WITH:
<blank>


```



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


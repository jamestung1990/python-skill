Converting string into datatime [1]
Remember this and you didn't need to get confused in datetime conversion again.

String to datetime object = strptime

datetime object to other formats = strftime

Jun 1 2005  1:33PM

is equals to

%b %d %Y %I:%M%p

%b Month as locale’s abbreviated name(Jun)

%d Day of the month as a zero-padded decimal number(1)

%Y Year with century as a decimal number(2015)

%I Hour (12-hour clock) as a zero-padded decimal number(01)

%M Minute as a zero-padded decimal number(33)

%p Locale’s equivalent of either AM or PM(PM)

so you need strptime i-e converting string to

>>> dates = []
>>> dates.append('Jun 1 2005  1:33PM')
>>> dates.append('Aug 28 1999 12:00AM')
>>> from datetime import datetime
>>> for d in dates:
...     date = datetime.strptime(d, '%b %d %Y %I:%M%p')
...     print type(date)
...     print date
... 
Output

<type 'datetime.datetime'>
2005-06-01 13:33:00
<type 'datetime.datetime'>
1999-08-28 00:00:00
What if you have different format of dates you can use panda or dateutil.parse

>>> import dateutil
>>> dates = []
>>> dates.append('12 1 2017')
>>> dates.append('1 1 2017')
>>> dates.append('1 12 2017')
>>> dates.append('June 1 2017 1:30:00AM')
>>> [parser.parse(x) for x in dates]
OutPut

[datetime.datetime(2017, 12, 1, 0, 0), datetime.datetime(2017, 1, 1, 0, 0), datetime.datetime(2017, 1, 12, 0, 0), datetime.datetime(2017, 6, 1, 1, 30)]

[1]: https://stackoverflow.com/questions/466345/converting-string-into-datetime "converting-string-into-datetime"
==================================================================================================================================================================
datetime.strptime is the main routine for parsing strings into datetimes. It can handle all sorts of formats, with the format determined by a format string you give it:

from datetime import datetime

datetime_object = datetime.strptime('Jun 1 2005  1:33PM', '%b %d %Y %I:%M%p')
The resulting datetime object is timezone-naive.

Links:

Python documentation for strptime: Python 2, Python 3

Python documentation for strptime/strftime format strings: Python 2, Python 3

strftime.org is also a really nice reference for strftime

Notes:

strptime = "string parse time"
strftime = "string format time"
Pronounce it out loud today & you won't have to search for it again in 6 months.

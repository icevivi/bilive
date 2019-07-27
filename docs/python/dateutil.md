dateutil
=========

License: Apache Software License, BSD License (Dual License)

version: 2.8.0

The documentation is hosted at: https://dateutil.readthedocs.io/en/stable/

Code
The code and issue tracker are hosted on Github: https://github.com/dateutil/dateutil/

Features
Computing of relative deltas (next month, next year, next monday, last week of month, etc);
Computing of relative deltas between two given date and/or datetime objects;
Computing of dates based on very flexible recurrence rules, using a superset of the iCalendar specification. Parsing of RFC strings is supported as well.
Generic parsing of dates in almost any string format;
Timezone (tzinfo) implementations for tzfile(5) format files (/etc/localtime, /usr/share/zoneinfo, etc), TZ environment string (in all known formats), iCalendar format files, given ranges (with help from relative deltas), local machine timezone, fixed offset timezone, UTC timezone, and Windows registry-based time zones.
Internal up-to-date world timezone information based on Olson’s database.
Computing of Easter Sunday dates for any given year, using Western, Orthodox or Julian algorithms;
A comprehensive test suite.
Quick example
Here’s a snapshot, just to give an idea about the power of the package. For more examples, look at the documentation.

Suppose you want to know how much time is left, in years/months/days/etc, before the next easter happening on a year with a Friday 13th in August, and you want to get today’s date out of the “date” unix system command. Here is the code:

>>> from dateutil.relativedelta import *
>>> from dateutil.easter import *
>>> from dateutil.rrule import *
>>> from dateutil.parser import *
>>> from datetime import *
>>> now = parse("Sat Oct 11 17:13:46 UTC 2003")
>>> today = now.date()
>>> year = rrule(YEARLY,dtstart=now,bymonth=8,bymonthday=13,byweekday=FR)[0].year
>>> rdelta = relativedelta(easter(year), today)
>>> print("Today is: %s" % today)
Today is: 2003-10-11
>>> print("Year with next Aug 13th on a Friday is: %s" % year)
Year with next Aug 13th on a Friday is: 2004
>>> print("How far is the Easter of that year: %s" % rdelta)
How far is the Easter of that year: relativedelta(months=+6)
>>> print("And the Easter of that year is: %s" % (today+rdelta))
And the Easter of that year is: 2004-04-11
Being exactly 6 months ahead was really a coincidence :)

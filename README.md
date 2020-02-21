# using-datetime-in-python
Stackoverflow is just full of nonesense, so its better to create this one based on my experience
This is based on python3 by the way.

### Datetime with timezone?
Python's `datetime` library is quite good when dealing with date and time in general. Its not comparable to the `time` library however because that is supposed to be `unix` or `windows` process time operations.
Using `datetime` is relatively straightforward:

```python3
#!/usr/bin/env python3

import datetime
datetime.datetime.now() # Outputs non-tz aware datetime but local clock based
datetime.datetime.now().astimezone() # Outputs tz aware datetime in local clock and local timezone
datetime.datetime.now(datetime.timezone.utc) # Converts tz aware datetime in UTC clock time and assign UTC timezone

dt = datetime.datetime.now()
dt = dt.replace(tzinfo=datetime.timezone.utc) # Replace (not convert) the timezone of line 13 with UTC (mucks up the time)
dt - datetime.datetime.now(datetime.timezone.utc) # Gives you the difference between UTC and Your time zone ;)

dt - datetime.datetime.now() # Throws an error saying "TypeError: can't subtract offset-naive and offset-aware datetimes"
```

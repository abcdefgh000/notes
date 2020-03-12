# Get the last previous specific weekday/weekend of a week

```py
import datetime

def get_last_weekday(offset):
    today = datetime.date.today()
    # Default index is: Mon = 0, Tue = 1, Wed = 2... Sun = 6.
    # After the following conversion, it will be changed to:
    # Sun = 0, Mon = 1, Tue = 2... Sat = 6.
    index = (today.weekday() + 1) % 7
    # When offset = 0, it will return the last previous Sunday,
    # when offset = 1, it will return the last previous Saturday, etc.
    # Return value is of datetime type.
    return today - datetime.timedelta(index + offset)

def get_last_sunday():
    return get_last_weekday(0)

def get_last_saturday():
    return get_last_weekday(1)

def get_last_monday():
    return get_last_weekday(-1)

```

## Construct civil day object
```cpp
absl::CivilDay some_day = absl::CivilDay(2000, 1, 1);
```

## Convert civil day object to "YYYY-MM-DD" string
```cpp
absl::CivilDay some_day = absl::CivilDay(2000, 1, 1);
const std::string day_string = absl::FormatCivilTime(some_day);
```

## Diff number of days
```cpp
absl::CivilDay day1 = absl::CivilDay(2000, 1, 1);
absl::CivilDay day2 = absl::CivilDay(2002, 1, 1);
int diff_num_days = day1 - day2;
```

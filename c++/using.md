# usages of `using`

## replacing the keyword `typedef`

### Everything that `typedef` can do, `using` can do in a more friendly/comfortable style/syntax (all the following pairs do the same thing within each pair):

```cpp
using StudentId = int32_t;
typedef int32_t StudentId;
```

```cpp
using NameIdMap = std::map<std::string, int32_t>;
typedef std::map<std::string, int32_t> NameIdMap;
```

```cpp
using MyFunction = void (*)(int, bool);
typedef void (*MyFunction)(int, bool);
```

### `using` can define types that contain templates, `typedef` cannot do so

```cpp
template <typename T>
using LocationTemplateMap = std::map<std::string, T>;

LocationTemplateMap<double> locations_and_temperatures;
locations_and_temperatures["Boston"] = 31.05;  // Fahrenheit
```

So `typedef` should not be used anymore.


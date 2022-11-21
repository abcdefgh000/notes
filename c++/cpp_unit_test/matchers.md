# Matchers

## Compare `std::pair`
```cpp
std::pair<std::string, std::string> ReturnSomeStringPair() {
  return {"aaa", "bbb"};
}

TEST(ReturnSomeStringPairTest, Works) {
  EXPECT_THAT(ReturnSomeStringPair(), Pair(Eq("aaa"), Eq("bbb")));
}
```

## Compare 2 protos
### When all fields in the 2 protos must match
```cpp
EXPECT_THAT(proto1, EqualsProto(proto2));
```

### When all fields exist in proto2 must match those in proto1
The fields that exist in proto1 but not in proto2 are ignored!!!
```cpp
EXPECT_THAT(proto1, Partially(EqualsProto(proto2)));
```
注意！
* `EqualsProto` 是在 `Partially()` 里面的

## Compare 2 vectors of protos
### All match
```cpp
EXPECT_THAT(proto_vector1, Pointwise(EqualsProto(), proto_vector2));
```

For example:
```cpp
EXPECT_THAT(MyFunction(some_params), 
            IsOkAndHolds(UnorderedPointwise(EqualsProto(),
                                            {expected_proto1, expected_proto2, expected_proto3})));
```

注意！
* `proto_vector2` 是在 `EqualsProto()` 外面的

### Partially match
```cpp
EXPECT_THAT(proto_vector1, Pointwise(Partially(EqualsProto()), summaries));
```
注意！
* `proto_vector2` 是在 `EqualsProto()` 外面的
* `EqualsProto` 是在 `Partially()` 里面的

## Compare a repeated field (of protos) against some specific protos
```cpp
EXPECT_THAT(some_proto.some_repeated_field(), 
            UnorderedPointwise(EqualsProto(), 
                               {expected_proto1, expected_proto2, expected_proto3)));
```

OR: the following syntax means the same thing:

```cpp
EXPECT_THAT(some_proto.some_repeated_field(), 
            UnorderedElementsAre(EqualsProto(expected_proto1),
                                 EqualsProto(expected_proto2),
                                 EqualsProto(expected_proto3)));
```


## Check a `StatusOr<container>` returns ok status and the elements of the container are certain values

```cpp
  EXPECT_THAT(
      vector_of_filenames,
      IsOkAndHolds(ElementsAre("filename1, filename2")));
```

## Check if a string element in a container ends with a certain substring

```cpp
  EXPECT_THAT(
      vector_of_filenames,
      IsOkAndHolds(ElementsAre(EndsWith("_test.cc"))));
```

## Check a container is empty

```cpp
  EXPECT_THAT(
      vector_of_filenames,
      IsOkAndHolds(IsEmpty()));
```

## Check a container's size

```cpp
  EXPECT_THAT(
      vector_of_filenames,
      IsOkAndHolds(SizeIs(3))));
```


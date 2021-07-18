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
注意！
* `proto_vector2` 是在 `EqualsProto()` 外面的

### Partially match
```cpp
EXPECT_THAT(proto_vector1, Pointwise(Partially(EqualsProto()), summaries));
```
注意！
* `proto_vector2` 是在 `EqualsProto()` 外面的
* `EqualsProto` 是在 `Partially()` 里面的

# Matchers

## 如何 比较 std::pair
```cpp
std::pair<std::string, std::string> ReturnSomeStringPair() {
  return {"aaa", "bbb"};
}

TEST(ReturnSomeStringPairTest, Works) {
  EXPECT_THAT(ReturnSomeStringPair(), Pair(Eq("aaa"), Eq("bbb")));
}
```

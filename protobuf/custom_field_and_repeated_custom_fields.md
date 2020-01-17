# Custom Field and repeated Custom Fields

## Protobuf
```protobuf
// fruit_and_fruit_basket.proto

syntax = "proto3";

message FruitBasket {
    Fruit fruit = 1;
    repeated Fruit fruit_pack = 2;
}

message Fruit {
    string name = 1;
    int price = 2;
}
```

## Python
```py
import fruit_and_fruit_basket_pb2

fruit_basket = fruit_and_fruit_basket_pb2.FruitBasket()

# add
```

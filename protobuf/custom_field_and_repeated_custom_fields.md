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
    float price = 2;
}
```

## Python
```py
import fruit_and_fruit_basket_pb2

fruit_basket = fruit_and_fruit_basket_pb2.FruitBasket()

# add a Fruit to FruitBasket
fruit_basket.fruit.name = "Banana"
fruit_basket.fruit.price = 1.5

# add repeated Fruit objects to FruitBasket
first_fruit = fruit_basket.fruit_pack.add()  # <== this is a very counter-intuitive way!
first_fruit.name = "Red Apple"
first_fruit.price = 2
# add another one
second_fruit = fruit_basket.fruit_pack.add()
second_fruit.name = "Green Apple"
second_fruit.price = 1.8
# add in another way
fruit_basket.fruit_pack.add(name="Yellow Apple", price=2.1)
# yet another way
fourth_fruit = fruit_and_fruit_basket_pb2.Fruit()
fourth_fruit.name = "Orange Apple"
fourth_fruit.price = 0.1
fruit_basket.fruit_pack.extend([fourth_fruit]) # <== this is a deep copy of fourth_fruit
```

## C++
```cpp
FruitBascket fruit_basket;
for (Fruit fruit : fruit_list) {
  fruit_basket.add_fruit_pack(fruit);
}
```

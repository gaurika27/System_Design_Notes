# What is an Enum?
- An enum is a special data type that defines a collection of constant values under a single name. Unlike primitive constants or string literals, enums are type-safe, you can’t assign just any value to a variable declared as an enum type.

- Enums are perfect when a variable can only take one out of a small set of predefined values.

- Enums (short for enumerations) are a powerful yet underappreciated feature in object-oriented design. They allow you to define a fixed set of named constants that improve clarity, type safety, and maintainability in your system.

- Used correctly, enums can make your code more expressive, self-documenting, and resilient to errors.

## Example Enums
 - States (e.g., ```PENDING```, ```IN_PROGRESS```, ```COMPLETED```)
 - Roles (e.g., ```ADMIN```, ```CUSTOMER```, ```DRIVER```)
 - Vehicle Types (e.g., ```CAR```, ```BIKE```, ```TRUCK```)
 - Directions (e.g., ```NORTH```, ```SOUTH```, ```EAST```, ```WEST```)

Enums help avoid magic strings or numbers, improve readability, enable compiler checks, IDE auto-completion and reduce bugs caused by invalid values.

## Examples
### Simple Enum
Enum representing status of an order in an e-commerce application.
```cpp
enum class OrderStatus {
    PLACED,
    CONFIRMED,
    SHIPPED,
    DELIVERED,
    CANCELLED
};
```
This defines a clear set of valid statuses for an order.

Using it in code:
```cpp
OrderStatus status = OrderStatus::SHIPPED;

if (status == OrderStatus::SHIPPED) {
    cout << "Your package is on the way!" << endl;
}
```

### Enums with Properties and Methods
Enums can have additional data and even behavior. This makes them even more powerful.
#### Coin Enum with Denomination
```cpp
enum class Coin {
    PENNY,
    NICKEL,
    DIME,
    QUARTER
};

// Helper function to get coin value
int getCoinValue(Coin coin) {
    switch(coin) {
        case Coin::PENNY:   return 1;
        case Coin::NICKEL:  return 5;
        case Coin::DIME:    return 10;
        case Coin::QUARTER: return 25;
        default:            return 0;
    }
}
```
Usage:
```cpp
int total = getCoinValue(Coin::DIME) + getCoinValue(Coin::QUARTER); // 35
```
This is far more elegant and safe than using integers directly.

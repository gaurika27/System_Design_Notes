# Definition
A class is a blueprint or template. It defines the properties (attributes) and behaviors (methods) that the objects created from it will have.

## Quick meaning!
Think of a class as a recipe. It tells you what ingredients (fields) and instructions (methods) are needed, but it’s not the actual dish. You use the recipe to bake a cake (i.e., create an object).

## Key Characteristics
- It encapsulates data and behavior.
- Defines attributes as variables.
- Defines methods (functions inside a class) to operate on that data.

```
class Car {
private:
    // Attributes
    string brand;
    string model;
    int speed;

public:
    // Constructor
    Car(const string& brand, const string& model) 
        : brand(brand), model(model), speed(0) {
    }

    // Method to accelerate
    void accelerate(int increment) {
        speed += increment;
    }

    // Method to display info
    void displayStatus() const {
        cout << brand << " is running at " << speed << " km/h." << endl;
    }
};
```
This ```Car``` class defines what every car object should look like and what it can do.

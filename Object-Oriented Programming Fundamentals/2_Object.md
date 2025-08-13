# Definition
An object is an instance of a class. When you create an object, you are bringing the blueprint of the class into reality. It consists of state and behavior defined by the class, with each object holding its own copy of the data.

```cpp
int main() {
    // Creating objects of the Car class
    Car corolla("Toyota", "Corolla");
    Car mustang("Ford", "Mustang");

    corolla.accelerate(20);
    mustang.accelerate(40);

    // Displaying status of each car
    corolla.displayStatus();
    std::cout << "-----------------" << std::endl;
    mustang.displayStatus();

    return 0;
}
```

Here, ```corolla``` and ```mustang``` are objects of the ```Car``` class. They have their own ```brand``` , ```model``` , and ```speed``` fields and can use methods defined in the class.

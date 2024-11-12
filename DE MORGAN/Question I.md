
They gave me a piece of codevoid func(){ int arr[10];}They told me that this function is being called recursively infinite number of times and I have a memory of 2 Mega Bytes.
Then he asked me if this will give an error or it will keep on running infinite times or my system will crash. I was able to answer this question and the interviewer was also satisfied with it.


Here’s how you can explain the difference between Call by Value and Call by Reference along with examples:

Call by Value:

Definition: In Call by Value, the actual value of the argument is passed to the function. The function works with a copy of the value and any changes made to the parameter do not affect the original argument.

Behavior: Changes made to the parameter inside the function do not reflect in the original variable outside the function.

Use Case: This method is commonly used when you don't want to modify the original value in the calling function.


Example (Call by Value):

#include <iostream>
using namespace std;

void modifyValue(int num) {
    num = num + 10; // Modify the local copy of num
    cout << "Inside modifyValue: " << num << endl;
}

int main() {
    int x = 5;
    modifyValue(x);  // Passes a copy of x
    cout << "Inside main: " << x << endl;  // Original x remains unchanged
    return 0;
}

Output:

Inside modifyValue: 15
Inside main: 5

Explanation:

The value 5 is passed to the modifyValue function.

Inside the function, num is updated to 15, but this change is only on the copy, not on the original variable x.

The original value x remains unchanged in main.



Call by Reference:

Definition: In Call by Reference, instead of passing the actual value, the memory address (or reference) of the argument is passed to the function. The function operates on the original variable directly, meaning changes made to the parameter inside the function will affect the original variable.

Behavior: Any changes made to the parameter inside the function will directly modify the argument in the calling function.

Use Case: This method is used when you want to modify the actual value of the argument from within the function.


Example (Call by Reference):
```cpp
#include <iostream>
using namespace std;

void modifyValue(int &num) {
    num = num + 10; // Modify the actual value of num
    cout << "Inside modifyValue: " << num << endl;
}

int main() {
    int x = 5;
    modifyValue(x);  // Passes the reference (memory address) of x
    cout << "Inside main: " << x << endl;  // x is modified
    return 0;
}

```

Output:

Inside modifyValue: 15
Inside main: 15

Explanation:

The reference to the variable x is passed to modifyValue.

Inside the function, the value of num is modified, and since num refers to x directly, the change is reflected in the original variable x.

The value of x is updated to 15.



Key Differences:

This explanation should give you a clear distinction between the two and an idea of when to use each approach.

**He asked why had used MongoDB over SQL database**

**psuedo code for car**
Here's a C++ code that represents the basic operations of a car, which includes starting, stopping, driving, refueling/recharging, and checking the car’s status.

C++ Code for Car Operations
```cpp
#include <iostream>
using namespace std;

class Car {
private:
    int fuel_level;  // Fuel level in percentage (0-100)
    bool engine_status;  // Engine status (ON or OFF)
    int speed;  // Speed of the car
    int location;  // Location of the car (in kilometers)
    int battery_status;  // For electric car (0-100)

public:
    // Constructor to initialize car attributes
    Car() {
        fuel_level = 100;  // Initially, the fuel tank is full
        engine_status = false;  // Initially, the car is stopped
        speed = 0;
        location = 0;
        battery_status = 100;  // Electric car battery full initially
    }

    // Method to start the car
    void startCar() {
        if (!engine_status) {
            engine_status = true;
            cout << "Car is now running." << endl;
        } else {
            cout << "Car is already running." << endl;
        }
    }

    // Method to stop the car
    void stopCar() {
        if (engine_status) {
            engine_status = false;
            speed = 0;
            cout << "Car is stopped." << endl;
        } else {
            cout << "Car is already stopped." << endl;
        }
    }

    // Method to drive the car
    void driveCar(int distance) {
        if (engine_status && fuel_level > 0) {
            speed = 60;  // Assume constant speed of 60 km/h
            fuel_level -= distance / 10;  // Reduce fuel based on distance (simplified)
            location += distance;
            cout << "Driving for distance: " << distance << " km." << endl;
        } else {
            cout << "Unable to drive. Check if engine is ON and fuel level is sufficient." << endl;
        }
    }

    // Method to refuel or recharge (for electric car)
    void refuelOrRecharge(int amount) {
        if (fuel_level < 100) {
            fuel_level += amount;
            if (fuel_level > 100) fuel_level = 100;  // Cap fuel level at 100%
            cout << "Car refueled by: " << amount << "%" << endl;
        }
        else {
            battery_status += amount;  // Recharging electric car
            if (battery_status > 100) battery_status = 100;  // Cap battery level at 100%
            cout << "Car recharged by: " << amount << "%" << endl;
        }
    }

    // Method to get the current status of the car
    void getCarStatus() {
        cout << "Engine Status: " << (engine_status ? "ON" : "OFF") << endl;
        cout << "Fuel Level: " << fuel_level << "%" << endl;
        cout << "Speed: " << speed << " km/h" << endl;
        cout << "Location: " << location << " km" << endl;
        cout << "Battery Status: " << battery_status << "%" << endl;
    }
};

int main() {
    // Create a Car object
    Car myCar;

    // Perform various operations
    myCar.startCar();          // Start the car
    myCar.driveCar(50);        // Drive 50 kilometers
    myCar.getCarStatus();      // Get the current status of the car
    myCar.refuelOrRecharge(20); // Refuel or recharge the car
    myCar.stopCar();           // Stop the car
    myCar.getCarStatus();      // Check car status after stopping

    return 0;
}
```
Explanation of the Code:

1. Attributes:

fuel_level: Represents the fuel level (0-100%).

engine_status: A boolean indicating whether the car is running or stopped.

speed: The current speed of the car (in km/h).

location: The car’s current location in kilometers.

battery_status: For electric cars, this represents the battery level (0-100%).



2. Methods:

startCar(): Starts the engine if it is not already running.

stopCar(): Stops the engine and sets the speed to 0.

driveCar(int distance): Drives the car for a specified distance and decreases fuel accordingly.

refuelOrRecharge(int amount): Refuels a gasoline car or recharges an electric car by the specified amount.

getCarStatus(): Prints the current status of the car.




Usage:

The main() function demonstrates the process of starting, driving, checking the status, refueling/recharging, and stopping the car.

The fuel decreases as the car drives, and it can be refueled or recharged if necessary.


This code covers basic operations of a car and can be extended with more features like handling different car types, calculating fuel consumption more precisely, or adding more complex behavior.





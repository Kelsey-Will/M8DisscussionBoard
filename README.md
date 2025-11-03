# M8DisscussionBoard
#include <iostream>
using namespace std;

class Car {
public:
    string model;
    int speed;

    Car(string m, int s) {
        model = m;
        speed = s;
    }

    void displayInfo() {
        cout << "Model: " << model << ", Speed: " << speed << " mph" << endl;
    }
};

class Garage {
public:
    Car* carInGarage; // Pointer to a Car object

    void showCar() {
        // Error 1: Using uninitialized pointer (runtime crash)
        carInGarage->displayInfo();
    }

    int calculateAverageSpeed(int totalSpeed, int numCars) {
        // Error 2: Possible divide by zero
        return totalSpeed / numCars;
    }
};

int main() {
    Garage g;

    cout << "Showing car info..." << endl;
    g.showCar(); // Causes segmentation fault (carInGarage not initialized)

    cout << "Average speed: " << g.calculateAverageSpeed(120, 0) << endl; // Divide by zero
    return 0;
}
